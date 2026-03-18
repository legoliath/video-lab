# Test 004: LTX-2 MLX T2V — HD 1920×1088 (CRASHED)

**Date**: 2026-03-17
**Model**: LTX-2 MLX AV
**Machine**: M2 Max (98GB)
**Framework**: MLX 0.31.1 bfloat16

## Parameters
| Param | Value |
|-------|-------|
| Resolution | 1920×1088 |
| Frames | 249 |
| FPS | 25 |
| Duration | 10s |

## Results
| Metric | Value |
|--------|-------|
| Stage 1 | 960×544, 8 steps @ 78s/step = 10min25s ✅ |
| Stage 2 | 1920×1088, step 1/3 = 11min16s ✅ |
| Stage 2 | step 2/3 **CRASHED** |
| Peak RAM | ~50GB |
| Error | Metal GPU: `Command buffer execution failed: Impacting Interactivity` |

## Analysis
- 1920×1088 × 249 frames exceeds Metal GPU command buffer limits on M2 Max
- Not an OOM — GPU compute timeout/resource limit
- Stage 1 at 960×544 worked fine; the 2x upscaled 1920×1088 refinement is too heavy
- **Max proven stable resolution: 1024×576** (test 003)

## Next Steps
- Try 1280×768 (720p-ish) as middle ground
- Or reduce frames at 1920×1088
- Investigate Metal GPU timeout settings
