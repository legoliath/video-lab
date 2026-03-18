# Test 007: LTX-2 MLX T2V — 1280×768 15s SUCCESS

**Date**: 2026-03-18
**Model**: LTX-2 MLX AV
**Machine**: M2 Max (98GB)
**Framework**: MLX 0.31.1 bfloat16

## Parameters
| Param | Value |
|-------|-------|
| Resolution | 1280×768 |
| Frames | 377 |
| FPS | 25 |
| Duration | 15.08s |
| Tiling | aggressive |
| Stage 1 | 640×384, 8 steps @ 50s/step = 6min40s |
| Stage 2 | 1280×768, 3 steps @ 407s/step = 20min21s |

## Results
| Metric | Value |
|--------|-------|
| Generation time | **1855.1s (30min 55s)** |
| Peak memory | **49.71GB** |
| File size | 2.1MB |
| Codec | H.264 |

## Complete M2 Max Capability Matrix
| Resolution | 5s | 10s | 15s |
|-----------|-----|-----|-----|
| 768×448 | ✅ 2min | ✅ 2min | — |
| 1024×576 | ✅ 4min | ✅ 8min | — |
| 1280×768 | ✅ 8min | ✅ 16min | **✅ 31min** |
| 1920×1088 | ✅ 18min | ❌ crash | ❌ |
