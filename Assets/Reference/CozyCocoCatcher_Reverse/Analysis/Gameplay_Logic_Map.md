# 玩法逻辑索引（事件结构导航）

> 本页根据事件组名称、对象引用、条件/动作 API 名称归纳。精确数值、概率、交易比率和升级公式仍以原始参数 blob 为准，不在这里猜测。

## 玩家与 HUD（ePlayer）
- `Player controls`：键盘输入驱动 Player 的 Platform 行为模拟控制，并更新玩家实例变量。
- 玩家创建时挂接 PlayerSprite、PlayerEyes 与摇晃 UI；每帧同步视觉位置、朝向、动画和最大速度。
- 跳跃、落地分别触发角色视觉动画、尺寸 Tween 与音效；移动时生成 Dust。
- HUD 组更新经验条、星星生成/跟随和资源获得提示。

## 主游戏循环（eGame）
- `Level general`：布局开始时初始化状态、转场和玩家输入；每帧更新海面/云层；定时生成并移动 Bird；更新 Clock、Timer、Sun 等环境元素。
- `Signposts`：玩家碰撞/重叠告示牌时切换告示牌帧，并显示/淡入 Message 提示。
- `Coconut tree`：树创建时挂接 TreeTop、TreeCooldown、CocoAmount、CocoBar；玩家靠近/重叠时进入摇树交互流程，使用 Timer、实例变量、ShakeProgress、音效和冲击效果；事件会生成 Coconut。
- 椰子事件处理落地、物理行为、玩家拾取、销毁、Resources 数据更新和 HUD 数值更新。精确掉落数量、概率、速度和冷却公式需继续解码参数。
- `Chest`：玩家靠近时显示 ChestArrow；宝箱帧状态变化时处理 Coin 生成、资源变化和拾取反馈。
- `Shop`：更新 MerchantProgress 动画与计数；玩家与 Shop 重叠且满足 Resources 条件时更新资源和 Shop 实例变量。交易比率需解析参数。
- `Captain`：玩家碰撞/重叠 Captain 时显示提示、控制玩家输入/移动，并触发 Transition 与布局切换。
- `Game HUD`：Dictionary 键值维护、资源文字更新、Clock 与 TipText 显示。

## 技能树（eNodes）
- `Controls`：鼠标滚轮缩放、按住拖动视口、释放时 Tween；键盘也可控制 Camera。
- `Resources`：遍历资源数据并更新文字/进度。
- `Nodes`：节点创建时初始化显示状态、颜色、动画和粒子；鼠标悬停显示 ItemInfo/UpgradeButton/NodeSelect；点击/释放节点触发节点状态、资源、节点连线和 Tween 更新。
- `World tier`：更新世界等级相关文字和视觉反馈。
- `eNodes` include `eDebug`，`ePlayer` include `eDebug`，`eGame` include `ePlayer`。实现时检查引用关系与共享状态。

## 其他场景
- `eIntro`：Logo/FeatureKreep 标识、Tween 动画、淡入淡出及进入下一个布局。
- `eTitle`：标题界面输入、开始按钮/点击交互和转场；含 `Transition` 自定义调用块。
- `eEnd`：结束界面动画、转场及返回/重开相关交互。

## 待精确解码重点
1. 树木摇晃的触发次数、持续时间、掉落概率、掉落数量和冷却。
2. 椰子收集后的资源字段、经验和等级阈值。
3. 宝箱产出、商人交易与船只/船长进度条件。
4. 技能树 Node 的 Name、Description、UpgradeType、UpgradeNumber、Cost、Currency、Level、MaxLevel 对应的数据和升级公式。
5. `Transition` 自定义调用的参数含义与转场效果。