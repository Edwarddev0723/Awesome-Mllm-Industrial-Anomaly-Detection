# Awesome VLM Industrial Anomaly Detection

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](./CONTRIBUTING.md)
[![Last Update](https://img.shields.io/badge/Last_Update-2026--03-blue.svg)](#)

> A curated list of papers, benchmarks, datasets, and resources on **Vision-Language Model (VLM)** approaches for **Industrial Anomaly Detection (IAD)**. Focused on the intersection of multimodal foundation models and manufacturing/industrial quality inspection.

<p align="center">
  <img src="assets/taxonomy.png" alt="Taxonomy Overview" width="800"/>
</p>

## Why This List?

Existing awesome lists cover either *general* industrial anomaly detection (e.g., [M-3LAB/awesome-industrial-anomaly-detection](https://github.com/M-3LAB/awesome-industrial-anomaly-detection)) or *broad* foundation-model-based AD (e.g., [mala-lab/Awesome-Anomaly-Detection-Foundation-Models](https://github.com/mala-lab/Awesome-Anomaly-Detection-Foundation-Models)). **This list narrows the scope** to methods that leverage VLMs / MLLMs specifically for industrial image anomaly detection and reasoning, providing:

- **Paradigm-level taxonomy** — not just a flat paper list
- **Reproducibility tags** — code availability, dataset, backbone info at a glance
- **Research gap annotations** — what's unsolved and where opportunities lie
- **Bilingual support** — English primary, Traditional Chinese annotations (繁體中文) where helpful

---

## Table of Contents

- [Surveys & Tutorials](#surveys--tutorials)
- [Papers by Paradigm](#papers-by-paradigm)
  - [1. CLIP-based Zero/Few-Shot Detection](#1-clip-based-zerofew-shot-detection)
  - [2. MLLM-based Detection & Reasoning](#2-mllm-based-detection--reasoning)
  - [3. VLM-guided Anomaly Synthesis](#3-vlm-guided-anomaly-synthesis)
  - [4. Training-Free / Prompt-Only Methods](#4-training-free--prompt-only-methods)
  - [5. Reinforcement Learning + VLM](#5-reinforcement-learning--vlm)
- [Benchmarks & Datasets](#benchmarks--datasets)
  - [Established Datasets](#established-datasets)
  - [VLM-Era Benchmarks](#vlm-era-benchmarks)
- [Key Metrics](#key-metrics)
- [Open Research Gaps](#open-research-gaps)
- [Related Resources](#related-resources)
- [Contributing](#contributing)
- [Star History](#star-history)

---

## Surveys & Tutorials

| Title | Venue | Year | Links | Notes |
|-------|-------|------|-------|-------|
| Deep Industrial Image Anomaly Detection: A Survey | Machine Intelligence Research | 2024 | [paper](https://link.springer.com/article/10.1007/s11633-023-1459-z) | Comprehensive traditional + DL survey |
| A Survey on RGB, 3D, and Multimodal Approaches for Unsupervised IAD | Information Fusion | 2025 | [paper](https://doi.org/10.1016/j.inffus.2025.103139) / [github](https://github.com/Sunny5250/Awesome-Multi-Setting-UIAD) | Multi-setting taxonomy |
| Large Vision-Language Models for Industrial Anomaly Detection: A Comprehensive Survey | IJERM | 2025 | [paper](https://www.ijerm.com/download_data/IJERM1205001.pdf) | First LVLM × IAD survey |
| Foundation Models in Visual Anomaly Detection (Tutorial) | ICCV 2025 | 2025 | [webpage](https://github.com/mala-lab/Awesome-Anomaly-Detection-Foundation-Models) | Half-day tutorial |
| A Survey on Industrial Anomalies Synthesis | — | 2025 | [paper](https://github.com/M-3LAB/awesome-anomaly-synthesis) | Anomaly generation methods |

---

## Papers by Paradigm

### 1. CLIP-based Zero/Few-Shot Detection

Methods that adapt CLIP's visual-textual alignment for anomaly scoring without (or with few) target-domain anomaly samples.

> **核心概念 (Core Idea):** 利用 CLIP 的 vision-text alignment，將「正常/異常」語義映射到 feature space 進行 zero-shot 或 few-shot 偵測。

| Paper | Venue | Year | Code | Backbone | Dataset | Key Contribution |
|-------|-------|------|------|----------|---------|------------------|
| WinCLIP: Zero-/Few-Shot Anomaly Classification and Segmentation | CVPR | 2023 | [code](https://github.com/caoyunkang/WinCLIP) | CLIP ViT-L/14 | MVTec AD, VisA | Window-based multi-scale CLIP matching |
| AnomalyCLIP: Object-agnostic Prompt Learning for Zero-shot AD | ICLR | 2024 | [code](https://github.com/zqhang/AnomalyCLIP) | CLIP ViT-L/14 | MVTec AD, VisA, MPDD, BTAD | Object-agnostic prompt learning |
| CLIP-AD: A Language-Guided Staged Dual-Path Model for Zero-shot AD | arXiv | 2024 | [code](https://github.com/caoyunkang/CLIP-AD) | CLIP | MVTec AD | Staged dual-path architecture |
| PromptAD: Learning Prompts with only Normal Samples for Few-Shot AD | CVPR | 2024 | [code](https://github.com/FuNz-0/PromptAD) | CLIP | MVTec AD, VisA | Normal-only prompt learning |
| AdaptCLIP: Adapting CLIP for Universal Visual AD | AAAI | 2026 | [code](https://github.com/YoojLee/AdaptCLIP) | CLIP | MVTec AD, VisA | Universal adaptation framework |
| AA-CLIP: Enhancing Zero-Shot AD via Anomaly-Aware CLIP | CVPR | 2025 | [code](https://github.com/ByChelsea/AA-CLIP) | CLIP | MVTec AD, VisA | Anomaly-aware CLIP fine-tuning |
| GenCLIP: Generalizing CLIP Prompts for Zero-shot AD | arXiv | 2025 | [code](https://github.com/GenCLIP/GenCLIP) | CLIP | MVTec AD | Generalized prompt design |
| LAFT: Language-Assisted Feature Transformation for AD | ICLR | 2025 | [code](https://github.com/YunYunY/LAFT) | CLIP | MVTec AD, VisA | Language-assisted feature transform |

### 2. MLLM-based Detection & Reasoning

Methods that leverage Multimodal LLMs (GPT-4V, InternVL, LLaVA, Qwen-VL, etc.) for anomaly detection AND natural-language reasoning/explanation.

> **核心概念:** 利用 MLLM 的推理能力，不僅偵測異常，更能以自然語言解釋異常原因與位置。

| Paper | Venue | Year | Code | Base MLLM | Dataset | Key Contribution |
|-------|-------|------|------|-----------|---------|------------------|
| AnomalyGPT: Detecting Industrial Anomalies Using Large VLMs | AAAI | 2024 | [code](https://github.com/CASIA-IVA-Lab/AnomalyGPT) | LLaVA | MVTec AD | First MLLM for industrial AD |
| Customizing VL Foundation Models for Multi-modal AD and Reasoning | arXiv | 2024 | [code](https://github.com/Xiaohao-Xu/Customizable-VLM) | — | MVTec AD, VisA | Customizable VLM pipeline |
| Anomaly-OV: Towards Zero-Shot AD and Reasoning with MLLMs | CVPR | 2025 | [code](https://github.com/hq-deng/Anomaly-OV) | InternVL / LLaVA | MVTec AD, VisA | Two-stage: anomaly expert + visual instruction tuning |
| MMAD: Comprehensive Benchmark for MLLMs in IAD | ICLR | 2025 | [code](https://github.com/jam-cc/MMAD) | Multiple | MMAD benchmark | Multimodal benchmark for IAD |
| EMIT: Enhancing MLLMs for IAD via Difficulty-Aware | arXiv | 2025 | [code](https://github.com/EMIT-AD/EMIT) | — | MVTec AD | Difficulty-aware training |
| OmniAD: Detect and Understand Industrial Anomaly via Multimodal Reasoning | arXiv | 2025 | — | — | MVTec AD, VisA | Multi-task reasoning |
| IAD-R1: Reinforcing Consistent Reasoning in IAD | ICCV | 2025 | [code](https://github.com/IAD-R1/IAD-R1) | — | MVTec AD | RL-based consistent reasoning |
| AnomalyR1: A GRPO-based End-to-end MLLM for IAD | arXiv | 2025 | [code](https://github.com/AnomalyR1/AnomalyR1) | — | MVTec AD | GRPO reinforcement for IAD |
| Judo: Juxtaposed Domain-oriented Multimodal Reasoner for IAD QA | ICLR | 2026 | — | — | — | Domain-oriented QA reasoning |
| Triad: Empowering LMM-based AD with Vision Expert-guided Tokenizer | arXiv | 2025 | — | — | — | Manufacturing process aware |

### 3. VLM-guided Anomaly Synthesis

Methods that use VLMs or text guidance to generate/synthesize anomaly images for training.

> **核心概念:** 用 VLM 或文字描述引導異常影像合成，解決工業場景中異常樣本稀缺的問題。

| Paper | Venue | Year | Code | Key Contribution |
|-------|-------|------|------|------------------|
| AnoStyler: Text-Driven Localized Anomaly Generation via Style Transfer | AAAI | 2026 | [code](https://github.com/AnoStyler/AnoStyler) | Text-driven style transfer for anomaly generation |
| Anomagic: Crossmodal Prompt-driven Zero-shot Anomaly Generation | AAAI | 2026 | [code](https://github.com/Anomagic/Anomagic) | Cross-modal prompt-driven generation |
| Anomaly Anything: Promptable Unseen Visual Anomaly Generation | CVPR | 2025 | [code](https://github.com/IMOS/AnomalyAny) | Promptable anomaly generation |
| FAST: Foreground-aware Diffusion for Anomaly Synthesis | NeurIPS | 2025 | [code](https://github.com/FAST-AD/FAST) | Foreground-aware diffusion |

### 4. Training-Free / Prompt-Only Methods

Methods requiring no fine-tuning — pure inference-time adaptation via prompting or in-context learning.

> **核心概念:** 完全不需要訓練或微調，僅透過 prompt engineering 或 in-context learning 即可偵測工業異常。

| Paper | Venue | Year | Code | Key Contribution |
|-------|-------|------|------|------------------|
| InCTRL: Toward Generalist AD via In-context Residual Learning | CVPR | 2024 | [code](https://github.com/mala-lab/InCTRL) | In-context residual learning with few-shot prompts |
| UniVAD: Training-free Unified Model for Few-shot Visual AD | CVPR | 2025 | [code](https://github.com/ByChelsea/UniVAD) | Training-free unified detection |
| Towards Training-free AD with Vision and Language Foundation Models | CVPR | 2025 | [code](https://github.com/Training-free-AD/TFAD) | Zero training overhead |
| AnomalyMoE: Language-free Generalist Model for Unified Visual AD | AAAI | 2026 | [code](https://github.com/AnomalyMoE/AnomalyMoE) | Mixture-of-experts without language |

### 5. Reinforcement Learning + VLM

Emerging paradigm: using RL (GRPO, PPO, etc.) to refine VLM reasoning for IAD.

> **核心概念:** 用強化學習微調 VLM 的推理過程，提升工業異常偵測的一致性與準確性。新興方向。

| Paper | Venue | Year | Code | Key Contribution |
|-------|-------|------|------|------------------|
| IAD-R1: Reinforcing Consistent Reasoning in IAD | ICCV | 2025 | [code](https://github.com/IAD-R1/IAD-R1) | Consistency via RL |
| AnomalyR1: A GRPO-based End-to-end MLLM for IAD | arXiv | 2025 | [code](https://github.com/AnomalyR1/AnomalyR1) | GRPO for end-to-end IAD |

---

## Benchmarks & Datasets

### Established Datasets

| Dataset | Year | Modality | Categories | Anomaly Types | Scale | Notes |
|---------|------|----------|------------|---------------|-------|-------|
| [MVTec AD](https://www.mvtec.com/company/research/datasets/mvtec-ad) | 2019 | RGB | 15 | 73 defect types | ~5K images | De facto standard for IAD |
| [MVTec LOCO-AD](https://www.mvtec.com/company/research/datasets/mvtec-loco) | 2022 | RGB | 5 | Logical + structural | ~3K images | Logical anomaly detection |
| [VisA](https://github.com/amazon-science/spot-diff) | 2022 | RGB | 12 | Complex structures | ~10K images | Multi-instance + complex |
| [MPDD](https://github.com/stepanje/MPDD) | 2021 | RGB | 6 | Metal parts defects | ~1K images | Metal parts domain |
| [BTAD](https://avires.dimi.uniud.it/papers/btad/) | 2021 | RGB | 3 | Body/surface textures | ~2.8K images | Texture-focused |
| [Real-IAD](https://realiad4ad.github.io/Real-IAD/) | 2024 | RGB | 30 | Real industrial | ~150K images | Large-scale realistic |
| [Real3D-AD](https://github.com/M-3LAB/Real3D-AD) | 2023 | Point Cloud | 12 | 3D anomalies | ~1.2K samples | 3D point cloud |

### VLM-Era Benchmarks

| Benchmark | Year | Venue | Focus | Key Feature |
|-----------|------|-------|-------|-------------|
| [MMAD](https://github.com/jam-cc/MMAD) | 2025 | ICLR | MLLM evaluation for IAD | Multi-modal QA benchmark |
| [ASBench](https://github.com/M-3LAB/awesome-anomaly-synthesis) | 2025 | — | Anomaly synthesis evaluation | Synthesis quality metrics |

---

## Key Metrics

| Metric | Full Name | Level | Usage |
|--------|-----------|-------|-------|
| **AUROC** | Area Under ROC Curve | Image / Pixel | Primary classification metric |
| **AU-PRO** | Area Under Per-Region Overlap | Pixel | Segmentation quality at component level |
| **AP** | Average Precision | Image / Pixel | Precision-recall summary |
| **F1-max** | Maximum F1 Score | Image / Pixel | Threshold-optimized F1 |
| **IoU** | Intersection over Union | Pixel | Segmentation overlap |
| **AUPRO** | Area Under PRO Curve | Pixel | Integration limit typically at 0.3 FPR |

---

## Open Research Gaps

> 🔬 **Research opportunities** identified from literature analysis. See [methodology.md](./methodology.md) for how gaps were identified.

| # | Gap | Description | Difficulty | Potential Impact |
|---|-----|-------------|------------|------------------|
| 1 | **Fine-Grained Spatial Alignment** | Current VLMs operate at image/patch level; pixel-precise localization remains weak. Anomaly-OV's LTFM is one attempt, but local attention mechanisms (e.g., dual-path) are underexplored. | ⭐⭐⭐ | 🔥🔥🔥 |
| 2 | **Logical Anomaly Understanding** | VLMs struggle with *logical* anomalies (missing parts, wrong assembly order) vs *structural* defects. LOCO-AD performance lags significantly. | ⭐⭐⭐ | 🔥🔥🔥 |
| 3 | **Domain-Specific Knowledge Integration** | Generic VLMs lack manufacturing domain knowledge (material properties, process specs). How to inject domain priors efficiently? | ⭐⭐ | 🔥🔥 |
| 4 | **Efficiency for Edge Deployment** | Most MLLM methods are too heavy for real-time on-line inspection. Compact VLM + quantization + distillation for industrial edge is open. | ⭐⭐⭐ | 🔥🔥🔥 |
| 5 | **Multi-Modal Fusion (RGB + 3D + Thermal)** | Industrial inspection often uses multiple sensors. VLM-based multi-modal fusion is barely explored. | ⭐⭐ | 🔥🔥 |
| 6 | **Continual / Incremental Learning** | Production lines evolve — new product types appear. How to update VLM-based detectors without catastrophic forgetting? | ⭐⭐⭐ | 🔥🔥 |
| 7 | **Explainability & Trustworthiness** | Industrial users need auditable explanations. Current MLLM reasoning can hallucinate. Grounded, verifiable explanations are needed. | ⭐⭐ | 🔥🔥🔥 |

---

## Related Resources

**Awesome Lists**
- [M-3LAB/awesome-industrial-anomaly-detection](https://github.com/M-3LAB/awesome-industrial-anomaly-detection) — Comprehensive general IAD paper list
- [mala-lab/Awesome-Anomaly-Detection-Foundation-Models](https://github.com/mala-lab/Awesome-Anomaly-Detection-Foundation-Models) — Foundation models for all AD domains
- [Sunny5250/Awesome-Multi-Setting-UIAD](https://github.com/Sunny5250/Awesome-Multi-Setting-UIAD) — Multi-setting unsupervised IAD taxonomy

**Frameworks & Tools**
- [Anomalib](https://github.com/openvinotoolkit/anomalib) — OpenVINO anomaly detection library
- [open-iad](https://github.com/M-3LAB/open-iad) — Open benchmark framework for IAD

**Conferences to Watch**
- CVPR / ICCV / ECCV (computer vision)
- NeurIPS / ICLR / ICML (machine learning)
- AAAI / IJCAI (artificial intelligence)
- ACM MM (multimedia)

---

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

**Quick Add — Submit a Paper:**
1. Fork this repo
2. Add the paper entry in the correct paradigm section
3. Include: Paper title, venue, year, code link (if available), key contribution
4. Submit a PR following the template

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=YOUR_USERNAME/awesome-vlm-industrial-anomaly-detection&type=Date)](https://star-history.com/#YOUR_USERNAME/awesome-vlm-industrial-anomaly-detection&Date)

---

## Citation

If you find this resource helpful, please consider citing:

```bibtex
@misc{awesome-vlm-iad,
  author = {ED Huang},
  title = {Awesome VLM Industrial Anomaly Detection},
  year = {2026},
  publisher = {GitHub},
  howpublished = {\url{https://github.com/YOUR_USERNAME/awesome-vlm-industrial-anomaly-detection}}
}
```

---

## License

This project is licensed under the MIT License — see [LICENSE](./LICENSE) for details.

---

<p align="center">
  <i>Maintained by <a href="https://github.com/YOUR_USERNAME">ED Huang</a> · Last updated: 2026-03</i>
</p>
