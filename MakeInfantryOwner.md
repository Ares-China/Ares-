基因突变的步兵归属
=============
MakeInfantryOwner
-----------------

    [Animation]►MakeInfantryOwner= (enumeration invoker|killer|victim|neutral|random)

决定是谁的
    invoker看情况|killer击杀者|victim死人|neutral野生|random随机

一堆next动画的话`MakeInfantry=`应该写在最后一个，`MakeInfantryOwner=`应该写第一个，动画使用单位色盘

这东西，`MakeInfantryOwner`只对`InfDeathAnim`, `DeathAnims`和地图触发生效 ，默认是看情况

`InfDeathAnim`是击杀者

`DeathAnims`是死人

触发里的就是触发的拥有国家

现在`MakeInfantryOwner`已经扩展到普通步兵死亡动画了