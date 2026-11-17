# 给 Codex 的执行任务：Cozy Coco Catcher → Unity 复刻

你正在当前 Unity 项目中复刻 `Cozy Coco Catcher`。本压缩包解压后会得到 `CozyCocoCatcher_Reverse/` 资料目录。建议将它放到 Unity 项目根目录的 `Reference/CozyCocoCatcher_Reverse/`。如果 Codex 收到的是 ZIP 附件，先解压并以包含 `START_HERE_FOR_CODEX.md` 的文件夹作为资料根目录。不要假设存在原始 Construct 3 `.c3p` 工程。

## 工作原则
1. 先完整阅读 `START_HERE_FOR_CODEX.md` 和其中列出的资料，不要只看图片或 README。
2. 以 `GameFiles/html/18013330/data.json` 为原始结构依据，以 `Analysis/EventSheets_Readable.md` 为可读事件索引，以 `Analysis/EventSheets_Normalized.json` 和 `Analysis/ReferenceTable.json` 核对条件/动作的真实 API 名称；优先查看 `Analysis/ReferenceTable_Used.json`。
3. `EventSheets_Readable.md` 中的参数 JSON 是原始序列化参数，不是已经解释好的 C# 表达式。不得凭空猜公式、价格、速度、升级效果。需要时追踪 `objRefTable.js` 引用索引，并结合对应对象变量、布局实例和原始运行资源。
4. 结合 `Analysis/Gameplay_Logic_Map.md`、`Analysis/ObjectTypes_Readable.md`、`Analysis/Layouts_Readable.md` 先建立玩法和场景映射。保留所有重要对象名、变量名、动画名、技能名、资源名和场景名。Unity 代码可以采用清晰命名，但要保留与原始对象的映射。
5. 优先使用 `Unity_Ready/SpriteFrames/` 中拆好的 313 张单帧 PNG，使用 `Analysis/SpriteFrameManifest.json` 恢复帧顺序、帧速率、Loop、Origin/ImagePoint 和碰撞轮廓；可用 `Analysis/SpriteFrames_Contact_Sheet.jpg` 快速查看；不要把图集整张拉伸成一个 Sprite。
6. 优先使用 `Unity_Ready/Audio_Ogg/` 的 14 个 OGG 音频；原始 WebM 在 `GameFiles/html/18013330/media/`。
7. 使用原始布局尺寸：Game 1200×270，Title/Intro/End 480×270，Skill Tree 960×540。按原始长宽比设计相机和 Canvas，不要擅自统一尺寸。
8. `Game` 的主要逻辑在 `eGame`，并 include `ePlayer`；玩家相关逻辑在 `ePlayer`；技能树在 `eNodes`；Intro/Title/End 各有独立事件表。检查 include 和 layout 对应关系。
9. 先从原始事件表与对象定义还原机制，再写 Unity C#。禁止用简单的“收集椰子加分”占位玩法代替原系统。
10. 当前资料无法证明的细节，标注为待验证并优先从原始事件参数、变量、对象和录屏中继续核对；不要编造。

## 实施要求
- 先扫描当前 Unity 工程，沿用现有 Unity 版本、URP/内置管线和输入设置，不要重建工程。
- 将参考资料放在项目外部 `Reference/CozyCocoCatcher_Reverse/` 或项目根目录 `Reference/`，不要把 HAR、原始 Construct Runtime 和无关 HTML 运行文件导入 `Assets`。
- 将可用 PNG 帧和 OGG 音频按需要复制/导入 `Assets/Art`、`Assets/Audio`，不要重复复制已有资源。
- 先实现场景结构、相机、图层、UI 和资源引用；再实现角色移动、交互、树木摇晃、椰子生成/拾取、资源计数、商人/船只交互、技能树和进度；最后补齐动画、声音、转场和存档。以上是工作拆分方向，具体机制以事件表为准。
- 将事件表中的逻辑拆成可维护的 Unity 系统，但不要过度架构化。
- 每个阶段直接在 Unity 项目中落地，编译并修复错误后继续；不要只输出分析报告或只生成空场景。
- 不要在未核对事件参数前自创数值公式。所有未能确认的公式集中标注，避免误当成原作事实。

## 完成标准
最终项目应从 Intro/Title 流程进入 Game，能操作玩家，执行原作采集/资源/交互/升级流程，并能进入 Skill Tree 和 End 等对应场景。UI、动画、音频尽量复用本包资源。项目必须脱离浏览器和 Construct Runtime 独立运行。

**现在开始：先读取交接资料并扫描 Unity 项目，然后直接实施；不要先给我长篇计划，不要停留在分析阶段。**
