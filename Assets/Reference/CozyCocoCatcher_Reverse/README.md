# Cozy Coco Catcher — Unity Codex 逆向交接包

本包只针对 `Cozy Coco Catcher`，来源是用户提供的 itch.io 游戏页面 HAR 网络抓包。它包含本次浏览器成功加载的部署文件、Construct 3 `data.json`、事件表/布局/对象定义和实际加载的图片与音频。

## 推荐阅读顺序
1. `START_HERE_FOR_CODEX.md`
2. `CODEX_TASK_PROMPT.md`（直接交给 Codex）
3. `Analysis/Reverse_Engineering_Overview.md`
4. `Analysis/Gameplay_Logic_Map.md`
5. `Analysis/EventSheets_Readable.md`
6. `Analysis/EventSheets_Normalized.json` + `Analysis/ReferenceTable.json`
7. `Analysis/ObjectTypes_Readable.md` + `Analysis/ObjectTypes_Normalized.json`
8. `Analysis/SpriteFrameManifest.json` + `Analysis/Layouts_Readable.md`
9. `Unity_Ready/README_Unity_Import.md`

## 主要处理结果
- 93 个对象类型已整理为标准化 JSON，含变量、行为和动画定义。
- 205 个 Construct 3 引用表条目已编号映射；事件表中的条件/动作引用已转换为可读函数名。
- 7 张事件表已生成可读 Markdown 和标准化 JSON，保留每个原始事件节点及参数 blob。
- 313 个动画帧已从 WebP 图集切出为独立透明 PNG；其中 68 个旋转打包帧已恢复方向，并生成帧预览图。
- 14 个 WebM/Opus 音频已额外转码为 Unity 可导入的 OGG Vorbis，并生成时长/声道目录。
- 6 个布局已整理为布局/图层索引，并保留原始实例数据。

## 重要限制
- 这不是开发者本地 `.c3p` 原始工程。
- 事件参数的原始表达式仍保留序列化格式；表达式引用提示仅列出候选 Exps 函数，不代表完整表达式已翻译。
- 事件条件/动作的函数名来自原始 `objRefTable.js` 的索引映射。
- 只包含本次 HAR 中成功加载并保存的资源，未加载的动态/后续内容不保证存在。
- 资源和音频使用需遵守原作者授权；本包不授予商业再发布权。
