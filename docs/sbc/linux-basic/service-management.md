# 服务管理

本篇简单介绍如何管理系统服务

更多内容请参考 [ArchWiki](https://wiki.archlinuxcn.org/wiki/Systemd)，[RHEL 9 中关于 systemd 的介绍](https://access.redhat.com/documentation/zh-cn/red_hat_enterprise_linux/9/html/configuring_basic_system_settings/introduction-to-systemd_configuring-basic-system-settings) 或者 [systemd 官方文档（英语）](https://www.freedesktop.org/wiki/Software/systemd/)

## 什么是服务

服务是在后台运行的程序，它们可以在系统启动时自动启动，也可以在系统运行时手动启动，还可以通过定时器或者某些事件来触发。服务可以从系统的包管理器安装，也可以是用户自己编写/安装的。

例如，`sshd` 服务是 `openssh` 包提供的，它会在开机联网之后启动，以便用户可以通过 SSH 连接到系统；而 `logrotate` 服务是 `logrotate` 包提供的，它默认会在每天 0 点执行一次，对日志文件进行轮转（压缩旧的日志文件，删除过期的日志文件，以节约硬盘空间）。

## 服务的状态

服务有这样几种运行状态：

这些状态属于 **正常运行（active）** 状态：

* **已启动（running）**：服务正在运行
* **已停止（stopped）**：服务已经停止运行
* **等待中（waiting）**：服务正在等待某些事件的发生，例如 `logrotate` 服务在等待每天 0 点的到来，或者是日志文件大小超过了某个阈值
* **已退出（exited）**：服务是短暂运行的，运行结束后就会退出

这些状态属于 **异常状态** 或者 **未运行（inactive）** 状态：

* **已失败（failed）**：服务运行失败，这是代表服务运行出现了问题的一种状态
* **已停止（dead）**：服务运行失败后，系统会尝试重启服务，如果重启失败，服务就会进入这种状态

还有 **启用（enabled）** 和 **禁用（disabled）** 两种状态，它们是指服务是否会在系统启动时自动启动。
