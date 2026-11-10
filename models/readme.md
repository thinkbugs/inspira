# 端侧模型（灵感笔记 / inSpira）

本目录是 App「设置 → 端侧模型」下载所用的**清单与校验值**。模型二进制不在本目录提交。

## 为什么不把模型放进本目录

单个模型文件 164–584 MB，超过 GitHub 普通仓库**单文件 100 MB 硬限制**，无法直接 `git add`。
模型以 **GitHub Release 资产**发布（单资产上限 2 GB），App 从 Release 下载；本目录只放清单、校验值与说明。

## 发布位置

- Release tag：`models-v1`
- URL 前缀：`https://github.com/thinkbugs/inspira/releases/download/models-v1/`
- 机器可读清单：[`manifest.json`](./manifest.json)

| 模型 | App 内目录 | 资产文件名 | 大小（字节） | SHA-256 |
|---|---|---|---|---|
| SenseVoice-Small int8（中文转写） | `files/models/asr-sensevoice-small-int8/` | `model.int8.onnx` | 239233841 | `c71f0ce00bec95b07744e116345e33d8cbbe08cef896382cf907bf4b51a2cd51` |
| 同上 · 词表 | 同上 | `tokens.txt` | 315894 | `f449eb28dc567533d7fa59be34e2abca8784f771850c78a47fb731a31429a1dc` |
| EmbeddingGemma 2 270M（向量，256d） | `files/models/emb-embeddinggemma2-270m/` | `model.litertlm` | 164626432 | `2d079ee2f6f066b1f368e8d7c819f55214eaef1d0513b312321901f30ab286fb` |
| Gemma 3 1B int4（摘要，可选） | `files/models/llm-gemma3-1b-int4/` | `gemma3-1b-it-int4.litertlm` | 584417280 | `1325ae366d31950f137c9c357b9fa89448b176d76998180c08ceaca78bba98be` |

合计约 988 MB（不含运行时生成的 XNNPack 缓存）。

## 上传步骤（仓库维护者）

1. GitHub → Releases → **Draft a new release**；
2. Tag：`models-v1`（新建），标题：`端侧模型 v1`；
3. 把上表 4 个文件拖进附件区（Release 单资产上限 2 GB，不受仓库 100 MB 限制）；
4. **Publish release**；
5. 下载核对 `sha256sum`，与本表一致后把本文件底部状态改为「已发布」。

本地文件（维护者机器）位于：

```
C:\temp\idn-models-out\files\models\asr-sensevoice-small-int8\model.int8.onnx
C:\temp\idn-models-out\files\models\asr-sensevoice-small-int8\tokens.txt
C:\temp\idn-models-out\files\models\emb-embeddinggemma2-270m\model.litertlm
C:\temp\idn-models-out\files\models\llm-gemma3-1b-int4\gemma3-1b-it-int4.litertlm
```

## 许可与来源

见 [`LICENSES.md`](./LICENSES.md)。**Gemma 系列（Gemma 3 1B、EmbeddingGemma）受 Gemma Terms of Use 约束**，
转发时必须随附该条款与使用限制；SenseVoice 的来源与许可以上游仓库为准。

## App 侧对接

- 下载后按上表目录与文件名落盘：`<app filesDir>/models/<id>/<文件名>`；
- 每个文件校验**大小 + SHA-256**，全部就位后模型状态置 READY；
- ASR 需要 `model.int8.onnx` 与 `tokens.txt` **两个文件**同时就位（缺词表无法初始化）；
- 云端密钥与模型无关，模型只影响端侧转写 / 向量 / 摘要。

## 状态

**资产待上传**：本目录当前只包含清单与说明，`models-v1` Release 尚未发布。
