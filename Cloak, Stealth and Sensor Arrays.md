隐形相关
==========
Cloak, Stealth and Sensor Arrays
-------------

#### 需要控制的单位

如果像遥控坦克这样的单位隐形，被杀死驾驶员之类的方法失去隐形后，这个反正依然能被友军的隐形装置影响。
 
#### 寄生单位

现在蜘蛛钻隐型单位不会被甩出来。

#### 空中单位的隐形

现在空中的单位也能受到隐形装置的影响

有`Cloakable=yes`或`CLOAK` 能力升级的单位可以无视高度而隐形. 其他的则可以用以下语句来调整：

    [General]►CloakHeight= (integer) 

在该高度下才能隐形。默认为`[General]►HoverHeight`的值（悬浮单位高度）

#### 隐形声音

    [AudioVisual]►DecloakSound= (Sound) 

全局方面暴露出的声音，默认和 `[AudioVisual]►CloakSound`一样

    [TechnoType]►CloakSound= (Sound) 
微观调控该单位进入隐形状态的声音。默认为 `[AudioVisual]►CloakSound`

    [TechnoType]►DecloakSound= (Sound) 

微观调控该单位暴露出的声音。默认为 `[AudioVisual]►DecloakSound`

#### 隐形层级

给每个单位微观定义隐形层级，覆盖全局值。

    [TechnoType]►Cloakable.Stages= (integer) 

要经历多少层才能进入隐形状态，越小越快。默认为`[General]►CloakingStages`

#### 隐形的条件控制

静止时才隐形

有`CloakStop=yes`的单位只有在静止时才隐形，移动时会暴露，有`BalloonHover=yes`的单位无效

部署时才隐形

该步兵必须有`Cloakable=yes`或`CLOAK`能力升级。

    [InfantryType]►Cloakable.Deployed= (boolean) 

需要部署才能隐形，默认否

只有有电时隐形

`Powered=yes`的建筑在没电时也是隐形的，这种情况可以用这个修正

    [BuildingType]►Cloakable.Powered= (boolean) 

是否要有电才隐形，默认否

#### 完全禁止隐形

    [TechnoType]►Cloakable.Allowed= (boolean)

是否可以隐形，如果写否那么就算用隐形装置也不能让这玩意儿隐形，默认是

#### 反隐形

在TS里`SensorArray=yes`使用`SensorsSight=`的范围来探知隐形和地下单位,并且绘制范围扫描圈。

即使被摧毁然而探知能力仍然存在的问题将不再发生。

两个新的EVA警告已经被添加，`EVA_CloakedUnitDetected`和`EVA_SubterraneanUnitDetected`，这两个会在探测到隐形单位或地下单位时播放。

抑制反隐传感器的警告

    [TechnoType]►SensorArray.Warn= (boolean) 

如果写否那么即使这个单位被传感器侦测到也不会发出警告。默认是
