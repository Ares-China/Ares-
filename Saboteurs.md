破坏者
=========
Saboteurs
--------------------

沙丘2000中有一种名为破坏者的步兵，他们能够进入建筑并摧毁之，同时牺牲自己，HARES复刻了这个逻辑。
 
只有敌方建筑可以被破坏，在可破坏的建筑上玩家会得到进入光标。

    [InfantryType]>Saboteur= (boolean)

是否这个步兵可以进入可破坏建筑。这个建筑将会像按了C4一样被摧毁，并且破坏者在这个过程中被消耗。需要`Infiltrate=yes`。不能和偷车贼逻辑，`CanDrive=yes`, C4和`Occupier=yes`语句连用。默认为no
 
    [BuildingType]>ImmuneToSaboteurs= (boolean)

这个建筑能否被破坏，如果填yes，破坏者就不能进入。如果写了`CanC4=no`或者`TechLevel=-1`或者`CanBeOccupied=yes`则默认yes，其他情况下为no