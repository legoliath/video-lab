# Apple Silicon Optimization for Video Generation

## Current State: ~40% Utilization

We're running ComfyUI with PyTorch MPS + `--force-fp32`, which:
- Uses only the GPU (38 cores on M2 Max)
- Forces float32 (2x memory waste, slower compute)
- Ignores Neural Engine (16 cores sitting idle)
- Uses PyTorch instead of Apple-native MLX

## M2 Max Architecture

| Component | Cores | Status | Notes |
|-----------|-------|--------|-------|
| GPU | 38 | ⚠️ Underused (fp32) | MPS backend, should be fp16 |
| Neural Engine | 16 | ❌ Idle | Needs CoreML conversion |
| CPU (Perf) | 8 | ✅ Used | Text encoding, VAE |
| CPU (Efficiency) | 4 | ✅ Used | Background tasks |
| Unified Memory | 98GB | ⚠️ Wasted | fp32 doubles memory usage |
| Memory Bandwidth | 400GB/s | ✅ | Key advantage for inference |

## Optimization Path

### Level 1: Quick Wins (now)
- [ ] Remove `--force-fp32` → fp16 inference
- [ ] Update PyTorch to 2.10 on M2 (M5 already has it)

### Level 2: Framework Switch
- [ ] Evaluate MLX for video generation (Apple-native, faster than PyTorch+MPS)
- [ ] Check if LTX-2 has MLX implementation
- [ ] Check if ComfyUI has MLX backend

### Level 3: Full Architecture Use
- [ ] CoreML conversion of LTX-2 → enables Neural Engine
- [ ] Pipeline parallelism: text encoder on CPU, diffusion on GPU+NE simultaneously

### Level 4: Multi-Machine
- [ ] M5 (prompt engineering) → M2 (generation) pipeline via SSH
- [ ] Distributed inference across M5+M2

## Key Insight
Apple Silicon's advantage is parallelism across heterogeneous compute units (GPU + Neural Engine + CPU) sharing unified memory. Running a single PyTorch process in fp32 on GPU-only is the WORST way to use this architecture.
