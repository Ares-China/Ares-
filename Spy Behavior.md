间谍渗透功能强化
===========
Spy Behavior
-------------

尤里的复仇中只允许间谍的渗透产生一种效果，这是由硬编码的优先顺序决定的。在Hares中，间谍渗透逻辑被重写的更为灵活，包括间谍可以实现一些新的效果。

**以下所有标签默认为no或0**

    [BuildingType]►SpyEffect.Custom= (boolean)

该建筑能否渗透

>必须设置为yes才能使以下任何效果起作用...

#### 雷达

    [BuildingType]►SpyEffect.ResetRadar= (boolean)

是否是雷达，被黑后黑掉地图

    [BuildingType]►SpyEffect.RevealRadar= (boolean)

是否把敌人的地图给你

    [BuildingType]►SpyEffect.KeepRadar= (boolean)

如果启用那么会一直持续效果

#### 电力

    [BuildingType]►SpyEffect.PowerOutageDuration= (integer - frames)

停电时间

#### 钱

    [BuildingType]►SpyEffect.StolenMoneyAmount= (integer - credits)

固定偷多少钱

    [BuildingType]►SpyEffect.StolenMoneyPercentage= (float - multiplier)

偷钱百分比

#### 超级武器

    [BuildingType]►SpyEffect.ResetSuperweapons= (boolean)

重新计时

#### 偷窃科技

    [BuildingType]►SpyEffect.StolenTechIndex= (integer)

这个建筑的偷窃项（0-31）

    [TechnoType]►Prerequisite.StolenTechs= (list of integers)

这个单位需要偷窃这个偷窃具有某个偷窃项的建筑才能被偷出来（0-31），可以多指定几个

 

比如你要弄一个超空间尤里，需要偷窃尤里兵营和盟军机场，那么就可以给兵营的偷窃项设置1，机场设置2，然后超空间尤里设置1,2，这样超空间尤里就必须偷了以上两个建筑才能建造。

 

如果你给[GATECH], [NATECH]或者[YATECH]（总之就是三方高科）设置了`SpyEffect.Custom=yes`， 那么旧的偷窃语句就不再适用。

#### 生产设施


    [BuildingType]►SpyEffect.UnitVeterancy= (boolean)

是否偷窃后能让同类单位出厂老兵

只支持步兵和载具

    [BuildingType]►SpyEffect.RevealProduction= (boolean)

是否可以看到对方在造什么，就像下面那张图

![](https://i.imgur.com/e2t0WgF.png)

逆向工程

取消掉对面所有的逆向工程单位，具体参考[逆向工程逻辑条目](www.baidu.com)
