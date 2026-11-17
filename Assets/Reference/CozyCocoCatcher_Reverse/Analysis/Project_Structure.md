# Cozy Coconut Catcher — Construct 3 逆向提取索引

> 本目录由用户提供的 HAR 网络抓包提取。内容代表本次浏览器会话实际成功返回的文件，不等同于开发者本地原始工程。

## 提取概况

- HAR 请求记录：183 条
- 去重后提取文件：66 个
- 游戏启动布局：`Intro`
- 项目版本字段：`1.0.0.0`
- 项目视口字段：`480 x 270`
- 图片文件：33 个（含图标与图集）
- WebP 转 PNG 副本：26 个
- JavaScript：14 个
- WebM 媒体：14 个

## Construct 3 项目结构

### 布局（Layouts）

- `ObjectDB`
- `Skill Tree`
- `Game`
- `Title`
- `Intro`
- `End`

### 事件表（Event Sheets）

- `eNodes`
- `ePlayer`
- `eDebug`
- `eGame`
- `eTitle`
- `eIntro`
- `eEnd`

### 对象类型（93 个）

- `Keyboard`
- `Mouse`
- `Audio`
- `Dictionary`
- `AJAX`
- `Dialogue`
- `Resources`
- `NodeText`
- `MainFont`
- `SkillTimer`
- `ControlHUD`
- `FloorName`
- `SkillLetter`
- `TipText`
- `MainFont2`
- `GainResource`
- `Divider`
- `ExpBar`
- `ExpHUD`
- `ResourceIcon`
- `ItemInfo`
- `Button`
- `Message`
- `DialogueBox`
- `Timer`
- `CaptainMessage`
- `CaughtMessage`
- `Clock`
- `Cursor`
- `MouseIcon`
- `ShakeBar`
- `ShakeProgress`
- `ShipIcon`
- `ThankYou`
- `TransitionCircle`
- `Node`
- `BG`
- `Camera`
- `Coconut`
- `Coin`
- `Player`
- `PlayerEyes`
- `PlayerSprite`
- `Tree`
- `Signpost`
- `NPC`
- `Captain`
- `Bush`
- `Chest`
- `Fence`
- `NoSign`
- `Rock`
- `Ship`
- `Shop`
- `Stair`
- `TreeTop`
- `Dust`
- `Ground`
- `Water`
- `Bird`
- `ChestArrow`
- `CocoAmount`
- `CocoBar`
- `GameZone`
- `ImpactSFX`
- `MerchantProgress`
- `Mountains`
- `ResourceGet`
- `Sea`
- `SeaClouds`
- `SeaRock`
- `ShipSteam`
- `Star`
- `StarFollow`
- `Sun`
- `Tilemap`
- `TreeCooldown`
- `NodeBox`
- `NodeLine`
- `NodeParticles`
- `NodeProgress`
- `SkillIcon`
- `UpgradeButton`
- `NodeSelect`
- `NodeBG`
- `TierBar`
- `TierHUD`
- `FeatureKreepLogo`
- `FeatureKreep`
- `ClickAnywhere`
- `GameTitle`
- `LogoCoco`
- `Nodes`

### 音频定义

- `tick`
- `tock`
- `Jump`
- `Sol`
- `treeshake`
- `coin`
- `coconut`
- `press-start`
- `pop`
- `progress`
- `unlock`
- `error`
- `alex-morgan-reggae-island-vibes-537451`
- `music_for_videos-caribbean-beach-164232`

### 项目内嵌文件清单

