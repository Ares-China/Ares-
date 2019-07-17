击杀驾驶员
=========
Killing Drivers
---------------

这个逻辑允许被弹头击中的载具驾驶员挂掉，载具变为中立状态，就像RA3娜塔沙的F技一样，无驾驶员的单位能够被占领。

    [Warhead]►KillDriver= (boolean)

该弹头能否杀死驾驶员

    [Warhead]►KillDriver.Owner= (enumeration - civilian,special,neutral)

驾驶员被杀后载具归属。默认`special`

    [Warhead]►KillDriver.KillBelowPercent= (float)

该弹头只有在被打击单位的生命低于这个百分比时才能杀死驾驶员，默认100%

    [TechnoType]►ProtectedDriver= (boolean)

该载具驾驶员能否被杀死，默认能

    [InfantryType]►CanDrive= (boolean)

该步兵能否占领驾驶车辆，默认不能。如果特定载具指定了`Operator`，那么该步兵将成为它的操作者，并可以被释放出来，否则将成为载具的永久驾驶员
