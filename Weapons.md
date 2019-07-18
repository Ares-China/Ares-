武器
=====
Weapons
---------

- [[WeaponTypes]注册表](#[WeaponTypes]注册表)
- [声波武器和喷火武器正常伤害](#声波武器和喷火武器正常伤害)
- [自定义伊文炸弹](#自定义伊文炸弹)
- [自定义辐射波](#自定义辐射波)
- [自定义特斯拉](#自定义特斯拉)
- [波逻辑](#波逻辑)
- [粗激光](#粗激光)

[WeaponTypes]注册表
----

武器现在已经可以直接注册在[WeaponTypes]注册表并且被使用

声波武器和喷火武器正常伤害
-----

现在`IsSonic=yes`或`UseFireParticles=yes`的武器可以设定正常伤害，就像穿透伤害一样
 
    [Weapon]►ApplyDamage= (boolean)

使`IsSonic=yes`或`UseFireParticles=yes`的武器赋予`Damage`的伤害，如果写no就会禁用任何伤害就像`Damage=0`一样，同时不产生弹头动画（这个问题以后会解决）。默认`IsSonic=yes`或`UseFireParticles=yes`的武器为no，其他武器yes

自定义伊文炸弹
------

    [Weapon]►IvanBomb.Warhead= (WarheadType)

炸弹爆炸弹头

    [Weapon]►IvanBomb.Damage= (integer)

炸弹伤害

    [Weapon]►IvanBomb.Detachable= (boolean)

能否拆弹

    [Weapon]►IvanBomb.DestroysBridges= (boolean)

能否能炸桥，桥梁维修小屋可以一直丢但是默认炸不掉

    [Weapon]►IvanBomb.CanDetonateTimeBomb= (boolean)

能否手动引爆

    [Weapon]►IvanBomb.Delay= (integer)

爆炸延时

    [Weapon]►IvanBomb.AttachSound= (sound name)

丢上去的声音

    [Weapon]►IvanBomb.TickingSound= (sound name)

计时器滴滴答答的声音，填`SOUNDMD`的注册名，必须带`Control=loop`

    [Weapon]►IvanBomb.Image= (filename, *excluding*the .shp extension)

图像，不要带扩展名（卧槽前面的都要这个怎么又不要了，一帮蛋疼B）。默认`bombcurs.shp`

    [Weapon]►IvanBomb.FlickerRate= (integer)

炸弹图像跳动频率，计算细则关我屌事

> frameToShow = (Game.CurrentFrame – Bomb.PlantingFrame) / (Bomb.Delay / (Bomb.Image.Frames – 1))
> 
> IF (CurrentFrame mod (2 * Bomb.FlickerRate) >= Bomb.FlickerRate) THEN frameToShow = frameToShow + 1

现在你可以在炸弹的最后一帧写上“炸死你个B”之类的话了，比如下图这个骷髅

![](https://i.imgur.com/aV7GI8s.png)

自定义辐射波
----------

    [Weapon]►Beam.Color= (R,G,B)

颜色

    [Weapon]►Beam.IsHouseColor= (boolean)

是否是玩家所属色

    [Weapon]►Beam.Duration= (integer)

持续时间，默认15，有RadEruption=yes的为5到20随机数

    [Weapon]►Beam.Amplitude= (float)

振幅大小，默认40

自定义特斯拉
---------

    [Weapon]►Bolt.Color1= (R,G,B)

    [Weapon]►Bolt.Color2= (R,G,B)

    [Weapon]►Bolt.Color3= (R,G,B)

颜色，没啥好说的

波逻辑
------

重启的功能

    [Weapon]►Wave.IsLaser= (boolean)

小波

    [Weapon]►Wave.IsBigLaser= (boolean)

大波

![](https://i.imgur.com/hHmcQpO.png)

可以用于电磁波和声波

#### 波的颜色

    [Weapon]►Wave.Color= (R,G,B)

颜色

    [Weapon]►Wave.IsHouseColor= (boolean)

是否是玩家所属色

#### 波的绘制方向

    [Weapon]►Wave.ReverseAgainstVehicles= (boolean)

默认IsMagBeam=yes的波会从目标向发射者绘制，发射者是车辆

    [Weapon]►Wave.ReverseAgainstBuildings= (boolean)

是否从目标向发射的建筑绘制

    [Weapon]►Wave.ReverseAgainstInfantry= (boolean)

是否从目标向发射的步兵绘制

    [Weapon]►Wave.ReverseAgainstAircraft= (boolean)

是否从目标向发射的飞机绘制

    [Weapon]►Wave.ReverseAgainstOthers= (boolean)

是否从目标向发射的其他玩意儿绘制

 

#### 穿透伤害

    [Weapon]►AmbientDamage= (integer)

伤害，默认0

    [Weapon]►Warhead= (WarheadType)

弹头

粗激光
------

    [Weapon]►LaserThickness= (integer)

激光宽度，和NP一样，渣效果，而且强制玩家所属色