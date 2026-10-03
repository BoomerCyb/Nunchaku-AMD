# AMD ComfyUI edition changes — 2026-10-03

Modified by BoomerCyb from the upstream ROCm proof of concept. This branch
contains independent Python/Triton packed-weight adapters and ComfyUI nodes
for the RX 9070 XT, matching workflows, a diagnostic fixture and packing
reference. The upstream native engine, unrelated examples and CI automation
were removed from the current branch; their source remains in Git history.

`reference/packer.py` is an unmodified upstream validation reference.
The AMD adapters are separate from the official NVIDIA native extension.
Upstream copyright and Apache-2.0 license notices are retained.
See `NOTICE*.txt` for additional source and checkpoint attribution.
