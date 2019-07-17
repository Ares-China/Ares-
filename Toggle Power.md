切换电源
======
Toggle Power
------------

通过该功能可以手动关闭或开启某个建筑的电源供应来停止其机能，这样可以在电力不足的时候得到应急用的电力。
 
    [General]►TogglePowerAllowed= (boolean)

是否允许手动切换电源，默认否，在游戏里默认没有这个功能的热键，需要自己在键位设置里找
 
    [General]►TogglePowerCursor= (cursor definition)

停电时的鼠标指针

    [General]►TogglePowerNoCursor= (cursor definition)

如果该建筑不能停电，就使用这个鼠标指针
 
建筑被切断电源后，和维修小扳手表现相同，敌人看不到标志，观察者可以看到，不过如果两种状态同时存在会优先表现维修小扳手，停电标志是poweroff.shp，使用鼠标色盘
 
小地图切换电源指针不支持
 
    [IQ]►TogglePower= (integer)

定义这个等级的AI会切换电源，默认-1
 
    [General]►TogglePowerDelay= (integer - frames)

切换电源的延迟，默认45