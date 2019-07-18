属性赋予
=========
AttachEffect
--------------

### 【AE功能为Hares核心功能之一】

AE逻辑被用来赋予单位各种属性，例如增加攻击力，削减防御，回复生命，以及其他，就像NP的升级超武一样，但AE更为强大，它不仅仅能用于超武，它还能应用在各种各样的地方。

在Hares中，AE逻辑还被用于虚单位等更多功能，是一项非常重要的核心功能

- [通用基本标签](#通用标签)
- [效果类型](#效果类型)
- [用于单位](#用于单位)
- [用于弹头](#用于弹头)
- [弹头替换](#弹头替换)
- [虚单位](#虚单位)

#### 通用标签：

    [Section]►AttachEffect.Animation= (AnimationType)

赋予属性的单位伴随的动画，就像伊文炸弹那样，动画要注册

    [Section]►AttachEffect.Duration= (integer) 

属性持续时间，默认为0

    [Section]►AttachEffect.TemporalHidesAnim= (boolean)

被超时空武器攻击时是否停止动画？默认否

    [Section]►PenetratesIronCurtain=[bool]

默认no，可穿透铁幕起作用

    [Section]►KindIndex= (int)

整数，指定该AE效果为哪个序列的，相同序列的AE将可以叠加或者抵消，而不是重叠。默认-1，即无序列

    [Section]►OverrideSameKind= (bool)

默认no，是否在遇到另一个`KindIndex`相同的AE实例时将那个AE的类型强制转变为现在这个，例如动画会重建，`Delay`会被覆盖，`Duration`则会被更新。

    [Section]►Animation.ExpiredType=[AnimType]

默认无，该AE失效时会播放的动画，同样会跟随单位，该标签可以配合动画发射武器的功能来释放一个新的AE。在AE赋予单位期间单位死亡不会触发，其他类似让单位“消失”的行为同样如此，但是有一个例外，当AllowedTransferingWhenDeploy=no时，单位部署变成别的单位会判定AE失效并导致该标签指定动画触发。

    [Section]►Animation.HideWhenCloak=[bool]

单位隐形时动画是否隐藏（不再可见，并且动画实例删除），默认是，写no可用于解决隐形单位AE动画丢失问题

    [Section]►Animation.Visibility=(enumeration none|owner|allies|team|enemies|all)

效果动画可见性，同超武的可见所属设置

    [Section]►ConvertionType=[TechnoType]

被赋予该AE的单位会真正地变形成指定的单位而不仅仅是变换外形，类似变形金刚

    [Section]►Animation.YSort=[int]

Y轴排序

    [Section]►Animation.ZAdjust=[int]

Z轴调整

#### 效果类型

    [Section]►AttachEffect.SpeedMultiplier= (float - multiplier)

速度加成

    [Section]►AttachEffect.ArmorMultiplier= (float - multiplier)

装甲加成

    [Section]►AttachEffect.FirepowerMultiplier= (float - multiplier)

伤害加成

    [Section]►AttachEffect.Cloakable= (boolean)

隐形加成

#### 用于单位

    [TechnoType]►AttachEffect.Delay= (integer)

该单位释放AE光环后冷却多少时间

    [TechnoType]►ResetDelayUnderAttack=[bool]

被攻击后重置Delay，可用于喘气回血大法

    [TechnoType]►RemovedWhenHealed=[bool]

默认no，是否在单位受到医疗时（任何方式，包括特殊医疗），将该AE效果的Duration计数器置零。

    [TechnoType]►DontDeactivate=[bool]

默认yes，该AE是否在单位瘫痪时立刻失效，no为失效

    [TechnoType]►AttachEffect.ForceDecloak= (boolean)

如果设置为是，那么使用该AE的单位会强制现行，默认否

    [TechnoType]►AttachEffect.DiscardOnEntry= (boolean)

如果设置为是，那么当这个单位从地图上消失，比如进入建筑或单位里，AE效果会消失，默认否

    [TechnoType]►RemainEffectiveInTransporter=[bool]

默认no，在载具里依然会保留效果

    [TechnoType]►AllowedTransferingWhenDeploy=[bool]

默认yes，部署后允许转移效果至转变的单位上，用于变形金刚

    [TechnoType]►ForcedCrawl= (bool)  
 
强制匍匐 

    [TechnoType]►DisableFiring= (bool)

禁止开火
 
    [TechnoType]►ReplaceInfDeath= (InfDeathAnim)

替换死亡动画

#### 用于弹头

    [Warhead]►AttachEffect.Cumulative= (boolean)

是否能够叠加作用，默认否

    [Warhead]►AttachEffect.AnimResetOnReapply= (boolean)

如果不能叠加作用，再次赋予属性时会重设动画，默认否

    [Warhead]►SeperateSpread=(float)

设定AE的影响范围，默认为弹头的`CellSpread`值（只对弹头释放时有效）。

    [Warhead]►SeperateVersusWarhead=(Warhead)

使该AE读取这个标签指定的弹头比率，用于做目标判定，只对弹头AE有效。

#### 弹头替换

现在可以利用该系列标签（WR）达到动态免疫（包括伤害和目标选择）的效果。

    [Warhead]►WR.Count=(int) 

替换多少弹头就写多少，必须一致 

    [Warhead]►WR.Original= 

原始弹头

    [Warhead]►WR.Replacement= 

替换掉的弹头 

如果需要替换多个弹头的话，就继续使用下面的标签，N要≥2。 

    [Warhead]►WR.OriginalN= 

原始弹头

    [Warhead]►WR.ReplacementN= 

替换掉的弹头 

携带该AE的单位，被`Original`指定弹头试图攻击时，会被转换为`Replacement`指定弹头。 

> 典型运用 
> 指示攻击目标：A单位和B单位混编，B单位拥有一个X弹头的武器，无法攻击任何目标，被A单位攻击的目标会被带上一个能将X弹头转换为Y弹头的AE，Y弹头的弹头比率允许攻击任何目标，因此被赋予该AE的单位此时能够被B单位选定为攻击目标。

#### 虚单位

** 警告！！！该逻辑目前尚不稳定，使用者出现任何问题后果自负！！！ **

虚单位逻辑（附件单位），可以用来做多炮塔。 
 
    [TechnoType]►AccessoryUnit.Type= (TechnoType)

挂载的单位，该单位强制无敌，并且会在被赋予AE的单位死亡时直接消失，而非死亡。

    [TechnoType]►AccessoryUnit.BindOnTurret= (bool)

炮塔联结，yes的时候AccessoryUnit.Offset才有效，同时会视为一个独立的单位，可以被选中，不过不能直接控制它攻击。

    [TechnoType]►AccessoryUnit.Offset= (X,Y,Z)

X控制左右偏移，Y控制前后，Z控制上下

    [TechnoType]►AccessoryUnit.TurretSync= (bool)

炮塔同步，炮塔是否会随着主体旋转而旋转，否则朝着一个方向不变直到攻击时，类似建筑炮塔和载具炮塔的区别，写no会旋转（载具炮塔），yes不旋转（建筑炮塔）

    [TechnoType]►AccessoryUnit.DirectionOffset= (int)

附件单位的旋转角度

    [TechnoType]►AccessoryUnit.RotationRange=？

应该是限制旋转角度，不过目前似乎无法正确表现

    [TechnoType]►AccessoryUnit.CheckTargetDistance= (bool)

检查目标距离？不明

    [TechnoType]►AccessoryUnit.DontLoseOwnTarget= (bool)

不丢失目标？不明
 
> 提示：如果你让航母类单位作为附件单位，那么该单位会不太“听话” ，目前的解决手段是把航母塞到要塞里，然后要塞作为附件单位。
 
> 注意：目前附件单位的表现类似于要塞，像是攻击空地后不按S而是移动依然会攻击空地，因此**不要试图用该功能完全取代初始载荷**。

---------------------------------------------------------------------

新分类：ZF你来康康这是什么
-------------

DontLoseDuration=[bool]    

默认no，即Duration是否随时间递减
