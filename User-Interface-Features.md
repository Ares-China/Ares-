用户界面功能
==========
User Interface Features
------------------------

- [位图截图](#位图截图)
- [战役列表](#战役列表)
- [战役载入界面](#战役载入界面)
- [命令行参数](#命令行参数)
- [自定义战役按钮](#自定义战役按钮)
- [可定制的玩家颜色](#可定制的玩家颜色)
- [图形/曲面的绘制](#图形/曲面的绘制)
- [内部错误IE/抓虫](#内部错误IE/抓虫)
- [热键](#热键)
- [载入屏幕](#载入屏幕)
- [单人遭遇战](#单人遭遇战)
- [菜单自定义](#菜单自定义)
- [MOD信息](#MOD信息)
- [分辨率](#分辨率)
- [随机地图生成器](#随机地图生成器)
- [开放游戏标签](#开放游戏标签)
- [用户界面颜色](#用户界面颜色)

位图截图
----------

现在截图出PCX而不是BMP，PCX比BMP更小且支持更广泛。

战役列表
----------

如果你的战役数量超过默认数量，你可以选择使用TS风格的战役列表。ARES能随意定制战役数量，在battlemd.ini里的非测试地图都会展现在下面的列表里，由Description=来定义。

![](https://i.imgur.com/Ln036nY.png)

在`uimd.ini`：

    [UISettings]►CampaignList= (boolean)
允许使用这种列表，默认否
 
    [UISettings]►ShowDebugCampaigns= (boolean)
在战役列表里显示`DebugOnly=yes`设置的地图. 默认否
 
自定义战役于`battlemd.ini`：
 
    [Battle]►HoverSound= (sound)
选择战役的时候出现这种声音。默认 `AlliedCampaignSelect，SovietCampaignSelect和BootCampSelect`

    [Battle]►Summary= (CSF label)
展现战役介绍在难度条下面

战役载入界面
-----------

**战役载入文本颜色**

YR一直用红色作为战役载入文本的颜色，现在能用这个`missionmd.ini`标签自定义。

    [Mission]►LoadScreenText.Color= (Color scheme)
使用`[Colors]`列表里的颜色，比如`LoadScreenText.Color=AlliedLoad`

**主题音乐**

现在每个单人任务或遭遇战都可以自定义载入时的主题音乐，需要用记事本打开地图自己写进去。

    [Basic]►LoadingTheme= (theme id)
载入任务时的音乐（必须用`thememd.ini`里写的），写none就是没音乐。默认是`LOADING`

    [Country]►LoadingTheme= (theme id)
用该国家玩遭遇战时的载入音乐。默认是`LOADING`

命令行参数
---------

-CD 免CD

-NOLOGO 不载入EASB的LOGO

-LOG 产生debug.log日志文件

-LOG-CSF 把csf缺失写进去

-STRICT 把ie写进去

-AI-CONTROL 允许玩家控制AI

自定义战役按钮
-----------

可以弄4个任务入口，自定义于`uimd.ini`。

![](https://i.imgur.com/Iorwcfw.png)

把X换成1234来使用

    [UISettings]►CampaignX= (battle)
按按钮从哪关开始，必须在`battle.ini`里有，如果要隐藏按钮就写`CampaignX=no`。默认`ALL1，SOV1，TUT1`或`norespectively`


    [UISettings]►CampaignX.Image= (filename, *including* the .shp extension)
按钮的样子，大小260x136，可参考`fsalg.shp`。默认`fsalg.shp`或`fsslg.shp`


    [UISettings]►CampaignX.Palette= (filename, *including* the .pal extension)
色盘。默认`fsalg.pal`，`fsslg.pal`或`fsbclg.pal`


    [UISettings]►CampaignX.Subline= (CSF label)
按钮下方的CSF。默认为`STT:AlliedCampaignIcon`，`STT:SovietCampaignIcon`或`STT:CampaignAnimTutorial`


    [UISettings]►CampaignX.Tooltip= (CSF label)
把鼠标放在按钮上底部工具条显示的CSF。默认为`CampaignX.Subline`


要调整把鼠标放在按钮上的语音参见战役列表的`HoverSound=`

可定制的玩家颜色
-----------

在uimd.ini里改，可以定制16种：

    [Colors]►Count= (integer)
要显示的颜色数，8-16
 
    [Colors]►SlotX.DisplayColor= (R,G,B)
第几个颜色显示的颜色

    [Colors]►SlotX.ColorScheme= (Color scheme)
在`rulesmd`的`[Colors]`定义配色方案的名称

    [Colors]►SlotX.Tooltip= (CSF label)
底部工具条显示的CSF
 
> Slot ID MenuColor ColorScheme ToolTip Note
> 
> Slot1 221,226,13 Gold STT:PlayerColorGold
> 
> Slot2 255,25,25 DarkRed STT:PlayerColorRed
> 
> Slot3 42,116,226 DarkBlue STT:PlayerColorBlue
> 
> Slot4 62,209,46 DarkGreen STT:PlayerColorGreen
> 
> Slot5 255,160,25 Orange STT:PlayerColorOrange
> 
> Slot6 50,215,230 DarkSky STT:PlayerColorSkyBlue
> 
> Slot7 149,40,189 Purple STT:PlayerColorPurple
> 
> Slot8 255,154,235 Magenta  STT:PlayerColorPink
> 
> Slot9 148,93,239 NeonBlue STT:PlayerColorLilac
> 
> Slot10 115,255,231 LightBlue STT:PlayerColorLightBlue
> 
> Slot11 255,239,99 Yellow STT:PlayerColorLime
> 
> Slot12 8,195,90 Green STT:PlayerColorTeal
> 
> Slot13 189,85,0 Red STT:PlayerColorBrown
> 
> Slot14 128,128,128 Grey STT:PlayerColorCharcoal
> 
> (others) 255,255,255 LightGrey NOSTR:
> 
> Observer 96,96,96 LightGrey STT:PlayerColorObserver

图形/曲面的绘制
------------

#### ARES开发者：谨慎使用！

> **编者注：建议菜鸡绕开本条**
 
在`ares.ini`里可以添加如下:
 
    [Graphics.Advanced]
    DirectX.Force= (hardware|emulation)
 
While hardware is the default, emulation has the same effect as the special ddraw.dll which made the games faster by not drawing the effects that aren’t supported by software emulation.
 
> emulation is not available on Windows Vista and later. Ares defaults to hardware on such systems.
 
> Ares.ini is not intended to be included or edited by mods, as this file may include various other settings in future that the end-user wishes to set themselves. Launch Base does not permit mods to include ares.ini, and also provides its own interface to allow the user to modify the above graphical settings.

内部错误IE/抓虫
-------------

IE时就会改变except.txt的内容，HARES对此进行了增强。

except.txt可以附带产生时间来防止现有的except.txt被覆盖。

HARES会让你选择是否产生崩溃转储文件来帮助确定导致错误的原因.该文件将被存储在一个调试在游戏主目录的文件夹（debug），请注意，崩溃转储文件是非常大的。

如果你打开调试日志记录（见命令行参数和调试记录）然后游戏会产生debug.log文件在上述调试文件夹，像except.txt，该文件将包含在文件名中的一个时间戳。日志文件可能包含有用的信息用于帮助诊断问题与您的MOD或ARES本身。

这样HARES就能告诉你是什么导致了IE。

例如:

![](https://i.imgur.com/EXOyFjT.png)

![](https://i.imgur.com/D8LR2Ec.png)

![](https://i.imgur.com/PNYvQ0F.png)

热键
---

HARES允许自定义热键，但是键盘代码已经被引擎定死，没法用特制的。

截地图
将现在的游戏保存为地图，之后就随便你用FA2载入这个YRM了
生成的地图文件加载游戏产生内部错误，因为雷达的预览图像没有保存，在地图文件里添加`[Preview]►Size=0,0,1,1`

该命令可以禁用，自行查看禁用键盘命令条目

抓虫子日志
自行查看抓虫子条目

数据类型释放（什么玩意儿...）
该功能能输出额外的信息到debug.log，这里面包括AI信息，所以mod作者可以看到AI的执行进程. 注意`debug.log` 文件写入必须打开否则无效

该命令可以禁用，自行查看禁用键盘命令条目

AI接管控制
自行查看命令行参数-AI-CONTROL

该命令可以禁用，自行查看禁用键盘命令条目

FPS帧数
显示帧数
 
切换电源
自行查看切换电源条目
 
 
禁用键盘命令

能禁用键盘命令
 
    [GlobalControls]►DebugKeysEnabled= (boolean)
抓虫子热键是否允许，默认是。
 
CSF显示给玩家的是`txt_command_disabled`，你可以重写此CSF。可以包括一个（不能更多）“`%s`”占位符，它将被禁用键盘命令的名称替换。
 
请注意，这不是一个安全功能，也没有任何一种真正的保护，这个参数仅仅是为了方便，使它难以从游戏中提取特定的文件。

载入屏幕
-------------

会显示版本信息之类的玩意儿。

单人遭遇战
-------------

无需AI，一个人也能开遭遇战。

菜单自定义
------------

![](https://i.imgur.com/mH62ZF4.png)

在`uimd.ini`里添加修改：

    [UISettings]►SinglePlayerButton= (action)

单人游戏

    [UISettings]►NetworkButton= (action)

局域网

    [UISettings]►WWOnlineButton= (action)

国际网络

    [UISettings]►MoviesAndCreditsButton= (action)

电影和制作人员名单

    [UISettings]►CampaignButton= (action)

战役


    [UISettings]►SkirmishButton= (action)

遭遇战

    [UISettings]►SneakPeeksButton= (action)

先睹为快

    [UISettings]►PlayMoviesButton= (action)

放小电影

    [UISettings]►ViewCreditsButton= (action)

制作人员

以下是可用动作:
> default：不变
> 
> disable：放在那但是没法点
> 
> hide：隐藏
> 
> message：点击会显示确认框里面的CSF是TXT_X_MSG，X相当于这玩意儿的名称
> 
> credits：开始看制作人员名单
> 
> sneakpeek：看先睹为快

MOD信息
--------

可以给你的MOD取名和指定版本号，只有在debug日志里可以看到
 
在`uimd.ini`里写：
 
    [VersionInfo]►Name= (string)
MOD名称，不要超过63字节。默认`Yuri’s Revenge`

    [VersionInfo]►Version= (string)
MOD版本号，不要超过63字节。默认`1.001`

分辨率
----

不用在RA2MD里写`AllowHiResModes`也能自定义分辨率，最大`4096x4096`。

随机地图生成器
----------

可以做群岛和沙漠，在有河流的地形还会有桥。
 
可以搞城市了，要把`[URBAN]`添加到`rgdmd.ini`然后在`Structure=`，`Vehicles=`和`Infantry=`之后添加以下语句：
 
    [URBAN]►Structures= (list of BuildingTypes)

会出现的建筑。默认`CABUNK01,CABUNK02,CAARMY01,CAARMY02,CAARMY03,CAARMY04,CACHIG03,CANEWY01,CANEWY14,CANWY09,CANWY26,CANWY25,CATEXS07`
 
    [URBAN]►Vehicles= (list of VehicleTypes)
车辆。默认`TRUCKA,TRUCKB,COP,EUROC,SUVW,SUVB,FTRK,AMBU`
 
    [URBAN]►Infantry= (list of InfantryTypes)
平民。默认`CIV1,CIV2,CIV3,CIVA,CIVB,CIVC`
 
**沙漠地形用这个可能出问题。**

开放游戏标签
----------

如果你的MOD还处于开发阶段可以用这个来显示信息。

这个文本包含版本号，警告和其他细节。

在CSF里叫做`TXT_RELEASE_NOTE`，要在`stringtable`文件里改（而非`ra2md.csf`）来允许这个标签。

用户界面颜色
-----------

可以定制界面上字的颜色。

在`uimd.ini`里改，全是RGB格式

观察者的颜色貌似没法改的样子。
 
    [UISettings]►Color.Border1= (R,G,B)
第一颜色控制边界的划定。默认167,190,197

    [UISettings]►Color.Border2= (R,G,B)
第二颜色控制边界的划定。默认104,122,128

    [UISettings]►Color.Text= (R,G,B)
所有文本的默认颜色，不影响观察者的颜色`Color.Observer.Text`，默认55,255,0(黄色)

    [UISettings]►Color.X.Text= (R,G,B)
对于某些类型的控件的文本颜色，X可以是一个按钮，标签（描述），列表，复选框，组合框 （下拉列表），观察者（下拉列表中，选择与观察者），GroupBox（框架），滑块，或编辑 （文本框）。默认238,238,238（浅灰色）为观测器，即`[UISettings]►Color`，除了文本

    [UISettings]►Color.Selection= (R,G,B)
选择项目的默认背景色。默认255,0,0(红色)

    [UISettings]►Color.X.Selection= (R,G,B)
对于某些类型的控件选定项的背景色，X可以是一个列表，ComboBox（下拉列表）或观察者（下拉列表中选择与观察者）。默认98,98,98（深黑）
 
    [UISettings]►Color.Disabled= (R,G,B)
禁用控件的默认文本颜色绘制。默认159,0,0（深红）
 
    [UISettings]►Color.X.Disabled= (R,G,B)
对某些类型的禁用控件的文本颜色，X可以是一个列表，ComboBox（下拉列表），观察者（下拉列表中选择与观察者）或滑块。默认167,0,0（深红) 按键，143,143,143（灰色）观察
 
此功能不支持重新着色启动游戏时对话框提示为插入尤里的复仇磁盘。