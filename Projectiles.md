抛射体
=========
Projectiles
--------

- 多方向抛射体动画化
- 弹道散布
- 有效追击范围
- 分裂和空爆

-------------------------

多方向抛射体动画化
-------------

多方向抛射体固定为32方向，每个方向只能用一帧表示，现在HARES可以使32面抛射体在每面都有动画（因此你可以做出一个自轴旋转的shp导弹）。
 
    [Projectile]>AnimLength= (integer - frames)

抛射体每面的动画长度，该抛射体需要`Rotates=yes`。默认1
 
**注意，不能用0，否则瞬间爆炸。**

弹道散布
------

全局设定里`[CombatDamage]►BallisticScatter`决定了全局弹道散布范围，ARES提供了微观值并且将其分为两个标签，这个标签想要起效，抛射体一定要写`Inaccurate=yes`和`Arcing=yes`才行

    [Projectile]►BallisticScatter.Min= (float - cell range)

散布最小范围。默认如果有`FlakScatter=no`或者`Invisible=yes`就是`[CombatDamage]►BallisticScatter/2`，否则是0

    [Projectile]►BallisticScatter.Max= (float - cell range)

散布最大范围。默认`[CombatDamage]►BallisticScatter`

有效追击范围
---------

这个功能已经从TS里恢复。它能决定一个抛射体是否引爆自己当攻击目标超过了它的有效追击范围时（防止无限追击）。默认是390格子。

    [Projectile]►Ranged= (boolean)

这个抛射体是否会用完燃料然后引爆自己。默认否

    [Weapon]►ProjectileRange= (float - cell range)

在引爆前能够飞多远,。默认390格子

分裂和空爆
-----------

#### 分裂逻辑

火风暴资料片中，半机械收割者可以发射两枚导弹，它们在半空中达到一定高度后, 产生两个新的导弹，然后分别攻击误差不超过两格范围内的目标或是随机攻击7x7范围的地面。

分裂发生在当一个有`Airburst=yes`的抛射体在目标头上，`Ranged=yes`则告诉该武器是否在ProjectileRange范围内继续追击否则直接引爆。

ModEnc上有更多的解释

    [Projectile]►Splits= (boolean)

是否该抛射体会分裂成若干由集束逻辑和空爆逻辑定义的抛射体。可以和空爆合用。默认否

    [Projectile]►RetargetAccuracy= (float - percentage)

分裂出来的抛射体和原来的抛射体攻击相同目标的概率。值越高，越不可能去打别的目标。有效值为0到1之间。默认0，一定会重新选择目标（如果该区域只有这一个单位那么还是会攻击这个单位）

#### 空爆逻辑

在原版里肯定空爆出9个，并且是3x3范围，现在可以自定义。

    [Projectile]►AirburstSpread= (float - cell range)

空爆覆盖面积，在这个范围内的所有格子都会被空爆出的武器攻击到，该抛射体需要`Airburst=yes`。不能和`Splits=yes`连用。默认1.5（3x3）

通用设置

    [Projectile]►AroundTarget= (boolean)

是否抛射体有`Splits=yes`或`Airburst=yes`时爆出来的每个抛射体会重新搜寻原目标周围的新目标进行攻击（包括原目标本身）。如果启用，分裂出的抛射体会继续原来的攻击目标，否则分裂出的抛射体会搜寻新目标，默认和Splits一样。