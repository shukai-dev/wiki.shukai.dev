# 硬件管理与控制

## 前言

在类 Unix 系统中，万物皆可文件，硬件设备也不例外。Linux 提供了一系列的文件来管理硬件设备，这些文件位于 `/sys` 和 `/proc` 目录下，其中 `/sys` 目录下的文件是用来管理硬件设备的，而 `/proc` 目录下的文件是用来管理进程的。此外，还有一些硬件设备的文件位于 `/dev` 目录下。

## 设备的类型

在 Linux 中，设备分为两种类型：块设备和字符设备。

块设备是指以块为单位进行数据读写的设备，例如硬盘、U 盘等。块设备的访问速度较慢，但是可以随机访问。

字符设备是指以字符为单位进行数据读写的设备，例如键盘、鼠标等。字符设备的访问速度较快，但是只能顺序访问。

## 常见的硬件设备

### CPU

CPU 的信息位于 `/proc/cpuinfo` 文件中。

```bash
❯ cat /proc/cpuinfo
processor	: 0
model name	: ARMv7 Processor rev 3 (v7l)
BogoMIPS	: 38.40
Features	: half thumb fastmult vfp edsp neon vfpv3 tls vfpv4 idiva idivt vfpd32 lpae evtstrm crc32
CPU implementer	: 0x41
CPU architecture: 7
CPU variant	: 0x0
CPU part	: 0xd03
CPU revision	: 3

processor	: 1
...
```

我们也可以通过 `lscpu` 命令来查看 CPU 的信息。

```bash
❯ lscpu
Architecture:        armv7l
Byte Order:          Little Endian
CPU(s):              4
On-line CPU(s) list: 0-3
Thread(s) per core:  1
Core(s) per socket:  4
Socket(s):           1
Vendor ID:           ARM
Model:               4
Model name:          Cortex-A53
Stepping:            r0p4
CPU max MHz:         1296.0000
CPU min MHz:         600.0000
BogoMIPS:            38.40
Flags:               half thumb fastmult vfp edsp neon vfpv3 tls vfpv4 idiva idivt vfpd32 lpae evtstrm crc32
```

todo 用准确的信息替换上面的信息，现在的是 copilot 生成的

### 内存

内存的信息位于 `/proc/meminfo` 文件中。

```bash
❯ cat /proc/meminfo
MemTotal:        1018160 kB
MemFree:          740048 kB
MemAvailable:     876876 kB
Buffers:           26420 kB
Cached:           117048 kB
SwapCached:            0 kB
...
```

我们也可以通过 `free` 命令来查看内存的信息。

```bash
❯ free -m # 以 MB 为单位显示内存信息
              total        used        free      shared  buff/cache   available
Mem:            994         119         720           0         154         834
```

### 硬盘

硬盘的信息位于 `/proc/partitions` 文件中。

```bash
❯ cat /proc/partitions
major minor  #blocks  name

 179        0    7744512 mmcblk0
 179        1      32768 mmcblk0p1
 179        2    7712768 mmcblk0p2
```

我们也可以通过 `lsblk` 命令来查看硬盘的信息。

```bash
❯ lsblk
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
mmcblk0     179:0    0  7.4G  0 disk
├─mmcblk0p1 179:1    0   32M  0 part /boot
└─mmcblk0p2 179:2    0  7.4G  0 part /
```

### 网卡

网卡的信息位于 `/proc/net/dev` 文件中。

```bash
❯ cat /proc/net/dev
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:  10240     128    0    0    0     0          0         0    10240     128    0    0    0     0       0          0
  eth0:  10240     128    0    0    0     0          0         0    10240     128    0    0    0     0       0          0
```

输出的信息可读性有可能比较差，我们可以通过 `ip` 命令来查看网卡的信息。

```bash
❯ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
...
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
...
```

#### 网卡设备的命名

##### 本地回环设备的名称

本地回环设备的名称为 `lo`，它的 MAC 地址为 `00:00:00:00:00:00`，IP 地址为 `127.0.0.1`。这个设备的用途是在本地进行网络通信，例如我们可以把测试用 Web 的服务绑定到 `127.0.0.2:80`，然后就可以在浏览器中访问这个地址，而不公开在外网。

##### 物理网卡的名称

有线网卡的名称通常以 `eth` 或者 `en` 开头，例如 `eth0`、`enp0s3` 等；无线网卡的名称通常以 `wlan` 或者 `wl` 开头，例如 `wlan0`、`wlp3s0` 等。网卡的 MAC 地址通常是由厂商分配的，例如 `00:0c:29:4f:8e:8a`。

`eth` 和 `wlan0` 是旧的命名方式，只有标号，没有其他信息，而且可能因为其他。`en` 和 `wl` 是新的命名方式，包含了网卡的类型和标号：

- `o` 表示 Onboard，也就是集成在主板上的网卡
- `s` 表示 Hotplug，也就是在 PCIe 插槽上，可以热插拔的网卡
- `p` 表示 Physical，后面的信息表示网卡的物理位置
- `x` 表示未知类型的网卡，例如 USB 网卡

在此之后，还有基于接口、位置、索引、MAC 地址等的命名方式，例如 `enp1s0`、`eno2`、`ens1`、`enx00e04c68001` 等，此处不再赘述，详情请参考 [systemd.net-naming-scheme](https://www.freedesktop.org/software/systemd/man/systemd.net-naming-scheme.html) 或者 [Consistent network interface device naming](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/configuring_and_managing_networking/consistent-network-interface-device-naming_configuring-and-managing-networking#network-interface-device-naming-hierarchy_consistent-network-interface-device-naming)

##### 虚拟网卡的名称

虚拟网卡的名称依类型而定，例如 Docker 的虚拟网卡的名称为 `docker0`，VirtualBox 虚拟机软件的虚拟网卡的名称为 `vboxnet0`，而桥接网卡的名称为 `br0`，可以查阅对应软件的文档来了解更多信息。
