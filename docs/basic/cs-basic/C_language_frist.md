# C语言引入

## Previous

当然由于笔者本人也蒟蒻，所以代码有什么问题，也欢迎指正！！！

然后有一些比喻可能有点点不恰当也请多多担待！！！！



## Hello World ！

那么下面我们就进入这个学习所有语言的必经之路——“Hello ,World”。

先打代码再说原理和每个语句的意思。

首先我们要认识C语言的源文件`.c`文件，并新建它。

根据我们使用的`IDE`环境——`VScode`，我们需要在在软件中打开文件夹，然后新建文件。

![新建.c文件](https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309152252327.gif)

在我们新建好的文件里面我们就可以愉快的进行编程了。

### 具体演示

源代码：

```c
#include<stdio.h>
int main()
{
	printf("Hello, World!");
	return 0;
}
```



那要怎么运行呢？

我们可以在`VScode`的右上角的地方，有一个三角形或者三角形旁边多了一只虫子，这里就是运行程序的地方了，当然在运行程序之前请确保正确配置C语言编译环境，具体请查看wiki站中的`基础-Windows下VScode配置`仔细确认自己是否完成编译环境配置。

点击图标旁边的小三角会出现：

<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309152326947.png" alt="image-20230915232618820" style="zoom:20%;" />

`Run code`选项是因为我们安装插件`Code Runner`而出现的选项，选择`Run code`或者`运行C/C++文件`选项都是可以的，我们可以比较一下两者的区别：

`Run code`:

<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309152332920.png" alt="image-20230915233210867" style="zoom:35%;" />

`运行C/C++文件`：

<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309152333814.png" alt="image-20230915233321759" style="zoom:40%;" />

其实我们可以发现使用`Run Code`的输出会简洁很多，这也是之前建议同学们安装这个插件的原因。

-  我们再来看看在我们对程序进行编译后产生了什么东西：

  - 我们可以发现在我们`hello.c`的同一个目录下产生了一个`hello.exe`，这就是windows下的可执行文件。
  - 当然在整个文件目录下产生了一个`.vscode`的文件夹，这个是我们在选择`运行C/C++文件`后产生的一个文件，保存了`VScode`对于这个文件夹下文件编译的配置信息

  <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/202309152351581.png" alt="image-20230915235122538" style="zoom:80%;" />

这里就说一个完整的同时也是最为简单的C语言示例。相信大家不管从何种渠道都多多少少了解过hello world程序的编写，但是笔者还是想要来啰嗦一两句话。

那么下面我们来解读一下这个代码每一行的意思：

```c
#include<stdio.h>
int main()
{
	printf("Hello, World!");
	return 0;
}
```



1. 首先就是第一句`#include<stdio.h>`

   

   > 这个是C语言中引用`头文件`的语句，尖括号内的内容就是`头文件`的名称，我们在这里引用了`stdio.h`这个头函数，这个头函数是C语言的基本头函数，很多基本的函数都在这个头函数里面。引用头函数的语句格式：`#include<name>`，其实通过英语我们就可以看出大概的意思就是包括了什么东西。（这里我们也可以将`头文件`称做`库`，`函数库`）

   

2. 然后下一句`int main(){ }`

   

   > 这条语句的意思是，声明了一个`主函数`，它是一个程序的执行步骤，你可以将主函数理解为一个 `ToDo List`，程序需要按照主函数内的步骤一步一步执行编码者对电脑的一行行命令。

   

3. The next `printf("Hrllo,World!");`

   

   > 这条语句就是对程序的一个命令，`print`是打印，很容易可以推导出`printf();`这条语句就是将括号内的内容“打印”到程序窗格内。`“ ”`就代表着将里面的内容没有改变的输出到程序窗格内。
   >
   > 特别提醒：`;`在C和C++中都是表示这一句命令完结的意思所以记得在所有的语句完成后加上`;`，就像写作文每一句话写完后记得加句号一样。

   

4. The end `return 0;`

    

   > 直接翻译：`返回0`，这里代表的就是主函数正常结束，没有什么异常情况。但是不要忘记`；`。

   

   我们这里来蹭蹭`Chat GPT`的热度：

   

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/image-20221214202800219.png" alt="image-20221214202800219" style="zoom:50%;" />

   

   首先我们可以来看看这个等价关系：

   

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/image-20221216001100114.png" alt="image-20221216001100114" style="zoom:50%;" />

   

   当然再来一张图来看看具体关系：

   

   <img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/image-20221215235909412.png" alt="image-20221215235909412" style="zoom:50%;" />

   

   ****

   

   然后我们就可以开始整新活了，还是之前那段代码，我们可以了解到`printf`可以输出一串字符，那么我们如果想要完成下面几个操作该如何做呢？

   1. 完成多个句子的输出
   2. 完成换行输出

   

- **完成多个句子的输出:**

  我们可以直接复制粘贴`printf`语句，`Ctrl+C`和`Ctlr+V`复制大法好！或者在`printf(” “)` 的引号里面添加相关内容代码如下：

  

  ```c
#include<stdio.h>
int main()
{
	printf("Hello, World!");
    printf("Hello, World!");
    //或者将上面的两句改为：printf("Hello, World! Hello, World!");
	return 0;
}
  ```

   

但是有一个问题，我们运行看看：



<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/image-20221215000654055.png" alt="image-20221215000654055" style="zoom:33%;" />

<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/image-20221215000713212.png" alt="image-20221215000713212" style="zoom:33%;" />



可以发现不管是直接添加还是复制语句都没有办法实现换行输出，所以就引出了下面的问题如何换行输出？

- **换行输出：**

  你们在平时思考过我们在`Word`和`NotePad`里面敲下一个回车键后输入了一个什么东西吗？估计没有，嘿嘿嘿。

  其实是输入了一个换行符，而在C语言里面的换行符就是`\n`我们只需要在`“ ”`里面我们想要换行的地方加上换行符`\n`就行了。



```c
#include<stdio.h>
int main()
{
    printf("Hello, World!\n");
    printf("Hello, World!");
	//可以将上面两行写为：printf("Hello, World!\nHello, World!");
	return 0;
}
```



那让我们来看看运行结果吧：



<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/image-20221215001648591.png" alt="image-20221215001648591" style="zoom:33%;" />

<img src="https://mzee-imge.oss-cn-shanghai.aliyuncs.com/images/image-20221215001747005.png" alt="image-20221215001747005" style="zoom:33%;" />

这就是一个很简单的，C语言入门程序啦。
