# Video Lab

Video generation testing, benchmarking & tracking across models and hardware.

## Machines
- **M5** (MacBook Pro M5, 24GB) — LTX-2 via ComfyUI
- **M2** (Mac Pro M2 Max, 98GB) — Wan 2.1, LTX-2 backup

## Models Tested
| Model | Type | Machine | Status |
|-------|------|---------|--------|
| LTX-2 (2B distilled) | Text-to-Video | M5 | ✅ Working |
| Wan 2.1 T2V 1.3B | Text-to-Video | M2 | 🔄 Downloaded, untested |
| Wan 2.1 T2V 14B | Text-to-Video | M2 | 📋 Planned |

## Pipeline
```
Prompt → [Gemma/Llama enhance] → [ComfyUI + LTX-2/Wan] → Video
```

## Results
See [results/](results/) for detailed benchmark data.
