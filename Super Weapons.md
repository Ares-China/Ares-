超级武器
===========
Super Weapons
------------

- 通用设置
- 原有超武
   - 闪电风暴
   - 核弹打击
   - 心灵支配
   - 空间传送
   - 铁幕&力场护盾
   - 基因突变
   - 空降部队
   - 侦察机
   - 心灵感测
- 新增超武
   - 超声波
   - 通用弹头
   - 单位投放
   - 火风暴
   - 狩猎者
   - 空降仓
   - 电磁脉冲

通用设置
--------

禁止在游戏模式ini里修改超武的`action`和`type`，要用就用rules，写个新的超武，在游戏模式里重做关联。

#### 额外的超级武器
 
在原版里一个建筑只能关联两个超级武器，使用`SuperWeapon`以及`SuperWeapon2`，ARES可以让一个建筑关联更多的超级武器。
 
    [BuildingType]►SuperWeapons= (list of SuperWeaponTypes)

该建筑关联这些超级武器。

>注：SuperWeapons的标签参数存在字数上限

#### 就绪动画

建筑物可以显示特定的动画，以显示附加的超级武器正在充电，几乎充电（正常游戏中剩余1分钟），准备好被射击以及何时发射。然而，在尤里的复仇中，这些动画只适用于原本的超级武器。在Hares中，这些适用于任何超级武器。
 
#### 通用语句

    [SuperWeapon]►SW.Range= (float,int)

填*或者*，*，前者是直径后者是椭圆的半长轴半短轴

    [SuperWeapon]►SW.CreateRadarEvent= (bool)

是否建立雷达事件

    [SuperWeapon]►SW.AffectsHouse= (enum none谁都不|owner发出者|allies盟友|team自己和盟友|enemies敌人|all全部)

影响对象，可以设多个

    [SuperWeapon]►SW.AffectsTarget= (enum land|water|empty|infantry|units|buildings)

可以作用的地形和对象，可以设多个

    [SuperWeapon]►SW.ShowCameo= (boolean)

是否在防御栏显示此超武，默认是，AutoFire的默认隐藏

    [SuperWeapon]►SW.Deferment= (integer frames)

超武生效前帧数，仅对部分有效
 
 
#### 定死的值

    [SuperWeapon]►SW.PostDependent= (SuperWeapon)

定义超时空的两个超武链接，例如[ChronoSphereSpecial]►SW.PostDependent=ChronoWarpSpecial
 

#### 释放条件

    [SuperWeapon]►SW.FireIntoShroud= (boolean)

能否丢进黑雾，默认是
 
#### [SuperWeapon]►SW.AutoFire= (boolean)

自动发出，会丢到效果最好的地方，默认否

#### [SuperWeapon]►SW.ManualFire= (boolean)

人工发出，如果autofire=no的话这行代码就没用，有个蛋用
 
#### [SuperWeapon]►SW.RequiresTarget= (enum land|water|empty|infantry|units|buildings)

可以点什么类型的目标，不是此目标的话就不能点下去，比如护盾只能点建筑

#### [SuperWeapon]►SW.RequiresHouse= (enum none|owner|allies|team|enemies|all)
是否对敌人盟友之类的生效

####[SuperWeapon]►SW.AITargeting= (enum SW Targeting Type)

AI怎么用

> None：不会用
> 
> LightningStorm：侵略性，不能和其他闪电一起
> 
> Nuke：侵略性或用触发指定
> 
> PsychicDominator；最大的敌人单位集群
> 
> GeneticMutator：3X3内最大的敌人步兵集群
> 
> ParaDrop：敌人家防御最差的地方
> 
> ForceShield：敌人超武砸的地方
> 
> NoTarget：随便砸
> 
> Offensive：侵略性
> 
> Stealth：只攻击隐形单位，受SW.RequiresTarget和SW.RequiresHouse影响
> 
> Base：砸自己基地
> 
> EnemyBase：砸敌人基地
> 
> HunterSeeker：像NoTarget一样，但是会打敌人的单位，这个只对一些超武有用
> 
> Self：砸这个超武的超武建筑（干啥啊，蛋疼啊）

默认值表：

