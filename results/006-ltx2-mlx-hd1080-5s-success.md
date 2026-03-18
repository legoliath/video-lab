# Test 006: LTX-2 MLX T2V — FULL HD 1920×1088 5s SUCCESS

**Date**: 2026-03-18
**Model**: LTX-2 MLX AV
**Machine**: M2 Max (98GB)
**Framework**: MLX 0.31.1 bfloat16

## Parameters
| Param | Value |
|-------|-------|
| Resolution | **1920×1088** (Full HD) |
| Frames | 121 |
| FPS | 25 |
| Duration | 4.84s |
| Tiling | aggressive |
| Stage 1 | 960×544, 8 steps @ 31.9s/step = 4min15s |
| Stage 2 | 1920×1088, 3 steps @ 217s/step = 10min51s |

## Results
| Metric | Value |
|--------|-------|
| Generation time | **1063.2s (17min 43s)** |
| Peak memory | **45.20GB** |
| File size | 1.1MB |
| Codec | H.264 |

## Key Finding
- **Full HD WORKS at 5 seconds (121 frames)**
- Test 004 crashed at 10s (249 frames) — the frame count was the issue, not resolution alone
- `--tiling aggressive` may have helped with VAE decode stability
- Step timing: 217s/step vs 676s/step (test 004) confirms fewer frames = manageable GPU load

## Updated Resolution/Duration Matrix for M2 Max (98GB)
| Resolution | 5s (121fr) | 10s (249fr) |
|-----------|-----------|------------|
| 768×448 | ✅ ~1min | ✅ 2min |
| 1024×576 | ✅ ~4min | ✅ 8min |
| 1280×768 | ✅ ~8min | ✅ 16min |
| **1920×1088** | **✅ 18min** | ❌ Crash |
