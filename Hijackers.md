劫车犯
========
Hijackers
----------

劫车犯能够偷窃敌方载具。

如果你给一个步兵设定`VehicleThief=yes`，那么有以下语句进行自定义

    [InfantryType]►VehicleThief.EnterSound= (Sound name)

进车声音

    [InfantryType]►VehicleThief.LeaveSound= (Sound name)

被偷载具破坏劫车犯出来的声音

    [InfantryType]►VehicleThief.BreakMindControl= (boolean)

是否能偷窃被心灵支配的载具，当进入载具该载具会切断与控制者的联系，默认为是

    [InfantryType]►VehicleThief.OneTime= (boolean)

劫车犯是否只能偷一次车（载具摧毁后将无法逃出）

    [InfantryType]►VehicleThief.KillPilots= (integer)

劫车犯偷装人的车能够杀死多少人，-1为杀死全部人，默认为0

    [TechnoType]►VehicleThief.Allowed= (boolean)

该载具是否允许被偷窃，默认为是

> 注意
> 
> 劫车犯不能偷友军与中立车辆，被狙杀驾驶员的车辆不能开，但是可以连用`VehicleThief=yes`和`CanDrive=yes`来允许。
