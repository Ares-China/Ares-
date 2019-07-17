自定义导弹
==========
Custom Missiles
-------------

Hares允许你创建新的导弹类型和自定义现有类型（`V3RocketType，DMislType，CMislType`）。

***【本节翻译存疑】***

**导弹** 是具有特殊逻辑的飞机类型，其行为类似于从另一个单元发射的弹丸并且将弹头携带到其目标。

    [AircraftType]►Missile.Custom= (boolean)

是否为自定义导弹，默认否

-------------------------

以下标签仅在`[AircraftType]►Missile.Custom=yes`设置时才有效

#### 自定义导弹设置

    [AircraftType]►Missile.PauseFrames= (integer)

定义导弹在倾斜前在发射装置上暂停的帧数。默认为0。

    [AircraftType]►Missile.TiltFrames= (integer)

定义导弹倾斜到射击位置所需的帧数。默认为0。

    [AircraftType]►Missile.PitchInitial= (float)

在向上倾斜之前定义导弹的起始俯仰角。有效范围是 0.0（水平）到1.0（垂直）。默认为 0.0。

    [AircraftType]►Missile.PitchFinal= (float)

定义导弹在倾斜和射击后的结束俯仰。有效范围是0.0（水平）到1.0（垂直）。默认为0.0。
    [AircraftType]►Missile.TurnRate= (float)

定义导弹在空中的俯仰可操纵性。有关示例，请参阅原始导弹。有效范围是0.0到1.0。默认为0.0。

    [AircraftType]►Missile.RaiseRate= (float)

定义导弹在发射装置上每转一圈的程度。默认为0.0。

    [AircraftType]►Missile.Acceleration= (float)

定义在发射期间每一帧导弹的速度增加多少。默认为0.0。

    [AircraftType]►Missile.Altitude= (integer)

定义高度导弹开始平直飞行的巡航高度。默认为0。

    [AircraftType]►Missile.BodyLength= (integer)

定义导弹体在平直高度中的持续时间。这用于绘制尾烟。默认为0。

    [AircraftType]►Missile.LazyCurve= (boolean)

导弹的路径是否像原始的V3火箭一样是弹道曲线。否则导弹将保持定义的高度。默认为 否。

#### 弹头和伤害

    [AircraftType]►Missile.Damage= (integer)

定义从新兵或老兵单位发射导弹时造成的伤害。默认为0。

    [AircraftType]►Missile.EliteDamage= (integer)

定义从精英发射导弹所造成的伤害。默认为0。

    [AircraftType]►Missile.Warhead= (Warhead)

定义导弹用于从新手或老兵单位发射时造成伤害的弹头。默认为`none`。

    [AircraftType]►Missile.EliteWarhead= (Warhead)

定义导弹用于从精英发射时造成伤害的弹头。默认为`none`。

#### 或者使用武器

不是使用一对伤害和弹头设置来造成伤害，也可以定义一种在导弹爆炸时会发射的武器。该武器用于控制抛射体，弹头，伤害和闪光的设置。

>用于下面标签的武器必须添加到 WeaponTypes列表中，否则可能无法正确解析它们。

    [AircraftType]►Missile.Weapon=（Weapon）

用来造成伤害的武器。如果未设置，`Missile.Damage`并 `Missile.Warhead`用于创建爆炸。默认为`none`。

    [AircraftType]►Missile.EliteWeapon=（Weapon）

用来造成伤害的武器。如果未设置，`Missile.EliteDamage`并 `Missile.EliteWarhead`用于创建爆炸。默认为`none`。

#### 相关动画

    [AircraftType]►Missile.TakeOffAnim= (Animation)

定义导弹起飞时播放的可选动画。默认为`V3TAKOFF`。

    [AircraftType]►Missile.TrailerAnim= (Animation)

定义用于绘制此导弹尾烟的可选动画。默认为`V3TRAIL`。

    [AircraftType]►Missile.TrailerSeparation= (integer)

定义创建另一个尾烟动画的帧数。默认为3。