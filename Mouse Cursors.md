自定义鼠标指针
=============
Mouse Cursors
--------------

ARES允许自定义鼠标，总共有两种样式，一种是独立的六个标签，另一种是合并进一个标签里，用逗号隔开的表现形式。
 
    [Section]►BaseTag.Frame= (integer)

起始帧，注意在`mouse.sha`里第一帧是0

    [Section]►BaseTag.Count= (integer)

多少帧

    [Section]►BaseTag.Interval= (integer)

动画周期，默认5

    [Section]►BaseTag.MiniFrame= (integer)

和`BaseTag.Frame`一样，不同的是这是小地图的鼠标，-1将禁用迷你地图鼠标（只允许玩家点击战场）

    [Section]►BaseTag.MiniCount= (integer)

迷你鼠标的帧数

    [Section]►BaseTag.HotSpot= (HotSpotX,HotSpotY)

点击位置在`mouse.sha`里使用的位置，HotSpotX应该是**Left，Center或者Right**，HotSpotY应该是**Top，Middle或者Bottom**。默认Center,Middle，即正中间
 
便于复制：

    [Section]►BaseTag.Frame=
    
    [Section]►BaseTag.Count=
    
    [Section]►BaseTag.Interval=
    
    [Section]►BaseTag.MiniFrame=
    
    [Section]►BaseTag.MiniCount=
    
    [Section]►BaseTag.HotSpot=
 
-------------------------
 
    [Section]►BaseTag= (cursor definition)

写七个值，分别代表*Frame，Count，Interval，MiniFrame，MiniCount，HotSpotX，HotSpotY*，需要用逗号分开（逗号得用英文的逗号切记）

> You cannot directly use the same definitions as used with other patches for Yuri’s Revenge, because Ares uses descriptive names instead of numbers for the HotSpotX,HotSpotY parts. To convert the values, replace 0 by either Left or Top, 12345 by either Center or Middle, and 54321 by either Right or Bottom.（Ares0A）