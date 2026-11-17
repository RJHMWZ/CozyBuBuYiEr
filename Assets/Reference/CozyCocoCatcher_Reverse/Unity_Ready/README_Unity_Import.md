# Unity 导入指南

## 推荐导入
- 将 `SpriteFrames/` 中按对象/动画拆分的 PNG 复制到 Unity `Assets/Art/SpriteFrames/`。每帧是独立透明 PNG。
- 将 `Atlas_PNG/` 复制到 `Assets/Art/Atlases/`，用于对照或自定义切片。
- 将 `Audio_Ogg/` 复制到 `Assets/Audio/`。14 个 WebM/Opus 音频均已转码为 OGG Vorbis；原件仍在 `GameFiles/.../media/`。

## Sprite 使用注意
- `SpriteFrameManifest.json` 是切片索引，包含对象、动画、帧顺序、原图坐标、帧宽高、动画速度/Loop、Origin、Image Points 和 Collision Polygon。
- 动画帧速度与 Loop 来自 Construct 序列化定义；不要把所有动画统一设为 12 FPS。
- PNG 已按对象名/动画名/帧序号组织，可使用 Sprite Mode = Single。
- PPU 不强制指定；应结合原始布局坐标与相机比例确定。
- `rotated_in_atlas=true` 的帧已从图集旋转区域恢复为独立 PNG；manifest 保留原始旋转标记。

## Audio 使用注意
- 短音效可考虑 Decompress On Load；长背景音乐可考虑 Streaming。
- `Audio_Import_Manifest.json` 对应原始 WebM 与 OGG 转码文件。
- 播放时机以 ePlayer/eGame/eNodes 的 Audio.Play 参数为准。

## 不要导入 Assets 的文件
- `c3runtime.js`、`main.js`、`objRefTable.js`、`data.json`、HAR、HTML、CSS 是逆向参考，不是 Unity 运行时代码。
