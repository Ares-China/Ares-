PCX文件图标
==========
PCX Cameos
-------------

图标能使用PCX文件而不仅仅是SHP了，这可以使图标更精细。

在`artmd.ini`里:

    [UnitArt]►CameoPCX= (filename, *including* the .pcx extension)

    [UnitArt]►AltCameoPCX= (filename, *including* the .pcx extension)

指定该单位的PCX图标，格式为“`filename.pcx`“

在`rulesmd.ini`里:

    [SuperWeapon]►SidebarPCX= (filename, *including* the .pcx extension)

超武用，和上面一样

和其他PCX文件一样，需要用**索引色**，并且图标PCX必须是**256色**且大小为**60x48**像素。
