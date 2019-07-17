碾压伤害
=======
Crush Damage
----------

来自沙丘2000的复刻逻辑，这个逻辑可以让坦克在压死步兵时对坦克造成伤害。 
 
    [TechnoType]►CrushDamage= (integer - hitpoints)
 
    [TechnoType]►CrushDamage.Rookie= (integer - hitpoints)
 
    [TechnoType]►CrushDamage.Veteran= (integer - hitpoints)
 
    [TechnoType]►CrushDamage.Elite= (integer - hitpoints)
当载具压过带有以上语句的单位时会对碾压者造成的伤害。默认0
 
    [TechnoType]►CrushDamage.Warhead= (Warhead)
碾压伤害的弹头。默认`[General]>C4Warhead`