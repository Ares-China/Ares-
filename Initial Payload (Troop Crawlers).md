初始载员
=======
Initial Payload (Troop Crawlers)
--------------------------------

在命令与征服将军中中国的运兵车出厂时自带一个红卫兵，现在这个功能被加入了HARES豪华午餐。
 
如果是建筑，必须带有`CanBeOccupied=yes`或者`InfantryAbsorb=yes`设置，不然将不支持初始载荷逻辑。建筑只支持步兵载荷。
 
初始载荷不能超过建筑的`MaxNumberOccupants`或者载具的`Passengers`，并且确保`Size`和`SizeLimit`没问题。
 
步兵不能用这逻辑。
 
    [TechnoType]>InitialPayload.Types= (list of TechnoTypes)

初始载荷这些单位，可以写多个，不允许写建筑和空军！由于连环套会导致死循环，所以修复了，可以放心用
 
    [TechnoType]>InitialPayload.Nums= (list of integers)

数量，对应上面那个，不设定的话全部都是1