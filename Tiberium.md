泰伯利亚功能
==========
Tiberium
---------------

- [储藏和矿井](#储藏和矿井)
- [泰伯利亚泄露](#泰伯利亚泄露)
- [泰伯利亚治愈](#泰伯利亚治愈)
- [泰伯利亚残留](#泰伯利亚残留)
- [泰伯利亚伤害](#泰伯利亚伤害)
- [器官兽](#器官兽)
- [泰伯利亚爆炸](#泰伯利亚爆炸)
- [连锁反应](#连锁反应)

储藏与矿井
----

在更早的游戏中，泰伯利亚与矿石都不能够直接转化为资金。作为代替，资源会被贮存在精炼厂中，然后储存到储藏井。这项萝鸡在红色警戒2里不再有效。Hares恢复了储藏功能。

由矿石精炼器所获得的额外的资金总是转化为现金而非储藏井。这是因为矿井在爆炸时是按照收集数额在原地生成等价矿石，而多余的金钱则不会转化为任何东西。

**提示**

在类似奴隶矿场那样的可移动精炼厂不支持此萝鸡。奴隶矿场不能提供储藏空间，因为它由建筑状态进行反部署时会丢失那些储藏的矿石。

**启用储藏萝鸡**

该萝鸡将同其在TS里一样工作。出于是复原的萝鸡的原因，你需要给储藏矿石的建筑附加一条代码：

    [BuildingType]►Refinery.UseStorage= (boolean)

这条代码决定精炼厂是否会将矿石储存起来而不是化为现金。被直接转化的矿石将不占据储存空间。默认值为no。

**EVA提示**

当储藏空间已经或即将被占满时，EVA会通过一条`EVA_SilosNeeded`语音提示警告玩家。

> *注：*
> 
> *游戏里没有这条语言也没有其对应的文件，在用之前你需要自己找一个加上。（可以直接从ts里拿一个）*

    [General]►Message.SilosNeeded= (csf label)

矿满的时候出现CSF提示

    PipScale=Tiberium

储藏的矿石将以一个特定的`PipScale`表现出来。储藏矿石的建筑将通过格子显示当前有多少被占据的空间，并将其与该建筑的总格数进行直观对比。矿石将显示为黄色，彩色矿石则是蓝色。

若要将该萝鸡用于带有`Refinery=yes`或`ResourceDestination=yes`的建筑上，你还需要添加`Refinery.UseStorage=yes`。这个条件之所以被添加，是因为如果没有的话，游戏会自动让所有未被修改过的矿石精炼厂都带有相应的`PipScale`。


 

> 流程
> 
> 1.游戏规定一个玩家所持有现金的最大数额Cmax，玩家的游戏开局资金不计入其中。设每一座储藏井的储藏量为C0。
> 
> 2.玩家建设一座启用储藏萝鸡的精炼厂。
> 
> 3.采矿车采矿完毕，到精炼厂进行精炼。设精炼开始前玩家现金数额为C，采矿车所提供的矿石价值为C1。
> 
> 4.若C+C1＞Cmax，且玩家有多余的储藏空间，则玩家在精炼完成时的现金数额将达到Cmax，同时游戏自动将矿石按照比例储藏于精炼厂内；若无多余储藏空间，则发出提示EVA_SilosNeeded。（相当于你的额外部分矿石作废）
> 
> 5.若C+C1≤Cmax，则玩家在精炼完成时的现金数额将达到C+C1，此时储藏空间将不会发生变化。
> 
> 6.当玩家已建设n座精炼厂/储藏井时，其当前所持现金的最大数额将增长到Cmax+n*C0。

泰伯利亚泄露
-----------

携带泰矿的单位被摧毁时会泄露泰矿。
 
    [TechnoType]►TiberiumSpill= (boolean)
是否被摧毁时泄露泰矿。默认否

泰伯利亚治愈
------------

某个有该属性的单位（比如器官受）移到泰伯利亚矿上就能回血的设定已经恢复并且可以自由定制。
 
**允许泰伯利亚治愈**
 
注意在`[General]►HoverHeight`高度以上的单位无效
 
    [General]►TiberiumHealEnabled= (boolean)
是否允许泰伯利亚矿可以治疗单位，同时需要以下参数设定。默认否
 
    [General]►TiberiumHeal= (float - minutes)
每多少分钟回血。默认1.13333，即68秒
 
 
**治疗对象**
 
升级能力设定里有TIBERIUM_HEAL的单位可以被治疗
 
    [TechnoType]►TiberiumHeal= (boolean)
有这条语句的单位可以被治疗。默认否。
 
 
**以下参数可以用于调整泰伯利亚矿的治愈值**
 
    [Tiberium]►Heal.Delay= (float - minutes)
治疗间隔，默认为`[General]►TiberiumHeal`
 
    [Tiberium]►Heal.Step= (integer)
对空军的治愈值，默认`[General]►RepairStep`
 
    [Tiberium]►Heal.IStep= (integer)
对步兵的治愈值，默认`[General]►IRepairStep`
 
    [Tiberium]►Heal.UStep= (integer)
对载具的治愈值，默认`[General]►URepairStep`

泰伯利亚残留
--------

有`TiberiumHeal=yes`（而不是`TIBERIUM_HEAL`升级能力）的单位被摧毁时会随机留下泰伯利亚矿，现在这个效果已经脱离泰伯利亚治愈了

    [TechnoType]►TiberiumRemains= (boolean)

该单位被摧毁时是否留下泰伯利亚，默认`TiberiumHeal`当`[General]►TiberiumHealEnabled=yes`开启时，否则不

泰伯利亚伤害
----------

在TS里，一般步兵站在泰伯利亚矿上会受到伤害，并且有几率死亡后变成器官受。

HARES有新的语句来启动该逻辑，此外，高于`[General]►HoverHeight`的单位不会受到伤害。

    [General]►TiberiumDamageEnabled= (boolean)

泰伯利亚是否能够伤害步兵，默认否，同时需要以下语句的设置

**伤害目标**

    [TechnoType]►TiberiumProof= (boolean)

是否免疫泰矿伤害。步兵默认否，其他类型单位是

**泰矿伤害和弹头**

    [Tiberium]►Damage= (integer)

伤害。默认Power / 10（什么玩意儿）, 至少1

    [Tiberium]►Warhead= (warhead)

弹头。默认`[CombatDamage]►C4Warhead`

器官兽
-------

器官受萝鸡已被部分还原。

他们会在地图内乱跑，当两个带有`SmallVisceroid=yes`(而非`[General]►SmallVisceroid`)的载具单位相遇时，他们会合并为`[General]►LargeVisceroid`所规定的载具单位。

EX1友情提示：根据GD所言，`[General]►LargeVisceroid`可能无效，你需要在一个载具单位下添加`LargeVisceroid=yes`以定义该载具是一个`LargeVisceroid`。

注意

器官受目前不会在严重受损时自行跑到一片泰矿上自行回复HP。

当一个步兵单位由于泰矿伤害而致死时，他们有一定几率会转化为`[General]►SmallVisceroid`所规定的单位（如果存在定义）。该逻辑需要地图中存在`[Basic]►TiberiumDeathToVisceroid=yes`以生效。器官受由所属方`Natural`控制。

Hares增加了一条代码以允许自定义各单位的转化可能性。全局代码在TS中就已经存在，但没有任何效果。

    [General]►TiberiumTransmogrify= (integer - percent)

一个因泰矿伤害而死的单位转化为`[General]►SmallVisceroid`的概率。默认值为0。

> *EX1注：该语句在Ares中生效后，其默认概率并非为0，而是40%，该语句最早在TS中存在时后面的数值就是40。*

    [TechnoType]►TiberiumTransmogrify= (integer - percent)

一个因泰矿伤害而死的特定单位转化为`[General]►SmallVisceroid`的概率。默认值为`[General]►TiberiumTransmogrify`。 

泰伯利亚爆炸
--------

当采集了泰矿的采矿车（好像矿仓也可以？不清楚）被摧毁时会爆炸，爆炸威力取决于矿石的量，这个功能还没有完全恢复，有这些语句可以用。

    [CombatDamage]►TiberiumExplosive= (boolean)

是否在采矿车里的泰矿当采矿车被摧毁时产生爆炸，默认否

    [CombatDamage]►TiberiumExplosiveWarhead= (warhead)

在TS里被强制为C4弹头，并且范围固定1.5，现在可以自定义，默认是none 

连锁反应
-----------

某些覆盖物被带有`TiberiumChainReaction=yes`的动画攻击后就会产生泰伯利亚矿爆，在TS里可以产生一系列连锁反应，在YR里这个无效，不过现在可以了，并且有更多自定义。

    [Tiberium]►ExplosionWarhead= (warhead)

矿爆的弹头，默认`[General]►C4Warhead`

注意

TS里的弹头是HE，可以产生连锁反应，而在RA里却是Super，不能产生连锁反应

    [Tiberium]►ExplosionDamage= (integer)

矿爆伤害，默认是`[CombatDamage]►TiberiumExplosionDamage`

    [Tiberium]►Debris.Chance= (integer - percent)

产生碎片的概率，影响到连锁反应的进程，整数，默认33（即33％）

    [General]►OverlayExplodeThreshold=(integer)

伤害高于这个值才会产生矿爆，默认0