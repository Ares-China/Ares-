国家和阵营
=====
Sides & Countries
-----

在原红色警戒2中，阵营和国家在很大程度上都是硬编码内容，无法额外添加，删除，重新排列10个国家/地区或3个阵营。

但是在Hares中，这将成为过去式，现在你可以定义最多16个可以完整的国家/地区。

>实际在Hares中我们可以创建最多32个国家，但是嘲讽语音功能在前16个国家以外将无法正常工作，建议不要超过16个完整功能国家，32个可游戏国家。如有需要，将需要嘲讽语音功能的国家放在前列，之后是其他国家。

## 阵营

阵营需要在`rulesmd.ini`中的`[Sides]`注册

阵营可以被无限创建，但是只有16个国家可以正常工作（见上文）。

- 阵营全局数值
   - 生还者，驾驶员，以及其他
   - AI基础防御
   - 伞兵相关
   - 狩猎者相关
- 用户界面等
   - UI界面
   - 文字颜色
   - 对话框
   - 加载主题
   - EVA
- 记分屏和背景音乐
   - 战役
   - 多人游戏
   - 游戏结束时的图片

## 国家

国家需要在`rulesmd.ini`中的`[Countries]`注册。任何`Multiplay=yes`设置的国家/地区都会显示在国家/地区选择下拉列表中，如果玩家选择“随机”，则可以随机选择。可以将国家排除在“随机国家”选项之外，或者给予不同的权重。

`[Countries]`列表最多可包含32个国家/地区，但嘲讽语音仅适用于其中的16个国家/地区。

- 国家全局数值
   - AI基础建筑
   - 伞兵相关
   - 其他
- 国家界面

------------------------------------------------------------------

---------------------------------------------------------------------

阵营
===

阵营全局数值
-----------

#### 生还者，驾驶员，以及其他

    [Side]►DefaultDisguise= (InfantryType)

间谍出厂时默认的伪装类型

    [Side]►Crew= (InfantryType)

步兵驾驶员类型，该车辆或建筑要有`Crewed=yes`

    [Side]►Engineer= (InfantryType)

基地类的建筑卖掉或者被摧毁出来的工程师。默认`[General]►Engineer`

    [Side]►Technician= (InfantryType)

技术员，某些特殊建筑卖掉或被摧毁时出来。默认`[General]►Technician`

    [Side]►SurvivorDivisor= (integer)

卖建筑炸建筑的残兵数量，越大越少

#### AI基础防御

    [Side]►AI.BaseDefenses= (list of BuildingTypes)

AI用的防御建筑名单

    [Side]►AI.BaseDefenseCounts= (list of integers)

AI的防御建筑数目，数字对应上面


#### 伞兵

    [Side]►ParaDrop.Types= (list of InfantryTypes and/or VehicleTypes)

默认的科技机场伞兵，和国家设定一样，如果国家设定没有就用阵营设定，原有三阵营的默认值就是`YuriParaDropInf`附近那些，你懂的

    [Side]►ParaDrop.Num= (list of integers)

和国家设定一样，如果国家设定没有就用阵营设定

    [Side]►ParaDrop.Aircraft= (AircraftType)

和国家设定一样，如果国家设定没有就用阵营设定

    [Side]►Parachute.Anim= (Animation)

和国家设定一样，如果国家设定没有就用阵营设定。默认使用`PARACH.Parachute.Anim=`
 
#### 狩猎者

    [Side]►HunterSeeker= (VehicleType)

狩猎者超武使用的单位，覆盖全局值的`[General]►GDIHunterSeeker`和`[General]►NodHunterSeeker`。默认`none`

用户界面
----------

    [Side]►Sidebar.MixFileIndex= (integer)

使用`Sidec0*.mix`作为界面

    [Side]►Sidebar.YuriFileNames= (boolean)

是否用尤里的界面`sidec02md.mix`和里面包含的其他内容

    [Side]►ToolTipColor= (R,G,B)

提示文本和分数界面等等的字体颜色第二第三阵营默认`255,255,0`，其余的都是`164,210,255`

    [Side]►MessageTextColor= (Color scheme)

