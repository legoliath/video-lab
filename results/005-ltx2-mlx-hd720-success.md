# Test 005: LTX-2 MLX T2V — HD720 1280×768 SUCCESS

**Date**: 2026-03-17
**Model**: LTX-2 MLX AV
**Machine**: M2 Max (98GB)
**Framework**: MLX 0.31.1 bfloat16

## Parameters
| Param | Value |
|-------|-------|
| Resolution | 1280×768 |
| Frames | 249 |
| FPS | 25 |
| Duration | 9.96s |
| Stage 1 | 640×384, 8 steps @ 29.8s/step = 4min |
| Stage 2 | 1280×768, 3 steps @ 198s/step = 10min |

## Results
| Metric | Value |
|--------|-------|
| Generation time | **984.9s (16min 25s)** |
| Peak memory | **44.64GB** |
| File size | 1.3MB |
| Codec | H.264 |
| Quality | TBD |

## M2 Resolution Limits (10s, 249 frames)
| Resolution | Pixels | Status | Time | Peak RAM |
|-----------|---------|--------|------|----------|
| 768×448 | 344K | ✅ | 2min | ~38GB |
| 1024×576 | 590K | ✅ | 8min | 41GB |
| **1280×768** | **983K** | **✅** | **16min** | **45GB** |
| 1920×1088 | 2.1M | ❌ Crash | — | ~50GB |

**Sweet spot: 1280×768** for 10s videos on M2.
