会被建筑阻挡的抛射体
================
Solid Buildings
---------------

这是一个新的抛射体语句，设定这个语句的抛射体在攻击建筑后的单位时会被建筑物阻挡。

在`rulesmd.ini`里:

    [Projectile]►SubjectToBuildings= (boolean)

是否会被建筑阻挡，默认为否

在`artmd.ini`里:

    [BuildingArt]►SolidHeight= (integer - cells)

建筑的阻挡高度，默认为0，即可以完全穿透，-1意味着可以完全阻挡

**这个逻辑不能用在多边形的建筑。**