- `Dialogue.xml` — 934 bytes
- `icons/icon-128.png` — 22267 bytes
- `icons/icon-16.png` — 16505 bytes
- `icons/icon-256.png` — 28930 bytes
- `icons/icon-32.png` — 17541 bytes
- `icons/icon-512.png` — 30345 bytes
- `icons/icon-64.png` — 19120 bytes
- `icons/loading-logo.png` — 19120 bytes
- `media/alex-morgan-reggae-island-vibes-537451.webm` — 2315808 bytes
- `media/coconut.webm` — 12680 bytes
- `media/coin.webm` — 5237 bytes
- `media/error.webm` — 11406 bytes
- `media/Jump.webm` — 3112 bytes
- `media/music_for_videos-caribbean-beach-164232.webm` — 1123982 bytes
- `media/pop.webm` — 14073 bytes
- `media/press-start.webm` — 19928 bytes
- `media/progress.webm` — 5946 bytes
- `media/Sol.webm` — 4335 bytes
- `media/tick.webm` — 3547 bytes
- `media/tock.webm` — 4242 bytes
- `media/treeshake.webm` — 7172 bytes
- `media/unlock.webm` — 7483 bytes

## 关键文件说明

- `GameFiles/html/18013330/index.html`：游戏 HTML 入口。
- `GameFiles/html/18013330/data.json`：Construct 3 项目数据，包含对象、布局、事件表等序列化数据；它不是普通可读脚本。
- `GameFiles/html/18013330/scripts/main.js`：Construct 导出的游戏侧脚本/运行时桥接代码。
- `GameFiles/html/18013330/scripts/c3runtime.js`：Construct 3 运行时。
- `GameFiles/html/18013330/scripts/objRefTable.js`：对象引用表。
- `Analysis/EventSheet_*.json`：从 `data.json` 分离出来的事件表原始结构。
- `Analysis/EventSheets_Readable.md` / `EventSheets_Normalized.json`：已通过 `objRefTable.js` 映射条件和动作函数名的可读/标准化事件表；原始参数仍保留。
- `Analysis/Layout_*.json`：从 `data.json` 分离出来的布局原始结构。
- `Analysis/SpriteFrameManifest.json`：动画帧、原图坐标、帧速度、Loop、Origin、Image Point 和碰撞轮廓索引。
- `Analysis/Gameplay_Logic_Map.md`：按事件组和对象归纳的玩法导航；未解码公式不做猜测。
- `Unity_Ready/Atlas_PNG/`：由 WebP 图集转换的 PNG 副本；原始 WebP 仍保留在 GameFiles 中。
- `Unity_Ready/SpriteFrames/`：依据 Construct 动画帧矩形切出的 313 张独立透明 PNG；68 张旋转打包帧已恢复方向。
- `Unity_Ready/Audio_Ogg/`：14 个 WebM/Opus 音频的 OGG Vorbis 转码副本。

## 完整性说明

- 本次 HAR 中成功抓取到 `data.json`、Construct 3 runtime、图片图集、图标及 WebM 音视频文件。
- HAR 中没有发现独立 `.c3p` 工程文件；因此不能把本包称为开发者原始可编辑工程。
- `data.json` 内的事件表是 Construct 序列化结构，不是已经还原成可直接运行的 C# 或 JavaScript 游戏逻辑。
- 只包含本次浏览器会话实际加载并被 HAR 保存响应体的资源；未触发加载的后续关卡/远程资源不会凭空出现在包内。
- 本次抓包未发现独立 `.wasm` 或字体文件。
- `Dialogue.xml` 存在未加引号的属性值，不能按严格 XML 解析；已保守提取文本。其文本涉及 Dreadkeep/地下墓穴，与当前热带采集主题不一致，可能是残留/未使用数据；Codex 不应直接当作主线剧情。
- Codex 专用包未重复附带 12.7 MB 原始 HAR，避免重复和空响应条目；已提取的部署文件和 data.json 已包含在 GameFiles 中。

## 文件目录

```text
CozyCocoCatcher_Reverse/
├── GameFiles/html/18013330/   # 原始网页、脚本、JSON、图片、媒体
├── GameFiles/external/        # itch.io 外部运行时辅助脚本
├── ProjectData_pretty.json   # 格式化后的完整 data.json
├── Analysis/                 # 布局、事件表、对象与资源索引
└── Unity_Ready/
    ├── Atlas_PNG/              # WebP 图集 PNG 副本
    ├── SpriteFrames/           # 313 张独立动画帧
    ├── Audio_Ogg/              # 14 个 Unity 可导入 OGG
    └── README_Unity_Import.md
```
