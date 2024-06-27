### 1. File类的使用[#](https://www.cnblogs.com/deyo/p/17496096.html#1-file%E7%B1%BB%E7%9A%84%E4%BD%BF%E7%94%A8)

```markdown
1. File类的理解
> File声明在java.io包下的。
> File类的对象可以表示一个文件或一个文件目录。
> File类中包含了关于文件、文件目录的新建、删除、重命名、查询所在路径、获取文件大小等方法。
  但是不包含读写文件内部内容的方法。要想读写文件内容，我们需要使用IO流。
> File类的对象常作为IO流读写数据的端点出现：常作为IO流的构造器的形参出现。


2. 内部api使用说明
2.1 构造器
* `public File(String pathname) ` ：以pathname为路径创建File对象，可以是绝对路径或者相对路径，如果pathname是相对路径，则默认的当前路径在系统属性user.dir中存储。
* `public File(String parent, String child) ` ：以parent为父路径，child为子路径创建File对象。
* `public File(File parent, String child)` ：根据一个父File对象和子文件路径创建File对象


2.2 方法
 1、获取文件和目录基本信息
* public String getName() ：获取名称
* public String getPath() ：获取路径
* `public String getAbsolutePath()`：获取绝对路径
* public File getAbsoluteFile()：获取绝对路径表示的文件
* `public String getParent()`：获取上层文件目录路径。若无，返回null
* public long length() ：获取文件长度（即：字节数）。不能获取目录的长度。
* public long lastModified() ：获取最后一次的修改时间，毫秒值

2、列出目录的下一级

* public String[] list() ：返回一个String数组，表示该File目录中的所有子文件或目录。
* public File[] listFiles() ：返回一个File数组，表示该File目录中的所有的子文件或目录。

3、File类的重命名功能
- public boolean renameTo(File dest):把文件重命名为指定的文件路径。

4、判断功能的方法
- `public boolean exists()` ：此File表示的文件或目录是否实际存在。
- `public boolean isDirectory()` ：此File表示的是否为目录。
- `public boolean isFile()` ：此File表示的是否为文件。
- public boolean canRead() ：判断是否可读
- public boolean canWrite() ：判断是否可写
- public boolean isHidden() ：判断是否隐藏

5、创建、删除功能
- `public boolean createNewFile()` ：创建文件。若文件存在，则不创建，返回false。
- `public boolean mkdir()` ：创建文件目录。如果此文件目录存在，就不创建了。如果此文件目录的上层目录不存在，也不创建。
- `public boolean mkdirs()` ：创建文件目录。如果上层文件目录不存在，一并创建。
- `public boolean delete()` ：删除文件或者文件夹
  删除注意事项：① Java中的删除不走回收站。② 要删除一个文件目录，请注意该文件目录内不能包含文件或者文件目录。

3. 概念：
绝对路径：在windows操作系统中，以盘符开始的路径。

相对路径：相较于某个指定路径下的具体路径。
        单元测试方法：相较于当前的module
        main():相较于当前的工程
```

### 2. IO流的概述[#](https://www.cnblogs.com/deyo/p/17496096.html#2-io%E6%B5%81%E7%9A%84%E6%A6%82%E8%BF%B0)

- 流的分类
    - 流的流向：输入流、输出流
    - 操作的数据单位：字节流、字符流
    - 角色的不同：节点流、处理流
- 4个抽象基类

