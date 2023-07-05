# QuecPython 模组 Linux 系统 USB 驱动安装说明



QuecPython 模组 Linux 系统 USB 驱动以源码形式提供，需要开发者根据所用 Linux 系统内核版本，使用源码自行编译。

目前支持的模组型号有：EC600U、EC200U、EC600N、EC800N、EC200A、EC800G、EC600M、EC800M、EC600E、EC800E

## 环境依赖

该驱动安装流程依赖 git、make 与 gcc，执行以下命令进行安装：

```bash
sudo apt update
sudo apt upgrade
sudo apt install git make gcc
```

## 源码下载

```bash
git clone https://github.com/QuecPython/Quectel_Linux_USB_Serial_Option_Driver.git
```

## 编译安装

> 若安装过该驱动，则需先执行`rmmod option`移除已安装驱动。

1. 驱动代码在 src 文件夹内，以内核版本号进行分类，开发者需要选择与所用系统的内核版本最接近的文件夹进行编译。

    使用`uanme -r`命令查看系统的内核版本，执行结果如下：

```bash
carl@carl-OptiPlex-7050:~$ uname -r
5.4.0-150-generic
```

2. 找到与所用系统的内核版本最接近的文件夹，进入该目录：`cd src/v5.4.1`
3. 执行`sudo make install`编译和安装驱动。

>编译 EC200A 的驱动时，在执行完`make install`之后，需再执行如下两步：
>
>```bash
>cd drivers/usb/serial
>insmod option.ko
>```
