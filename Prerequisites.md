新的出兵逻辑
=============
Prerequisites
-------------

    [Unit]>Prerequisite.RequiredTheaters= (list of theater names)

需要这种气候才能造

    TEMPERATE - most maps
    
    SNOW - arctic/snowy maps
    
    URBAN - some city maps
    
    DESERT - some desert maps, older maps use Temperate
    
    LUNAR - Soviet Mission 6
    
    NEWURBAN - most YR urban maps

`PrerequisiteOverride`不会覆盖`Prerequisite.RequiredTheaters`

    [Unit]>Prerequisite.Negative= (list of BuildingTypes)

有这个建筑就没法造

`PrerequisiteOverride`不会覆盖`Prerequisite.Negative`

    [Unit]>Prerequisite.Lists= (integer)

指定有多少建造前提

    [Unit]>Prerequisite.List#= (list of BuildingTypes (where # is the 1-based index of the prerequisite list, the maximum specified by Prerequisite.Lists))

指定新的建造前提，想设置多少都可以（根据Prerequisite.Lists决定）

    [Unit]>Prerequisite.StolenTechs= (list of integers)

指定有多少偷窃前提，其他具体的参考后面的偷窃科技条目

    [BuildingType]>FactoryOwners.Permanent= (boolean)

    [BuildingType]>FactoryOwners.HaveAllPlans= (boolean)

占领该建筑后是否获得对应工厂的专用科技，效果为永久（即一旦占领不可撤销），默认否。

    [BuildingType]>FactoryOwners.HasAllPlans= (boolean)

占领该建筑后是否获得对应工厂的专用科技，效果为临时（即一旦失去建筑则失去科技），默认否。

 

    [TechnoType]>FactoryOwners= (list of houses)

这个列表内国家的工厂可以建造该单位。如果是空的，每个国家都可以建造。此外，玩家至少需要一个在该列表内国家的工厂来建造或者这些国家里至少一个的科技树来建造它。

    [TechnoType]>FactoryOwners.Forbidden= (list of houses)

与上面相反，这个列表内国家的工厂不能建造该单位。

注意

AI无视建筑上的这两条语句，仅在单位上有效

![](https://i.imgur.com/OBpmfqj.png)

通用的先决条件组

你现在能自定义先决条件组就像原来的
> 
> POWER (PrerequisitePower)
> 
> FACTORY (PrerequisiteFactory)
> 
> BARRACKS (PrerequisiteBarracks)
> 
> RADAR (PrerequisiteRadar)
> 
> TECH (PrerequisiteTech)
> 
> PROC (PrerequisiteProc and PrerequisiteProcAlternate)这些
> 

你需要创建一个新的条目`[GenericPrerequisites]`然后才能添加先决条件组像

    GROUPNAME= (list of BuildingTypes)

-----------------------------------------------------

    [GenericPrerequisites]
    
    NAVALYARD=GAYARD,NAYARD,YAYARD
    
    etc...
    
    [TechnoType]
    
    ...
    
    Prerequisites=NAVALYARD
    
    ...
