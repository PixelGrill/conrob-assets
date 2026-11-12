# Mismo assets

Model files for the Mismo app (voice cloning and on-device translation).
These bytes were verified on desktop in the Mismo language assurance
phase 1 run (2026-11-10) before mirroring; what is here is byte for byte
what was tested.

## Releases

| Tag | Contents | Assets | Bytes |
|---|---|---|---|
| `mismo-voice-1` | Chatterbox Multilingual V3 voice models (q4 ONNX set) plus a provenance copy of the in-app 5-step decoder graph | 10 | 1,558,129,619 |
| `mismo-translation-1` | Opus-MT translation packs: the 34 shipped packs, the self-converted en to sw and en to ko packs, and a corrected en to tr tokenizer (see below) | 145 | 4,826,369,062 |

Asset names carry their origin: voice assets are the model paths with
`/` flattened to `--`; translation assets are `<pack key>--<file name>`.

Download URL shape:
`https://github.com/PixelGrill/conrob-assets/releases/download/<tag>/<asset>`

## Manifests

- `manifests/voice-models-v1.sha256`: SHA-256 for every voice asset.
- `manifests/translation-packs-v1.sha256`: SHA-256 for every translation
  asset, including the corrected Turkish tokenizer and the Korean decode
  sidecar (`opus-mt-en-ko--tokenizer_target.json`).

## The corrected Turkish tokenizer

The upstream `onnx-community/opus-mt-tc-big-en-tr` pack ships a
tokenizer.json whose vocabulary order is permuted relative to the model
(only 6 of 57,060 tokens agree with the repo vocab.json), which makes the
direction output garbage as shipped. The mirrored
`opus-mt-tc-big-en-tr--tokenizer.json` is the one deliberate deviation
from upstream bytes in this mirror: the same file with the vocabulary
reordered through the repo vocab.json and `unk_id` corrected. The model
graphs are the untouched upstream bytes, and the corrected pack was
re-proven end to end after upload. Full evidence: Mismo language
assurance TRANSLATION_MATRIX.md, en to tr section.

## Provenance and licenses

See `ATTRIBUTION.md` in this folder. Short version: voice models are MIT
(Resemble AI Chatterbox, community ONNX export by Masterx); translation
packs are Apache-2.0 or CC-BY-4.0 (Helsinki-NLP Opus-MT base models,
ONNX exports by Xenova and onnx-community; the en to sw and en to ko
packs were converted in-house from the Helsinki-NLP weights).
