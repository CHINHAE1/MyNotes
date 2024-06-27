
# 插件
1. PowerToys
2. TTime
3. Pixpin
4. icloud
5. everything
6. 终端Terminal



# 谷歌浏览器多开

在“chrome.exe”添加“空格--user-data-dir="E:\谷歌多开1"”

"C:\Program Files\Google\Chrome\Application\chrome.exe" --user-data-dir="E:\谷歌多开1"

修改如图

![](https://pic1.zhimg.com/80/v2-e1c7bf8fc3acde3f30a1115371928f50_1440w.webp)



# 软件自启文件夹
```java
shell:startup
```


# 双显示器下，应用/游戏在副屏幕启动

所有窗口应用可使用【快捷键win+Shift+←/→】，

但应用场景在开游戏刷日常的时候，每天都要开一两次，特别是某二字、三字、六字游戏一轮下来。双击打开就在第2屏出现才符合期望。

下述启动参数方案适合unity引擎的游戏，例如奥日与失落之森、深海迷航、崩坏：星穹铁道（米家全家桶）等。

创建快捷方程式/用启动器，添加启动参数“ -monitor 2”，（没效果就“-”前加空格）

快捷方程式：

![](https://pic1.zhimg.com/80/v2-b907beaaacb0dd096cf57d072a9f42f8_720w.webp)

启动器（我用的第三方Starward）：

![](https://pic3.zhimg.com/80/v2-dcf94f0277a076a7c7959cb3e2a9f0f2_720w.webp)

用到第二屏一般就是放游戏上去挂日常了吧hhh

顺便记录一下原神无边框的方法，启动参数“ -popupwindow”

进入游戏后按Alt+Enter生效。

