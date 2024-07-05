# virtme-ng

## 安装QEMU

[virtme-ng](https://github.com/arighi/virtme-ng)是基于qemu构建的测试工具。

安装qemu，以及libvirt工具

```shell
sudo apt install qemu-kvm virt-manager virtinst libvirt-clients bridge-utils libvirt-daemon-system
```

将本用户加入kvm和libvirt组，这样不用sudo就能启动虚拟机
```shell
sudo usermod -aG kvm $USER
sudo usermod -aG libvirt $USER
sudo usermod -aG libvirt-qemu $USER
sudo usermod -aG libvirt-dnsmasq $USER
```

操作完需要重启一下。


## 安装virtme-ng

```shell
sudo add-apt-repository ppa:arighi/virtme-ng
sudo apt install virtme-ng
```

## 编译内核

vng 提供了编译命令，笔者还是更习惯直接make

关闭KASLR

\# CONFIG_RANDOMIZE_BASE is not set

开启debug

CONFIG_DEBUG_INFO=y

```shell
make O=build defconfig ARCH=x86

make O=buildq ARCH=x86 -j `nproc`
make O=buildq ARCH=x86 scripts_gdb
```

## 启动虚拟机

设置qemu网桥，将"allow all"添加到`/etc/qemu/bridge.conf`
```shell
sudo filecap /usr/lib/qemu/qemu-bridge-helper net_admin
```

vng可以模拟的场景很多，这里启动一个numa的

```shell
vng --user root -m 4G --numa 2G,cpus=0-1 --numa 2G,cpus=2-3  --cpus 4 --network bridge --debug
```

vng默认会将本机的rootfs作为虚拟机的rootfs

## GDB

创建 ~/.gdbinit
```plain
set debuginfod enabled on
add-auto-load-safe-path /home/yuan/learn_linux/linux-6.6.36/buildq/vmlinux-gdb.py
```

执行远程gdb
```shell
(gdb) file vmlinux
(gdb) target remote :1234
```

