# 模型来源、许可与转发须知

本仓库 `models-v1` Release 中的模型权重均为**上游发布物的原样副本**（未修改）。
转发/下载时必须遵守各上游许可；如与上游条款冲突，以上游为准。

## 1. SenseVoice-Small int8（`model.int8.onnx` + `tokens.txt`）

- 上游：FunAudioLLM / SenseVoice（经 sherpa-onnx 发布转成 onnx）
  - https://github.com/FunAudioLLM/SenseVoice
  - https://github.com/k2-fsa/sherpa-onnx/releases/tag/asr-models
- 用途：中文/英/日/韩/粤语离线转写
- 许可：以 FunAudioLLM/SenseVoice 仓库的 LICENSE 与模型卡为准；转发时请一并保留上游许可与出处

## 2. EmbeddingGemma 2 270M（`model.litertlm`）

- 上游：Google DeepMind EmbeddingGemma（LiteRT 分发）
  - https://ai.google.dev/gemma/docs/embeddinggemma
- 用途：端侧向量（MRL 截断 256 维）
- 许可：**Gemma Terms of Use**

## 3. Gemma 3 1B int4（`gemma3-1b-it-int4.litertlm`）

- 上游：Google DeepMind Gemma 3 1B IT（LiteRT 量化分发）
  - https://ai.google.dev/gemma/docs/gemma-3
- 用途：端侧摘要（Tier B，可选）
- 许可：**Gemma Terms of Use**

## Gemma 转发须知（必读）

Gemma 模型的使用、复制、修改与分发受 **Gemma Terms of Use** 约束：

- 条款：https://ai.google.dev/gemma/terms
- 使用限制：https://ai.google.dev/gemma/prohibited_use_policy
- 转发时必须：(1) 随附 Gemma Terms of Use（或可稳定访问的链接与本说明）；
  (2) 保留版权与许可声明；(3) 不得移除或规避使用限制。

如本 Release 的受众与上述条款不符，请自行停止分发并下架资产。

## 校验

每个文件的字节数与 SHA-256 见 [`manifest.json`](./manifest.json)。上传后请先用 `sha256sum` 核对再发布。
