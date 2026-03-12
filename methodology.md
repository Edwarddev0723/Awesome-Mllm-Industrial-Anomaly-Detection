# Paper Selection Methodology

This document describes how papers are selected, categorized, and maintained in this awesome list. Transparency in curation methodology is essential for a trustworthy research resource.

---

## 1. Scope Definition

### Primary Scope
Papers must satisfy **both** conditions simultaneously:

1. **MLLM involvement** — The method uses a Multimodal Large Language Model (LLaVA, InternVL, GPT-4V, Qwen-VL, etc.) as a core component. The MLLM must be capable of receiving images and generating natural language output. CLIP-only methods (contrastive models without language generation) are **out of scope**.

2. **Industrial anomaly detection target** — The method is evaluated on or designed for industrial/manufacturing anomaly detection tasks (defect detection, quality inspection, anomaly segmentation on products/parts). Benchmarks include MVTec AD, MVTec LOCO-AD, VisA, MPDD, BTAD, Real-IAD, or similar industrial datasets.

### Boundary Cases

| Scenario | Included? | Reasoning |
|----------|-----------|-----------|
| Uses CLIP for zero-shot anomaly scoring (no language generation) | ❌ | CLIP is not a generative MLLM |
| Uses GPT-4V for anomaly reasoning on MVTec AD | ✅ | MLLM + industrial dataset |
| Uses LLaVA to explain detected defects | ✅ | Generative MLLM + industrial application |
| Anomaly synthesis guided by MLLM-generated descriptions | ✅ | MLLM-guided generation for IAD |
| Anomaly synthesis using diffusion + text prompts only (no MLLM) | ❌ | No generative MLLM involvement |
| General zero-shot CLIP method evaluated only on ImageNet OOD | ❌ | Not MLLM, not industrial AD |
| Training-free method using MLLM prompting on industrial images | ✅ | MLLM + industrial application |

---

## 2. Source Channels

Papers are collected through the following channels, prioritized in order:

### Tier 1: Primary Sources (Actively Monitored)
- **Top-venue proceedings:** CVPR, ICCV, ECCV, NeurIPS, ICLR, ICML, AAAI, IJCAI, ACM MM
- **arXiv cs.CV daily feed:** Filtered by keywords (see §3)
- **Semantic Scholar alerts:** Saved searches for key terms

### Tier 2: Secondary Sources (Periodically Checked)
- **Related awesome lists:** M-3LAB, mala-lab repos (monthly review)
- **Google Scholar citations:** Forward/backward citation tracking from seed papers
- **Conference workshop papers:** CVPR/ECCV anomaly detection workshops
- **Top journals:** TPAMI, IJCV, TIP, Information Fusion, Pattern Recognition

### Tier 3: Community Input
- **GitHub Issues:** Community-submitted papers
- **Pull Requests:** Contributor additions (reviewed against criteria)

---

## 3. Search Strategy

### Keyword Combinations

Papers are retrieved using boolean combinations of terms from two groups:

**Group A (MLLM terms):**
`multimodal large language model`, `MLLM`, `LVLM`, `GPT-4V`, `GPT-4o`, `LLaVA`, `InternVL`, `Qwen-VL`, `visual instruction tuning`, `multimodal reasoning`, `vision-language model`

**Group B (IAD terms):**
`anomaly detection`, `defect detection`, `anomaly segmentation`, `industrial inspection`, `quality inspection`, `MVTec`, `VisA`, `surface defect`, `manufacturing`, `industrial image`

**Query template:** `(Group A term) AND (Group B term)`

### Temporal Coverage
- **Retrospective:** All papers from 2023 onward (when CLIP-based IAD methods emerged)
- **Ongoing:** New papers checked weekly via arXiv alerts and conference proceedings

---

## 4. Inclusion Criteria

A paper is included if it passes **all** of the following checks:

| # | Criterion | Details |
|---|-----------|---------|
| 1 | **Scope match** | Satisfies both MLLM and IAD conditions from §1 |
| 2 | **Accessibility** | Public preprint or published paper available (arXiv, OpenReview, publisher) |
| 3 | **Venue quality** | Tier-1 venue, OR arXiv with ≥10 citations, OR arXiv from a recognized research group |
| 4 | **Technical contribution** | Introduces novel method, benchmark, or significant empirical insight (not just an application report) |
| 5 | **Recency** | Published 2023 or later (MLLM-era). Foundational pre-2023 papers included only if directly seminal |
| 6 | **Non-duplicate** | Not a minor revision of an already-listed paper (extended journal versions may replace conference versions) |

