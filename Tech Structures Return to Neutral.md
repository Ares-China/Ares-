中立科技建筑重归属
=============
Tech Structures Return to Neutral
-----------------

现在在游戏中当中立科技建筑的占有者败北，投降后，被占领的科技建筑将不会被一起摧毁而是回归到初始拥有者（即中立方）。

只有有`MultiplayPassive=yes`的所属方可以允许这个条件，同时在单人游戏里无效。

    [General]►ReturnStructures= (boolean)

是否被占领建筑可以回归中立方当占有者败北或投降时，默认否

    [BuildingType ]►Returnable= (boolean)

是否该建筑可以回归中立方，默认`[General]►ReturnStructures`

    [BuildingType]►LostEvaEvent= (EVA event)

当该已经被我方占领的科技建筑被其他玩家占领时播放EVA语音。需要`NeedsEngineer=yes`。默认`EVA_TechBuildingLost`

    [BuildingType]►Message.Capture= (CSF label)

占领时显示CSF。需要`NeedsEngineer=yes`。默认`none`

    [BuildingType]►Message.Lost= (CSF label)

丢失时显示CSF。需要`NeedsEngineer=yes`。默认`none`

