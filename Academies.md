训练所
=====
Academies
---------

训练所能够使现有的指定单位以及未来生产的指定单位得到经验并且升级，即使训练所被摧毁，已升级的单位的升级状态依然保留，该效果不能叠加，需要注意指定单位必须是`Trainable=yes`，你可以借该逻辑创建步兵学院，战车学院或者阵地学院之类的玩意儿。

以下的值填写1.0即升为精英单位，填写2.0即升为老兵单位，0.0无效果。
 
    [BuildingType]►Academy.InfantryVeterancy= (double - veterancy levels)
 
拥有这样的建筑后步兵以及带有Organic=yes的车辆得到多少经验
 
    [BuildingType]►Academy.AircraftVeterancy= (double - veterancy levels)
 
拥有这样的建筑后空军以及带有ConsideredAircraft=yes的车辆得到多少经验
 
    [BuildingType]►Academy.VehicleVeterancy= (double - veterancy levels)
 
拥有这样的建筑后载具得到多少经验
 
    [BuildingType]►Academy.BuildingVeterancy= (double - veterancy levels)
 
拥有这样的建筑后建筑得到多少经验

----------------------------------
 
以下语句可以用来指定部分单位得到训练所的影响，不写的话就是默认全部一类单位
 
    [BuildingType]►Academy.Types= (list of TechnoTypes)
 
这些单位会受到训练所的影响

    [BuildingType]►Academy.Ignore= (list of TechnoTypes)
 
这些单位不会受到训练所的影响