### Special Cases for arXiv Papers
arXiv papers without peer review are included if they meet **at least one** of:
- ≥10 citations on Semantic Scholar/Google Scholar
- From a well-known research group with track record in the field
- Introduces a new benchmark or dataset used by subsequent work
- Provides open-source code with reproducible results

---

## 5. Exclusion Criteria

Papers are excluded if **any** of the following apply:

- Method does not use a generative MLLM (CLIP-only methods, pure CNN/reconstruction methods are excluded)
- MLLM is used only as a frozen feature extractor without generating natural language output
- Evaluated only on non-industrial datasets (CIFAR, ImageNet OOD, surveillance videos)
- No publicly accessible paper (private/proprietary)
- Pure survey with no novel method (surveys are listed in a separate section)
- Workshop abstracts or extended abstracts without full technical content

---

## 6. Categorization Taxonomy

Papers are categorized into paradigms based on their **primary technical approach**:

```
MLLM-based IAD
├── 1. MLLM-based Detection & Reasoning
│   └── Methods using generative MLLMs for detection + explanation
│       Key signal: Uses LLaVA/InternVL/GPT-4V, generates text output
│       Includes fine-tuned and customized MLLM approaches
│
├── 2. Training-Free / Prompt-Only MLLM Methods
│   └── Methods requiring zero fine-tuning of MLLM, pure inference-time
│       Key signal: No training loop, in-context learning, MLLM prompt engineering
│
└── 3. Reinforcement Learning + MLLM
    └── Methods using RL to optimize MLLM reasoning for IAD
        Key signal: GRPO, PPO, reward models for detection quality
```

**Assignment rules:**
- If a paper spans multiple categories, assign to the **primary novelty**
- Cross-list in secondary category only if contribution is substantial in both
- If a new paradigm emerges with ≥3 papers, create a new category

---

## 7. Research Gap Identification

Research gaps listed in `README.md` are identified through:

1. **Systematic comparison:** Mapping what existing methods can/cannot do against industrial requirements
2. **Performance analysis:** Identifying dataset categories or metrics where all methods underperform
3. **Survey cross-referencing:** Synthesizing "future work" sections from recent surveys
4. **Community feedback:** Issues and discussions from the research community

Each gap is annotated with:
- **Difficulty** (⭐ to ⭐⭐⭐): Estimated research effort
- **Potential Impact** (🔥 to 🔥🔥🔥): Estimated value to the field

Gaps are revisited quarterly and updated as new papers address them.

---

## 8. Maintenance Schedule

| Activity | Frequency | Description |
|----------|-----------|-------------|
| arXiv scan | Weekly | Check new papers matching keyword filters |
| Conference proceedings | Per event | Bulk add papers from major conferences (CVPR, ICCV, NeurIPS, ICLR, etc.) |
| Related list sync | Monthly | Cross-check with M-3LAB, mala-lab, and other awesome lists |
| Gap reassessment | Quarterly | Update research gaps based on new publications |
| Link verification | Quarterly | Check all URLs for dead links using automated checker |
| Community PR review | Ongoing | Review and merge community contributions |

---

## 9. Quality Assurance

### For Each Paper Entry
- [ ] Title matches the official paper exactly
- [ ] Venue and year are correct (checked against proceedings/arXiv)
- [ ] Code link points to an active, official repository (not a fork)
- [ ] Dataset column lists all industrial datasets used for main evaluation
- [ ] Key contribution is accurate and ≤15 words
- [ ] Paradigm assignment is correct

### For the Overall List
- [ ] No duplicate entries
- [ ] Tables are sorted by year (descending) within each paradigm
- [ ] All sections have consistent formatting
- [ ] Related resources are up to date
- [ ] Star history badge URL is correct

---

## 10. Limitations & Biases

We acknowledge the following limitations in our curation:

- **Language bias:** Primarily English-language papers. Chinese-language papers from top CN venues (e.g., 中国计算机学会 CCF-A) may be underrepresented.
- **Recency bias:** Strong focus on 2024–2026 papers. Foundational 2023 work may be less exhaustively covered.
- **Venue bias:** Preference for top-tier venues may exclude innovative workshop papers.
- **Availability bias:** Papers without open-source code are still included but may receive less attention.
- **Maintainer expertise:** This list is maintained by researchers with specific backgrounds, which may introduce blind spots.

We actively work to mitigate these through community contributions and periodic comprehensive reviews.

---

## Changelog

| Date | Change |
|------|--------|
| 2026-03-12 | Scope pivot: VLM → MLLM focus. Removed CLIP-only methods from scope. Updated keywords, criteria, taxonomy. |
| 2026-03 | Initial methodology document created |

---

*This methodology is itself a living document. Suggestions for improvement are welcome via Issues or PRs.*
