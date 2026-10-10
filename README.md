# Nunchaku-AMD

AMD packed-weight model loaders for ComfyUI. Supported GPU: **Radeon RX 9070 XT
(gfx1201) only**, Windows, ROCm PyTorch and Python Triton kernels.

## Install

Clone this repository into `ComfyUI/custom_nodes/ComfyUI-Nunchaku-AMD`.
Restart ComfyUI. Import one of the included `Nunchaku-AMD-*.json` workflows.
Place separately downloaded checkpoints in the model folders specified by
the workflow. The ComfyUI-Easy-Install-AMD Nunchaku add-on provides pinned
model downloads and the matching tested environment.

Tested environment: Python 3.12, PyTorch 2.15.0a0+rocm10.2.0a20261001,
HIP 7.17.26391, Triton Windows 3.7.0.post26. Keep an existing working bundle;
this repository does not install or replace GPU packages automatically.

## Tested families

Representative full generation has passed for Qwen-Image, Qwen-Image 2.1,
Viggle 6-step Turbo and editing, FLUX.1 Schnell, FLUX.2 Klein 9B,
Z-Image Turbo INT4 and software FP4, SDXL, SANA, T5 INT4 with FLUX.1,
and LTX 2.3 distilled video/audio. Support is checkpoint-specific;
other variants are not implied by a family name.

## Limits

NVIDIA numerical parity is unverified. Packed INT4/FP4 weights are decoded
for BF16/FP16 compute; native NVIDIA INT4/NVFP4 instructions are not used.
Arbitrary LoRA merging is unsupported; Viggle Turbo uses its dedicated
runtime adapter. Qwen 2.1 chained edits (using an output as the next
reference) need a new seed for every edit: reusing the seed of the step
that made the reference "replays" its noise, and the background turns
grainy and compounds. The edit workflow randomizes the seed for this. Large models require substantial system RAM and VRAM.
No full model weights are included. The small fixture is for diagnosis only.

## Sources and licenses

Fork base: https://github.com/ivandobskygithub/nunchaku_rocm_poc
(reference revision 0812ebe6388fd8e4180460b0dd2966157d16270c).
Nunchaku / SVDQuant: MIT HAN Lab and contributors.
Additional references: https://github.com/nunchux-ai/nunchaku and
https://github.com/rootonchair/nunchaku-lite.
This AMD ComfyUI integration contains independent modifications and is not
an official upstream release. See `NOTICE*.txt`, `LICENSE`, and the fixture
receipt for source revisions and attribution. Model licenses apply separately.
