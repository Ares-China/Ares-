Introduction - 基本介绍
============
Hares是扩展Yuri Revenge功能的新工具.....

【关于Hares的介绍】

兼容性说明
---------
【关于兼容性的内容】

已知主要问题
----------
### 保存游戏
Hares现已支持保存游戏
>Hares保存游戏是否会影响光照？【存疑】

使用Hares对Mod进行必要的更改
--------------------------
### artmd.ini
<div id="artmd.ini"></div>
>[TELE]►SecondaryFireFLH=85,0,130

See [RadBeams And Waves Using The Wrong FLH.](http://www.baidu.com "【还没翻译】")

### bombcurs.shp
<div id="bombcurs.shp"></div>
>bombcurs.shp

如果你不想看到以前没有用过的头骨图像，这个动画需要删除最后一帧。

详见[IvanBomb.FlickerRate.](http://www.baidu.com "IvanBomb.FlickerRate.")

The `bombcurs.shp` animation needs to have its last frame removed if you don’t want to see the previously unused skull image. See IvanBomb.FlickerRate.

### ares.mix
<div id="ares.mix"></div>

Mods不应该包含他们自己的版本`ares.mix`。这个新的MIX文件与Ares捆绑在一起，以提供Ares 更改/添加所依赖的任何新/修改的文件。此MIX文件目前包括：

`ares.csf` 包括一些新的字符串：

- GUI:SelectCampaign=Select your Campaign
- GUI:PlayMission=Play
- GUI:UrbanAreas=Create Urban Areas
- Name:Desert=Desert
- STT:RMGUrbanAreas=Choose whether urban areas will be present on the map.
- STT:MultiEngineer=Engineers can capture damaged buildings only.
- STT:PlayerColorLilac=Choose this to be lilac.
- STT:PlayerColorLightBlue=Choose this to be light blue.
- STT:PlayerColorLime=Choose this to be lime.
- STT:PlayerColorTeal=Choose this to be teal.
- STT:PlayerColorBrown=Choose this to be brown.
- STT:PlayerColorCharcoal=Choose this to be dark grey.
- TXT_COMMAND_DISABLED=The %s command is not available.
- TXT_RELEASE_NOTE= (empty text)
- TXT_SCRNCAP_DESC=Take a snapshot of the game screen. (Saved as ‘SCRN.date-time.BMP’ file in Red Alert 2 run directory.)
- TXT_RELEASE=Launch
