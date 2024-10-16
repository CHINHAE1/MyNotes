
想要用Java进行编程，就离不开jdk这个东西。首先简单介绍一下jdk是什么？

jdk（Java Development Kit），就是java开发的工具，是整个Java的核心，包括了Java运行环境（jre）、一堆Java工具以及Java基础的类库。也可以说jdk就java。

这里提一下jre，jre是java运行时环境，包含了java虚拟机，java基础类库。是使用java语言编写的程序运行所需要的软件环境，是提供给想运行java程序的用户使用的。在jdk1.8版本中jdk中已经包含了jre，所以这里安装jre其实是重复安装了。

这里我们以jdk1.8为例来讲解一下jdk的安装流程。

## 一、下载

官网下载：

[jdk官网下载](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)


## 二、安装

这里我使用的系统是Win10_64位_专业版，自己注意下载的版本是否匹配，下面开始安装

### 1、下载文件

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201230173913448-1593919158.png)

### 2、双击下载好的exe文件（可能反应会有点慢）

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201230174009002-1088220615.png)

###  3、修改安装目录，也可以默认目录（默认C盘），但是请记住你的安装目录（后面有用的！）

也可以仿照我的安装目录：E:\anzhuang\JAVA\jdk_8u191\

 ![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231101909333-716434907.png)

###  4、点击“下一步”安装，这个时候就是已经在安装了，如果进度条很长时间不动了，注意可能是弹出来另一个界面,请看第5步

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201230174916326-1047962523.png)

###  5、可能会弹出这个界面，这是进行jre安装配置，直接点击确定就行

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201230175224319-1259351300.png)

###  6、jre安装

E:\anzhuang\JAVA\jre_8u191\

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231102403881-564964301.png)

###  7、安装界面

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201230175643031-916519907.png)

###  8、安装成功，直接点击关闭就行

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201230175736514-1940313003.png)

## 三、配置jdk环境变量

jdk安装完成后，还需要配置一下环境变量，以便我们在任何目录下都可以调用java命令。

### 1、打开高级系统设置界面

右击桌面的“此电脑”图标，点击“属性”，弹出系统窗口，然后点击“高级系统设置”

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231142216536-1178103273.png)

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231105004122-1091807623.png)

 **注意：有时候你桌面上的“此电脑”图标是快捷方式，这样可能就没有“属性”这个选项了，这里提供另一种方法：**

双击桌面“此电脑”图标，打开文件资源管理器，输入：控制面板\系统和安全\系统，然后回车就可进入上图界面。

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231110514641-423070699.png)

###  2、打开环境变量配置界面

 ![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231111718995-1529877525.png)

###  3、配置环境变量

在“环境变量”界面中，分为上下两部分，上面部分是“某某某的用户变量”的设置，针对的是当前你登录电脑的账户；下面部分是系统变量的设置，针对的是这台电脑，相当于是所有账户。对于自己使用的电脑来说，建议直接在下面部分的“系统变量”中来配置。下面来以系统变量为例讲解：

#### 　　a、在系统变量中新建一个JAVA_HOME变量，设置变量名跟变量值

JAVA_HOME这个变量里面可以只存放java相关的路径配置，方便日后管理。

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231132415550-8170149.png)

　　　　 这个时候在系统变量里面便会多了JAVA_HOME这个变量

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231132559952-899739185.png)

###  　　b、将JAVA_HOME配置到系统环境变量path中

 　　　双击path变量，新建一参数，输入%JAVA_HOME%\bin后点击确定即可。
 　　　
![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231141619491-732683985.png)

　　　　环境变量path的作用：提供windows命令行中指令的可执行文件路径，当我们在命令行中键入指令时，根据环境变量中的path值，找到对应的指令可执行文件进行执行。

　　　　简单的说就是配置在path中的目录参数，在命令行中的任何目录下都可以使用。

## 四、验证安装成功

经过以上步骤，jdk已经初步安装配置成功了，下面我们可以利用cmd验证下是否安装成功：

注意在此步骤前需要保存并关闭上面步骤窗口

### 1、键盘同时按住Windows + r，弹出运行界面。也可以右击“开始”，点击“运行”，弹出界面

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231103317580-372845199.png)

### 2、输入cmd，点击确定打开cmd窗口

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231103452132-1230494470.png)

### 3、在cmd窗口中键入java -version后回车，如果出现下面的版本号，及说明jdk安装成功

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231103640214-163909052.png)

### 4、验证java、javac命令

同样在cmd窗口中，输入java或者javac命令，如果两者皆出现下图显示，则jdk安装成功，且环境变量配置成功。

![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231134922072-917982028.png)

 ![](https://img2020.cnblogs.com/blog/1858147/202012/1858147-20201231134953063-103561901.png)