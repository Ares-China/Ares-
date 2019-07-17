受损粒子系统
=============
Damage Particle Systems
------------------------

### 受损火花

当单位受损时会冒烟和飙出火花来，现在可以用这个做到，详情可见ModEnc。

    [TechnoType]►DamageSparks= (boolean)

定义该单位是否会飙出`DamageParticleSystems`所指定的粒子系统。默认`InfantryTypes`是`Cyborg`时有，其他都不会有

### 烟雾和火花的受损粒子系统

HARES加入了两个新标签来启用这个功能，该功能所使用的粒子系统必须包含`BehavesLike=Smoke`或`BehavesLike=Spark`才行。

    [TechnoType]►DamageSmokeParticleSystems= (list of ParticleSystems)

定义使用的烟雾粒子系统。默认为所有有`BehavesLike=Smoke`设置的`DamageParticleSystems`

    [TechnoType]►DamageSparksParticleSystems= (list of ParticleSystems)

定义使用的火花粒子系统。默认为所有有`BehavesLike=Spark`设置的`DamageParticleSystems`
