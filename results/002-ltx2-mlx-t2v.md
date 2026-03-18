# Test 002: LTX-2 MLX Text-to-Video (First MLX Run)

**Date**: 2026-03-17
**Model**: LTX-2 MLX Audio-Video (notapalindrome/ltx2-mlx-av, ~42GB)
**Machine**: M2 Max (98GB)
**Text Encoder**: Gemma-3-12B bf16 (auto-downloaded by MLX pipeline)
**Framework**: MLX 0.31.1 (native Apple Silicon, bfloat16)

## Parameters
| Param | Value |
|-------|-------|
| Resolution | 768×448 |
| Frames | 97 |
| FPS | 25 |
| Duration | 3.9s |
| Mode | Text-to-Video |
| Stage 1 | 384×224, 8 steps (~4.3s/step) |
| Stage 2 | 768×448, 3 steps (~15.6s/step) |

## Prompt
```
A lone figure in a dark trench coat walks away from the camera across an orange-hazed wasteland towards a massive dystopian cityscape. A futuristic vehicle to the right lifts off the ground and ascends into the hazy orange sky. Cinematic Blade Runner style, atmospheric, melancholic.
```

## Results
| Metric | Value |
|--------|-------|
| Generation time | 132.8s |
| Peak memory | 38.64GB |
| File size | 201KB |
| Codec | H.264 |
| Quality | TBD |
| Output | blade_runner_t2v.mp4 |

## vs Baseline (Test 001, ComfyUI PyTorch)
| | Test 001 | Test 002 |
|---|---|---|
| Framework | PyTorch MPS fp32 | **MLX bfloat16** |
| Resolution | 512×320 | **768×448** |
| Frames | 41 | **97** |
| Pixels×Frames | 6.7M | **33.4M (5x)** |
| Time | 85s | **132s (1.5x)** |
| Efficiency | 79K px·fr/s | **252K px·fr/s (3.2x)** |

## Notes
- MLX is 3.2x more efficient than PyTorch+MPS per pixel-frame
- Uses 2-stage pipeline: low-res generation → 2x upsample → refinement
- Image-to-Video (I2V) has a VAE encoder bug (conv3d channel mismatch) — T2V works
- ffmpeg not installed on M2 → video saved without audio
- No prompt enhancement (missing system prompt file)

## Issues Found
- I2V VAE encoder bug: `conv3d` channel mismatch in `video_vae.py`
- `--enhance-prompt` fails: missing `gemma_t2v_system_prompt.txt`
- M2 needs `brew` / ffmpeg for audio muxing