![](https://i.imgur.com/tU1Urzh.png)

#### 范围限制

可以设置超武的射程，以超武建筑为中心，超过其发射范围就不能发射超武。

    [SuperWeapon]►SW.RangeMaximum= (float - cell range)

    [SuperWeapon]►SW.RangeMinimum= (float - cell range)

最大范围和最小范围，负数即无限。默认-1，随便打

#### 指示者

以下标签设置单位为指示者，超武只能在指示者的范围内发射。

    [SuperWeapon]►SW.Designators= (list of TechnoTypes)

需要这些单位作为指示者，不写就是不需要

    [SuperWeapon]►SW.AnyDesignator= (boolean)

是否任何单位都能做指示者，覆盖`SW.Designators`。默认否

    [TechnoType]►DesignatorRange= (integer - cells)

指示者的指示范围。默认和`[TechnoType]►Sight`一样

#### 抑制者

和抑制者相反，超武不能在这些单位周围发射。

另外如果建筑作为抑制者没电，没有被占领的话，那么抑制功能就会无效。

    [SuperWeapon]►SW.Inhibitors= (list of TechnoTypes)

需要这些单位作为抑制者。

    [SuperWeapon]►SW.AnyInhibitor= (boolean)

是否任何单位都能做抑制者，覆盖上面那个。

    [TechnoType]►InhibitorRange= (integer - cells)

抑制者的抑制范围。

#### 阵营国家限制

现在可以设定超武的归属国家，如果另一个国家占领了这个国家的超武建筑，超武也不能够被占领国家使用。

    [SuperWeapon]►SW.RequiredHouses= (list of HouseTypes) 

这个超武归属于那个国家。

    [SuperWeapon]►SW.ForbiddenHouses= (list of HouseTypes) 

哪些国家不能用这个超武。

#### 辅助建筑

在TS里NOD有一个叫化学飞弹的超武，这个超武必须要有另一个非超武建筑化学工厂（介绍是化学工厂生产化学飞弹）才能使用，化学工厂被称为辅助建筑，这个逻辑在ARES里得到了复原。

    [SuperWeapon]►SW.AuxBuildings= (list of BuildingTypes)

这个超武需要这些建筑存在时才能使用。

    [SuperWeapon]►SW.NegBuildings= (list of BuildingTypes)

这个超武在有这些建筑存在时不能使用。

#### 新增鼠标

具体可以看鼠标指针

    [SuperWeapon]►Cursor= (cursor definition)

可以释放时的鼠标，默认攻击鼠标指针

    [SuperWeapon]►NoCursor= (cursor definition)

不能释放时的鼠标，默认禁止鼠标指针

#### 长期生效超武

超武需要设置`UseChargeDrain=yes`

    [SuperWeapon]►SW.ChargeToDrainRatio= (float multiplier)

此超武有效时间，默认为`[General]►ChargeToDrainRatio`

    [SuperWeapon]►SW.Unstoppable= (boolean)

是否禁止手工停止，注意这个功能简直就是火风暴专用，用于别的超武会发生不可预期的效果

#### 花费

    [SuperWeapon]►Money.Amount= (integer - credits)

超武开火时加钱，负数扣钱，默认0

    [SuperWeapon]►Money.DrainAmount= (integer - credits)

火风暴扣钱，默认0

    [SuperWeapon]►Money.DrainDelay= (integer - frames)

火风暴扣钱间隔

#### 动画/音效

    [SuperWeapon]►SW.Animation= (animation)

目标地点的动画

    [SuperWeapon]►SW.AnimationHeight= (integer)

动画高度

    [SuperWeapon]►SW.AnimationVisibility= (enumeration none|owner|allies|team|enemies|all)

谁能看见动画

    [SuperWeapon]►SW.Sound= (sound)

目标地点的声音

    [SuperWeapon]►SW.ActivationSound= (sound)

超武成功触发的声音，如闪电风暴

#### EVA事件

    [SuperWeapon]►EVA.Detected= (EVA event)

超武建筑建造

    [SuperWeapon]►EVA.Ready= (EVA event)

就绪

    [SuperWeapon]►EVA.Activated= (EVA event)

启动

    [SuperWeapon]►EVA.Impatient= (EVA event)

超武还不能释放

    [SuperWeapon]►EVA.InsufficientFunds= (EVA event)

钱不够，默认EVA_InsufficientFunds

    [SuperWeapon]►EVA.SelectTarget= (EVA event)

点超武图标时

不想用就写none。

#### 信息提示（CSF）

    [SuperWeapon]►Message.Detected= (CSF label)

探测到

    [SuperWeapon]►Message.Ready= (CSF label)

就绪

    [SuperWeapon]►Message.Launch= (CSF label)

发动

    [SuperWeapon]►Message.Activate= (CSF label)

某超武产生效果，如闪电风暴

    [SuperWeapon]►Message.Abort= (CSF label)

同类超舞已发动

    [SuperWeapon]►Message.InsufficientFunds= (CSF label)

钱不够

    [SuperWeapon]►Message.FirerColor= (boolean)

是否用玩家色显示信息，默认否

    [SuperWeapon]►Message.Color= (Color scheme)

指定颜色，比Message.FirerColor=yes 权限低

#### 图标文本设定

显示超舞状态的CSF。

    [SuperWeapon]►Text.Hold= (CSF label)

没电

    [SuperWeapon]►Text.Ready= (CSF label)

就绪

    [SuperWeapon]►Text.Charging= (CSF label)

火风暴，尚未充能完毕

    [SuperWeapon]►Text.Active= (CSF label)

火风暴，已激活

    [SuperWeapon]►Text.Preparing= (CSF label)

准备中

#### 超级武器全局光

    [SuperWeapon]►Light.Enabled= (boolean)

是否引起全局光改变，只支持第一超武

    [SuperWeapon]►Light.Ambient= (integer)

环境亮度，太高会卡

    [SuperWeapon]►Light.Red= (integer)
    [SuperWeapon]►Light.Green= (integer)
    [SuperWeapon]►Light.Blue= (integer)

颜色，一群蛋疼的家伙居然没有把RGB合成一个标签

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------

原有超武
-------------

# 闪电风暴

**Type=LightningStorm**

默认值：

    [SuperWeapon]►SW.Range= (float,integer)
雷击范围。默认`[General]►LightningCellSpread`

    [SuperWeapon]►SW.Damage= (integer)
伤害。默认`[General]►LightningDamage`

    [SuperWeapon]►SW.Warhead= (Warhead)
弹头。默认`[General]►LightningWarhead`

    [SuperWeapon]►SW.Deferment= (integer frames)
启动前准备帧数。默认`[General]►LightningDeferment`

    [SuperWeapon]►SW.ActivationSound= (Sound)
闪电风暴激活声音`[AudioVisual]►StormSound`

    [SuperWeapon]►SW.AITargeting= (enum)
AI瞄准模式。默认`LightningStorm`

    [SuperWeapon]►Light.*= (integer)
设定光线效果 默认是地图的`[Lighting]►Ion*`

特殊值:

    [SuperWeapon]►Lightning.Duration= (integer - frames)
持续时间。默认`[General]►LightningStormDuration`，-1是无限长

    [SuperWeapon]►Lightning.RadarOutage= (integer - frames)
受到`SW.AffectsHouse`影响的玩家的雷达关闭时间。默认`[General]►LightningStormDuration`

    [SuperWeapon]►Lightning.RadarOutageAffects= (enum)
影响对象。默认`enemies`

    [SuperWeapon]►Lightning.HitDelay= (integer - frames)
两个云放电的间隔。默认`[General]►LightningHitDelay`
 
    [SuperWeapon]►Lightning.ScatterDelay= (integer - frames)
刷出云的间隔。默认`[General]►LightningScatterDelay`

    [SuperWeapon]►Lightning.ScatterCount= (integer)
一次刷云产生的数目。默认`Lightning.ScatterDelay` ，0或负数导致只有中心雷击

    [SuperWeapon]►Lightning.Separation= (integer - distance)
两个云之间的最小距离。默认`[General]►LightningSeparation`

    [SuperWeapon]►Lightning.PrintText= (boolean)
是否会出现闪电风暴接近中的CSF。默认`[General]►LightningPrintText`
 
    [SuperWeapon]►Lightning.IgnoreLightningRod= (boolean)
是否无视建筑避雷针`LightningRod=yes`。默认no

    [SuperWeapon]►Lightning.DebrisMin= (integer)
一次最少产生碎片数。默认2

    [SuperWeapon]►Lightning.DebrisMax= (integer)
最大。默认4
 
    [SuperWeapon]►Lightning.CloudHeight= (integer - leptons)
云的高度，小于0的话会把云放在闪电表的第一个闪电上面

    [SuperWeapon]►Lightning.BoltExplosion= (Animation)
雷击动画。默认 `[General]►WeatherConBoltExplosion`
 
    [SuperWeapon]►Lightning.Sounds= (list of Sounds)
雷击声音。默认 `[AudioVisual]►LightningSounds`
 
    [SuperWeapon]►Lightning.Clouds= (list of Animation)
云类型，不得缺少。默认`[General]►WeatherConClouds`

    [SuperWeapon]►Lightning.Bolts= (list of Animation)
电类型，可以缺少。默认`[General]►WeatherConBolts`

    [SuperWeapon]►Lightning.Debris= (list of Animation)
雷击产生的碎片类型`[General]►MetallicDebris`
`Bouncer=yes`不得用于雷的动画，否则击中建筑立刻IE

---------------------------------------------------------------------------------------------------

# 核弹打击

**Type=MultiMissile**
 
默认值：
 
    [SuperWeapon]►SW.Damage= (integer) 
伤害，负数则用`payload`的伤害。默认-1
 
    [SuperWeapon]►SW.Warhead= (Warhead) 
不写的话就用`payload`的弹头
 
    [SuperWeapon]►SW.ActivationSound= (Sound) 
核弹警告。默认`[AudioVisual]►DigSound`
 
    [SuperWeapon]►SW.AITargeting= (enum) 
AI瞄准参数。默认`Nuke`.
 
    [SuperWeapon]►Light.*= (integer) 
 
光线设定。差不多就是`Light.Ambient=200，Light.Red=175，Light.Green=150，Light.Blue=125`
 
特殊值:
 
    [SuperWeapon]►Nuke.Payload= (Weapon) 
砸下来的核弹类型。默认`nukepayload`
 
    [SuperWeapon]►Nuke.TakeOff= (Animation) 
 
核弹起灰时候的动画。默认`[General]►NukeTakeOff.Nuke.TakeOff=`
 
    [SuperWeapon]►Nuke.PsiWarning= (Animation) 
 
心灵探测器探测到核弹的警告动画。默认`PSIWARN.Nuke.PsiWarning=`
 
    [SuperWeapon]►Nuke.SiloLaunch= (boolean) 
 
是否从核弹井发射，否的话弹头会直接落下
 
核弹的一切起灰武器之类都要用子武器列表注册，总之要照抄原来的那套，ARES允许多个类型核弹井发射同一超武。

----------------------------------------------------------------------------------------

# 心灵支配

**Type=PsychicDominator**
 
默认值：
 
    [SuperWeapon]►SW.Range= (float,integer) 
控制范围。默认为`[General]►DominatorCaptureRange`
 
    [SuperWeapon]►SW.Damage= (integer) 
控制前伤害，负数是没伤害。默认`[General]►DominatorDamage`
 
    [SuperWeapon]►SW.Warhead= (Warhead) 
伤害弹头。默认`[General]►DominatorWarhead`
 
    [SuperWeapon]►SW.Deferment= (integer - frames) 
启动之前的延时。默认0
 
    [SuperWeapon]►SW.ActivationSound= (Sound) 
启动声音。默认`[AudioVisual]►PsychicDominatorActivateSound`
 
    [SuperWeapon]►SW.AITargeting= (enum) 
瞄准模式。默认`PsychicDominator`
 
    [SuperWeapon]►SW.AffectsHouse= (enum) 
影响对象。默认`all`
 
    [SuperWeapon]►SW.AffectsTarget= (enum) 
控制对象。默认`infantry，units`
 
    [SuperWeapon]►Light.*= (integer) 
颜色，默认是 `[Lighting]►Dominator*Psychic`
 
特殊值:
 
    [SuperWeapon]►Dominator.FirstAnim= (Animation) 
尤里的大头动画。默认`[General]►DominatorFirstAnim`
 
    [SuperWeapon]►Dominator.FirstAnimHeight= (integer - leptons) 
大头高度。默认750
 
    [SuperWeapon]►Dominator.SecondAnim= (Animation) 
生效时候的动画。默认 `[General]►DominatorSecondAnim`
 
    [SuperWeapon]►Dominator.SecondAnimHeight= (integer - leptons) 
生效动画高度。默认0
 
    [SuperWeapon]►Dominator.FireAtPercentage= (integer) 
写整数。表示在这个百分比的大头动画播放完毕时候控制生效，默认`[General]►DominatorFireAtPercentage`
 
    [SuperWeapon]►Dominator.ControlAnim= (Animation) 
被控制的单位头上的圆圈。默认`[CombatDamage]►PermaControlledAnimationType`
 
    [SuperWeapon]►Dominator.Capture= (boolean) 
是否可以控制。默认可以
 
    [SuperWeapon]►Dominator.Ripple= (boolean) 
是否使用波纹效果
 
    [SuperWeapon]►Dominator.CaptureMindControlled= (boolean) 
是否可以控制已经被控制的单位。默认是
 
    [SuperWeapon]►Dominator.CapturePermaMindControlled= (boolean) 
是否控制已经被控制器永久控制的单位。默认是
 
    [SuperWeapon]►Dominator.CaptureImmuneToPsionics= (boolean) 
是否可以强行控制免疫的单位。默认否
 
    [SuperWeapon]►Dominator.PermanentCapture= (boolean) 
是否永久。默认是，不得再控制回去

-----------------------------------------

# 空间传送

**Type=ChronoSphere**
 
超时空需要 `ChronoWarp`以生效
 
默认值：
 
    [SuperWeapon]►SW.Range= (float,integer) 
    [SuperWeapon]►SW.Animation= (Animation) 
    [SuperWeapon]►SW.AnimationHeight= (integer) 
    [SuperWeapon]►SW.AITargeting= (enum) 
    [SuperWeapon]►SW.AffectsHouse= (enum) 
    [SuperWeapon]►SW.AffectsTarget= (enum) 
废话不说了，默认值自己看原版
 
    [SuperWeapon]►SW.PostDependent= (super weapon) 
超时空的副超武，默认超舞列表的第一个ChronoWarp类
 
特殊值：
 
    [SuperWeapon]►Chronosphere.BlastSrc= (Animation) 
起始点动画。默认[General]►ChronoBlast
 
`[SuperWeapon]►Chronosphere.BlastDest= (Animation)` 
目标点动画。默认[General]►ChronoBlastDest
 
`[SuperWeapon]►Chronosphere.ReconsiderBuildings= (boolean)` 
是否移动车辆变成的建筑。默认移动
 
    [SuperWeapon]►Chronosphere.KillOrganic= (boolean) 
是否杀兵。默认yes，no的话步兵也可超时空
 
    [SuperWeapon]►Chronosphere.KillTeleporters= (boolean) 
是否杀Teleporter=yes的单位。默认no
 
    [SuperWeapon]►Chronosphere.AffectsIronCurtain= (boolean) 
是否可以移动铁幕单位。默认no
 
    [SuperWeapon]►Chronosphere.AffectsUnwarpable= (boolean) 
是否受Warpable=no影响。默认yes
 
    [SuperWeapon]►Chronosphere.AffectsUndeployable= (boolean) 
是否影响可以打包的建筑，如果yes,建筑会像车辆一样找最近的空地着陆。默认no
 
    [SuperWeapon]►Chronosphere.BlowUnplaceable= (boolean) 
是否摧毁超时空失败的建筑。默认yes
 
现在可以直接移动一般建筑，其他规则同上。
 
这里还是有问题，超时空的机场不允许生产飞机，探照灯会留在原地。
 
 
Type=ChronoWarp
 
这个超武一切参数只有AI瞄准，鼠标动作和圆圈大小有效，因为是个承载性质的超武。

-----------------------------

# 铁幕&力场护盾

**Type=IronCurtain&Type=ForceShield**

铁幕和力盾的区别就是目标颜色，指定为力盾的超武使用力盾参数。

默认值:

    [SuperWeapon]►SW.Range= (float,integer)
    [SuperWeapon]►SW.Animation= (Animation)
    [SuperWeapon]►SW.AnimationHeight= (integer)
    [SuperWeapon]►SW.AITargeting= (enum)
    [SuperWeapon]►SW.AffectsHouse= (enum)
    [SuperWeapon]►SW.AffectsTarget= (enum)
    [SuperWeapon]►SW.RequiresTarget= (enum)
    [SuperWeapon]►SW.RequiresHouse= (enum) 

特殊值：

    [SuperWeapon]►Protect.Duration= (integer - frames)
持续时间。默认`[General]►ForceShieldDuration和[CombatDamage]►IronCurtainDuration`

    [SuperWeapon]►Protect.PowerOutage= (integer - frames)
掐电时间。护盾默认`[General]►ForceShieldBlackoutDuration`，其他0

    [SuperWeapon]►Protect.PlayFadeSoundTime= (integer - frames)
消失声音在彻底消失之前若干帧开始播放`[SuperWeapon]►SpecialSound`，必须小于`Protect`.`Duration`。护盾默认`[General]►ForceShieldPlayFadeSoundTim`e，其他0

------------------------------------

# 基因突变

**Type=GeneticConverter**

默认值：
 
    [SuperWeapon]►SW.Range= (float,integer)
如果设定`Mutate.Explosion=yes`会被无视

    [SuperWeapon]►SW.Damage= (integer)
    [SuperWeapon]►SW.Warhead= (Warhead)
    [SuperWeapon]►SW.Animation= (Animation)
    [SuperWeapon]►SW.AnimationHeight= (integer)
    [SuperWeapon]►SW.Sound= (Sound)
    [SuperWeapon]►SW.AITargeting= (enum)
    [SuperWeapon]►SW.AffectsHouse= (enum) 

基本参数

    [SuperWeapon]►SW.AffectsTarget= (enum)
设定只能影响 land 或water 的目标，不能写单位名称，默认all

特殊值：

    [SuperWeapon]►Mutate.Explosion= (boolean)
如果是，就用`damage`和`warhead`造个爆炸，无视其他，否的话就用`SW.Warhead`杀兵，无视比例和免疫系统。默认`[General]►MutateExplosion`

    [SuperWeapon]►Mutate.IgnoreCyborg= (boolean)
是否无视电子人`Cyborg=yes`，`Mutate.Explosion=yes`则无视。默认no

    [SuperWeapon]►Mutate.IgnoreNotHuman= (boolean)
是否影响`NotHuman=yes set`，如果 `Mutate.Explosion=yes`无视。默认no

    [SuperWeapon]►Mutate.KillNatural= (boolean)
是否直接地杀死`Natural=yes`，用弹头`SW.Warhead`。默认yes，在有那啥啥代码的时候被无视

------------------------------------------

# 空降部队

**Type=ParaDrop&Type=AmerParaDrop**
 
注意：`Type=AmerParaDrop`只能有一个
 
默认值：
 
    [SuperWeapon]►SW.AITargeting= (enum) 
默认AI瞄准类型为`ParaDrop`
 
旧式空降只能用步兵，坦克填写进去的话会强制用一个步兵类型单位，要有效降坦克，必须用ARES专用代码。
 
不定义类型的话，会用国家和阵营的设定。旧版INI只支持三阵营和美国的默认步兵设定，要降坦克必须用ARES代码重设定，原版的四类全局代码可以删除，改成阵营局部设定。原版删除会IE，ARES可以放心。
 
特殊值：
 
    [SuperWeapon]►ParaDrop.Types= (list of InfantryTypes and/or VehicleTypes) 
单位类型。对于`Type=AmerParaDrop`默认为`AmerParaDropInf=`
 
    [SuperWeapon]►ParaDrop.Num= (list of integers) 
每个单位的数字。对于`Type=AmerParaDrop`默认`AmerParaDropNum=`
 
    [SuperWeapon]►ParaDrop.Aircraft= (AircraftType) 
默认飞机和国家相同
 
    [SuperWeapon]►ParaDrop.Count= (integer - number of planes) 
飞机数目默认1，可以单独设定超武的每一个飞机
 
    [Superweapon]►ParaDrop.ID.PlaneX.*=
ID 是国家或阵营名 X 是正整数，起始点 2 终点是飞机数目 Count。第一架飞机不要用 PlaneX ，如果要，设定所有阵营，ID不写
这个功能就是比如第一个飞机是入侵者第二个飞机是黑鹰第三个是运输机

    [Superweapon]►Paradrop.Country.PlaneX.*=国家设定
    [Superweapon]►Paradrop.Side.PlaneX.*=阵营设定X
    [Superweapon]►Paradrop.PlaneX.*= 超武默认飞机X
    [Superweapon]►Paradrop.Country.*= 国家默认飞机X
    [Superweapon]►Paradrop.Side.*= 阵营默认飞机X
    [Superweapon]►Paradrop.*= 超武的默认飞机
    [Country]►Paradrop.*=国家默认飞机
    [Side]►Paradrop.*= 阵营默认飞机
    [General]►*=全局默认飞机
 
`Type=ParaDrop`和`Type=AmerParaDrop`只有一些默认值的区别，AI都会使用。

-------------------------------

# 侦察机

**Type=SpyPlane**
 
默认值:
 
    [SuperWeapon]►SW.AITargeting= (enum)

特殊值:
 
    [SuperWeapon]►SpyPlane.Type= (AircraftType) 
飞机类型
 
    [SuperWeapon]►SpyPlane.Count= (integer) 
数量
 
    [SuperWeapon]►SpyPlane.Mission= (mission) 
执行任务,任务名称(Guard, Attack, Move , etc)。默认`pyPlane_Approach`

--------------------------------------

#心灵侦测

**Type=PsychicReveal**
 
默认值:
 
    [SuperWeapon]►SW.Range= (float,integer)
使用-1的时候直接开全图，并且不需要手动点。
 
    [SuperWeapon]►SW.Sound= (Sound)
 
    [SuperWeapon]►SW.AITargeting= (enum)

---------------------------------------
----------------------------------------

新增超武
---------

# 超声波

**Type=SonarPulse**
 
可以揭露隐形单位。
 
默认值：
 
    [SuperWeapon]►SW.Range= (float,integer) 
    [SuperWeapon]►SW.AITargeting= (enum) 
    [SuperWeapon]►SW.AffectsHouse= (enum) 
    [SuperWeapon]►SW.AffectsTarget= (enum) 
 
特殊值：
 
`[SuperWeapon]►SonarPulse.Delay= (integer - frames)` 
持续多少帧，默认60

----------------------------------

# 通用弹头

**Type=GenericWarhead**
 
在指定地点引爆一个弹头。
 
默认值：
 
    [SuperWeapon]►SW.Damage= (integer) 
    [SuperWeapon]►SW.Warhead= (warhead) 
    [SuperWeapon]►SW.AITargeting= (enum) 
 
如果要让超武打发射建筑就别忘了给建筑设置`DamageSelf=yes`（就像核弹井），这有个毛用，一帮蛋疼。

------------------------------

# 单位投放

**Type=UnitDelivery**
 
在指定地点投放单位，类似空降仓。
 
默认值：

    [SuperWeapon]►SW.Deferment= (integer - frames)
单位丢上来之前的延迟，默认20

    [SuperWeapon]►SW.ActivationSound= (Sound)
    [SuperWeapon]►SW.AITargeting= (enum) 

特殊值:

    [SuperWeapon]►Deliver.Types= (list of TechnoTypes)
丢出来的单位，建筑也可以

    [SuperWeapon]►Deliver.Buildups= (boolean)
丢建筑出来是否播放建造动画。默认否
 
    [SuperWeapon]►Deliver.Owner= (enum invoker|neutral|special|civilian) 
丢出来的单位归属谁。默认超武发射者

-----------------------

# 火风暴

**Type=Firestorm**

这是个从TS恢复过来的超武，当启动这个超武时，将会激活火风暴围墙，其能量场可以摧毁任何从上面越过的东西包括炮弹（注意，如果在抛射体上有`SubjectToFirestorm=no`的话可以穿过）。

有`Firestorm.Wall=yes`的建筑将会被视为火风暴围墙并且自动连接。

该超武一旦激活，其维持时间由`SW.ChargeToDrainRatio`控制，直到能量耗尽重新进入充能状态，你也可以手动关闭它以防浪费，具体请参考上面的`Charge/Drain`部分，你也可以在ModEnc获得更多信息。

注意：
AI不会用这个超武。
这个超武使用的动画强制为`FSIDLE`，`FSGRND`和`FSAIR`。

-------------------------

# 狩猎者

**Type=HunterSeeker**
 
狩猎者超武是从TS里恢复过来的，这个超武启动时会从建筑飞出一个单位，把地图上任意东西撞爆，可能是步兵，可能是载具，也可能是建筑，如果把基地撞爆就搞笑了，总之是个很蛋疼的超武。
 
译者注：HunterSeeker必需是个载具类的单位而不是飞机类的单位，此外，经过测试，该单位的主武器将会作为撞击的武器，这点将使该超武变得更可控。
 
默认值：
 
    [SuperWeapon]►SW.MaxCount= (integer) 
当拥有多个发射建筑时，一次能够发射最多几个狩猎者，例如设置为5时即使你有10座发射建筑，一次也只能发射最多5个，低于5个发射建筑还是以发射建筑数量为准发射相同数量的狩猎者。默认为1
 
    [SuperWeapon]►SW.AITargeting= (enum) 
默认无目标
 
    [SuperWeapon]►SW.AffectsHouse= (enum) 
默认敌人
 
    [SuperWeapon]►SW.AffectsTarget= (enum) 
默认全部
 
    [SuperWeapon]►EVA.Detected= (EVA event) 
默认`EVA_HunterSeekerDetected`
 
    [SuperWeapon]►EVA.Ready= (EVA event) 
默认`EVA_HunterSeekerReady`
 
    [SuperWeapon]►EVA.Activated= (EVA event) 
默认`EVA_HunterSeekerLaunched`
 
    [SuperWeapon]►Text.Ready= (CSF label) 
默认`TXT_RELEASE`
 
特殊值：
 
    [SuperWeapon]►HunterSeeker.Buildings= (list of BuildingType) 
能够发出狩猎者的建筑，可以不是挂载超武的建筑，如果没有建筑可以发出的话那么狩猎者无法发出且超武不会重新计时。默认`[SpecialWeapons]►HSBuilding`
 
    [SuperWeapon]►HunterSeeker.Type= (VehicleType) 
释放出去的单位，覆盖默认值。默认是这个阵营的HunterSeeker（在新增阵营板块）
 
    [SuperWeapon]►HunterSeeker.RandomOnly= (boolean) 
是否所有敌人单位都能成为狩猎者的目标，如果不是, 非平民目标会成为多人游戏中玩家的首选，如果没有首选目标， 那么就会选择一个随机的目标进行攻击。默认否
 
如何设置狩猎者和攻击目标请去阵营与国家看。
 
关于狩猎者
狩猎者在TS里是一种飞行类单位并且有`HunterSeeker=yes`的设置，它由狩猎者超武发出，具体的请去ModEnc查看。
 
    [SpecialWeapons]►HSBuilding= (list of BuildingTypes) 
能够发出狩猎者的建筑，不一定必须是挂载狩猎者超武的建筑。默认none, TS使用的是`GAPLUG`，`NATMPL`

-------------------------

# 空降仓

**Type=DropPod**
 
这个神奇的超武是从TS里来的，使用这个超武时会有一堆套子从天而降并且对地面进行射♂击，然后从里面跑出一个个兄贵。
 
默认值：
 
    [SuperWeapon]►SW.AITargeting= (enum) 
默认`ParaDrop`
 
    [SuperWeapon]►EVA.Detected= (EVA event) 
默认`EVA_DropPodDetected`
 
    [SuperWeapon]►EVA.Ready= (EVA event) 
默认`EVA_DropPodReady`
 
    [SuperWeapon]►EVA.Activated= (EVA event) 
默认`EVA_DropPodActivated`
 
特殊值：
 
    [SuperWeapon]►DropPod.Types= (list of InfantryTypes) 
空降仓里的兄贵类型，只能是步兵，可以设多个，出来的可能性都是一样的。默认为`[General]►DropPodTypes`
 
    [SuperWeapon]►DropPod.Veterancy= (float) 
出来的兄贵等级，这个值可以取0.0到`[General]►VeteranCap`定义的值。默认2.0（老兵）
 
    [SuperWeapon]►DropPod.Minimum= (integer) 
丢下来的套子的最小数量。默认`[General]►DropPodMinimum`
 
    [SuperWeapon]►DropPod.Maximum= (integer) 
丢下来的套子的最大数量。默认`[General]►DropPodMaximum`
 
这个超武必须放在空地上才能让部队有效着陆，如果释放失败，没有释放出去的部队将会储存到下一次空降仓内。

--------------------------

# 电磁脉冲

**Type=EMPulse**
 
这个超武是从TS里移植的，有点类似于一般武器，不但有攻击范围，还有各种和一般武器类似的特性。
 
默认值：
 
    [SuperWeapon]►SW.RangeMinimum= (float - cell range)
攻击最小范围。默认0
 
    [SuperWeapon]►SW.RangeMaximum= (float - cell range)
最大范围。默认-1，无限大
 
    [SuperWeapon]►SW.MaxCount= (integer)
发射武器的最大数量，负数即有无限发。默认1
 
    [SuperWeapon]►SW.AITargeting= (enum)
默认AI不会用

特殊值：
 
    [SuperWeapon]►EMPulse.Cannons= (list of BuildingType)
指定这个建筑作为EMP炮的发射器，如果不设定，所有`EMPulseCannon=yes`的建筑都会被认定为发射器，需要注意，使用EMP炮的所有建筑都必须设置主武器。默认`none`

    [SuperWeapon]►EMPulse.TargetSelf= (boolean)
是否打自己，和死亡武器很类似，如果要成功发射，必须设置`DamageSelf=yes`，卧槽什么蛋疼功能。默认否
 
    [SuperWeapon]►EMPulse.Linked= (boolean)
是否当仅一门炮需要满足发射范围，其他炮是否满足发射范围也无所谓，只有在`SW.MaxCount`超过1时才会表现出来，区别在于这门炮可以只作为指示者，不必要参与开火。默认否

    [SuperWeapon]►EMPulse.PulseBall= (Animation)
发射武器前在炮口FLH位置表现的准备动画，写`none`可以禁用。默认`PULSBALL`

    [SuperWeapon]►EMPulse.PulseDelay= (integer - frames)
发射前的延迟，默认32。
 
发射表现为EMP炮瞄准目标，炮口产生准备动画，然后发射出一个炮弹打击指定地点，该建筑实际上没有真正地开火，武器的效果也是无效的。
 
如果`EMPulse.TargetSelf=yes`，一个炮弹会立即引爆在所有EMP炮的位置，当然，这些建筑实际上也没有真正地开火。
 
如果建筑有`EMPulseCannon=no`被放进`EMPulse.Cannons`，这个建筑会很正常地发射它的主武器，不需要充能和检测发射范围。