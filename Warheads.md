弹头
====
Warheads
----------

- [通用设置](#通用设置)
- [溅射范围](#溅射范围)
- [铁幕弹头](#铁幕弹头)
- [永久心灵控制](#永久心灵控制)
- [自定义空间武器弹头死亡动画](#自定义空间武器弹头死亡动画)
- [环状波纹](#环状波纹)
- [缓冲动画](#缓冲动画)
- [部署步兵受伤百分比](#部署步兵受伤百分比)
- [新增步兵死亡动画](#新增步兵死亡动画)
- [狂怒状态的攻击速度](#狂怒状态的攻击速度)

通用设置
----------

#### 是否伤害敌人

    [Warhead]►AffectsEnemies= (boolean)

默认yes，no即不伤害。

#### 非恶意弹头

    [Warhead]►Malicious= (boolean)

这个弹头施加在单位上是否会引起伊娃的警告以及雷达事件。

默认值yes，no为非恶意，即不会引起警告。

#### 防止散布

    [Warhead]►PreventScatter= (boolean)

当这个弹头施加到目标单位的时候，单位将不会散开以企图躲避。

默认no，yes即防止散开。

溅射范围
---------

在YR里，弹头的溅射范围最大只能达到11，而且极不稳定，在HARES里加强了这玩意儿，现在溅射范围将不再受到限制，并且对AE，铁幕等特殊类型弹头同样有效。

警告：如果你把数值翻了一倍，那么范围将会翻两番，为了游戏稳定性最好不要滥用……真的会卡的。

#### 溅射伤害限制

在YR里一个溅射弹头打中建筑，由于建筑占多个格子，这个伤害将会多次计算（这也就是为什么V3这种东西打防御建筑效果一般，但是打大型建筑简直是拆迁王的原因），在ARES里可以设定一个溅射弹头击中建筑后伤害次数限制，通过以下标签来指定。

    [Warhead]►CellSpread.MaxAffect= (integer)

该弹头打中建筑伤害最多计算几次，如果是1的话那么无论该弹头对该建筑命中多大范围，伤害就是武器的正常伤害。默认-1，即无限

铁幕弹头
-------

可以加铁幕，可以消铁幕。

和EMP一样为局部定义，一个弹头有自己的叠加参数，比如强力铁幕弹头可以+100，最高151帧，垃圾铁幕弹头最高堆20帧一次+10，一个铁幕计数器50的单位被强力弹头打了变150，再被弱的打一下还是150。

    [Warhead]►IronCurtain.Duration= (integer - frames)
正数加，负数减，帧数

    [Warhead]►IronCurtain.Cap= (integer)
负数不能叠加，0无限叠加，不是0就是有个最大值除非铁幕计数器已经超过最大值

    [TechnoType]►IronCurtain.Modifier= (float - multiplier)
单位受铁幕影响的倍数关系，默认100，0就是不受影响

如果铁幕效果和普通效果同时存在，必定是先常规伤害，organic和步兵会秒杀

永久心灵控制
----------

    [Warhead]►MindControl.Permanent= (boolean)

和NP一样

自定义空间武器弹头死亡动画
------------------

    [Warhead]►Temporal.WarpAway= (animation)

超空间兵抹除单位后的动画，微观动画会覆盖`[General]►WarpAway=`

环状波纹
--------

    [Warhead]►Ripple.Radius= (integer, scale unknown)

心灵控制，离子炮那个波纹视觉效果，建议不要设置半径79以上

缓冲动画
---------

核弹实际爆炸前有个短暂的爆光动画，YR里被平台定死了，现在可以自定义了

    [Warhead]►PreImpactAnim= (string, animation ID)

这个弹头实际爆炸前会先播放这个动画

部署步兵受伤百分比
--------------

    [Warhead]►Damage.Deployed= (float - multiplier)

部署单位受伤比例，现在部署单位和匍匐单位独立了

新增步兵死亡动画
-----------

    [Warhead]►InfDeathAnim= (string, animation ID)

和NP一样

狂怒状态的攻击速度
--------------

在YR里，被混乱气流（带有`Psychedelic=yes`的弹头）波及到的单位会进入狂怒状态，除了不受控制任意攻击外，其开火速度会大幅增强，现在可以自定义每个单位在狂怒状态下的开火速度倍数。
 
    [CombatDamage]►BerserkROFMultiplier= (float - multiplier)

全局开火速度倍数，越小越快。默认0.5，即开火速度快两倍
 
    [TechnoType]►Berserk.ROFMultiplier= (float - multiplier)

微观开火速度倍数，默认`[CombatDamage]►BerserkROFMultiplier`