# 编译

## 代码下载

内核代码地址： [https://www.kernel.org/](https://www.kernel.org/)

官方GIT的速度比较慢，如果要克隆GIT仓库，可以选择从国内的镜像克隆，例如 [https://mirrors.tuna.tsinghua.edu.cn/help/linux-stable.git/](https://mirrors.tuna.tsinghua.edu.cn/help/linux-stable.git/)


## 安装依赖

```shell
sudo apt install build-essential libncurses-dev flex bison
sudo apt install xz-utils wget ca-certificates bc
```


## 编译命令

```shell
rm build -rf && mkdir build
make O=build defconfig ARCH=um SUBARCH=x86_64
make O=build linux ARCH=um SUBARCH=x86_64 -j `nproc`
```

* 编译输出到指定的build目录
* ARCH表示机器的架构，可选项很多，具体看`arch/`目录下的子目录，这里的um指的是User-Mode

defconfig 根据当前架构生成一个默认的配置文件 .config，如果还要进一步定制可以这样：
```shell
make O=build menuconfig ARCH=um SUBARCH=x86_64
```