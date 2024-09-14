## 1、jdk的版本自由切换

### 1.1、[jdk11](https://so.csdn.net/so/search?q=jdk11&spm=1001.2101.3001.7020)，jdk17，jdk21

我的电脑有三个版本的jdk，jdk11就算变成jdk8也是和我接下来的操作是一样的

首先我们确定好三个版本的jdk安装,我这里三个jdk安装的目录都是一样的

![](https://img-blog.csdnimg.cn/direct/62bbdd16179b4fc89eed45e95aba1868.png)

### 1.2、配置环境变量

既然已经安装好了，jdk我们得先配置好环境变量，才能共全局使用

配置环境变量我们直接按下WIN键，搜索环境变量，然后打开即可

![](https://img-blog.csdnimg.cn/direct/323cf8e3213b443ca38b3aee8fef63b9.png)

然后我们点击，环境变量

![](https://img-blog.csdnimg.cn/direct/65a91fc62bf841ffadc2eecea8a5c51a.png)

然后会弹出一个对话框，我们在系统变量下新建，然后输入CLASS_PATH和对应的值即可

`.;%JAVA_HOME%\lib\dt.jar;%JAVA_home%\lib\tools.jar`

![](https://img-blog.csdnimg.cn/direct/2c95bfca04f34cac9aa1c688ca1071c7.png)

然后再去配置我们的JAVA_HOME，我这里三个jdk一共三个JAVA_HOME，再加上一个指定版本的JAVA_HOME，变量名：JAVA(这里的数字就是对应的多少版本)_HOME，变量值就是安装jdk的路径，这个路径主要就是点开文件安装路径后。看到该目录下有bin目录等其他目录，直接复制地址栏上的目录即可


![](https://img-blog.csdnimg.cn/direct/fb39cf0315924fb5a066f4162a60fd07.png)

这里的目录就是以bin的上一级目录就是这个，这个jdk17是这样子的

![](https://img-blog.csdnimg.cn/direct/bec9fa23216e47db92f72678a6b4e9d6.png)

这是jdk21的bin目录的上一级目录不要进去bin目录

![](https://img-blog.csdnimg.cn/direct/55f8de739e014e9c8db706b0ec26623b.png)

这是jdk11的

![](https://img-blog.csdnimg.cn/direct/ced3b6be3f04470a944377021edc7304.png)

然后我们在配置一个选择版本的JAVA_HOME，变量名依旧是JAVA_HOME只不过这里不需要加数字，然后变量名就是：%JAVA(这里的数字代表着你前面配置的三个JAVA_HOME的名字对应着)_HOME%

比如你要切换为11版本的jdk，那么你的值就可以写成：%JAVA11_HOME%，要切换为21的就写：%JAVA21_HOME%即可，前提是一定要对应

![](https://img-blog.csdnimg.cn/direct/08a603cdba6e47d5977297065166a91c.png)

然后我们在系统变量中找到Path，选中它点击编辑

![](https://img-blog.csdnimg.cn/direct/1006406089bc42ef85ca5211fe5bb61c.png)

在这个里面我们配置一下三个JDK的环境变量的bin目录

首先我们先找到，jdk11的文件夹的bin目录

![](https://img-blog.csdnimg.cn/direct/ed047d30c88240c5b93d9322c66ce2ca.png)

找到bin目录我们点进去，然后就可以复制地址栏上的地址了，这就是jdk需要配置的最终的环境变量地址，其他的jdk也一样，找到bin目录点进去，然后复制地址

![](https://img-blog.csdnimg.cn/direct/45a2d1ea01834af994c616277d4fce35.png)

然后我们回到path环境变量中，点击新建，然后粘贴我们刚才复制的路径，就好了。三个jdk都需要配置

![](https://img-blog.csdnimg.cn/direct/64e07550870447a5a026ff9a244c4961.png)

最后的最后我们只需要在path环境变量中再次新建一个，%JAVA_HOME%\bin，并且把这个放到最上面


![](https://img-blog.csdnimg.cn/direct/24dd8d989841440ab313b42dd705a346.png)

最后一路确定就可以了，然后重新打开命令提示符，输入java -version就可以看到java 的版本了

![](https://img-blog.csdnimg.cn/direct/342999db5ff148638401cf245d466adf.png)

### 1.3、自由切换jdk版本

当我们想要修改jdk版本，我不想要21，我有一些需要jdk8才可以运行的jar，我们只需要在，环境变量中的系统变量，改变一下JAVA_HOME的值就可以了，例如我要改成11的jdk版本

![](https://img-blog.csdnimg.cn/direct/1a2c11192c6d443fbff4425c4adcbb7d.png)

然后我们一路确定确定，最后重新打开命令提示符，输入 java -version即可修改成功

![](https://img-blog.csdnimg.cn/direct/bffc251c35764ff19c05f5782fa5fa5f.png)