# 逆向分析总览：Cozy Coco Catcher

## 来源与范围
- 游戏入口：`https://html-classic.itch.zone/html/18013330/index.html`
- HAR 请求记录：183 条；成功响应资源已去重提取。
- 本次提取不是开发者原始 Construct 3 工程，而是浏览器部署文件 + `data.json`。
- 本次部署数据中未发现 `.c3p` 文件。

## 场景/布局

- **ObjectDB**：2×2；事件表 `None`；1 个图层。
- **Skill Tree**：960×540；事件表 `eNodes`；6 个图层。
- **Game**：1200×270；事件表 `eGame`；11 个图层。
- **Title**：480×270；事件表 `eTitle`；7 个图层。
- **Intro**：480×270；事件表 `eIntro`；1 个图层。
- **End**：480×270；事件表 `eEnd`；7 个图层。

## 主要对象（根据对象类型名称、变量、行为和动画定义整理）

- `Player`（ObjectTypes[40]）：变量：MoveX, MoveY, MoveAngle, Side；行为：ScrollTo, MoveTo, Timer, Tween, Platform, BoundTo, Persist；动画：Animation 1
- `PlayerSprite`（ObjectTypes[42]）：行为：Tween；动画：IdleRight, MoveRight, JumpRight, IdleLeft, MoveLeft, JumpLeft
- `PlayerEyes`（ObjectTypes[41]）：动画：Right, Left
- `Tree`（ObjectTypes[43]）：变量：Coconuts, Shake；行为：Tween, Timer；动画：Animation 1
- `TreeTop`（ObjectTypes[55]）：行为：Tween, Sine, Sine2；动画：Animation 1, Animation 2
- `Coconut`（ObjectTypes[38]）：变量：Side, Active；行为：Platform, Tween；动画：Animation 1
- `Coin`（ObjectTypes[39]）：变量：Active, Side；行为：Platform, Tween；动画：Gold
- `NPC`（ObjectTypes[45]）：变量：Name, Line；动画：Animation 1
- `Captain`（ObjectTypes[46]）：行为：Tween；动画：Animation 1
- `Shop`（ObjectTypes[53]）：变量：Coconuts；行为：Tween, Persist；动画：Animation 1
- `Ship`（ObjectTypes[52]）：行为：Sine, Sine2；动画：Animation 1
- `Chest`（ObjectTypes[48]）：变量：Coins；行为：Tween, Persist；动画：Animation 1
- `Bush`（ObjectTypes[47]）：行为：Tween；动画：Animation 1
- `Rock`（ObjectTypes[51]）：动画：Animation 1
- `SkillIcon`（ObjectTypes[81]）：变量：Button, Name, Mana, Cooldown, Unlocked, Activated, Type；行为：Timer；动画：Active, Reload, Activated
- `Node`（ObjectTypes[35]）：变量：Unlocked, Name, Description, UpgradeType, UpgradeNumber, Level, MaxLevel, Cost, Currency, Color, NodeProgress；动画：Big
- `Nodes`（ObjectTypes[92]）：变量：Unlocked, Name, Description, UpgradeType, UpgradeNumber, Level, MaxLevel, Cost, Currency, Color, NodeProgress；行为：Persist, Tween
- `ResourceIcon`（ObjectTypes[19]）：动画：Gold, Coconut, Star
- `CocoAmount`（ObjectTypes[61]）：
- `CocoBar`（ObjectTypes[62]）：
- `MerchantProgress`（ObjectTypes[65]）：行为：Persist；动画：Default
- `Clock`（ObjectTypes[27]）：行为：Sine, Sine2；动画：Animation 1
- `Timer`（ObjectTypes[24]）：行为：Tween, Sine
- `GameZone`（ObjectTypes[63]）：动画：Animation 1
- `Sea`（ObjectTypes[68]）：
- `Water`（ObjectTypes[58]）：行为：Sine；动画：Default
- `Mountains`（ObjectTypes[66]）：
- `Sun`（ObjectTypes[74]）：行为：Orbit；动画：Animation 1

## 事件表规模

- `eNodes`：67 个事件、4 个组、4 个变量、1 个事件表引用；81 个条件、135 个动作。
- `ePlayer`：21 个事件、2 个组、5 个变量、1 个事件表引用；31 个条件、47 个动作。
- `eDebug`：13 个事件、0 个组、0 个变量、0 个事件表引用；16 个条件、14 个动作。
- `eGame`：67 个事件、7 个组、3 个变量、1 个事件表引用；86 个条件、169 个动作。
- `eTitle`：12 个事件、0 个组、0 个变量、0 个事件表引用；13 个条件、55 个动作。
- `eIntro`：3 个事件、0 个组、0 个变量、0 个事件表引用；3 个条件、14 个动作。
- `eEnd`：6 个事件、0 个组、0 个变量、0 个事件表引用；6 个条件、18 个动作。

## 当前可确认与不可确认
- 可确认：对象名、实例变量名/类型码、行为组件名、动画帧矩形、布局尺寸、图层名称、事件条件/动作函数引用名。
- 需要继续解释：事件参数内部表达式的全部语义、部分运行时生成对象的精确时序、所有升级公式与资源数值。原始参数 blob 已保留，避免错误翻译。
- `Game` 布局 1200×270 是横向长场景；不要只按浏览器初始视口 480×270 推断其世界宽度。
