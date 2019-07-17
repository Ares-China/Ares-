单位被毁的独立EVA语音
==================
Unit Lost EVA Report
--------------------

现在单位被毁可以设置其独有的EVA语音，当然也可以借此把EVA语音关闭，这样就不用给单位写不计入损失数的语句什么的了

当然，有`DontScore=yes`，`Insignificant=yes`或者`Spawned=yes`的单位是不会被播报的。

    [Unit]►EVA.Lost= (evamd entry)

填`none`就是不播报，默认是`EVA_UnitLost`
