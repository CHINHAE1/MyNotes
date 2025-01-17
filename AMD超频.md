# AMD通用Pbo超频教程（AM5CPU）

## 1.CPU的频率及限制

### 1.1 打开PBO 操作:

华硕主板:

![Uploading image.png…]()




微星主板:

![image-20250117183612129](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117183612129.png)



最新的x870主板bios

![image-20250117183649122](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117183649122.png)



### 1.2 打开AMD Overclocking

![image-20250117183850625](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117183850625.png)



选择accept,没有提示这个也没事



### 1.3 precision boost overdrive

然后我们就会看到 precision boost overdrive选项

在这里我们回车选中auto将其改为advanced

下面就会弹出详细的pbo选项设置

首先是pbo limits

这个选项即pbo的电流电压功耗的限制选项

![image-20250117184158171](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117184158171.png)



选择Manual,便能看到电流,电压和功耗三个可供调整的选项

![image-20250117184229003](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117184229003.png)



那么请注意这里不同的主板其单位可能有所不同

有的主板是安A和瓦W，有的呢则是mA/mW

那么不同的CPU其应当设置的限制并不一致

所以建议各位小自直接选择motherboard选项

![image-20250117184357880](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117184357880.png)



### 1.4 Precision Boost Overdrive scalar control

这个选项是pbo标准量

就是CPU的性能以怎样的一个标准量去进行提升

选择manual后,这个选项有1x~10x差可供选择

*选择10x*



### 1.5 CPU boost clock override

就是增加CPU频率的超频选项

我们应当将这里的选项改为Enable positive

Amd官方将pbo的频率 上限设置到了200,也就意味着我们将频率设置为200时,CPU的最高睿频会增加200

比如7500f默认状态下最高睿频为5ghz,在这里200频率后,其最高睿频会达到5.2ghz

这里并不是所有的CPU都能够给到最高上限的200频率,如果你的CPU体质较差可能就会无法稳定运行,所以这里也需要根据实际情况进行动态调整



![image-20250117184957371](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117184957371.png)



建议小白从100起手,再根据实际运行情况进行动态的增减



### 1.6 Platform thermal throttle limit

也可能不是直接显示Platform thermal throttle limit

那就可能是这样(Platform thermal throttle ctrl改成manual,会显示Platform thermal throttle limit)

这个就是温度墙

![image-20250117185233151](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117185233151.png)



9800x3d我个人建议设置在95度

7800x3d我个人建议设置在85度

那么7500f我个人建议设置为90度或95度

当你在pbo中将CPU的频率及各种限制正确设置好之后,就到了给CPU进行负压的阶段



## 2.CPU负压

### 2.1 curve optimizer

往下移动两格,选择curve optimizer 选项

这里就是给cpu进行负压的地方,负压的意思就是给CPU降低电压

也就是这一整套pbo的超频的含义就是让CPU在更高的频率以更低的电压来运行

![image-20250117185701095](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117185701095.png)

![image-20250117185715158](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117185715158.png)

![image-20250117185952534](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117185952534.png)



打开curve optimizer选项后,有All Cores,Per core,Per CCD

all cores就是全核负压,也就是所有的核心统一给完全一致的负压值

Per core就是每一个核心分别给不同的负压值

per ccd是在一些双CCD的CPU上可以使用,所以这个设置就是让你能够给不同的ccd分别给定负压值

CCD是什么意思:例如9950×具备16核心32线程,Amd为了分散核心压力,更好地堆核心数,便会将16个核心分为两个具有8个核心的ccd,也就是说每个ccd会是8个核心,两个 ccd组合形成16核心



小白选择全核负压

Per core分核负压,需要借助软件测量出每一个核心最合适的负压值

![image-20250117190358391](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117190358391.png)



选择all cores后,下面这个选项选择negative(negative就是减少,Positive是增加)

最后在第三个选项中我们就需要手动填入你需要负压的值

这个值就意味着你减少多少电压

数值越高所减少的电压就越多，数值越低所减少的电压就越少

如果CPU体质越好,这个负压的值就能给的越高

![image-20250117190653158](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117190653158.png)

![image-20250117190632595](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117190632595.png)



以10或者15的数值为第一次尝试的数值

然后都设置好之后进入系统跑满载压力测试

根据CPU实际运行的电压,温度来进一步调整负压值以及前面所讲到的cpu频率

例如在你进行满载压力测试的时候,你的CPU温度已经十分接近温度墙了,电压值也相对较高

但是此时你能够稳定通过满载压力测试,那么你就可以选择在负压选项中增加负压值,增加到你不能过测为止

使用r23通过30分钟的稳定性测试



## 3. 观察CPU频率,电压,温度
![image-20250117191018757](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117191018757.png)

