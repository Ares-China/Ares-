新增护甲以及免疫方案
==================
Additional ArmorTypes and Verses
--------------------------------

新增护甲
-------

Hares允许新的`[ArmorTypes]`来定义新的护甲类型（除了现有的11种ArmorTypes ; 无， flak，plate，light，medium， heavy，wood，steel，concrete， special_1和special_2）

    [ArmorTypes]
    paper=steel
    magic=11%

`paper=steel`可以定义新护甲类型paper，使其性效等同于steel

而`magic=11%`定义了新护甲类型magic，使所有的弹头对其效果默认为11%

而弹头对特定护甲类型的性效，则通过以下标签定义：

    [Warhead]►Versus.magic= (float - modifier)

本标签定义了该弹头对magic护甲类型的伤害百分比

    弹头百分比特殊值
    
    0%不主动不还击不响应强行攻击
    
    1% 不还击不主动攻击
    
    2% 不主动攻击

现在可以独立于伤害乘数来打开或关闭这些行为（因此，您现在可以使用对装甲类型100％有效的弹头，但同时不会直接瞄准具有该装甲类型的单位）。

    [Warhead]►Versus.shit.ForceFire=(boolean)

是否对shit护甲可以强行攻击

    [Warhead]►Versus.shit.Retaliate=(boolean)

是否可以对shit护甲反击

    [Warhead]►Versus.shit.PassiveAcquire=(boolean)

是否对shit护甲主动攻击

HARES纠正了WW的弱智拼写错误Aquire

免疫
---

事例：

    [ArmorTypes] 
    flakImmuneToFrost = flak
    
    [IceMan] 
    Armor = flakImmuneToFrost 
    Primary = IceBlast
    
    [IceBlast] 
    弹头= IceBlastWH
    
    [IceBlastWH] 
    Versus.flakImmuneToFrost = 0％
    Versus.flakImmuneToFrost.ForceFire = yes 
    Versus.flakImmuneToFrost.Retaliate = yes 
    Versus.flakImmuneToFrost.PassiveAcquire = yes