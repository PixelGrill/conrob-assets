# Mismo asset attribution

Every file in the Mismo releases of this repo is an open licensed model.
This file is the credit record for the licenses that require attribution
(CC-BY-4.0) and the provenance record for the rest.

## Voice models (release `mismo-voice-1`), MIT

- Chatterbox Multilingual V3 by Resemble AI, MIT License.
  Upstream: https://github.com/resemble-ai/chatterbox
- ONNX export by Masterx, repo `Masterx/chatterbox-multilingual-v3-ONNX`
  (commit 19b94afe41de738624b2f3afc75b4cd56221fbeb), MIT per its model
  card.
- `conditional_decoder_steps5.onnx` is our own graph surgery on the stock
  decoder above (a 5-step variant produced in the Mismo project). It
  ships inside the app; the copy in the release is for provenance only.

## Translation packs (release `mismo-translation-1`)

Base models are all Helsinki-NLP Opus-MT (University of Helsinki).
ONNX exports are by Xenova (transformers.js) unless noted. The en to sw
and en to ko packs were converted by the Mismo project from the
Helsinki-NLP PyTorch weights (Optimum ONNX export plus dynamic int8
quantization).

### CC-BY-4.0 (attribution required)

The following packs are licensed under the Creative Commons Attribution
4.0 International License (https://creativecommons.org/licenses/by/4.0/).
Credit: Helsinki-NLP, University of Helsinki, via the Opus-MT project
(https://github.com/Helsinki-NLP/Opus-MT).

- `opus-mt-en-de` (en to de): Helsinki-NLP/opus-mt-en-de, ONNX export
  Xenova/opus-mt-en-de.
- `opus-mt-ru-en` (ru to en): Helsinki-NLP/opus-mt-ru-en, ONNX export
  Xenova/opus-mt-ru-en.
- `opus-mt-zh-en` (zh to en): Helsinki-NLP/opus-mt-zh-en, ONNX export
  Xenova/opus-mt-zh-en.
- `opus-mt-tc-big-en-tr` (en to tr): Helsinki-NLP/opus-mt-tc-big-en-tr,
  ONNX export onnx-community/opus-mt-tc-big-en-tr. The mirrored
  tokenizer.json is corrected as described in this folder's README;
  the model graphs are unchanged upstream bytes.
- `opus-mt-en-ko` (en to ko): Helsinki-NLP/opus-mt-tc-big-en-ko,
  converted by the Mismo project. Includes the decode sidecar
  `tokenizer_target.json`; see the language assurance PACK_NOTES.md for
  why this pack carries two token vocabularies.

### Apache-2.0

All other packs in the release (the remaining bilingual pairs and the
two shared multilingual packs `opus-mt-en-mul` and `opus-mt-mul-en`,
plus the self-converted `opus-mt-en-sw` from Helsinki-NLP/opus-mt-en-sw)
are Apache License 2.0 base models by Helsinki-NLP, with ONNX exports
by Xenova except `opus-mt-en-sw`, which the Mismo project converted.