![image-20250117191134826](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117191134826.png)



## 4.DDR5内存同步超频教程

### 4.1 打开EXPO

EXPO厂家会预设两套数值,选择详细看看

EXPOtweaked就是华硕的高效能模式



![image-20250117191550944](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117191550944.png)

![image-20250117191715501](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117191715501.png)

![image-20250117191735829](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117191735829.png)



主板厂家也有自动纠正小参以及内存自动超频的功能

例如微星的memory try it与  High-efficiency mode（高效能模式）

华硕的EXPO tweaked（高效能模式）

![image-20250117191942525](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117191942525.png)

![image-20250117192038481](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117192038481.png)



这里的微星memory try it,就是内置了更多的超频预设参数可供选择

其余都是主板进一步自动优化内存参数的选项

在低频同频的情况下都建议开启

![image-20250117192123991](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117192123991.png)



其中微星的高效能模式在开启后还有更多档位可供选择

从上到下等级依次递减

建议优先选择balance平衡档

![image-20250117192210388](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117192210388.png)





### 4.2 频率调整

![image-20250117192336504](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117192336504.png)

![image-20250117192346298](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117192346298.png)





### 4.3 调整FCLK

![image-20250117192423720](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117192423720.png)

![image-20250117192458087](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117192458087.png)



这个设置是影响AMD内存读写和延迟的关键设置

在AMD23年8月更新微码开放异步高频超频之前,AMD的D5内存受到高延迟垢病,均是以同步低频的模式设置

即让UCLK与 MCLK同步1：1运行,而FCLK则实际运行在内存设置频率的三分之一,此时能达到最佳运行状态

反映到实际参数上就是当你内存频率设置为6000时,FCLK设置为2000,就能获得最佳延迟表现

但是FCLK同样影响着读写效能,也就是AID64测试出来的读取写入复制参数,FCLK越高，读写效能便会越强,生产力表现会相对更强

但网游更多是依赖延迟的表现,则更加建议设置在三分之一



### 4.4 锁定同步模式

FCLK设置好后，就需要锁定同步模式

即设置UCLK=MCLK

该选项在各大主板均称之为 UCLK DIV1 mode/模式

![image-20250117193000351](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117193000351.png)

![image-20250117193033081](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117193033081.png)



除华硕主板需要在其Dram timingcontrol选项,进入小参调整页面往下使劲儿翻之外,微星技嘉映泰等主板均在FCLk设置选项的下方即可找到

![image-20250117193103529](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117193103529.png)





### 4.5 PDM 和 MCR

接下来就要讲两个需要同步开启和关闭的选项

power down mode 和 memory context restore

这两个模式在进行超频时都建议关闭,能提高超频参数的稳定性

前者是内存节能,你可以理解为省电模式,后者是内存上下文恢复,开启后在第一次内存参数设置自检完成后,后续开机内存就会快速自检,开机速度会很快,但是会影响内存超频参数稳定性,所以如果你要超频，请二者同时关闭,但关闭后的开机时间增加,则是你需要理解并接受的问题



这两个选项华硕主板前面讲到的UCLK Dlv1mode 的上面

![image-20250117193251103](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117193251103.png)

![image-20250117193322511](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117193322511.png)

![image-20250117193337646](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117193337646.png)





### 4.6 gear down mode/iommu/tsme



对于小白玩家超频而言,全部自动即可

Gear down 模式是一种兼容模式,是以前为了解決AMD内存兼容性差的问题的产物,但在AM5平台7000/9000系CPU而言,这个选项已经相对不重要了

并且如果你的超频参数本身已经极限稳定的话,再关闭这个模式你会发现原本稳定的参数会不稳定了

![image-20250117193717712](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117193717712.png)





### 4.7 内存电压VDD/VDDQ

VDD/VDDQ/VPP

有的主板需要先打开高电压模式,才能拉高内存电压以供超频



微星DRAM High Voltage Mode,选择允许

![image-20250117194101811](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117194101811.png)



华硕主板,找到 high DRAM voltage mode选择开启高电压模式后,在其下方便是VDD/VDDQ电压

其VPP电压则需要进入更下方的Advanced memory voltage选项中调整

![image-20250117194210442](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117194210442.png)

![image-20250117194320593](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117194320593.png)





首先是VDD/VDDQ,主要是影响内存的频率和小参,频率越高/时序越低,这两个电压就需要越高

其中VDD与频率关联更大,VDDQ与小参关联更大



而在低频同频中,如果你是6000C28/C30或者6200C28/C30或者 6400C32/C30/C28

一般就选择填入1.4/1.45/1.5即可

具体多少就是前面说的频率越高/时序越低,这两个电压就需要越高





严重警告！

此处微星主板在调整VDD/VDDQ电压是会自动把后面要说的cpu IO电压同步为一样的数值

