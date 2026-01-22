# Kun-Translator 模型来源与映射

本仓库只保存 `manifest.json` 与模型来源说明，模型二进制通过 GitHub Release 资产分发。

当前 Release 资产主要来自 [RTranslator](https://github.com/niedev/RTranslator) 2.0.0 发布包（Apache-2.0），用于与 Kun-Translator 的 Whisper + NLLB 引擎兼容层对齐。上游模型许可证请以对应模型卡/仓库说明为准。

## VAD
- 来源：`onnx-community/silero-vad`
- 许可证：MIT
- 使用文件：`onnx/model.onnx`
- 映射：`silero_vad.onnx`

## ASR (Whisper)
- 来源：RTranslator 2.0.0 Release
- 许可证：Apache-2.0（RTranslator）/ Whisper 上游模型许可证以原始模型卡为准
- 使用文件：
  - `Whisper_initializer.onnx`
  - `Whisper_encoder.onnx`
  - `Whisper_decoder.onnx`
  - `Whisper_cache_initializer.onnx`
  - `Whisper_detokenizer.onnx`

## MT (NLLB)
- 来源：RTranslator 2.0.0 Release
- 许可证：Apache-2.0（RTranslator）/ NLLB 上游模型许可证以原始模型卡为准
- 使用文件：
  - `NLLB_encoder.onnx`
  - `NLLB_decoder.onnx`
  - `NLLB_embed_and_lm_head.onnx`
  - `NLLB_cache_initializer.onnx`

## Tokenizer
- 来源：RTranslator 2.0.0 Release
- 使用文件：`sentencepiece_bpe.model`

## TTS
- 当前版本默认使用系统 TTS，不在模型仓库分发 TTS 模型文件。
