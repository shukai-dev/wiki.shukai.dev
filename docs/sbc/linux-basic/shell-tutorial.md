# 如何使用 Shell

## 前言

Shell 的使用是 Linux 系统中最基础的技能之一，也是开发者必备的技能。但与此同时，由于 Shell 的功能非常强大，因此它的学习曲线也比较陡峭。本章节将会介绍一些基础的 Shell 使用技巧，以便于大家能够更好地在单板机上进行开发。

为了能让各位克服对于 Shell 的恐惧，在开始讲解常用的 Shell 命令之前，我们会先做一些美化工作，让 Shell 的界面看起来更加舒适，同时使用起来更加顺手。

## 美化 Shell

### 更换 Shell

在默认情况下，Ubuntu 的默认 Shell 是 Bash，但是 Bash 的功能比较弱，而且它的提示符也比较丑。因此，我们可以将默认的 Shell 更换为 Zsh，它的功能比 Bash 更加强大，而且它的提示符也比较漂亮。在 Ubuntu 中，我们可以通过以下命令来安装 Zsh，并同时安装一些常用的插件：

```bash
sudo apt update
sudo apt install zsh zsh-syntax-highlighting zsh-autosuggestions
```

安装完成后，我们可以通过以下命令来查看当前系统中可用的 Shell：

```bash
cat /etc/shells
```

在输出的结果中，我们可以看到 Zsh 的路径是 `/usr/bin/zsh`，因此我们可以通过以下命令来将默认的 Shell 更换为 Zsh：

```bash
chsh -s /usr/bin/zsh
```

执行完上述命令后，我们需要重新登录系统，才能够看到 Zsh 的效果。在重新登录系统后，我们可以通过以下命令来查看当前系统中默认的 Shell：

```bash
echo $SHELL
```

在输出的结果中，我们可以看到默认的 Shell 已经变成了 Zsh。

### 安装 Oh My Zsh

Oh My Zsh 是一个开源的 Zsh 配置管理框架，它提供了大量的主题和插件，可以让我们更加方便地管理 Zsh 的配置。在 Ubuntu 中，我们可以通过以下命令来安装 Oh My Zsh：

```bash
sudo apt install curl git
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

\*由于 Github 在国内的访问速度可能比较慢，我们可以使用 [FastGit](https://fgit.ml) 来加速 Github 的访问：

```bash
sudo apt install curl git
curl -fsSL -o install.sh https://raw.fgit.ml/ohmyzsh/ohmyzsh/master/tools/install.sh 
REMOTE="https://hub.fgit.ml/ohmyzsh/ohmyzsh.git" bash install.sh
```

安装完成后，我们可以通过以下命令来查看当前系统中可用的主题：

```bash
ls ~/.oh-my-zsh/themes
```

在输出的结果中，我们可以看到 Zsh 默认提供了 100 多种主题，我们可以通过以下命令来查看这些主题的效果：

```bash
for theme in ~/.oh-my-zsh/themes/*; do
    echo $theme
    ZSH_THEME=${theme##*/}
    echo $ZSH_THEME
    zsh -c "source $theme; prompt"
done
```

选定一个主题以后，我们可以通过以下命令来将默认的主题更换为我们选定的主题：

```bash
sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="agnoster"/g' ~/.zshrc
```

然后，把 `zsh-syntax-highlighting` 和 `zsh-autosuggestions` 的配置添加到 `~/.zshrc` 文件的末尾：

```bash
echo "source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc
echo "source /usr/share/zsh-autosuggestions/zsh-autosuggestions.zsh" >> ~/.zshrc
```

最后，我们可以通过以下命令来重新加载 Zsh 的配置：

```bash
exec zsh
```

在接下来的内容中，我们将会利用 zsh 的补全等功能来提高我们的开发效率。

## 常用命令

*更多内容请参考 [常用命令](./common-commands.md)*
