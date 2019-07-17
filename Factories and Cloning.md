指定工厂&克隆工厂
==============
Factories and Cloning
----------------------

#### 不同单位的工厂(狗屋)

    [InfantryOrVehicle]►BuiltAt= (list of BuildingTypes)

指定该单位在哪个建筑建造，但是必须是和该单位类型相对应的工厂类型，例如飞机只能在`Factory=AircraftType`的工厂建造，而不能在`VehicleType`的工厂

    [BuildingType]►Factory.ExplicitOnly= (boolean)

是否只允许指定单位建造，默认否，单位必须有上面一句标签指定才能在这个建筑被建造出来

> 如果想实现RA1里的狗屋，则`[KENN]►Factory=InfantryType`,`[KENN]►Factory.ExplicitOnly=yes`, `[DOG]►BuiltAt=KENN` 并在`[DOG]►Prerequisite`列表里加上`KENN`
> 
#### 载具克隆缸

    [BuildingType]>CloningFacility= (boolean)

允许该建筑克隆载具，默认否

#### 克隆选项

    [InfantryOrVehicle]>Cloneable= (boolean)

该单位能否被克隆，默认是

    [InfantryOrVehicle]>ClonedAt= (list of BuildingTypes)

在哪里克隆

>克隆将会忽略建筑中 `Factory=` 的设定，但似乎我亲测是Factory指定会使克隆逻辑失效。注意影响单位正确从建筑里走出来或是开出来的语句是`WeaponsFactory=yes, GDIBarracks=yes, NODBarracks=yes andYuriBarracks=yes`

--------------------------------------------------------------------------

>如果某单位`ClonedAt`被指定了, 其它未被指定`Cloning=yes` 或 `CloningFacility=yes` 的建筑将不会生产这个单位