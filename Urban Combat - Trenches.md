巷战-战壕
===========
Urban Combat - Trenches
--------------

#### 战壕和掩体

巷战时武器能对这个建筑内的人进行多少百分比的攻击而不仅仅是对建筑本身攻击，用来做战壕和掩体。

    [BuildingType]►UC.PassThrough= (float - chance)

有多少几率攻击能够穿透这个掩体攻击到里面的步兵，默认0

    [BuildingType]►UC.FatalRate= (float - chance)

如果武器能够攻击到驻兵，一击必杀的几率，默认0

    [BuildingType]►UC.DamageMultiplier= (float - multiplier)

如果武器能够攻击到驻兵，伤害倍率

    [Projectile]►SubjectToTrenches= (boolean)

该弹体是否无视UC.PassThrough，100%命中驻兵，yes的话UC.PassThrough依然有效，no的话直接贯通，默认是

![](https://i.imgur.com/FZgxcjR.png)

![](https://i.imgur.com/pZnP8LB.png)

#### 掩体占领者

这个功能能允许敌人的步兵进入自家的战斗碉堡。

    [BuildingType]►Bunker.Raidable= (boolean)

这个建筑能否被敌人步兵占据

当被敌人占领时所属权属于敌人，玩家不能变卖这玩意儿除非敌人步兵离开

#### 废墟逻辑

当建筑被摧毁时，会变成另外一种建筑，通常是披着废墟的外衣，工程师可以把废墟建筑恢复成原来的建筑。

    [BuildingType]►Rubble.Destroyed= (BuildingType)

该建筑被摧毁时会变成这种建筑，同时将具有下列属性强加在他们身上：

    Capturable=no
    
    TogglePower=no
    
    Unsellable=yes 
    
    CanBeOccupied=no

该建筑是满血状态，同时工程师进入后能修复成以下标签指定的建筑

**警告：不要把这个建筑设置成本身，否则游戏卡死**

    [BuildingType]►Rubble.Destroyed.Remove= (boolean)

该建筑被摧毁时直接消失，不会转变为废墟建筑，覆盖`Rubble.Destroyed=`。默认否

    [BuildingType]►Rubble.Destroyed.Owner= (enum default|civilian|special|neutral)

被摧毁时废墟建筑给谁。默认给原来的所有者

    [BuildingType]►Rubble.Destroyed.Strength= (integer)

变成废墟建筑时的血量，正值意味着还剩这么多血量，负值里，-99意味着剩99%的血量，-1意味着剩1%的血量，剩余的值全都意味着满血。默认和设定建筑血量相同

    [BuildingType]►Rubble.Destroyed.Anim= (AnimationType)

变成废墟或者被摧毁直接消失时的动画

    [BuildingType]►Rubble.Intact= (BuildingType)

工程师修复后变成这种建筑，如果不指定的话就无法再恢复原来的建筑（设置成别的建筑也是可以的！）

    [BuildingType]►Rubble.Intact.Remove= (boolean)

工程师进去后把废墟建筑移除，覆盖`Rubble.Intact=`。默认否

    [BuildingType]►Rubble.Intact.Owner= (enum default|civilian|special|neutral)

不需要解释

    [BuildingType]►Rubble.Intact.Strength= (integer)

不需要解释。默认-1，1%的血量

    [BuildingType]►Rubble.Intact.Anim= (AnimationType)

不需要解释

#### 在战壕之间移动

战壕能将步兵从一段战壕移动到下一个战壕

    [BuildingType]►IsTrench= (string - trench type ID)

指定这个战壕的名称，只有同种战壕能够穿越，意味着战壕得用围墙，激光墙类型的建筑

#### 指定能占领该建筑的步兵

    [BuildingType]►CanBeOccupiedBy= (list of InfantryTypes)

只有这种步兵能占据这个建筑，该步兵必须设置可以占据建筑