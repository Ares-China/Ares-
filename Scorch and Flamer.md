烧焦和火焰喷射器
=============
Scorch and Flamer
----------------------

在TS里支持凝固汽油弹等纵火武器的动画效果，现在这个功能已经在ARES里恢复了，这个效果由`SmallFire`和`LargeFire`这两个标签定义。
 
    [Animation]►Scorch= (boolean)

这个动画会将`[AudioVisual]►SmallFire`指定的动画蔓延到周围，不过不会在水，冰，岩石等地方产生
 
    [Animation]►Flamer= (boolean)

这个动画会在周围随机产生`[AudioVisual]►SmallFire`和`[AudioVisual]►LargeFire`指定的动画 