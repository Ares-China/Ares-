空中动画帧率
===========
AirRate
--------

当一个单位移动时，`WalkRate`是用来控制该单位的图像的，当其空闲时，`IdleRate`被使用，一个单位若不在移动则视为空闲，包括起飞，着陆和漂浮，直升机型的单位就算看起来真的在空中时也不会播放他们的螺旋桨图像，Hares为了应对这种情况加了一个新标签。

    [TechnoType]►AirRate= (integer - number of frames)

如果该值大于零，规定了该单位在空中时，计划要给该单位几帧的动画，`AirRate`覆盖`WalkRate`与`IdleRate`，若该值为零，则禁用`AirRate`，默认为0