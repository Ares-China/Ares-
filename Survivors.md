生还者
======
Survivors
-----------

在原来的红色警戒里，飞行员会从毁坏的飞机跳伞。HARES重新引入这个功能以及一些额外的改进，所有这一切都是可以自定义的。

    [TechnoType]►Survivor.Side#= (InfantryType)
 (#代表阵营例如0代表盟军，1代表苏联，2代表尤里)

指定某个阵营的单位被毁后出来的生还者类型

    [TechnoType]►Survivor.Pilots= (integer)

会产生多少单位，有Crewed=yes 默认1，没有就是0

------------------------------------------------------

    [TechnoType]►Survivor.RookiePilotChance= (integer between 0 and 100)
    
    [TechnoType]►Survivor.VeteranPilotChance= (integer between 0 and 100)
    
    [TechnoType]►Survivor.ElitePilotChance= (integer between 0 and 100)

新兵，老兵，精英时驾驶员逃出概率，没有的话`[General]►CrewEscape`控制

    [TechnoType]►Survivor.RookiePassengerChance= (integer between 0 and 100)
    
    [TechnoType]►Survivor.VeteranPassengerChance= (integer between 0 and 100)
    
    [TechnoType]►Survivor.ElitePassengerChance= (integer between 0 and 100)

乘客逃出概率，在空中必死

值得一提的是逃出的驾驶员和载具获得的经验值量是相同的，相对而言。

----------------------------------------------------------------

除了残兵和技师，被占领建筑也可以逃出占有者的工程师，当然这个也要从回收资金里扣除，最小逃出一个，最多五个。

    [BuildingType]►Crew.EngineerChance= (integer - percent between 0 and 100)

占有者逃出工程师的几率（代替一般逃兵），正常情况下被占领建筑绝对不会出工程师除非加上这个语句，默认Factory=BuildingType类建筑是25（25％），其他都是0
