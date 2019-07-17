光棱塔递光逻辑
==========
Prism Forwarding
--------------

![](https://i.imgur.com/wveWBI3.png)

Hares完全取代了原本的光棱塔代码来修复一些小错误，并且扩展它以提供了一整套额外标签

> 如果你想做的就是保留现有的光棱塔，但是将它们扩展到多个链，就像上面的预发布截图一样，只需设置 `[ATESLA]►PrismForwarding.MaxChainLength=3`或你想要的后向链接数（-1表示无限）。

    [BuildingType]►PrismForwarding.Targets= (list of BuildingTypes)

这个建筑能够递光支援的建筑

    [BuildingType]►PrismForwarding.MaxFeeds= (integer)

最大支援数量，-1表示无限制，默认`[General]►PrismSupportMax`覆盖

    [BuildingType]►PrismForwarding.MaxChainLength= (integer)

反向连接数量，-1表示无限制，默认1，如果要达到上图效果就要设置3

    [BuildingType]►PrismForwarding.MaxNetworkSize= (integer)

如果开火中的塔超过支援的塔，这个标签表示在递光网络的总数，不包括开火中的塔，默认`[General]►PrismSupportMax`覆盖

    [BuildingType]►PrismForwarding.SupportModifier= (float - multiplier)

递光杀伤倍数，默认`[General]►PrismSupportModifier`覆盖

    [BuildingType]►PrismForwarding.DamageAdd= (integer - damage bonus)

增加固定的伤害而不是倍数，默认0

    [BuildingType]►PrismForwarding.MyHeight= (integer - leptons)

递光高度，默认`[General]►PrismSupportHeight`覆盖

    [BuildingType]►PrismForwarding.ToAllies= (boolean)

是否能支援友军的塔，默认否

    [BuildingType]►PrismForwarding.BreakSupport= (boolean)

可以在终止的最后一刻进行支援，而不需要重新充能，默认否

    [BuildingType]►PrismForwarding.ChargeDelay= (integer - frames)

递光时充能的延迟，默认1，最好别动（作者如是说，这玩意儿是用来测试玩的）

    [BuildingType]►PrismForwarding.Intensity= (integer - laser thickness)

随着递光增加激光的宽度

    [BuildingType]►Overpowerable= (boolean)

是否能攻击递光同时进行

    [BuildingType]►PrismForwarding.SupportWeapon= (weapon)

    [BuildingType]►PrismForwarding.EliteSupportWeapon= (weapon)

副武器的递光不再使用而是用这个标签的武器递光



#### 以下标签可以被用来定义支援时的光束武器，都是原版标签。

    [PrismForwarding.SupportWeapon]►Range= (integer - cells)

支援半径，默认主武器射程+1

    [PrismForwarding.SupportWeapon]►MinimumRange= (integer - cells)

最小半径

    [PrismForwarding.SupportWeapon]►ROF= (integer - frames)

支援速率，默认`[General]►PrismSupportDelay`覆盖

    [PrismForwarding.SupportWeapon]►Report= (sound)

支援声音

    [PrismForwarding.SupportWeapon]►IsLaser= (boolean)

是否是激光

    [PrismForwarding.SupportWeapon]►IsElectricBolt= (boolean)

是否是特斯拉

    [PrismForwarding.SupportWeapon]►IsRadBeam= (boolean)

是否是辐射波


 

为了方便计算，压缩包里有个工具可以用来弄这玩意儿

文件地址为Documentation/_downloads/PrismForwarding.xls
