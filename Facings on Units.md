单位的更多面数
===========
Facings on Units
--------------------

Hares现已支持为`VehicleTypes`提供超过8个面板。设置为`artmd.ini`：

    [VehicleType]►Facings=（整数）（8*2^n）

用于基于SHP的单位的方向数量。支持等于或大于8的2的幂。小于8的值仅导致使用第一帧。默认为8。