地图触发动作11产生的文本颜色，第二阵营默认6号颜色，第三阵营默认13号颜色，其余的都是11号颜色，在原版rules里，这几个颜色分别是`DarkRed，DarkSky，DarkBlue`

    [Side]►DialogBackground.Image= (filename, *including* the .shp extension)

这个阵营的背景对话框shp，大小452x326，默认`PUDLGBGA.SHP，PUDLGBGS.SHP和PUDLGBGY.SHP`为第一第二以及其他阵营需要设置`DialogBackground.Palette=`

    [Side]►DialogBackground.Palette= (filename, *including* the .pal extension)

色盘默认`DIALOG.PAL`为第一第二阵营，其他阵营`DIALOG.PAL`

    [Side]►EVA.Tag= (EVA event)

Eva文件的设定名，如酥菌的所有都是`Russian`，萌菌的所有都是`Allied`，原NP的第四阵营都是`Fourth`

记分屏和背景音乐
---------------

#### 战役





**对这个不了解的直接去翻原版mix里的相关文件。**

    [Side]►CampaignScore.Background= (filename, *including* the .shp extension)

一个632x568的图片用做背景。使用的色盘定义为`CampaignScore.Palette`。默认是`ASCRBKMD.SHP，SSCRBKMD.SHP`或`SYCRBKMD.SHP`作为第一，第二，第三及其他阵营的背景

    [Side]►CampaignScore.Transition= (filename, *including* the .shp extension)

过渡形态。使用色盘定义为`CampaignScore.Palette`。默认是`ASCRTMD.SHP，SSCRTMD.SHP或SYCRTMD.SHP`作为第一，第二，第三及其他阵营的过渡

    [Side]►CampaignScore.Animation= (filename, *including* the .shp extension)

不断转的那个东西，过渡形态结束后将会循环这玩意儿。使用的色盘定义为`CampaignScore.Palette`。默认是`ASCRAMD.SHP，SSCRAMD.SHP或SYCRAMD.SHP` 作为第一，第二，第三及其他阵营的转动动画

    [Side]►CampaignScore.Palette= (filename, *including* the .pal extension)

色盘。默认是`ASCORE.PAL，SSCORE.PAL`或`YSCORE.PAL`作为第一，第二，第三及其他阵营的色盘

-----------------------------------------------------------------------------------

分数画面的音乐也是可以自定义的。

    [Side]►CampaignScore.UnderParTheme= (theme id)

比最快时间完成得还快时播放这个。默认`SCORE`

    [Side]►CampaignScore.OverParTheme= (theme id)

比最快时间完成得慢时播放这个。默认`SCORE`

 

#### 多人游戏

    [Side]►MultiplayerScore.Background= (filename, *including* the .shp extension)

一个632x568的图片用做背景。使用的色盘定义为`MultiplayerScore.Palette`。默认是`MPASCRNL.SHP，MPSSCRNL.SHP`或`MPYSCRNL.SHP`作为第一，第二，第三及其他阵营的背景

    [Side]►MultiplayerScore.Palette= (filename, *including* the .pal extension)

色盘。默认`MPASCRN.PAL，MPSSCRN.PAL`或`MPYSCRN.PAL`作为第一，第二，第三及其他阵营的背景

    [Side]►MultiplayerScore.Bars= (filename, *including* the .pcx extension)

各种条子，因为是pcx文件所以不需要色盘，一共有10条，编号01到10，写到这条语句里的时候要把编号换成~~，默认是`mpascrnlbar~~.pcx，mpsscrnlbar~~.pcx`或`mpyscrnlbar~~.pcx`作为第一，第二，第三及其他阵营的条子（~~是编号）

----------------------------------------------------------------

    [Side]►MultiplayerScore.WinTheme= (theme id)

战胜的音乐。默认`SCORE`

    [Side]►MultiplayerScore.LoseTheme= (theme id)

战败的音乐。默认`SCORE`

#### 游戏结束时的图片

就是一辆坦克开火，显示游戏结束之类的那张图片，在原版里所有国家都一样，现在可以自定义，这个shp至少要有4帧：战役胜利战败，遭遇战胜利战败。

    [Side]►GraphicalText.Image= (filename, *including* the .shp extension)

图片。默认`GRFXTXT.SHP`

    [Side]►GraphicalText.Palette= (filename, *including* the .pal extension)

色盘。默认`GRFXTXT.PAL`
