# Test 003: LTX-2 MLX T2V — 10 seconds, 1024×576

**Date**: 2026-03-17
**Model**: LTX-2 MLX AV (notapalindrome/ltx2-mlx-av)
**Machine**: M2 Max (98GB)
**Framework**: MLX 0.31.1 bfloat16

## Parameters
| Param | Value |
|-------|-------|
| Resolution | 1024×576 |
| Frames | 249 |
| FPS | 25 |
| Duration | 9.96s |
| Stage 1 | 512×288, 8 steps (16.7s/step) |
| Stage 2 | 1024×576, 3 steps (93.2s/step) |

## Results
| Metric | Value |
|--------|-------|
| Generation time | **485.6s (8min 5s)** |
| Peak memory | **40.95GB** |
| File size | 619KB |
| Codec | H.264 |
| Audio | No (ffmpeg missing on M2) |

## Efficiency Comparison
| Test | Res | Frames | Px·Fr | Time | Efficiency |
|------|-----|--------|-------|------|-----------|
| 001 PyTorch | 512×320 | 41 | 6.7M | 85s | 79K/s |
| 002 MLX | 768×448 | 97 | 33.4M | 133s | 252K/s |
| **003 MLX** | **1024×576** | **249** | **146.8M** | **486s** | **302K/s** |

MLX consistently 3-4x more efficient than PyTorch+MPS.
