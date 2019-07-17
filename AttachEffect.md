属性赋予
=========
AttachEffect
--------------

### 【AE功能为Hares核心功能之一】

AE逻辑被用来赋予单位各种属性，例如增加攻击力，削减防御，回复生命，以及其他，就像NP的升级超武一样，但AE更为强大，它不仅仅能用于超武，它还能应用在各种各样的地方。

在Hares中，AE逻辑还被用于虚单位等更多功能，是一项非常重要的核心功能

#### 通用标签：

    [Section]►AttachEffect.Animation= (AnimationType)

赋予属性的单位伴随的动画，就像伊文炸弹那样，动画要注册

    [Section]►AttachEffect.Duration= (integer) 

属性持续时间，默认为0

    [Section]►AttachEffect.TemporalHidesAnim= (boolean)

被超时空武器攻击时是否停止动画？默认否

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

    [TechnoType]►AttachEffect.ForceDecloak= (boolean)

如果设置为是，那么使用该AE的单位会强制现行，默认否

    [TechnoType]►AttachEffect.DiscardOnEntry= (boolean)

如果设置为是，那么当这个单位从地图上消失，比如进入建筑或单位里，AE效果会消失，默认否

#### 用于弹头

    [Warhead]►AttachEffect.Cumulative= (boolean)

是否能够叠加作用，默认否

    [Warhead]►AttachEffect.AnimResetOnReapply= (boolean)

如果不能叠加作用，再次赋予属性时会重设动画，默认否
