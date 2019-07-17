吊运载具
=======
Carryalls
---------

在TS中运输机能够吊运载具并投放到任意地点，Hares恢复了这个逻辑并新增了一些语句。

    [AircraftType]►Carryall.SizeLimit= (integer)

吊运规格的最大限制，默认为能够吊运任意单位即值为-1

    [UnitType]►Carryall.Allowed= (boolean)

这个载具能否吊运，`Organic=yes`和`NonVehicle=yes`的单位不能吊运. 如果指定那么覆盖全局，目前不可能“撤消”这个标签，所以必须指定这个标签

> 蜘蛛什么的不能吊运
> 
> 该单位要成功吊运必须要有`AirportBound=no`并且没有`Dock=`，否则不能吊运
> 
> 建议不要吊运船，否则放不回水里，而扔到地上会爆掉，所以船尽量设置`Carryall.Allowed=no`