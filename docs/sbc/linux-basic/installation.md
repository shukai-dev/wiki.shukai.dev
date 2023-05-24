# 如何安装 Linux

本章节将简单介绍如何在常用的 PC 机和开发板上安装 Linux。

详细的安装步骤请参考各个 Linux 发行版的官方文档，如 [Ubuntu 官方文档](https://ubuntu.com/tutorials/install-ubuntu-desktop)、[ArchWiki](https://wiki.archlinuxcn.org/wiki/%E5%AE%89%E8%A3%85%E6%8C%87%E5%8D%97)

## 在树莓派等开发板上安装 Linux

### 下载为开发板准备的 Linux 镜像

此处举例几种常见的开发板与发行版镜像的下载方法：

#### 下载树莓派的镜像

* Ubuntu 的镜像可以在 [Ubuntu 官网](https://ubuntu.com/download/raspberry-pi)下载，或者前往 [tuna 镜像站](https://mirrors.tuna.tsinghua.edu.cn/)，点击右侧的 **获取下载链接**，在弹出的窗口中选择 **Ubuntu**，然后选择带有 `arm64+raspi` 的版本下载，其中 `Preinstalled Server` 无桌面，而 `Preinstalled Desktop` 有桌面。
* Raspbian 的镜像可以在 [Raspbian 官网](https://www.raspberrypi.com/software/operating-systems/#raspberry-pi-os-64-bit) 下载，或者前往 [tuna 镜像站](https://mirrors.tuna.tsinghua.edu.cn/)，点击右侧的 **获取下载链接**，在弹出的窗口中选择 **Raspberry Pi OS**，然后选择 `arm64` 的 `bullseye` (Debian 11) 版本下载，其中 `lite` 版本没有桌面，默认版本和 `full` 版本有桌面。
* Arch Linux ARM 的镜像可以在 [Arch Linux ARM 官网](https://archlinuxarm.org/about/downloads) 下载，或者前往 [tuna 镜像站](https://mirrors.tuna.tsinghua.edu.cn/)，点击右侧的 **获取下载链接**，在弹出的窗口中选择 **Arch Linux ARM**，然后选择 `rpi-aarch64` 下载。

#### 下载 Orange Pi 的镜像

请前往 [官方网站](http://www.orangepi.cn/html/serviceAndSupport/index.html) 下载镜像。

#### 下载 NanoPi 的镜像

请前往 [官方网站](https://www.friendlyelec.com/index.php?route=information/information&information_id=7) 下载镜像。

### 烧录镜像

#### 使用 Raspberry Pi Imager 烧录镜像

[Raspberry Pi Imager](https://www.raspberrypi.com/software/) 是官方提供的镜像烧录工具，支持 Windows、macOS 和 Ubuntu。

#### 使用 balenaEtcher 烧录镜像

[balenaEtcher](https://www.balena.io/etcher/) 是一个开源的镜像烧录工具，支持 Windows、macOS 和 Linux。

#### 使用 dd 烧录镜像

Linux 下可以使用 `dd` 命令烧录镜像，例如：

```bash
sudo dd if=ubuntu-21.04-preinstalled-server-arm64+raspi.img of=/dev/sdX bs=1M status=progress
```

其中 `if` 是输入文件，`of` 是输出文件，`bs` 是块大小，`status` 是显示进度。
