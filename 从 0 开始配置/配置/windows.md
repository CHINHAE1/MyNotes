
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

在Windows 10中，通过注册表删除开机启动项的步骤如下‌：

‌打开注册表编辑器‌：按下Win + R键，输入regedit，然后按回车键，打开注册表编辑器。
‌导航到启动项的位置‌：注册表中的启动项通常位于以下几个位置：
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run：这是用户级别的启动项，删除这些项目通常不会影响系统运行。
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run：这是系统级别的启动项，通常是第三方软件的驱动程序。删除这些项目时需要谨慎，以免影响系统正常运行。
HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Run：这个位置通常包含与操作系统正常运行相关的启动项，删除时需要特别小心。
‌删除启动项‌：在注册表编辑器中，找到上述路径下的相应启动项。右键点击要删除的项目，选择“删除”。删除前建议先备份注册表，以防误操作导致系统问题。
‌注意事项‌：

在修改注册表之前，务必创建备份，以防不小心修改导致系统问题。
删除注册表项时需要谨慎，尤其是系统级别的启动项，错误的操作可能会对系统造成不可逆的损伤。
如果不确定某个启动项的作用，可以先禁用而不是直接删除，观察系统反应再决定是否彻底删除。
通过以上步骤，你可以有效地管理和删除Windows 10的开机启动项，从而提高系统启动速度和性能‌


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

