操作者
=======
Operator
--------

单位必须有人进去才能启动

    [TechnoType]►Operator= (string, either an InfantryType or “_ANY_”)

指定某个驾驶者才能操作，`_ANY_`的话是任意驾驶者都行，默认`none`，不需要驾驶者

这个单位必须至少有一个乘客位置，建筑则需要设置`InfantryAbsorb=yes`

建筑没有操作者只会表现出无法使用武器，但是诸如生产，超武，反部署，雷达等不会受到影响

需要注意的是AI不会用这样的功能，所以应该避免AI造需要操作者的单位
