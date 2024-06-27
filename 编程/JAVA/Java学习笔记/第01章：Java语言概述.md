# 1. Java基础学习的章节划分

```kotlin
第1阶段：Java基本语法
Java语言概述、Java的变量与进制、运算符、流程控制语句（条件判断、循环结构）、break\continue、
IDEA开发工具的使用、数组

第2阶段：面向对象编程（基础、进阶、高级）

第3阶段：Java高级应用
异常处理、多线程、集合框架、File类与IO流、网络编程、日期相关的API与比较器、反射、Java8-17新特征
```

> 语言 = 语法 + 逻辑

# 2. 计算机的构成

- 硬件：CPU、内存、硬盘、输入设备、输出设备、调制解调器
- 软件

# 3. 软件

- 软件：即一系列按照`特定顺序组织`的计算机`数据`和`指令`的集合。
    - 有**系统软件**和**应用软件**之分。
        - 系统软件：windows、mac os、android、ios、linux
        - 应用软件：qq、微信、音乐播放器等

# 4. 人机交互方式

- 图形化界面的方式
    
- 命令行的方式交互
    
- DOS命令（掌握）
    
    - cd cd.. cd/ md rd del exit cls等

# 5. 语言

- 计算机语言的分代
    
    - 第1代：机器语言：0和1
    - 第2代：汇编语言：出现了助记符
    - 第3代：高级语言：
        - 面向过程阶段：C
        - 面向对象阶段：C++，Java，C#，Python，JS等
- **没有“最好”的语言**，只有在特定场景下相对来说，最适合的语言而已。
    

# 6. Java概述

- Java简史
    
    - 1995诞生
    - 1996：jdk1.0版本
    - 2004：Java5.0（jdk1.5）--->里程碑式的版本；J2SE->JavaSE、J2EE->JavaEE、J2ME->JavaME
    - 2014：Java8.0--->里程碑式的版本；目前，市场占有率仍然很高。（lambda表达式、StreamAPI）
    - 后续：Java11、Java17都属于LTS(长期支持版本)
- SUN、Oracle、Google等
    
- Java之父：詹姆斯·高斯林
    
- Java的应用场景：
    
    - JavaSE：开发桌面级应用 （不靠谱）
    - JavaEE：开发企业级后台应用
    - JavaME：开发小型设备的应用（不靠谱）

​ ----> JavaEE、Android应用、大数据开发

# 7. JDK的下载、安装及环境变量的配置（重点）

- jdk下载：官网下载
- 安装：jdk8.0和jdk17.0 （傻瓜式安装）
- path环境变量的配置（重点）

# 8. 第1个Java程序

新建java文件：PersonInfo.java
```
class PersonalInfo{
    public static void main(String[] args){
        System.out.println("姓名：家琪琪\n");
        //System.out.println();//换行操作
        System.out.println("性别：女"); 
        System.out.println("住址：成都青创园"); 
    }
}
```

针对于第1个程序的小结及常见问题的分析
```

1. HelloWorld程序如下：编写在HelloWorld.java文件中
class HelloJava{
	public static void main(String[] args){
		System.out.println("HelloWorld!!");
		System.out.println("HelloWorld!!");
		System.out.println("你好，世界!");
	}

}


2. Java程序要想执行成功，需要如下的三个步骤：
第1步：编写：将java源代码编写在.java结尾的源文件中。
第2步：编译：针对于编写好的源文件进行编译操作。格式：javac 源文件名.java
             编译以后，会生成一个或多个.class结尾的字节码文件。字节码文件的名称即为源文件中对应的类名
第3步：运行：针对于编译好的字节码文件，进行解释运行操作。格式： java 字节码文件名  或  java 类名



3. 针对于编写过程来说：
3.1 class:是一个关键字，小写，后面跟着一个类名。
3.2 编写的类或方法必须使用一对{}。
3.3 
> main()作为程序的入口出现！格式如下：
    public static void main(String[] args)
> main()的格式是固定的！大家刚开始学习，可以"死记硬背"一下。
> 但是，可以考虑修改为如下的格式：
  方式1：public static void main(String args[])
  方式2：public static void main(String[] a)   args:是arguments的缩写

3.4 输出语句的编写：
> System.out.println(123);  表示：输出123之后换行

> System.out.print(123);    表示：输出123之后不需换行


3.5 编译过程中的小结：
> 编译源文件。此时要求在源文件所在的路径下执行"javac 源文件名.java"的操作

可能编译时报错的情况：
情况1：如果源文件名写错（不包括大小写不同的情况）或者不是在源文件所在的路径下执行javac操作则会报错。
情况2：编写的程序中有非法的语法或非法的字符。
    > 缺少必要的大括号、大小写的问题（Java是严格区分大小写的）、出现的标点符号必须是英文格式下的

3.6 解释运行过程的小结：
> 针对于字节码文件对应的类，执行java.exe命令。格式：java 类名。
> 此操作需要在字节码文件所属的路径下执行。

可能运行时报错的情况：
情况1：执行字节码文件所在的路径不对或字节码文件的名写错了（注意，java严格区分大小写，如果大小写出错了，仍然认为文件名写错了）。
情况2：可以出现运行时异常（放到第9章中讲解）


3.7 说明
1. Java是严格区分大小写的
2. 每一行执行语句必须以;结尾
3. 程序在编写过程中，为了可读性更强，增加必要的缩进，使用tab键即可。
4. 一个源文件中可以声明一个或多个类。
   一个源文件中最多只能有一个类声明为public。
   声明为public的类的类名必须与源文件名相同。
```

# 9. 注释
- 掌握：单行注释、多行注释
    - 作用1：对程序中的代码进行解释说明
    - 作用2：有助于调试程序
- 熟悉：文档注释 （可以被javadoc解析）

# 10. API文档

- API：（Application Programming Interface，应用程序编程接口）是 Java 提供的基本编程接口。
    - 像String、System都属于API
- API文档：用于解释说明API如何使用的一个文档。