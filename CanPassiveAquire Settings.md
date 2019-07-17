主动攻击设置
===========
CanPassiveAquire Settings
-------------------------
在TS里（当然在RA2里也是），所有单位默认`CanPassiveAquire=yes`，即主动攻击，这导致像隐形坦克这样的单位在不该开火的时候会开火（如果玩家不控制），现在有新功能可以解决这类问题。
 
    [TechnoType]►CanPassiveAquire.Guard= (boolean)

是否在防御模式（放在那不管）下能够主动攻击，如果设置no，那么这个单位不会主动攻击，不过在区域防守模式下依然可以主动攻击。默认yes

    [TechnoType]►CanPassiveAquire.Cloak= (boolean)

是否能够主动攻击当隐形并且在防御模式，如果设置no, 那么这个单位在隐形时不会主动攻击，，不过在区域防守模式下依然可以主动攻击。

`CanPassiveAquire.Guard=no`会覆盖这个标签，默认yes

如果第一条yes（默认），第二条no，那隐形坦克在隐形状态就不会主动攻击，但是暴露时就会主动攻击，或者一些平时不会隐形的单位，也可以设置这条，当偶然获得隐形时就不会随便惹事了。