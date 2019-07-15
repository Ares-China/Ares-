Hares Documentation
============================
哈瑞斯使用说明
-------------
![Hares](https://i.imgur.com/n5DnMZg.png)

HARES平台由Zero Fanker及其HARES工作组制作

本说明书内容Ares部分，内容根据Ares原文以及原Ares0.9rc1中文版说明书进行翻译，Ares0.9rc1中文版说明书由MK，十進制，一插一翻译。

申明：假使本说明书翻译内容与原文若有错误，缺失，重复，使用者因此而造成的问题请自行承担，翻译者无义务对问题负责，档燃，你可以联系现任翻译者指出问题，是否解释由翻译者决定

# **Table of Contents**
## 目录
### Introduction
#### -*基本介绍*
- Known Major Issues - 已知的主要问题
   - Save Games - 保存游戏
### Required Changes For Mods Using Ares
#### -*使用Hares的Mod所需的修改*
- artmd.ini
- bombcurs.shp
- ares.mix
### What’s New and Bug Fixes
#### -*BUG修复和更新内容*
## Restored Tiberian Sun Logic - 被修复的TS逻辑
- Action=SellUnit - **等待翻译**
- Amphibious Image Changes - 两栖单位水陆切换不同形态
- Electromagnetic Pulse (EMP) - 电磁脉冲
- Firestorm Wall - 火风暴
- Laser Fences - 激光围栏
- Multi Engineer - 多位工程师
- Spotlights - 聚光/探照灯
- Vehicle Thief - 窃车
# New & Enhanced In-Game Logic - 新增的逻辑内容
- 新增护甲以及免疫方案 - Additional ArmorTypes and Verses
- 飞机损坏尾烟 - Aircraft Smoke
- 空中动画帧率 - AirRate
- 空袭语音 - Airstrike Voices
- 根据气候换装 - AlternateTheaterArt
- **★属性赋予★** - **★AttachEffect★**
- 主动攻击设置 - CanPassiveAquire Settings
- 吊运载具 - Carryalls
- 超时空监狱/劫持者 - Chrono Prisons / Abductors
- 超时空转移 - Chronoshift
- 平民敌对目标 - Civilian Enemies
- 飞机坠毁控制 - Crashing  
- 碾压伤害 - Crush Damage
- 自定义鼠标指针 - Mouse Cursors
- 自定义动画及抛射体色盘 - Custom Animation and Projectile Palettes
- 自定义图标色盘 - Custom Cameo Palettes
- 自定义军衔标识 - Veterancy Insignia
- 自定义降落伞 - Customizable Parachute Animations
- 自定义获得经验方法 - Customizable Veterancy
- 自定义导弹 - Custom Missiles
- 受损粒子系统 - Damage Particle Systems
- 电磁脉冲摧毁单位 - **缺少原文**
- 调整失灵单位的光照 - Dimming Deactivated Units
- 飞碟激光动画 - Disk Laser Animations
- 泰伯利亚恶魔 - Tiberian Fiends
- 吸取武器选项(飞碟) - Drain Weapon Options
- 空降仓 - Drop Pods
- 新增EVA语音 - EVA Types
- 单位的更多面数 - Facings on Units
- 森林火灾 - Forest Fires
- 盖特逻辑增强(可循环) - Gattling Enhancements
- 硬编码单位标签 - Hard-coded Unit Properties
- 劫车犯 - Hijackers
- 狩猎者 - Hunter Seeker
- 步兵触电死亡动画 - InfantryElectrocuted
- 初始载员 - Initial Payload (Troop Crawlers)
- 击杀驾驶员 - Killing Drivers
- 基因突变的步兵归属MakeInfantryOwner
- 新遥控坦克逻辑New Powered Unit Logic
- 泛碾压设置 - OmniCrusher Enhancements
- 操作者 - Operator
- 特定乘客类型 - Specific Passengers
- PCX文件图标 - PCX Cameos
- 自定义驻兵格子 - Pips
- 新的出兵逻辑 - Prerequisites
- 雷达干扰 - Radar Jammers
- 逆向工程逻辑 - Reverse Engineer logic
- *破坏者* - Saboteurs
- 烧焦和火焰喷射器 - Scorch and Flamer
- 更大视野 - Sight
- 子机 - Spawners
- 生还者 - Survivors
- 团队复仇 - Team Retaliate
- 类别选择组 - Type Selection Groups
- 单位被毁的独立EVA语音 - Unit Lost EVA Report
- **国家与阵营** - Sides & Countries
   - 阵营 - Sides
   - 国家 - Countries
- **建筑物** - Buildings
   - 训练所 - Academies
   - 突击者 - Assaulter
   - 自定义建筑面积 - Custom Building Foundations
   - 隐藏维修扳手 - EnemyWrench
   - 指定工厂&克隆工厂 - Factories and Cloning
   - 力场护盾的微观效果 - ForceShield
   - 闸门 - GateDown
   - 避雷针 - Lightning Rods
   - 可通行构造 - IsPassable
   - 光棱塔递光逻辑 - Prism Forwarding
   - 油井逻辑扩展 - Oil Derricks (ProduceCash)
   - 秘密科技实验室 - Secret Labs
   - 会被建筑阻挡的抛射体 - Solid Buildings
   - 间谍渗透功能强化 - Spy Behavior
   - 中立科技建筑重归属 - Tech Structures Return to Neutral
   - 切换电源 - Toggle Power
   - 建筑微损伤 - Trivial Structure Damage
   - 巷战-战壕 - Urban Combat - Trenches
- **隐形相关** - Cloak, Stealth and Sensor Arrays
   - 通用内容 - General Changes and Updates
   - 隐形高度 - Cloaking and Units Above Ground
   - 隐形声音 - Cloak Sounds
   - 隐形阶段 - Cloaking Stages
   - 隐形条件控制 - Cloak Depending On State
   - 反隐形 - Sensor Arrays
- **抛射体** - Projectiles
   - 多方向抛射体动画化 - Animations and Rotates=yes
   - 弹道分布 - BallisticScatter
   - 有效追击范围 - Ranged
   - 分裂和空爆 - Splits and Airburst
- **武器** - Weapons
   - [WeaponTypes]注册表 - [WeaponTypes] Section
   - 多面数开火动画 - Anim for Facings
   - 声波武器和喷火武器正常伤害 - Ordinary Damage for IsSonic and UseFireParticles
   - 自定义伊文炸弹 - Ivan Bombs
   - 自定义辐射波 - Radiation Beams
   - 自定义特斯拉 - Electric Bolt Coloring
   - 波逻辑 - Waves
   - 粗极光 - LaserThickness
   - 动画关联武器 - ProjectileRange
- **弹头** - Warheads
   - 通用特殊效果 - General Settings
   - 溅射范围 - CellSpread Enhancements
   - 铁幕弹头 - Iron Curtain Effect
   - 永久心灵控制 - Permanent Mind-Control
   - 自定义空间武器弹头死亡动画 - Customizable WarpAway
   - 环状波纹 - Ion Cannon Ripple Effect
   - 缓冲动画 - PreImpactAnim
   - 部署步兵受伤百分比和新增死亡动画 - Infantry-related Settings
   - 狂怒状态的攻击速度 - Berserk Reloading Time Modifier
   - 不触发死亡武器弹头 - Suppress Death Weapons
   - 立体爆炸弹头X
   - 机械与生物弹头X
- **超级武器** - Super Weapons
   - 通用设置 - General properties
   - ====原有====
   - 闪电风暴
   - 核弹打击
   - 心灵支配
   - 超时空传送
   - 铁幕&立场护盾
   - 基因突变
   - 空降部队
   - 侦察机
   - 心灵感测
   - ====新增====
   - 超声波
   - 通用弹头
   - 单位投放
   - 火风暴
   - 狩猎者
   - 空降仓
   - 电磁脉冲
- **泰伯利亚功能**Tiberium
   - 储藏和矿井 - Storage and Silos
   - 泰伯利亚泄露 - Tiberium Spill
   - 泰伯利亚治愈 - Tiberium Heal
   - 泰伯利亚残留 - Tiberium Remains
   - 泰伯利亚伤害 - Tiberium Damage
   - 器官兽 - Visceroids
   - 泰伯利亚爆炸 - Tiberium Explosive
   - 连锁反应 - Chain Reactions
- **其他新增** - Miscellaneous Modding Enhancements
   - 可拆分的规则文件 - [#include]
   - CSF功能增强 - String Table Enhancements
   - 标签长度 - List Lengths
   - MIX载入规则 - MIX Loading Order
   - 分散音频文件 - Loose Audio Files
   - Mouse.sha鼠标指针 - Mouse.sha
   - 可避免的内部错误(IE) - Avoidable Internal Errors
- **用户界面功能** User Interface Features
   - 位图截图 - Bitmap Screenshots
   - 战役列表
   - 战役载入界面
   - 命令行参数
   - 自定义战役按钮
   - 可定制的玩家颜色
   - 图形/曲面绘图
   - 内部错误IE/抓虫
   - 快捷键（热键）
   - 载入屏幕
   - 单人遭遇战
   - 菜单自定义
   - MOD信息
   - 分辨率
   - 随机地图生成器
   - 开发游戏标签
   - 用户界面颜色