![image-20250117194701456](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117194701456.png)

![image-20250117194718195](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117194718195.png)





频率、小参、电压的实际运行值都会影响到内存运行温度

对于一些耐温性差内存条来说,温度超过60度就会导致运行不稳定的情况产生,实际游戏时可能就会崩溃闪退蓝屏等

对于一些耐温性强,体质更好的内存条来说,70度可能才会出现问题

如果耐温性差内存条请在进行高负载压力测试时将温度控制到60度以内,同时为夏天留出余量





### 4.8 内存电压VPP

VPP电压你可以理解为内存启动电压

这个电压只要给足了就行,默认一般是1.8V,在同步超频 非极限时给到1.9V即可

![image-20250117195108588](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117195108588.png)





## 5. CPU电压

### 5.1 SOC电压

这里 非极限超频情况下常用的电压就SOC电压与IO电压

这两个电压即与 cpu内存控制器、 FCLK、 IO电路相关

华硕 映泰等主板则就是CPU SOC电压

![image-20250117195319187](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117195319187.png)





微星主板中为cpu NB/SOC voltage

![image-20250117195244706](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117195244706.png)





当你在内存同步模式下,你的内存控制器频率,也就是UCLK会与内存保持同步

因此相对异步超频会高出许多,内存控制器的压力较大,就需要拉高SOC电压以保证稳定运行

所以这里soc电压我建议以1.25V起手,再根据实际情况动态调整

且这个SOC电压的安全上限为1.3V,有的主板也将该电压上限锁到了1.3



### 5.2 IO电压

而IO电压在各大主板名称几乎都不一致



在华硕主板中称为cpu VD DIO/ MC Voltage

![image-20250117195540714](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117195540714.png)



微星主板中称为 CPU VD DIOvoltage

![image-20250117195616553](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117195616553.png)





这个io电压在安全稳定的情况下,请尽量控制在1.45V以内

可以先起手1.4V,根据实际运行情况动态增减少



## 6. 电压调整

接下来就讲这几个电压具体如何调整

思路

就是在你正确设置了小参之后,通过TM5压力测试的报错来调整

例如你设置1.4V时,正确跑TM5的压力测试,5分钟10个报错

这时你可以将该电压增加0.01,只调这一个

如果5分钟报错只有5个了,那就说明增加0.1的方向是正确的

如果报错增加了0.01后5分钟到了20个了,那就说明这个电压不应该在增加,应该降低

通过这种方式,挨个找到上述5个电压的最合适的值即可





你的内存CPU主板足够好的话

我上面说的通用起手电压,基本上就能一次过测，无需再次调整

例如6000c30设置为VDD1.4/VDDQ1.4/VPP1.9/SOC1.25/IO1.4

基本上正常Adie颗粒，正常CPU体质,非究极丐板，基本上都是能过测的

当然你小参也得设置正确



## 7.  内存小参

### 7.1 第一套6000频率

tcl也就是主时序,建议30 28,这个数值调整的差值为2

tRCD和tRP建议起手40,这两个的数值一定要高于第一个小参,上下调整的差值也建议是2,最小的也要比第一个小参高出6-8个数值

tRAS这个最低可以比上面的两个RCD与RP低2个数值,但同样要高于第一个小参tcl,这里通用小参建议给到46

接下来这个tRC上下调整的幅度可以相对较大,但最低不要低于tRCD与tRP这两个小参之和,建议起手100

例如:当你的tRCD与tRP设置为40时,个人建议最低请不要低于80

tWR这个小参,这个小参数值调整的差值为6,最低不可以低于48,通用小参先给到72

trfc1/2/SB这三 个小参调整的差值可以为10或者50

个人建议小自玩家tRFC1最低不低于500,tRFC2最低不低于350,tRFCSB最低不低于300,通用小参我建议给到600/500/400

微星tREFI,在华硕主板称之为 refresh interval,默认给65535,给不上就给65533

Trtp这个小参上下调整的差值也为2,同步低频的情况下最低不要低于12,通用小参建议先给到20

tRRD_L这个小参,大家上下调整的差值也为2,最低也要比tRRD _ S高4个数值,也就是12,通用小参建议先给到16

tRRD_S和tFAW这两个小参,小白玩家tRRD _ S这个小参无脑给8,tFAW无脑给32

tWTR _L 与tWTR _S,tWTR_L 的数值也需要大于tWTR_S,两个数值的上下调整差值也为2,tWTR_L最低不要低于16,tWTR _S最低不要低于4,通用小参建议26和8

![image-20250117202626555](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117202626555.png)



### 7.2 6400频率

![image-20250117213916311](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117213916311.png)

![image-20250117213926416](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20250117213926416.png)
