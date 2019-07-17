狩猎者
=====
Hunter Seeker
--------------

#### 狩猎者单位全局设置

    [General]►HunterSeekerDetonateProximity= (integer)

能够引爆目标的距离，单位是leptons。默认0，TS里是150

    [General]►HunterSeekerDescendProximity= (integer)

距离目标多远是狩猎者开始下降，单位是leptons。默认0, TS里是700

    [General]►HunterSeekerAscentSpeed= (integer)

当升到一个更高的飞行高度时的速度。默认0，TS里是40

    [General]►HunterSeekerDescentSpeed= (integer)

当降到一个更低的飞行高度时的速度。默认0，TS里是50

    [General]►HunterSeekerEmergeSpeed= (integer)

从发射设施发出时的速度。默认0，TS里是6

 

#### 狩猎者单位微观设置

以下值覆盖全局值

    [VehicleType]►HunterSeeker.DetonateProximity= (integer)

    [VehicleType]►HunterSeeker.DescendProximity= (integer)

    [VehicleType]►HunterSeeker.AscentSpeed= (integer)

    [VehicleType]►HunterSeeker.DescentSpeed= (integer)

    [VehicleType]►HunterSeeker.EmergeSpeed= (integer)

####不允许的目标

这个标签可以防止该单位成为狩猎者的攻击目标，以免高价值目标或微不足道的目标成为靶子

    [TechnoType]►HunterSeeker.Ignore= (boolean)

是否狩猎者不把这个单位作为攻击目标，即使没有其他目标了狩猎者也不会对其进行攻击。默认否