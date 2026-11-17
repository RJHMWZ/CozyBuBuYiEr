# Cozy Coco Catcher — Unity Codex 逆向交接包

本资料包只对应一个游戏：`Cozy Coco Catcher`。来源是用户提供的 HAR 中成功返回的浏览器部署资源，不是开发者本地 `.c3p` 工程。

## 必须先读
1. `CODEX_TASK_PROMPT.md`：可直接交给 Codex 的执行指令。
2. `Analysis/Reverse_Engineering_Overview.md`：游戏结构、场景、关键对象和资源概览。
3. `Analysis/EventSheets_Readable.md`：事件表已用 `objRefTable.js` 映射为真实 Construct 3 方法名；参数 blob 保留原样。
4. `Analysis/EventSheets_Normalized.json`：事件树机器可读版本，包含解析结果与原始条目。
5. `Analysis/ObjectTypes_Readable.md` / `Analysis/ObjectTypes_Normalized.json`：对象变量、行为和动画定义。
6. `Analysis/SpriteFrameManifest.json`：所有已成功切出的动画帧及其原图坐标、锚点、碰撞轮廓。
7. `Analysis/Layouts_Readable.md` / `Analysis/Layouts_Normalized.json`：布局尺寸、事件表和图层信息。
8. `Analysis/Audio_Import_Manifest.json` / `Analysis/Audio_Catalog.md`：WebM 音频原件与 Unity OGG 副本对应表。
9. `Analysis/Gameplay_Logic_Map.md`：按事件组和对象归纳的玩法导航（未猜测未解码公式）。
10. `Analysis/ReferenceTable_Used.json`：事件表实际使用到的 Construct API 引用与次数。
11. `Analysis/SpriteFrames_Contact_Sheet.jpg`：313 张独立动画帧的预览图。
12. `Unity_Ready/README_Unity_Import.md`：资源导入说明。

## 资源目录
- `Unity_Ready/Atlas_PNG/`：原始图集的 PNG 副本。
- `Unity_Ready/SpriteFrames/`：按对象/动画/帧拆分的透明 PNG。
- `Unity_Ready/Audio_Ogg/`：从 WebM/Opus 转码的 OGG 音频。
- `GameFiles/`：原始浏览器部署文件，供核对。

## 重要限制
- 不存在开发者原始 `.c3p` 文件。
- Construct 3 事件条件/动作参数以序列化表达式保存；本包能解析函数引用名，但没有把每个表达式参数强行翻译成伪 C#。Codex 必须结合 raw 参数和原始 `data.json` 继续推导。
- `Game` 布局原始设计尺寸为 1200×270；Title、Intro、End 为 480×270；Skill Tree 为 960×540。不要把所有场景都错误地固定为 480×270。
- 事件表 `eGame` 引用了 `ePlayer`；`eNodes` 引用了 `eDebug`；`ePlayer` 也引用 `eDebug`。实现时需检查引用关系。
- `eDebug` 可能包含调试/辅助行为，不应未经判断地当成正式玩法。
- OGG 是为 Unity 导入准备的转换副本，原始 WebM 音频仍保留。
- 素材和音频的使用需遵守原作者授权；本包是逆向分析和个人复刻参考，不代表获得商业再发布权。
