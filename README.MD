# QuecPython Module Linux System USB Driver Installation Guide

[[中文](./README-zh.md)]

The QuecPython module's Linux system USB driver is provided in source code form and needs to be compiled by developers according to the Linux kernel version used.

Currently supported module models include: EC600U, EC200U, EC600N, EC800N, EC200A, EC800G, EC600M, EC800M, EC600E, EC800E

## Environment Dependencies

The driver installation process depends on `git`, `make`, and `gcc`. Install them by running the following commands:

```bash
sudo apt update
sudo apt upgrade
sudo apt install git make gcc
```

## Source Code Download

```bash
git clone https://github.com/QuecPython/Quectel_Linux_USB_Serial_Option_Driver.git
```

## Compilation and Installation

> If the driver has been installed before, you need to first run `rmmod option` to remove the previously installed driver.

1. The driver code is located in the src folder, categorized by the kernel version. Developers should choose the folder that is closest to the kernel version used in their system for compilation.

    Use the `uname -r` command to check the system's kernel version. The result of the command will look like this:

```bash
carl@carl-OptiPlex-7050:~$ uname -r
5.4.0-150-generic
```

2. Find the folder that is closest to your system's kernel version and navigate to that directory: `cd src/v5.4.1`
3. Execute `sudo make install` to compile and install the driver.

>If you are compiling the driver for EC200A, after running make install, you need to perform the following two steps:
>
>```bash
>cd drivers/usb/serial
>insmod option.ko
>```
