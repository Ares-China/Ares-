电磁脉冲（EMP）
-------------

EMP禁用易受影响的单位和建筑物及其特殊功能，使其易受攻击。EMP可以通过各种方式影响单位和建筑物：

- 主要影响：单位不会响应任何命令。他们将停止移动，不会攻击任何东西。
- 悬停单位（如机器人坦克）将降落。
- 单位显示可选的闪光动画
- 基于Voxel的单元变暗（基于SHP的单元不是）。
- 可以打包为载具的建筑物（例如MCV）仍然可以，但是所产生的车辆将保持瘫痪，直到EMP效果消失。
- 飞机将立即坠毁。
- 发电厂停止发电。
- 工厂类建筑将停止工作。
- 基地防御将无法发射武器。
- 裂缝产生器将停止产生战争迷雾。
- 激光围栏的墙柱将停止发射激光围栏。
- 控制中心（遥控坦克）将停止工作。
- 超级武器建筑将关闭，超级武器本身将停止充能，如果他们被设置`[SuperWeapon]►IsPowered=yes`（需要电力）
- 雷达建筑物将停止提供雷达。
- 间谍卫星将失效。
- 子机发射器会被瘫痪，子机会直接坠落。
- 奴隶矿工奴隶将停止工作。
- *处于卸载状态的单元（例如矿石收割机存放矿石或Siege Choppers转换）只有在完成卸载后才会停用。*
- EMP击中时正在挖矿的矿车将在EMP消失后继续工作。

EMP动画由以下代码控制

    [General]►EMPulseSparkles=EMP_FX01

#### 定义EMP武器

泰伯利亚之日使用武器`Damage`标签来确定EMP效果会持续多长时间，在Hares中新加入了两条语句*(EMP.Duration and EMP.Cap)*控制，原先的语句是没用的。

    [Warhead]►EMP.Duration= (integer - frames)

默认为0

    [Warhead]►EMP.Cap= (integer - frames)

默认为-1

以上两条语句都被用来控制效果持续多长。

每个单位都有个EMP计时器，这就是原理。

如果你想让被EMP单位瘫痪十秒：`EMP.Duration=150`

除非Verses等于0%，那么单位将不受EMP影响，否则无论弹头比率，目标都会被赋予完全的效果。


> 例：如果你想要一个弹头对目标施放十秒的EMP，那么应该在弹头上添加`EMP.Duration=150`。

#### 瘫痪

当`EMP.Duration`的值为正数时，目标将被瘫痪

- **EMP.Cap＞0**

    EMP叠加效果，但是计数器最大值不会大于设定的cap，如果被此弹头攻击之前计数器已经大于这个cap，则保持不变，总之cap应该是一个武器能造成的给EMP计数器增加的最大值

    例：
   - EMP计数器为0 `EMP.Duration=10`, `EMP.Cap=20`。结果：EMP计数器将设置为10，因为尚未达到上限。
   - EMP计数器是15 `EMP.Duration=10`, `EMP.Cap=20`. 结果：EMP计数器将设置为20.此武器不会超出限额。
   - EMP计数器是60 `EMP.Duration=10`, `EMP.Cap=20`. EMP计数器将保持在60，因为它已经高于上限。

- **EMP.Cap=0**

    还是EMP攻击，不过计数器无上限。目标单位的EMP计数器`EMP.Duration`可以无限叠加。

    例：

   - EMP计数器是25 , `EMP.Duration=10`. 结果：EMP计数器将设置为35.因为没有上限，所以发射此弹头总是会增加10。

- **EMP.Cap=-1**

    当`EMP.Duration`除非目标的EMP计数器已经大于此值，否则 目标的EMP计数器将设置为此指定的绝对帧数 。

    例：

    - EMP计数器是5 , `EMP.Duration=10`. 结果：EMP计数器将设置为绝对值10。
    - EMP计数器是20 , `EMP.Duration=10`. EMP计数器将保持在20，因为它已经更高。

#### 激活

这可以用来激活瘫痪的非敌对单位。如果`EMP.Duration`值为负数，则EMP计数器将会减少指定帧数。