[![image-20230304085251005](https://s2.loli.net/2023/06/21/OJmhaoijrgStWZH.png)](https://s2.loli.net/2023/06/21/OJmhaoijrgStWZH.png)

- 整个流这一章涉及到的具体的流的使用，操作的步骤都是标准规范的。
    - 步骤1：创建File的对象
    - 步骤2：创建流的对象，构造器中需要传入File的对象
    - 步骤3：读取、写出操作的细节
    - 步骤4：关闭资源

### 3. 文件流的使用[#](https://www.cnblogs.com/deyo/p/17496096.html#3-%E6%96%87%E4%BB%B6%E6%B5%81%E7%9A%84%E4%BD%BF%E7%94%A8)

- FileInputStream与FileOutputStream、FileReader与FileWriter
    
- 注意点1：
    

```cmake
注意点：
> 因为涉及到资源的关闭，所有异常的处理需要使用try-catch-finally结构替换throws
> 对于输入流来讲，File对象对应的物理磁盘上的文件必须存在。否则，报FileNotFoundException
  对于输出流来讲，File对象对应的物理磁盘上的文件可以不存在。
        > 如果不存在，则在输出的过程中，会自动创建指定名的文件
        > 如果存在，如果使用的是FileWriter(File file)或FileWriter(File file,false)构造器，则在输出的过程中，会覆盖已有的文件
          如果存在，如果使用的是FileWriter(File file,true)构造器，则在输出的过程中，会在现有文件末尾追加内容。
> 务必记得关闭资源，否则出现内存泄漏
```

- 注意点2：

```markdown
> FileReader \ FileWriter :主要用来处理文本文件
  对于非文本文件的处理是失败的。

> FileInputStream \ FileOutputStream:主要用来处理非文本文件。

> 文本文件：.txt、.java、.c、.cpp、.py
  非文本文件：.doc、.jpg、.png、.avi、.mp3、.mp4、.ppt
```

### 4. 处理流之一：缓冲流[#](https://www.cnblogs.com/deyo/p/17496096.html#4-%E5%A4%84%E7%90%86%E6%B5%81%E4%B9%8B%E4%B8%80%E7%BC%93%E5%86%B2%E6%B5%81)

- BufferedInputStream与BufferedOutputStream、BufferedReader与BufferedWriter
    
- 作用：加快文件的读写效率。
    
- 原理：内部提供了缓冲区（数组实现的），减少和磁盘交互的次数。
    
- ```lua
    4个缓冲流                   使用的方法
    处理非文本文件的字节流：
    BufferedInputStream        read(byte[] buffer)
    BufferedOutputStream       write(byte[] buffer,0,len) \ flush()
    
    处理文本文件的字符流：
    BuffferedReader            read(char[] buffer)\readLine()
    BufferedWriter             write(char[] buffer,0,len) \ flush()
    
    3. 实现的步骤
    
    第1步：创建File的对象、流的对象（包括文件流、缓冲流）
    
    第2步：使用缓冲流实现 读取数据 或 写出数据的过程（重点）
        读取：int read(char[] cbuf/byte[] buffer) : 每次将数据读入到cbuf/buffer数组中，并返回读入到数组中的字符的个数
        写出：void write(String str)/write(char[] cbuf):将str或cbuf写出到文件中
             void write(byte[] buffer) 将byte[]写出到文件中
    
    第3步：关闭资源
    ```
    

### 5. 处理流之二：转换流[#](https://www.cnblogs.com/deyo/p/17496096.html#5-%E5%A4%84%E7%90%86%E6%B5%81%E4%B9%8B%E4%BA%8C%E8%BD%AC%E6%8D%A2%E6%B5%81)

- InputStreamReader和OutputStreamWriter
    
- 基本使用
    

[![image-20230304090354929](https://s2.loli.net/2023/06/21/ufKSBelPWvE6GYD.png)](https://s2.loli.net/2023/06/21/ufKSBelPWvE6GYD.png)

- ```lua
    1. 复习
    
    字符编码：字符、字符串 ----> 字节、字节数组。对应着编码集
    字符解码：字节、字节数组 ---> 字符、字符串。对应着解码集
    
    2. 如果希望程序在读取文本文件时，不出现乱码，需要注意什么？
    使用的解码集必须与当初保存文本文件使用的编码集一致。
    ```
    

### 6. 处理流之三：对象流[#](https://www.cnblogs.com/deyo/p/17496096.html#6-%E5%A4%84%E7%90%86%E6%B5%81%E4%B9%8B%E4%B8%89%E5%AF%B9%E8%B1%A1%E6%B5%81)

- 了解：数据流：DataInputStream 、DataOutputStream
    
    - 读写8种基本数据类型的变量、String、字节数组
- 掌握：ObjectInputStream、ObjectOutputStream
    
    - 读写8种基本数据类型的变量、对象（readObject();writeObject(Object obj)）
- 掌握：对象的序列化机制
    
    - 对象序列化机制允许把内存中的Java对象转换成平台无关的二进制流，从而允许把这种二进制流持久地保存在磁盘上，或通过网络将这种二进制流传输到另一个网络节点。//当其它程序获取了这种二进制流，就可以恢复成原来的Java对象。
        
    - ```mipsasm
        序列化过程：将内存中的Java对象转换为二进制流，保存在文件中或通过网络传输出去。
        使用ObjectOutputStream
        
        反序列化过程：将文件中或者通过网络接收到的二进制流转换为内存中的Java对象
        使用ObjectInputStream
        ```
        
- 熟悉：自定义类要想实现序列化机制，需要满足：
    
    ```markdown
    > 必须实现接口Serializable。 （此接口中没有抽象方法，称为标识接口）
    > 类中必须显式声明一个全局常量serialVersionUID，用于唯一标识当前类本身。
      如果不显式声明，系统会自动分配一个serialVersionUID，但是此属性在类修改的情况下，可能被改变。不建议使用默认情况。
    > 自定义类的所有属性也必须是可以序列化的。满足上述的两个条件。
      特别的：基本数据类型、String类型本身已经是可以序列化的了。
    
    
    6.注意点：
    > 类中声明为static或transient的变量，不能实现序列化。
    ```
    

### 7. 其它流的使用[#](https://www.cnblogs.com/deyo/p/17496096.html#7-%E5%85%B6%E5%AE%83%E6%B5%81%E7%9A%84%E4%BD%BF%E7%94%A8)

- 标准的输入、输出流

```makefile
System.in: 默认的输入设备：键盘
System.out: 默认的输出设备：显示屏
```

- 打印流

```undefined
PrintStream和PrintWriter
```

- 使用第三方框架
    
    - apache-common包