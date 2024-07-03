# UML

## 编译内核

```shell
make defconfig ARCH=um SUBARCH=x86_64
make linux ARCH=um SUBARCH=x86_64 -j `nproc`
```

构建GDB脚本
```shell
make O=build menuconfig ARCH=um SUBARCH=x86_64
# Kernel hacking  --->
#  Compile-time checks and compiler options  --->
#   [*] Provide GDB scripts for kernel debugging
make O=build ARCH=um scripts_gdb
```

## 构建rootfs

采用alpine提供的脚本[alpinelinux/alpine-make-rootfs](https://github.com/alpinelinux/alpine-make-rootfs)

```shell
mkdir rootfs
fakeroot ./alpine-make-rootfs rootfs/
echo "LABEL=ALPINE_ROOT / auto defaults 1 1" >> rootfs/etc/fstab
```

## 设置网络

```shell
sudo ip tuntap add tap0 mode tap 
sudo ip link set tap0 up
sudo ip address add 192.168.100.100/24 dev tap0
```

## 启动

下载 init
```shell
wget -O rootfs/sbin/tini https://github.com/krallin/tini/releases/download/v0.19.0/tini-static
chmod +x rootfs/sbin/tini
```

rootfs/init.sh
```shell
#!/bin/sh

mount -t proc proc /proc
mount -t sysfs sys /sys

ip link set eth0 up
ip address add 192.168.100.101/24 dev eth0

export PS1='\[\033[01;32mUML:\w\033[00m \$ '
exec /sbin/tini /bin/sh +m
```


启动脚本 UML.sh
```shell
#!/bin/sh
./linux umid=uml0 hostname=uml1 eth0=tuntap,tap0 \
        root=/dev/root rootfstype=hostfs hostfs=./rootfs \
        rw mem=64M init=/init.sh quiet
stty sane ; echo
```

第一次启动的时候，相关的软链还没有，需要执行（仅第一次）
```shell
/bin/busybox --install
```

## GDB

创建脚本 gdbinit
```shell
python gdb.COMPLETE_EXPRESSION = gdb.COMPLETE_SYMBOL
add-auto-load-safe-path vmlinux-gdb.py
file vmlinux
lx-version
set args umid=uml0 hostname=uml1 eth0=tuntap,tap0 root=/dev/root rootfstype=hostfs rootflags=FULLPATH/rootfs rw mem=64M init=/init.sh quiet
handle SIGSEGV nostop noprint
handle SIGUSR1 nopass stop print
```

将FULLPATH替换为绝对路径。

启动gdb
```shell
gdb -q -x gdbinit
```

在gdb中启动内核
```shell
(gdb) run
```

发送USR1信号将会唤醒GDB
```shell
pkill -SIGUSR1 -o vmlinux
```



---
1. https://hackmd.io/@sysprog/user-mode-linux-env