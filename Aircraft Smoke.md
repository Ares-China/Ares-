飞机损坏尾烟
===========
Aircraft Smoke
--------------

当一个飞机受到严重损伤或者被击落时会产生一堆尾烟，这个尾烟是硬编码的，也就是说所有飞机的尾烟都是一样的，现在可以对每架飞机进行自定义。

    [AircraftType]►Smoke.Anim= (animation)

产生的尾烟。默认SGRYSMK1

    [AircraftType]►Smoke.ChanceRed= (integer - percent)

严重损伤时产生烟雾的密度（每帧），越大越多。默认10

    [AircraftType]►Smoke.ChanceDead= (integer - percent)

被击落时产生烟雾的密度（每帧），越大越多。默认80
