# VSCode的安装与使用（C/C++，Python环境下的使用）

> 千里之行始于足下，而每一个伟大项目的开始都是简单的环境配置！！！
>
> 由于多平台支持、多语言和易用性角度，我们选择了`VSCode`作为我们教程的基本`IDE`。
>
> 下面将会演示一遍，完成`C\C++`编译器、`Python`解释器和`VSCode`及相关插件的安装。

这里我们提供一个自解压的软件包供大家使用，[点击下载](https://cowtransfer.com/s/b0a37fb4c9c043)，code：izja6a

在这个自解压包中，我们为大家提供了四个文件：

- `mingw64.zip`，MinGW的离线包，需要解压使用。
- `VSCodeSetup-x64-1.82.0.exe`,VSCode的安装包。
- `7z2301-x64.exe`，推荐使用的解压软件。
- `python-3.11.5-amd64.exe`，python3.11.5的解释器
- 具体说明可参见，`说明.txt`

![image-20230911071534482](https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/image-20230911071534482.png)

## 安装MinGW
> 安装MinGW可以通过官方提供的在线安装包进行安装同时也可以使用离线版本的已编译版本的离线包进行安装，本次记录考虑到后来同学们的网络环境问题，我们此次选择使用离线包进行安装。

- `MinGW`版本：MinGW-W64 GCC-8.1.0
- 建议使用提供的自解压软件包中的版本，如果需要更新版本可以访问：[点击访问](https://sourceforge.net/projects/mingw-w64/files/mingw-w64/)
  - 选择在线安装的同学注意自身的网络环境，不然容易安装失败或者安装缓慢。
  - 自己下载离线包请认真核对版本和自身系统环境是否相符。

<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131749656.png" alt="1" style="zoom:50%;" />


### 下载离线包并解压

> 我们只是提供了一个建议的解压软件`7-Zip`，可以使用其它解压软件，但是在`Windows`上个人还是推荐`Bandzip`和`7-Zip`

1. 下载我们提供的自解压软件包并解压：[点击下载](https://cowtransfer.com/s/b0a37fb4c9c043)，code：izja6a

2. 找到`mingw64.zip`，打开以后解压到一个你可以找到的地方。
   - 如果无法打开请双击安装提供的`7z2301-x64.exe`安装包
   
   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131750609.png" alt="2" style="zoom:35%;" />
   
3. 将解压出来的文件夹，剪贴到`C盘`根目录下。
   - 这里是建议将编译器放在`C盘`根目录下以免出现软件无法识别到编译器的情况。
   
   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131750591.png" alt="3" style="zoom:40%;" />

### 配置环境变量与检测安装是否完成

#### 配置环境变量

1. 复制你放在`C盘`的`mingw64`文件夹下的`bin`文件路径。
   - 如果你是放在`C盘`的话，路径应该是`C:\mingw64\bin`

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131753073.png" alt="4" style="zoom:30%;" />

2. 在开始菜单里搜索`编辑系统环境变量`，选择打开

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131804672.png" alt="5" style="zoom:30%;" />

3. 单击弹出窗口上的`环境变量`

4. 在用户环境变量的内容中点击选中变量`Path`，再从侧边栏中选择`编辑`

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131807642.png" alt="6" style="zoom:33%;" />

5. 在新弹出的页面上选择`新建`，并将复制的路径粘贴到新建行中。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131808881.png" alt="7" style="zoom:45%;" />

6. 选择三次`确定`

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131809548.png" alt="8" style="zoom:33%;" />

#### 检测编译器是否安装成功

> 大家可能无法确认自己的安装是否完成或者是否成功，下面的方法是帮助大家确认自己本地是否有编译环境的一个方法。
> **PS：并不是说这个方法能够检测其它IDE自带的编译环境，而是不依赖任何IDE的公有编译环境**

1. 在键盘上同时按下`Win+R`，在运行窗口输入`cmd`,然后点击运行或者回车。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131809132.png" alt="9" style="zoom:50%;" />

2. 在新出现的黑色窗口(命令行窗口)，输入命令`gcc -v`或者`g++ -v`。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131812492.png" alt="image-20230913181207459" style="zoom:67%;" />

3. 若出现`'gcc' 不是内部或外部命令，也不是可运行的程序或批处理文件`，如图的情况就是未成功，请返回环境变量的配置。[点击跳转](#配置环境变量)

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131811556.png" alt="10" style="zoom:50%;" />

4. 若出现下图所示的编译器版本及路径信息就是安装成功。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131810131.png" alt="11" style="zoom:50%;" />



## Python环境安装

### 本地解释器安装

> `Python`的环境安装就相对简单了，就是安装包一键式安装了。
>
> 当然在学习中注意`Python2`和`Python3`的区别，我们学习中使用的是`Python3`。
>
> 我们提供的安装包版本为`3.11.5`，当然你也可以去**Python**官网上，[点击查看](https://www.python.org/downloads/)

1. 双击打开软件包解压出来的`python-3.11.5-amd64.exe`

2. 勾选`Add python.exe to PATH`，这一步一定要勾选，但是如果忘记请到后续补充：[点击跳转](#(补充)Python系统环境变量)

3. 选择`Install Now`

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131843788.png" alt="image-20230913184352722" style="zoom:50%;" />

4. 然后耐心等待片刻。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131844151.png" alt="image-20230913184447102" style="zoom:50%;" />

5. 出现以下界面则表示安装完成

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131902155.png" alt="image-20230913184755444" style="zoom:50%;" />

   
   

### 测试Python解释器是否可用

> 一般来讲像上面那样安装成功以后就没有什么问题了，但是为了保险起见，我们还是来确认一下。

1. 在键盘上同时按下`Win+R`，在运行窗口输入`cmd`,然后点击运行或者回车。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131809132.png" alt="9" style="zoom:50%;" />

2. 在新出现的黑色窗口(命令行窗口)，输入`python`。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131913253.png" alt="image-20230913191307213" style="zoom:60%;" />

3. 出现以下界面则代表解释器正常运行。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131913242.png" alt="image-20230913191345206" style="zoom:50%;" />



### (补充)Python系统环境变量

> 有一部分同学提前安装了`python`但是没有配置好`PATH`变量或者在安装的时候忘记勾选`Add python.exe to PATH`
>
> 最直观的方法就是卸载重装，如果选择这个方式建议使用卸载软件`geek.exe`,[点击下载](https://geekuninstaller.com/download)

最开始打开`编辑系统环境变量`，和上面的步骤一样。[点击跳转](# 配置环境变量)

**但是得注意的一点是：`python`的路径和`mingw64`的路径不同**

而且需要向环境变量中新建两条（下面以python默认安装路径为例）：

1. `C:\Users\admin\AppData\Local\Pregrams\Python\Python3115`
2. `C:\Users\admin\AppData\Local\Pregrams\Python\Python3115\Script`

- 这个路径会因为你本地的安装目录、python具体版本而有所变化，所以我们还是建议卸载掉重装以免麻烦。



## VSCode安装与配置

### VSCode软件本体安装







