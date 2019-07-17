超时空监狱/劫持者
===============
Chrono Prisons / Abductors
--------------------------

超空间监狱可以把单位吸进来同时炮塔会改变，如果监狱爆掉这些单位会被释放出来。

    [Weapon]►Abductor= (boolean)

如果设置为是，武器能够吸入单位，当该单位被摧毁时被吸入的单位会重新出现.奴隶和自己会被归属到Special，如果该单位吸满了或者该单位无法吸入，就使用正常的武器伤害，默认否

> 确保这个单位有乘客位置，而且设置大小限制为0否则吸入会受限制
> 
> 建筑无法使用该逻辑否则IE

    [Weapon]►Abductor.Anim= (animation)

单位被吸入时产生的动画

    [Weapon]►Abductor.ChangeOwner= (boolean)

被吸入的单位是否会归属到攻击者的所属，默认否

    [Weapon]►Abductor.AbductBelowPercent= (float)

只有低于这个血量百分比的单位才会被吸入，默认100%

    [TechnoType]►ImmuneToAbduction= (boolean)

这个单位不能被吸入只会受到伤害，默认否

    [TechnoType]►PassengerTurret= (boolean)

吸单位后会改变炮塔，吸入一个改变一次

> 0 passengers footur.vxl
> 
> 1 passenger footur1.vxl
> 
> 5 passengers footur5.vxl
> 
> 要用这个逻辑该单位必须使用Turret=yes，TurretCount，WeaponX
