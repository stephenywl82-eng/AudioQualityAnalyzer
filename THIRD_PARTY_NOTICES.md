# Third-party notices — Audio Quality Analyzer

本应用使用以下开源组件与标准。各组件按其原许可证分发，谨此致谢。

## 开源组件

| 组件 | 用途 | 许可证 |
| --- | --- | --- |
| TagLib (`libtaglib.so`) | 全格式音频标签与封面读写 | LGPL-2.1 或 MPL-1.1 |
| FFmpeg (`libffmpeg-decoder.so`) | 极简构建，仅 ALAC/APE 解码；不含任何编码器 | LGPL-2.1-or-later |
| dr_flac | FLAC 无损解码与逐字节 MD5 校验（编译进 `libaudio_analyzer.so`，无独立 so） | Public Domain 或 MIT-0（David Reid） |
| LAME 3.100 (`liblame_encoder.so`) | MP3 编码 | LGPL |
| Oboe (`liboboe.so`) | 音频播放与 BPM 检测 | Apache-2.0 |
| libebur128 (`libebur128.so`) | EBU R128 响度计量 | MIT |
| Jetpack Compose · Material 3 Expressive | 界面 | Apache-2.0 |
| Kotlin · Kotlin Coroutines | 应用逻辑 | Apache-2.0 |

`liboboe_bridge.so` 为配套项目自研 JNI bridge，仅使用其中 BPM 相关符号。

## LGPL 说明

TagLib / FFmpeg / LAME 以动态链接 `.so` 方式使用。按 LGPL 要求，分发二进制时随附本声明，
并提供对应源码与重链接材料。相关组件的源码与构建脚本见配套仓库 `E:/SDWAudioKit` 与
`E:/Lyrico`（FFmpeg 的 `build-ffmpeg.sh`、LAME 3.100 源码）。

## 标准与数据

- MusicBrainz — 元数据查询，数据为 CC0（https://musicbrainz.org）
- Cover Art Archive — 封面图（https://coverartarchive.org）
- EBU R128 / ITU-R BS.1770 — 响度计量标准

## 声明

本应用的音质相关结果均为基于信号分析的**概率推断线索**，不构成音质判定证明。
FLAC 逐字节 MD5 校验「一致」可证明整曲解码后字节与文件头声明相符，但不代表听感评价。
