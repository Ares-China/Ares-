其他新增
==========
Miscellaneous Modding Enhancements
------------------------------

- [可拆分的规则文件](#可拆分的规则文件)
- [CSF功能增强](#CSF功能增强)
- [标签长度](#标签长度)
- [MIX载入规则](#MIX载入规则)
- [分散音频文件](#分散音频文件)
- [Mouse.sha鼠标指针](#Mouse.sha鼠标指针)
- [可避免的内部错误（IE）](#可避免的内部错误（IE）)

可拆分的规则文件
------------

你可以把ini文件拆成好几份然后用这玩意儿整合。
 
    [#include]

把`[#include]`建在`rulesmd.ini`然后这样写：
 
    [#include]
    1=rules_sw.ini
    2=rules_vehicles.ini
    3=rules_buildings.ini
    4=rules_aircraft.ini
    5=rules_infantry.ini

如果在`rulesmd`和`rules_infantry`都有相同代码，`rules_infantry`优先使用。

子ini文件名怎么写都可以。

CSF功能增强
--------

除了`ra2md.csf`，游戏还会载入`stringtable00.csf`到`stringtable99.csf`并且优先级更高。
 
你也能直接在ini里用`NOSTR:prefix`命名，比如，`UIName=NOSTR:Sonar Pulse`会被显示为“Sonar Pulse”，尽管如此，这玩意儿(包括prefix)**不能超过31个**。
 
CSF条目最大能写20000条。

标签长度
---------

从128个字符的限制提升到512个。

MIX载入规则
---------

`expandmd##.mix`会被优先载入，以此覆盖`langmd.mix`。 

分散音频文件
----------

游戏现在能直接读取`WAV`文件，也就是说没有必要再打包进`BAG`了，声音必须在`soundmd.ini`写（不需要`.wav`后缀）。 

Mouse.sha鼠标指针
------------

现在不用在sb里用压缩保存`mouse.sha`也能用了，在原版如果你不用这种方法保存`mouse.sha`就会糊成一坨。

**重要：没有成功实现（啥？）**

可避免的内部错误（IE）
------------------

在`Snowmd.ini`里写：

    [General]►Medians=71

按照它设置就是，否则创建城区出错。