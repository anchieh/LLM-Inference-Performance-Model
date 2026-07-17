# LLM Inference Performance Model

A single-file web tool for estimating LLM inference performance (decode throughput, first-token latency, RAM/VRAM requirements) across **CPU / iGPU / NPU / dGPU** on a unified physical model.

The entire application is contained within `index.html` — no build step, no dependencies.

For direct access and usage, please visit the [project homepage](https://anchieh.github.io/LLM-Inference-Performance-Model/).

## ✨ v5.0 Highlights

- **Wizard mode (default)** — pick a machine, pick a model, get a verdict (`smooth / usable / slow / unusable`) with tok/s, first-token latency and memory requirements in three clicks. Advanced panel with full parameter control remains one toggle away.
- **Unified physics** — decode is memory-bandwidth-bound on every device: `TPS = BW × util × sizeF / model_bytes`. CPU, iGPU and NPU share the same DRAM bus; per-family calibrated utilization constants replace the previous reuse heuristics.
- **dGPU support** — VRAM-fit check plus first-order VRAM-bandwidth estimation for common RTX / Arc cards. When model + KV cache exceed VRAM the tool shows a warning instead of an unreliable offload number.
- **Confidence labels** — every estimate is tagged `calibrated` (family has a measured basis) or `extrapolated` (spec-derived only). Custom-platform input covers unlisted or future hardware.
- **NPU runtime maturity badges** — hardware capability ≠ attainable performance; NPU results are tagged `mature` or `experimental` per generation.
- **GQA-aware KV cache** — per-token KV size comes from the model preset (architecture-dependent) and counts toward RAM/VRAM; context length up to 64k.
- **Model presets** — Llama 3.2, Qwen3 (dense & MoE), Mistral, Phi-4-mini, DeepSeek-R1 distills, GPT-OSS-20B (MXFP4), plus custom parameter count.
- **Shareable URLs** — platform / model / quant / context are encoded in the query string.

## 📏 Accuracy

This is a **semi-empirical engineering estimator**: public specs plus calibrated constants, not measured guarantees. Precision target ±15% (calibrated) / ±25% (extrapolated). Not applicable to multi-node inference, VRAM-offload throughput, cross-vendor NPU comparison, or batch-serving optimization. Validate on real hardware before purchasing decisions.

## 🚀 Installation & Usage

This project is a web application accessible directly via GitHub Pages. There is no installation required.

To use the tool, simply open the [project homepage](https://anchieh.github.io/LLM-Inference-Performance-Model/) in your web browser, or open `index.html` locally.

## 📄 License

This project is licensed under the **Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) License**.

You are free to:
*   **Share** — copy and redistribute the material in any medium or format.
*   **Adapt** — remix, transform, and build upon the material.

Under the following terms:
*   **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made.
*   **NonCommercial** — You may not use the material for commercial purposes.
*   **ShareAlike** — If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.

A copy of the full license text can be found [here](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode).
