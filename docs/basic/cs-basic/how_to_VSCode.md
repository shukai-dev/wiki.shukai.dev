# VSCode的安装与使用（C/C++，Python环境下的使用）

> 千里之行始于足下，而每一个伟大项目的开始都是简单的环境配置！！！
>
> 由于多平台支持、多语言和易用性角度，我们选择了`VSCode`作为我们教程的基本`IDE`。
>
> 下面将会演示一遍，完成`C\C++`编译器、`Python`解释器和`VSCode`及相关插件的安装。

这里我们提供一个自解压的软件包供大家使用，[点击下载](https://zen.lanzout.com/b0fonwg6h)密码:fvsc

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
- 建议使用提供的自解压软件包中的版本，如果需要更新版本可以访问：[点击访问](https://github.com/niXman/mingw-builds-binaries/releases)
  - 选择在线安装的同学注意自身的网络环境，不然容易安装失败或者安装缓慢。
  - 自己下载离线包请认真核对版本和自身系统环境是否相符。

<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309131749656.png" alt="1" style="zoom:50%;" />


### 下载离线包并解压

> 我们只是提供了一个建议的解压软件`7-Zip`，可以使用其它解压软件，但是在`Windows`上个人还是推荐`Bandzip`和`7-Zip`

1. 下载我们提供的自解压软件包并解压：[点击下载](https://zen.lanzout.com/b0fonwg6h)密码:fvsc

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

> 安装包在我们提供的软件包里面是有的，提供版本为`1.8.0 for all users`，当然大家也可以去官网下载最新版本。[点击下载](https://code.visualstudio.com/download)

1. 双击打开`VSCodeSetup-x64-1.82.0.exe`

2. 选择`我同意此协议`后下一步

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132014695.png" alt="image-20230913201441638" style="zoom:50%;" />

3. 选择安装路径，因为`VSCode`真不大，还是建议装在默认的C盘路径下：

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132015675.png" alt="image-20230913201538630" style="zoom:50%;" />

4. 一直下一步就好，知道出现下面界面：

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132017765.png" alt="image-20230913201700726" style="zoom:50%;" />

   - 将其它内容的前面两项勾选上，然后下一步

5. 点击安装后，耐心等待安装完成。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132020709.png" alt="image-20230913202054659" style="zoom:50%;" />

6. 点击完成，自动运行`VSCode`

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132021683.png" alt="image-20230913202151636" style="zoom:50%;" />

- 就这样我们完成了，`VSCode`的安装，但是现在的它只是一个纯文本编辑器，没有更多的功能，我们需要进一步设置配置它。



### VSCode的配置与插件安装

- 我们第一次运行`VSCode`可以看到,这个页面：

  <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132041020.png" alt="image-20230913204141834" style="zoom:30%;" />

  - 在这里我们可以选择不同风格的主题，当然默认的看起来就很不错了。
  - 可以看到目前VSCode是纯英文界面，下面我们将VSCode汉化

#### 汉化VSCode

> `VSCode`支持大量的额外插件，我们就可以通过这些插件进行各种操作

1. 选择VSCode左侧栏的拓展选项，在搜索栏中输入`Chinese`，搜索汉化插件，选择简体中文进行安装`install`

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132048868.png" alt="image-20230913204840752" style="zoom:30%;" />

2. 等待安装完毕以后会提示更改语言重新加载软件，点击重新加载。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132050123.png" alt="image-20230913205046020" style="zoom:33%;" />

3. 重新启动软件以后我们就得到了一个中文界面的`VSCode`

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132051043.png" alt="image-20230913205142942" style="zoom:33%;" />



#### 安装VSCode的C/C++拓展

> 前面我们已经完成了本地的`MinGW64`的C/C++编译器，但是我们目前还不能通过`VSCode`调用这个编译器来编译我们的代码，这时候就需要安装`C/C++`的插件了。

1. 选择VSCode左侧栏的拓展选项，在搜索栏中输入`C++`，搜索`C\C++`插件，`C\C++ Extension Pack`插件进行安装`install`

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132057371.png" alt="image-20230913205736258" style="zoom:33%;" />

2. 到下面这样就安装完成了。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132100047.png" alt="image-20230913210033948" style="zoom:33%;" />

3. 那我们如何运行一个C语言文件呢？

   1. 我们首先在桌面上新建一个`test`文件夹，右键选择更多选项，选择**使用`code`打开**

   2. 在接下来的界面里选择信任

      <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132103059.png" alt="image-20230913210327945" style="zoom: 25%;" />

   3. 在`test`文件夹下新建一个C语言源文件`test.c`

   4. 在`test.c`文件中输入代码时，不知道为什么头文件在提示有误。

      <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132226637.png" alt="image-20230913222633544" style="zoom:25%;" />

   5. 这其实是我们没有选择针对C\C++的编译器，我们点击编辑器右下角的`win32`,选择弹出的`编辑配置UI`

      <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132231599.png" alt="202309132228375" style="zoom:30%;" />
   
   6. 在新页面的编译器路径空处填入编译器路径，如果是和本教程一样的路径应该是`C:\mingw64\bin\gcc.exe`
   
      <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132230743.png" alt="image-20230913223007612" style="zoom:33%;" />
   
   7. 这样我们就可以运行我们的测试代码了，点击运行代码<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132246404.png" alt="image-20230913224632293" style="zoom:33%;" />
   
      
   
   8. 直接选择弹出的首选项
   
      <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132247466.png" alt="image-20230913224731420" style="zoom:50%;" />
   
   9. 最后可以看到我们成功运行并且输出了我们的内容
   
      <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132249864.png" alt="image-20230913224957766" style="zoom:33%;" />
   



 **test文件的路径下不要有中文目录，不然会报错。**
 **当然路径中也不要带空格。**



#### 安装VSCode的Python插件

> 我们之前已经安装python的解释器，其实已经可以在命令行运行python脚本了。
>
> 但是我们想要在VSCode里面快乐使用python还需要安装

1. 选择VSCode左侧栏的拓展选项，在搜索栏中输入`Python`，搜索`Python`插件，选择`Python Extension Pack`两个插件进行安装`install`

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132300808.png" style="zoom:33%;" />   

2. 那我们如何运行一个Python脚本呢？

   1. 我们首先在桌面上新建一个`test`文件夹，右键选择更多选项，选择**使用`code`打开**

   2. 在接下来的界面里选择信任

      <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132103059.png" alt="image-20230913210327945" style="zoom: 25%;" />

   3. 在`test`文件夹下新建一个C语言源文件`test.py`

3. 然后在`.py`文件中写入我们的代码，然后运行。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132305367.png" alt="image-20230913230500298" style="zoom:33%;" />

4. 我们成功运行了。

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132306838.png" alt="image-20230913230605766" style="zoom:33%;" />

   

#### 安装Code Runner插件

>可能大家会发现用VSCode自带的运行时候，会有很多干扰信息

<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132310993.png" alt="image-20230913231041941" style="zoom:40%;" />

跟着一起输出到了终端中，为了信息简单明了，我们可以安装另一款插件`Code Runner`，它能够简化输出内容，让信息更加直观。

安装过程和上面安装插件一样，只是搜索时候搜索`code runner`安装就行

<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309132313648.png" alt="image-20230913231324579" style="zoom:33%;" />

