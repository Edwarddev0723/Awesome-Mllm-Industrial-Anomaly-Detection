# Awesome MLLM Industrial Anomaly Detection

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](./CONTRIBUTING.md)
[![Last Update](https://img.shields.io/badge/Last_Update-2026--03-blue.svg)](#)

> A curated list of papers, benchmarks, datasets, and resources on **Multimodal Large Language Model (MLLM)** approaches for **Industrial Anomaly Detection (IAD)**. Focused on generative MLLMs (LLaVA, InternVL, GPT-4V, Qwen-VL, etc.) that receive images and produce natural language output for manufacturing/industrial quality inspection.

<p align="center">
  <img src="assets/taxonomy.png" alt="Taxonomy Overview" width="800"/>
</p>

## Why This List?

Existing awesome lists cover either *general* industrial anomaly detection (e.g., [M-3LAB/awesome-industrial-anomaly-detection](https://github.com/M-3LAB/awesome-industrial-anomaly-detection)) or *broad* foundation-model-based AD (e.g., [mala-lab/Awesome-Anomaly-Detection-Foundation-Models](https://github.com/mala-lab/Awesome-Anomaly-Detection-Foundation-Models)). **This list narrows the scope** to methods that leverage **MLLMs** — models that can receive images and generate natural language output — specifically for industrial image anomaly detection and reasoning, providing:

- **MLLM-focused taxonomy** — not just a flat paper list; CLIP-only methods are out of scope
- **Reproducibility tags** — code availability, base MLLM, dataset info at a glance
- **Research gap annotations** — what's unsolved and where opportunities lie
- **Bilingual support** — English primary, Traditional Chinese annotations (繁體中文) where helpful

### Scope Definition

**In scope:** Methods using generative MLLMs (LLaVA, InternVL, GPT-4V, Qwen-VL, etc.) as a core component for industrial anomaly detection, reasoning, or synthesis. The MLLM must produce natural language output (detection results, explanations, or reasoning).

**Out of scope:** CLIP-only methods (contrastive models without language generation), pure CNN/reconstruction-based methods, non-industrial anomaly detection.

---

## Table of Contents

- [Surveys & Tutorials](#surveys--tutorials)
- [Papers by Paradigm](#papers-by-paradigm)
  - [1. MLLM-based Detection & Reasoning](#1-mllm-based-detection--reasoning)
  - [2. Training-Free / Prompt-Only MLLM Methods](#2-training-free--prompt-only-mllm-methods)
  - [3. Reinforcement Learning + MLLM](#3-reinforcement-learning--mllm)
- [Benchmarks & Datasets](#benchmarks--datasets)
  - [Established Datasets](#established-datasets)
  - [MLLM-Era Benchmarks](#mllm-era-benchmarks)
- [Key Metrics](#key-metrics)
- [Open Research Gaps](#open-research-gaps)
- [Related Resources](#related-resources)
- [Contributing](#contributing)
- [Star History](#star-history)

---

## Surveys & Tutorials

| Title | Venue | Year | Links | Notes |
|-------|-------|------|-------|-------|
| Large Vision-Language Models for Industrial Anomaly Detection: A Comprehensive Survey | IJERM | 2025 | [paper](https://www.ijerm.com/download_data/IJERM1205001.pdf) | First LVLM × IAD survey |
| Deep Industrial Image Anomaly Detection: A Survey | Machine Intelligence Research | 2024 | [paper](https://link.springer.com/article/10.1007/s11633-023-1459-z) | Comprehensive traditional + DL survey |
| A Survey on RGB, 3D, and Multimodal Approaches for Unsupervised IAD | Information Fusion | 2025 | [paper](https://doi.org/10.1016/j.inffus.2025.103139) / [github](https://github.com/Sunny5250/Awesome-Multi-Setting-UIAD) | Multi-setting taxonomy |
| Foundation Models in Visual Anomaly Detection (Tutorial) | ICCV 2025 | 2025 | [webpage](https://github.com/mala-lab/Awesome-Anomaly-Detection-Foundation-Models) | Half-day tutorial |
| A Survey on Industrial Anomalies Synthesis | — | 2025 | [paper](https://github.com/M-3LAB/awesome-anomaly-synthesis) | Anomaly generation methods |

---

## Papers by Paradigm

### 1. MLLM-based Detection & Reasoning

Methods that leverage Multimodal LLMs (GPT-4V, InternVL, LLaVA, Qwen-VL, etc.) for anomaly detection AND natural-language reasoning/explanation.

> **核心概念 (Core Idea):** 利用 MLLM 的推理能力，不僅偵測異常，更能以自然語言解釋異常原因與位置。本 repo 的核心 section。

| Paper | Venue | Year | Code | Base MLLM | Dataset | Key Contribution |
|-------|-------|------|------|-----------|---------|------------------|
| AnomalyGPT: Detecting Industrial Anomalies Using Large VLMs | AAAI | 2024 | [code](https://github.com/CASIA-IVA-Lab/AnomalyGPT) | LLaVA | MVTec AD | First MLLM for industrial AD |
| Customizing VL Foundation Models for Multi-modal AD and Reasoning | arXiv | 2024 | [code](https://github.com/Xiaohao-Xu/Customizable-VLM) | — | MVTec AD, VisA | Customizable VLM pipeline |
| Anomaly-OV: Towards Zero-Shot AD and Reasoning with MLLMs | CVPR | 2025 | [code](https://github.com/honda-research-institute/Anomaly-OneVision) | InternVL / LLaVA | MVTec AD, VisA | Two-stage: anomaly expert + visual instruction tuning |
| MMAD: Comprehensive Benchmark for MLLMs in IAD | ICLR | 2025 | [code](https://github.com/jam-cc/MMAD) | Multiple | MMAD benchmark | Multimodal benchmark for IAD |
| EMIT: Enhancing MLLMs for IAD via Difficulty-Aware | arXiv | 2025 | — | — | MVTec AD | Difficulty-aware training |
| OmniAD: Detect and Understand Industrial Anomaly via Multimodal Reasoning | arXiv | 2025 | — | — | MVTec AD, VisA | Multi-task reasoning |
| Judo: Juxtaposed Domain-oriented Multimodal Reasoner for IAD QA | ICLR | 2026 | — | — | — | Domain-oriented QA reasoning |
| Triad: Empowering LMM-based AD with Vision Expert-guided Tokenizer | arXiv | 2025 | — | — | — | Manufacturing process aware |
| Echo: Multi-Expert Framework for MLLM in IAD | arXiv | 2025 | [code](https://github.com/Ed1sonChen/Echo) | Multiple | MMAD | Four expert modules for domain-aware reasoning |
| EIAD: Explainable Industrial AD via Multi-Modal LLMs | arXiv | 2025 | — | MLLM | MVTec AD | Decoupled defect localization + DDQA dataset |
| VELM: Vision Expert + LLM for Anomaly Classification | CVPR WS | 2025 | [code](https://github.com/Sassanmtr/VELM) | GPT-4o / Qwen2-VL | MVTec AD, VisA | Vision expert + LLM pipeline for classification |
| SAGE: VLM for AD via Fact Enhancement and Alignment | ACM MM | 2025 | [code](https://github.com/amoreZgx1n/SAGE) | VLM | MVTec AD | Self-guided fact enhancement + E-DPO |

### 2. Training-Free / Prompt-Only MLLM Methods

Methods requiring no fine-tuning — pure inference-time MLLM adaptation via prompting or in-context learning.

> **核心概念:** 完全不需要訓練或微調 MLLM，僅透過 prompt engineering 或 in-context learning 即可偵測工業異常。

| Paper | Venue | Year | Code | Base MLLM | Key Contribution |
|-------|-------|------|------|-----------|------------------|
| LogSAD: Training-free AD with Vision and Language Foundation Models | CVPR | 2025 | [code](https://github.com/zhang0jhon/LogSAD) | GPT-4V | Match-of-thought for logical + structural AD |
| LogicAD: Explainable Logical AD via VLM Text Features | arXiv | 2025 | — | AVLM | Autoregressive VLM for logical anomaly detection |
| LogicQA: Logical AD with VLM Generated Questions | ACL | 2025 | — | VLM | Training-free question-based logical AD |

### 3. Reinforcement Learning + MLLM

Emerging paradigm: using RL (GRPO, PPO, etc.) to refine MLLM reasoning for IAD.

> **核心概念:** 用強化學習微調 MLLM 的推理過程，提升工業異常偵測的一致性與準確性。新興方向。

| Paper | Venue | Year | Code | Base MLLM | Key Contribution |
|-------|-------|------|------|-----------|------------------|
| IAD-R1: Reinforcing Consistent Reasoning in IAD | ICCV | 2025 | [code](https://github.com/Yanhui-Lee/IAD-R1) | — | Consistency via RL |
| AnomalyR1: A GRPO-based End-to-end MLLM for IAD | arXiv | 2025 | — | — | GRPO for end-to-end IAD |

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

### MLLM-Era Benchmarks

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
| 1 | **Fine-Grained Spatial Alignment** | Current MLLMs operate at image/patch level; pixel-precise localization remains weak. Anomaly-OV's LTFM is one attempt. | ⭐⭐⭐ | 🔥🔥🔥 |
| 2 | **Logical Anomaly Understanding** | MLLMs show promise for logical anomalies (LogicAD, LogicQA, LogSAD address LOCO-AD), but performance gap vs structural defects remains. | ⭐⭐ | 🔥🔥🔥 |
| 3 | **Domain-Specific Knowledge Integration** | Generic MLLMs lack manufacturing domain knowledge. Echo's Knowledge Guide and SAGE's SFE are early attempts. | ⭐⭐ | 🔥🔥 |
| 4 | **Efficiency for Edge Deployment** | MLLMs are too heavy for real-time on-line inspection. Compact MLLM + quantization + distillation for industrial edge is wide open. | ⭐⭐⭐ | 🔥🔥🔥 |
| 5 | **Multi-Modal Fusion (RGB + 3D + Thermal)** | Industrial inspection often uses multiple sensors. MLLM-based multi-modal fusion is barely explored. | ⭐⭐ | 🔥🔥 |
| 6 | **Continual / Incremental Learning** | Production lines evolve — new product types appear. How to update MLLM-based detectors without catastrophic forgetting? | ⭐⭐⭐ | 🔥🔥 |
| 7 | **Explainability & Trustworthiness** | MLLM reasoning can hallucinate. EIAD and SAGE address this partially. Grounded, verifiable explanations are needed. | ⭐⭐ | 🔥🔥🔥 |
| 8 | **MLLM-guided Anomaly Synthesis** | No current methods use MLLMs to generate/guide anomaly image synthesis for training. Emerging opportunity. | ⭐⭐ | 🔥🔥 |

---

## Related Resources

**Awesome Lists**
- [M-3LAB/awesome-industrial-anomaly-detection](https://github.com/M-3LAB/awesome-industrial-anomaly-detection) — Comprehensive general IAD paper list
- [mala-lab/Awesome-Anomaly-Detection-Foundation-Models](https://github.com/mala-lab/Awesome-Anomaly-Detection-Foundation-Models) — Foundation models for all AD domains (includes CLIP-based methods)
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
3. Include: Paper title, venue, year, code link (if available), base MLLM, key contribution
4. Submit a PR following the template

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=YOUR_USERNAME/awesome-mllm-industrial-anomaly-detection&type=Date)](https://star-history.com/#YOUR_USERNAME/awesome-mllm-industrial-anomaly-detection&Date)

---

## Citation

If you find this resource helpful, please consider citing:

```bibtex
@misc{awesome-mllm-iad,
  author = {ED Huang},
  title = {Awesome MLLM Industrial Anomaly Detection},
  year = {2026},
  publisher = {GitHub},
  howpublished = {\url{https://github.com/YOUR_USERNAME/awesome-mllm-industrial-anomaly-detection}}
}
```

---

## License

This project is licensed under the MIT License — see [LICENSE](./LICENSE) for details.

---

<p align="center">
  <i>Maintained by <a href="https://github.com/YOUR_USERNAME">ED Huang</a> · Last updated: 2026-03</i>
</p>
