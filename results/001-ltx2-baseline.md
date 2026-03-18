# Test 001: LTX-2 Baseline

**Date**: 2026-03-17
**Model**: LTX-2 2B distilled (ltxv-2b-0.9.8-distilled.safetensors)
**Machine**: M5 (24GB)
**Text Encoder**: T5-XXL fp8

## Parameters
| Param | Value |
|-------|-------|
| Resolution | 512×320 |
| Frames | 41 |
| FPS | 25 |
| Duration | 1.6s |
| Steps | 20 |
| CFG | 4.0 |
| Sampler | euler / normal |
| Seed | 42 |

## Prompt
```
Style: cinematic with soft blue lighting. A translucent crystal cube floats in a dark void. Slowly, its sharp edges begin to soften and round, glowing particles of white light detach from its corners and drift outward. The cube gradually morphs into a perfect glowing sphere as the particles orbit around it. Soft ambient blue light illuminates the scene from below.
```

## Results
| Metric | Value |
|--------|-------|
| Generation time | ~85s |
| File size | 69KB |
| Codec | H.264 |
| Quality | TBD (awaiting review) |
| Output | ltx_test_00001_.mp4 |

## Notes
- First successful local video generation
- T5-XXL fp8 as text encoder (not Gemma — tokenizer issue)
- ComfyUI API workflow via Python script
