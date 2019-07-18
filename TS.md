Restored Tiberian Sun Logic 
===========================
被恢复的TS逻辑
====================================

在红色警戒2中，很多存在于泰伯利亚之日的游戏功能被删除，而且在尤里的复仇1.001补丁中删除了更多功能，这些有趣的功能，很多无法正常运行甚至已经被完全移除（有时仅仅使用这些逻辑就会导致IE报错）。

### 目录

- [Action=SellUnit](#Action=SellUni)
- [两栖单位水陆切换不同形态](#两栖单位水陆切换不同形态)
- [电磁脉冲](#电磁脉冲（EMP）)
   - 定义EMP武器
   - EMP免疫
   - EMP效果持续时间
   - EMP摧毁单位
   - EMP动画
- [火风暴](#火风暴)
   - 基本设置&全局设置
   - 地图行为
- [激光围栏](#激光围栏)
- [多位工程师](#多位工程师)
- [聚光灯/探照灯](#聚光灯/探照灯])
- [窃车贼](#窃车贼)

<div id="Action=SellUnit"></div>
Action=SellUnit
---------------

#### *缺少翻译校对*

在泰伯利亚之日中，您可以通过侧边栏中的出售按钮来出售*与结构对接的单位*。在尤里的复仇中，一种具有 `Action=SellUnit` 相同功能的超级武器。

但是如果这样的超级武器被释放在坦克碉堡内的一个单位上，就会发生IE报错（有时候效果会延迟到坦克碉堡被破坏）。而在Hares中不会出现这个错误

>In Tiberian Sun you could sell units that were docked with a structure by using the normal Sell button on the sidebar. In Yuri’s Revenge, a super weapon with `Action=SellUnit` achieves the same function. However, if such a super weapon were fired on a unit inside a Tank Bunker then an Internal Error would occur (sometimes this would be delayed until the destruction of the Tank Bunker). Ares prevents the error occurring.

>New in version 0.1.

<div id="两栖单位水陆切换不同形态"></div>
两栖单位水陆切换不同形态
---------------------

在泰伯利亚之日中，两栖APC能够在水中变成另外一种形态，它的素材apc.vxl会改变为apcw.vxl

现在在Hares里可以实现同样的功能：

    [VehicleType]►WaterImage= (VehicleType)

在水中转换为这个单位的素材，参考武装直升机，只是借用壳子,VXL和SHP格式会自动识别，不存在冲突。

<div id="电磁脉冲（EMP）"></div>
[电磁脉冲（EMP）](http://www.baidu.com)
-------

Hares对原Ares的电磁脉冲有额外的更强大的扩展，详情见[电磁脉冲（EMP）](http://www.baidu.com)页面

<div id="火风暴墙"></div>
火风暴墙
------

Firestorm Wall和相应的超级武器现在可以在尤里的复仇中实现。

详情请查阅[[超级武器]](http://www.baidu.com "超级武器")目录下[[火风暴]](http://www.baidu.com "火风暴")相关词条

<div id="激光围栏"></div>
激光围栏
-------

激光栅栏现在能像TS里一样使用. 你需要一个建筑有`LaserFencePost=yes`语句来创建节点（墙柱）, 其他有`LaserFence=yes`语句的建筑之间会以激光连接（具体参考TS）。单位通过就会被摧毁。

> 注意：在当前的Hares版本下，激光围栏在同一MOD中只能存在一套节点和激光墙的对应关系！

<div id="多位工程师"></div>
多位工程师
-----------

在Hares中引入了一种平衡工程师的办法。只有在已经损坏的情况下才能占领建筑物，使攻城狮RUSH变得更加困难。在占领建筑物之前，工程师将会损坏它，直到成功占领。

`EngineerDamage`在尤里的复仇中没有出现。Hares已恢复此功能。

![多位工程师](https://i.imgur.com/Yd1cFFn.png)

    [General]►EngineerCaptureLevel=(float - percent)

多少血以下建筑才能一个工程师占领，在这之前工程师造成伤害

    [General]►EngineerDamage= (float - percent)

工程师占领前一个扣多少血

    [General]►EngineerAlwaysCaptureTech= (boolean)

总是占领科技建筑，无视血量

> 任何归属方拥有`MultiplayPassive=yes`的建筑都被视为科技建筑。此定义可能会在以后的版本中更改。

    [General]►EngineerDamageCursor.*=(cursor definition)

自定义鼠标动作

> 使用合理的默认值。通常，`EngineerDamage`不应该高于`EngineerCaptureLevel`或者可能存在工程师炸毁要捕获的建筑物的情况。

请参阅[Multi Engineer Checkbox](http://www.baidu.com)以使用户能够从游戏菜单中打开和关闭Multi Engineer选项。如果未启用该复选框，游戏将强制执行中定义的设置`rulesmd.ini`。

![UI-多位工程师](https://i.imgur.com/J748yBE.png)

    [UISettings]►AllowMultiEngineer= (bool) 

启用多位工程师勾选框

> 目前只有遭遇战菜单支持更改Multi Engineer选项。这也许在以后会改变，以支持网络和在线游戏。
> 
> 编者注：目前通过DTA已支持多人游戏的Multi Engineer选项

<div id="聚光灯/探照灯"></div>
聚光灯/探照灯
-----------

现在探照灯已经能够正常使用，并且更强大。

    [Unit]►HasSpotlight= (boolean)

是否使用探照灯，现在探照灯能够用于单位，建筑上的按原样扫描，车上的只能往前

    [Unit]►Spotlight.StartHeight= (integer - leptons)

探照灯射出的高度，默认430

    [Unit]►Spotlight.Distance= (integer - leptons)

探照灯射出的距离

    [Unit]►Spotlight.AttachedTo= (enumeration - one of body|turret)

从单位的哪个单位射出来，车体，炮塔或炮管？

    [Unit]►Spotlight.DisableRed= (boolean)

    [Unit]►Spotlight.DisableGreen= (boolean)

    [Unit]►Spotlight.DisableBlue= (boolean)

光照参数（不使用红色，绿色，蓝色）

    [Unit]►Spotlight.DisableColor= (boolean)

黑灯

<div id="窃车贼"></div>
窃车贼
------

Hares能够在不使用`Thief=yes`等语句的情况下允许窃车逻辑，具体参考[劫车犯](http://www.baidu.com)条目。
