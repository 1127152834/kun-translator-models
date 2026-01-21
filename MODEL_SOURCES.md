# Kun-Translator 模型来源与映射

本仓库只保存 `manifest.json` 与模型来源说明，模型二进制通过 GitHub Release 资产分发。

> 注意：当前引擎实现与以下开源模型的输入/输出可能并不完全匹配，先用于填充真实模型文件与下载链路。后续如需“可运行”的端到端推理，请配套调整引擎输入/输出与词表。

## VAD
- 来源：`onnx-community/silero-vad`
- 许可证：MIT
- 使用文件：`onnx/model.onnx`
- 映射：`silero_vad.onnx`

## ASR
- 来源：`Xenova/whisper-tiny`
- 许可证：Apache-2.0（基于 `openai/whisper-tiny`）
- 使用文件：`onnx/encoder_model_quantized.onnx`
- 映射：复用到所有 `asr/funasr_*.onnx`
  - `asr/funasr_zh.onnx`
  - `asr/funasr_en.onnx`
  - `asr/funasr_th.onnx`
  - `asr/funasr_vi.onnx`
  - `asr/funasr_ms.onnx`
  - `asr/funasr_id.onnx`

## MT
- 来源：`Xenova/opus-mt-<pair>`（Helsinki-NLP/opus-mt 系列导出）
- 许可证：遵循对应 base model
- 使用文件：`onnx/encoder_model_quantized.onnx`
- 映射：
  - `mt/zh-en.onnx` ← `Xenova/opus-mt-zh-en`
  - `mt/en-zh.onnx` ← `Xenova/opus-mt-en-zh`
  - `mt/th-en.onnx` ← `Xenova/opus-mt-th-en`
  - `mt/vi-en.onnx` ← `Xenova/opus-mt-vi-en`
  - `mt/id-en.onnx` ← `Xenova/opus-mt-id-en`
  - `mt/ms-en.onnx` ← 复用 `Xenova/opus-mt-id-en`（暂无对应模型）

## TTS
- 来源：`rhasspy/piper-voices`
- 许可证：各 voice 遵循其模型卡（仓库公开分发）
- 使用文件：对应 voice 的 `*.onnx`
- 映射（同一 ONNX 复制为 acoustic/vocoder 以满足当前接口）：
  - `tts/zh/{acoustic,vocoder}.onnx` ← `zh_CN-huayan-medium`
  - `tts/en/{acoustic,vocoder}.onnx` ← `en_US-amy-low`
  - `tts/th/{acoustic,vocoder}.onnx` ← `en_US-amy-low`（暂无泰语 voice）
  - `tts/vi/{acoustic,vocoder}.onnx` ← `vi_VN-25hours_single-low`
  - `tts/ms/{acoustic,vocoder}.onnx` ← `id_ID-news_tts-medium`（暂无马来语 voice）
  - `tts/id/{acoustic,vocoder}.onnx` ← `id_ID-news_tts-medium`
