特定乘客类型
==========
Specific Passengers
---------------------

可以指定单位能否进某个特定单位，这个逻辑仅支持`VehicleTypes`和`AircraftTypes`。
 
    [TechnoType]>Passengers.Allowed= (list of TechnoTypes) 
这些单位可以进入这个单位。如果你想让所有单位都进不去，就设置成一个假单位或者一个建筑

    [TechnoType]>Passengers.Disallowed= (list of TechnoTypes)
这些单位不允许进入这个单位