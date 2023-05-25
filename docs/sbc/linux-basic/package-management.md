# 包管理器

## 术语

* **包**：软件的安装包，包含了软件的二进制文件、配置文件、依赖关系等信息；也有一些包是为了提供软件运行时所需的文件或是软件的文档、依赖关系等。
* **仓库**：软件仓库，是一个软件包的分发站点（通常是网站），包含了软件包、元数据、签名等信息，用户可以从仓库中下载软件包并安装。
* **元数据**：软件包的元数据，包含了软件包的名称、版本、简介、依赖关系等信息。
* **签名**：软件包或者仓库的签名，用于验证软件包/仓库文件的完整性和真实性。
* **依赖关系**：软件包之间的依赖关系，包括了软件包的依赖关系和版本依赖关系，用于在安装软件包时自动安装依赖的软件包。

## 包管理器的作用

包管理器是一种软件，用于管理软件包，包括了软件包的安装、升级、卸载等操作，以及软件仓库的添加、删除、更新等操作。

## 一些常见的包管理器

### APT 和 dpkg

APT（Advanced Packaging Tool）是一个软件包管理器，用于管理 Debian 系的 Linux 发行版的系统软件包，包括 Debian、Ubuntu、Linux Mint 等。

#### APT 的基本使用

APT 的基本使用方法如下：

* `apt update`：更新软件仓库的元数据，用于获取最新的软件包信息。
* `apt search <package>`：搜索软件包。
* `apt install <package>`：安装软件包。
* `apt remove <package>`：卸载软件包。
* `apt upgrade`：升级所有已安装的软件包。
* `apt autoremove`：卸载所有不再需要的软件包。

可能还会用到的参数：

* `-y`：自动回答 yes，可以配合 `apt install`、`apt remove`、`apt upgrade`、`apt autoremove` 等命令使用，用于在安装、卸载、升级、卸载不再需要的软件包时自动回答 yes。
* `-f`：修复软件包的依赖关系，可以配合 `apt install`、`apt remove`、`apt upgrade` 等命令使用，用于在安装、卸载、升级软件包时自动修复软件包的依赖关系。

#### dpkg 的基本使用

目前绝大多数的操作都可以通过 APT 完成，因此此处不再介绍，如果有兴趣的话，可以参考 [Debian 软件包管理](https://www.debian.org/doc/manuals/debian-reference/ch02.zh-cn.html)。

### Python 的 pip 和 pipenv

pip 是 Python 的包管理器，用于管理 Python 的包，包括安装、卸载、升级等操作。

pipenv 是一个 Python 的虚拟环境管理器，用于管理 Python 的虚拟环境，包括创建、删除、切换等操作。

#### pip 的基本使用

pip 的基本使用方法如下：

* `pip install <package>`：安装 Python 的包。
* `pip uninstall <package>`：卸载 Python 的包。
* `pip list`：列出已安装的 Python 的包。
* `pip show <package>`：显示 Python 的包的信息。

如果要搜索 Python 的包，可以使用 [PyPI](https://pypi.org/) 或者 [pip-search](https://pypi.org/project/pip-search/)。

**注意**：对于 Debian 系的 Linux 发行版，系统的 Python 环境由系统的包管理器 `apt` 管理，因此请使用 `apt` 安装 Python 的包，而不是使用 `pip` 安装 Python 的包。例如，如果要安装 OpenCV，应该使用 `apt install python3-opencv`，而不是使用 `pip install opencv-python`。

自 Python 3.11 起，Pip 已全面禁止安装软件包到系统 Python 环境（参考 [PEP 668 -- Marking Python base environments as “externally managed”](https://www.python.org/dev/peps/pep-0668/)），因此如果要安装系统包管理器仓库里没有的 Pip 包，应该使用 [`pipx`](https://pipxproject.github.io/pipx/) 或者 `pipenv`。

#### pipenv 的基本使用

可以使用 `sudo apt install pipenv` 安装 pipenv。

pipenv 的基本使用方法如下：

**注意**：请在项目的根目录下执行以下命令

* `pipenv install <package>`：安装 Python 的包。
* `pipenv uninstall <package>`：卸载 Python 的包。
* `pipenv graph`：列出已安装的 Python 的包。
* `pipenv run <command>`：在虚拟环境中运行命令。
* `pipenv shell`：进入虚拟环境。
* `exit`：退出虚拟环境。

更多的使用方法可以参考 [pipenv 的文档](https://pipenv.pypa.io/en/latest/)。

## 实例

todo