- **EMP.Cap=-1**

    目标的EMP计数器减少了指定的帧数 `EMP.Duration`。

    例：

    - EMP计数器是50 , `EMP.Duration=-10`. 结果：EMP计数器将设置为40。
    - EMP计数器为7，`EMP.Duration = -10`。结果：EMP计数器将设置为零，并且该单元将重新激活，因为EMP效果已完全删除。

- **EMP.Cap＞0**

    目标的EMP计数器减少了指定的帧数 `EMP.Duration`。如果该值仍然大于`EMP.Cap`那么EMP计数器进一步减小到相等`EMP.Cap`。

    例：

    - EMP计数器是50 `EMP.Duration=-10`, `EMP.Cap=70`. 结果：EMP计数器将设置为40。
    - EMP计数器是50 `EMP.Duration=-10`, `EMP.Cap=20`. 结果：EMP计数器将设置为20.它减少到上限值。
    - EMP计数器为7，`EMP.Duration = -10`。结果：EMP计数器将设置为零，并且设备将重新激活。即使没有上限，该单位也会重新激活。

- **EMP.Cap=0**

    `EMP.Duration`无关紧要，因为EMP计数器将通过上限设置为零，并且设备将立即重新激活。这是上述描述的特例。

#### EMP免疫

有几种方法可以创建不受EMP武器影响的单位。

    [TechnoType]►ImmuneToEMP= (boolean)

是否免疫EMP

- **BuildingTypes**：以下建筑类型默认no。

    `Powered=yes`

    `Power=(负数)`

    雷达

    超级武器 (`SuperWeapon` and `SuperWeapon2` only)

    为载具提供动力（例如遥控坦克控制中心）

    裂缝发生器

    隐形探测器

    激光栅栏

此外的其他建筑默认为yes

- **InfantryTypes**：默认为no，除`Cyborg=yes`以外

- **VehicleTypes and AircraftTypes**：默认为yes，除`Organic=yes`以外

新的升级能力**EMPIMMUNE**也可以获得EMP免疫

    VeteranAbilities=EMPIMMUNE
    EliteAbilities=EMPIMMUNE

EMP immunity also respects `TypeImmune` on the TechnoType, as well as `AffectsAllies` and `AffectsEnemies` on the warhead.

EMP效果持续时间
-------------

Hares允许不完全影响对象，即允许减少或增加每种EMP的持续时间。因此，高科技的载具可能比普通的载具会有更长的瘫痪时间，而相对技术较低的吉普车则可以比一般载具更快的恢复运行。

    [TechnoType]►EMP.Modifier= (float - multiplier)

对EMP的抗性，只受到EMP影响的百分之几，默认100%

EMP摧毁单位
----------

某些单位应该是直接被EMP摧毁而不是瘫痪。飞机会瞬间被EMP摧毁，但某些飞行器例如武装直升机，基洛夫，飞碟并不算是飞机。EMP.Threshold 能改变这个现象。

你可以创建一个陆地单位，在承受一定的EMP也会被摧毁，或者像武直一样的单位（`BalloonHover=yes` or `JumpJet=yes`），陆地不会被摧毁，然而在空中承受100帧EMP后掉下来。

    [TechnoType]►EMP.Threshold= (enumeration - one of yes|no|inair *or* integer - frames)

制定该单位是否会被EMP摧毁. 如果使用整数那么该单位在承受如此剂量的EMP后才会被摧毁。

- 正数表示达到这个量摧毁单位，填yes等同于1

- 负值表示只有在空中达到这个量才会摧毁这个单位. 填inair等同于-1

- 0就是无效，等同于no

EMP.Threshold 默认是inair，EMP能摧毁任何在空中的单位

> 跳伞的单位不算在这里面。只有超过其正阈值（如果存在）才会杀死它们。

EMP动画
-------

当单位或建筑物受到EMP的影响时，它可以显示可选的动画。

    [TechnoType]►EMP.Sparkles= (animation)

当该单位被EMP时显示该动画。默认[General]?EMPulseSparkles

    [Warhead]►EMP.Sparkles= (animation) 

弹头的EMP效果，如果设置了该语句就会覆盖单位本身的EMP效果。只有在单位本身已经没有其他EMP效果时才会表现。

> 注意：Yuri's Revengeemp_fx01.shp附带的文件 以及默认引用的文件仍然位于Tiberian Sun调色盘中，需要进行转换。[General]►EMPulseSparkles