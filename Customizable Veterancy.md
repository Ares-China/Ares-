自定义获得经验方法
===========
Customizable Veterancy
-------------

指定单位获得经验的方法。

以下本体单位不能带有Trainable=no，不然无效，如果乘客，空袭飞机，被控单位，子机带有Trainable=no，那么其获得经验将全部给予本体。

#### 来自乘客的击杀

    [TechnoType]►Experience.FromPassengers= (boolean)

载具里的乘客开火载具能够得到经验，默认是

    [TechnoType]►Experience.PromotePassengers= (boolean)

如果载具满级那么乘客得到经验，默认否

    [TechnoType]►Experience.PassengerModifier= (float - multiplier)

如果一个击杀是由乘客做的，那么所得经验为这个百分比，默认100%

#### 来自召唤空袭的击杀

    [TechnoType]►Experience.FromAirstrike= (boolean)

如果一个击杀由鲍里斯那样的召唤飞机做的, 召唤者能够得到经验而不是给飞机，默认否

    [TechnoType]►Experience.AirstrikeModifier= (float - multiplier)

召唤飞机摧毁对方获得的经验比，默认100%

#### 来自受控单位的击杀

    [TechnoType]►Experience.MindControlSelfModifier= (float - multiplier)

控制的单位摧毁敌方，控制者获得的经验百分比，默认0%

    [TechnoType]►Experience.MindControlVictimModifier= (float - multiplier)

控制的单位获得的经验百分比，默认100%

如果控制者和战斗要塞的所有者不是盟友的话，控制战斗要塞这样的单位，里面的乘客开火摧毁敌方后获得的经验不算在里面. 控制友军单位摧毁敌方，控制者不会得经验。

#### 来自航母子机的击杀 

    [TechnoType]►Experience.SpawnOwnerModifier= (float - multiplier)

子机摧毁敌方单位，航母获得的经验百分比，设置在航母上，默认0%

    [TechnoType]►Experience.SpawnModifier= (float - multiplier)

子机摧毁敌方单位，子机获得的经验百分比，设置在航母上，默认100%
