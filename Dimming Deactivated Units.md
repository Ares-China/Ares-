调整失灵单位的光照
==============
Dimming Deactivated Units
-------------------------

被EMP，需要驾驶员的载具无驾驶员，失去控制中心控制的单位会变黑，现在可以对变黑的程度进行自定义。

    [AudioVisual]►DeactivateDimEMP= (float - multiplier)

被EMP的单位的变黑程度。默认0.8

    [AudioVisual]►DeactivateDimOperator= (float - multiplier)

需要驾驶员的载具无驾驶员时的变黑程度。默认0.65

    [AudioVisual]►DeactivateDimPowered= (float - multiplier)

失去控制的单位的变黑程度。默认0.5

> 注意
> 
> 这个值一般取0到1之间，写1就是和原来亮度一样，如果超过1那么会变亮，你要做特殊效果我没话说。
> 
> SHP类的单位是不会被这个影响的。