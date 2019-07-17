建筑微损伤
==========
Trivial Structure Damage
-----------------------

在早期的游戏如TD和RA里建筑没电就会逐渐掉血，现在你也可以这样做。伤害弹头使用`[General]►C4Warhead`。

#### 全局设置

    [General]►Degrade.Enabled= (boolean)

是否启用该逻辑，伤害频率由`DamageDelay`定义

    [General]►Degrade.Percentage= (double - percentage)

损伤持续到建筑总血量的百分之几，1为不会损伤，0为损伤到建筑摧毁。默认黄血就停止损伤，即`[AudioVisual]►ConditionYellow`


    [General]►Degrade.AmountNormal= (int - hitpoints)

电力充足时损伤伤害，默认0

    [General]►Degrade.AmountConsumer= (int - hitpoints)

电力不足时损伤伤害，默认1

#### 微观设置

    [BuildingType]►Degrade.Percentage= (double - percentage)

损伤持续到多少停止。默认`[General]►Degrade.Percentage`


    [BuildingType]►Degrade.Amount= (int - hitpoints)

伤害量，默认电力充足时和`[General]►Degrade.AmountNormal`一样，其他情况`[General]►Degrade.AmountConsumer`


#### 国家设置

    [Country]►Degrades= (boolean)

是否该国家启用该逻辑，有`MultiplayPassive=yes`的国家默认no，其他yes

    [House]►Degrades= (boolean)

同上，不过这个是用于任务的，默认`[Country]►Degrades`
