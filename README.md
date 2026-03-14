# Awesome MLLM Industrial Anomaly Detection

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![CC0](https://img.shields.io/badge/license-CC0-green.svg)](https://creativecommons.org/publicdomain/zero/1.0/)
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

## Contents

- [Start Here](#start-here)
- [Surveys & Tutorials](#surveys--tutorials)
- [Papers by Paradigm](#papers-by-paradigm)
  - [1. MLLM-based Detection & Reasoning](#1-mllm-based-detection--reasoning)
  - [2. Training-Free / Prompt-Only MLLM Methods](#2-training-free--prompt-only-mllm-methods)
  - [3. Reinforcement Learning + MLLM](#3-reinforcement-learning--mllm)
- [By Task / By Capability](#by-task--by-capability)
- [Benchmarks & Datasets](#benchmarks--datasets)
  - [Established Datasets](#established-datasets)
  - [MLLM-Era Benchmarks](#mllm-era-benchmarks)
- [Key Metrics](#key-metrics)
- [Open Research Gaps](#open-research-gaps)
- [Related Resources](#related-resources)
- [Recently Added](#recently-added)

---

## Start Here

New to MLLM × IAD? Start with these papers in order before exploring the full list.

| Step | Paper | Why Read This First |
|------|-------|---------------------|
| 1. Foundation | [AnomalyGPT](https://github.com/CASIA-IVA-Lab/AnomalyGPT) — AAAI 2024 | Established MLLM-for-IAD as a paradigm; foundational architecture and vocab used by subsequent work |
| 2. Landscape | [Large VLMs for IAD Survey](https://www.ijerm.com/download_data/IJERM1205001.pdf) — IJERM 2025 | First survey scoping MLLM × IAD; maps all paradigms and places individual papers in context |
| 3. Evaluation | [MMAD](https://github.com/jam-cc/MMAD) — ICLR 2025 | Defines how MLLMs are benchmarked for IAD; essential for interpreting reported numbers |
| 4. Training-free | [LogSAD](https://github.com/zhang0jhon/LogSAD) — CVPR 2025 | Shows what prompting alone achieves on logical + structural anomalies; calibrates baselines |
| 5. Localization | [Anomaly-OV](https://github.com/honda-research-institute/Anomaly-OneVision) — CVPR 2025 | State-of-the-art pixel-level reasoning via two-stage pipeline |
| 6. Explainability | EIAD — arXiv 2025 | Decoupled localization + DDQA dataset; grounded, verifiable reasoning |
| 7. RL frontier | [IAD-R1](https://github.com/Yanhui-Lee/IAD-R1) — ICCV 2025 | RL-based consistency training; represents the newest training paradigm |
| 8. Open problems | [Research Gaps](#open-research-gaps) | Where the field is still unsolved — starting point for original contribution |

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

| Paper | Venue | Year | Code | Base MLLM | Dataset | Key Contribution | Tags |
|-------|-------|------|------|-----------|---------|------------------|------|
| AnomalyGPT: Detecting Industrial Anomalies Using Large VLMs | AAAI | 2024 | [code](https://github.com/CASIA-IVA-Lab/AnomalyGPT) | LLaVA | MVTec AD | First MLLM for industrial AD | `Peer-reviewed` `Reasoning` |
| Customizing VL Foundation Models for Multi-modal AD and Reasoning | arXiv | 2024 | [code](https://github.com/Xiaohao-Xu/Customizable-VLM) | — | MVTec AD, VisA | Customizable VLM pipeline | `arXiv` `Reasoning` |
| Anomaly-OV: Towards Zero-Shot AD and Reasoning with MLLMs | CVPR | 2025 | [code](https://github.com/honda-research-institute/Anomaly-OneVision) | InternVL / LLaVA | MVTec AD, VisA | Two-stage: anomaly expert + visual instruction tuning | `Peer-reviewed` `Reasoning` `Localization` |
| MMAD: Comprehensive Benchmark for MLLMs in IAD | ICLR | 2025 | [code](https://github.com/jam-cc/MMAD) | Multiple | MMAD benchmark | Multimodal benchmark for IAD | `Peer-reviewed` `Benchmark` |
| EMIT: Enhancing MLLMs for IAD via Difficulty-Aware | arXiv | 2025 | — | — | MVTec AD | Difficulty-aware training | `arXiv` `Reasoning` |
| OmniAD: Detect and Understand Industrial Anomaly via Multimodal Reasoning | arXiv | 2025 | — | — | MVTec AD, VisA | Multi-task reasoning | `arXiv` `Reasoning` |
| Judo: Juxtaposed Domain-oriented Multimodal Reasoner for IAD QA | ICLR | 2026 | — | — | — | Domain-oriented QA reasoning | `Peer-reviewed` `Reasoning` |
| Triad: Empowering LMM-based AD with Vision Expert-guided Tokenizer | arXiv | 2025 | — | — | — | Manufacturing process aware | `arXiv` `Reasoning` |
| Echo: Multi-Expert Framework for MLLM in IAD | arXiv | 2025 | [code](https://github.com/Ed1sonChen/Echo) | Multiple | MMAD | Four expert modules for domain-aware reasoning | `arXiv` `Reasoning` |
| EIAD: Explainable Industrial AD via Multi-Modal LLMs | arXiv | 2025 | — | MLLM | MVTec AD | Decoupled defect localization + DDQA dataset | `arXiv` `Reasoning` `Localization` |
| VELM: Vision Expert + LLM for Anomaly Classification | CVPR WS | 2025 | [code](https://github.com/Sassanmtr/VELM) | GPT-4o / Qwen2-VL | MVTec AD, VisA | Vision expert + LLM pipeline for classification | `Peer-reviewed` `Reasoning` |
| SAGE: VLM for AD via Fact Enhancement and Alignment | ACM MM | 2025 | [code](https://github.com/amoreZgx1n/SAGE) | VLM | MVTec AD | Self-guided fact enhancement + E-DPO | `Peer-reviewed` `Reasoning` |

### 2. Training-Free / Prompt-Only MLLM Methods

Methods requiring no fine-tuning — pure inference-time MLLM adaptation via prompting or in-context learning.

> **核心概念:** 完全不需要訓練或微調 MLLM，僅透過 prompt engineering 或 in-context learning 即可偵測工業異常。

| Paper | Venue | Year | Code | Base MLLM | Key Contribution | Tags |
|-------|-------|------|------|-----------|------------------|------|
| LogSAD: Training-free AD with Vision and Language Foundation Models | CVPR | 2025 | [code](https://github.com/zhang0jhon/LogSAD) | GPT-4V | Match-of-thought for logical + structural AD | `Peer-reviewed` `Training-free` `Reasoning` |
| LogicAD: Explainable Logical AD via VLM Text Features | arXiv | 2025 | — | AVLM | Autoregressive VLM for logical anomaly detection | `arXiv` `Training-free` `Reasoning` |
| LogicQA: Logical AD with VLM Generated Questions | ACL | 2025 | — | VLM | Training-free question-based logical AD | `Peer-reviewed` `Training-free` `Reasoning` |

### 3. Reinforcement Learning + MLLM

Emerging paradigm: using RL (GRPO, PPO, etc.) to refine MLLM reasoning for IAD.

> **核心概念:** 用強化學習微調 MLLM 的推理過程，提升工業異常偵測的一致性與準確性。新興方向。

| Paper | Venue | Year | Code | Base MLLM | Key Contribution | Tags |
|-------|-------|------|------|-----------|------------------|------|
| IAD-R1: Reinforcing Consistent Reasoning in IAD | ICCV | 2025 | [code](https://github.com/Yanhui-Lee/IAD-R1) | — | Consistency via RL | `Peer-reviewed` `RL` `Reasoning` |
| AnomalyR1: A GRPO-based End-to-end MLLM for IAD | arXiv | 2025 | — | — | GRPO for end-to-end IAD | `arXiv` `RL` `Reasoning` |

---

## By Task / By Capability

Cross-index to find papers by what they do, regardless of training paradigm.

### Image-level Anomaly Classification

- [AnomalyGPT](https://github.com/CASIA-IVA-Lab/AnomalyGPT) — AAAI 2024
- [VELM](https://github.com/Sassanmtr/VELM) — CVPR WS 2025
- [MMAD](https://github.com/jam-cc/MMAD) — ICLR 2025 *(benchmark)*

### Pixel-level Localization / Segmentation

- [Anomaly-OV](https://github.com/honda-research-institute/Anomaly-OneVision) — CVPR 2025 · LTFM for pixel-grounded reasoning
- EIAD — arXiv 2025 · Decoupled localization module + DDQA evaluation

### Logical Anomaly Detection

- [LogSAD](https://github.com/zhang0jhon/LogSAD) — CVPR 2025 · Match-of-thought on MVTec LOCO-AD
- LogicAD — arXiv 2025 · Autoregressive VLM for logical anomalies
- LogicQA — ACL 2025 · Question-based logical anomaly detection

### Explainable Reasoning / QA

- [MMAD](https://github.com/jam-cc/MMAD) — ICLR 2025 · Multi-modal QA benchmark
- Judo — ICLR 2026 · Domain-oriented QA reasoning
- EIAD — arXiv 2025 · DDQA dataset + decoupled explanation pipeline
- [Echo](https://github.com/Ed1sonChen/Echo) — arXiv 2025 · Four-module domain-aware reasoning

### Training-free / Zero-shot

- [LogSAD](https://github.com/zhang0jhon/LogSAD) — CVPR 2025
- LogicAD — arXiv 2025
- LogicQA — ACL 2025

### RL-based Reasoning Refinement

- [IAD-R1](https://github.com/Yanhui-Lee/IAD-R1) — ICCV 2025
- AnomalyR1 — arXiv 2025

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

## Recently Added

> Last updated: 2026-03.

| Paper | Venue | Year | Added |
|-------|-------|------|-------|
| Judo: Juxtaposed Domain-oriented Multimodal Reasoner for IAD QA | ICLR | 2026 | 2026-03 |
| Echo: Multi-Expert Framework for MLLM in IAD | arXiv | 2025 | 2026-03 |
| AnomalyR1: A GRPO-based End-to-end MLLM for IAD | arXiv | 2025 | 2026-03 |
| VELM: Vision Expert + LLM for Anomaly Classification | CVPR WS | 2025 | 2026-03 |
| SAGE: VLM for AD via Fact Enhancement and Alignment | ACM MM | 2025 | 2026-03 |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=Edwarddev0723/Awesome-Mllm-Industrial-Anomaly-Detection&type=Date)](https://star-history.com/#Edwarddev0723/Awesome-Mllm-Industrial-Anomaly-Detection&Date)

---

## Citation

If you find this resource helpful, please consider citing:

```bibtex
@misc{awesome-mllm-iad,
  author = {Ren He},
  title = {Awesome MLLM Industrial Anomaly Detection},
  year = {2026},
  publisher = {GitHub},
  howpublished = {\url{https://github.com/Edwarddev0723/Awesome-Mllm-Industrial-Anomaly-Detection}}
}
```

---

<p align="center">
  <i>Maintained by <a href="https://github.com/Edwarddev0723">Ren He</a> · Last updated: 2026-03 · <a href="https://creativecommons.org/publicdomain/zero/1.0/">CC0 1.0</a></i>
</p>
