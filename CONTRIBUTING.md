# Contributing to Awesome MLLM Industrial Anomaly Detection

Thank you for your interest in contributing! This document outlines the guidelines for submitting papers, fixing errors, and improving this resource.

---

## Scope

This list covers **Multimodal Large Language Model (MLLM) approaches** applied to **industrial anomaly detection**. MLLMs are defined as models that receive images and generate natural language output (e.g., LLaVA, InternVL, GPT-4V, Qwen-VL). Contributions must fall within this intersection.

**In scope:**
- Papers using LLaVA, InternVL, GPT-4V, Qwen-VL, or similar generative MLLMs for industrial anomaly detection/segmentation/reasoning
- MLLM-guided anomaly synthesis methods targeting industrial domains
- Benchmarks and datasets designed for evaluating MLLMs on industrial AD tasks
- Surveys covering MLLM × IAD topics

**Out of scope:**
- CLIP-only anomaly detection (contrastive models without language generation)
- General anomaly detection without MLLM involvement (e.g., pure CNN reconstruction methods)
- MLLM papers unrelated to anomaly detection (e.g., VQA, captioning)
- Video anomaly detection in surveillance (unless directly applicable to industrial settings)
- Time-series or tabular anomaly detection

---

## How to Contribute

### 1. Adding a Paper

**Step 1:** Fork this repository and create a branch:
```bash
git checkout -b add/paper-shortname-year
```

**Step 2:** Add the paper in the correct paradigm section of `README.md`. Use this format:

For **MLLM-based** tables:
```markdown
| Paper Title | VENUE | YEAR | [code](URL) | Base MLLM | Dataset(s) | One-line key contribution |
```

For **Training-Free / RL** tables:
```markdown
| Paper Title | VENUE | YEAR | [code](URL) | Base MLLM | One-line key contribution |
```

**Formatting rules:**
- Paper title: Use the exact title from the paper (no abbreviation)
- Venue: Use official abbreviation (CVPR, ICLR, NeurIPS, AAAI, arXiv, etc.)
- Year: Publication year (not submission year)
- Code: Link to official repo. Use `—` if no code is available
- Key contribution: ≤15 words, focus on what's novel

**Step 3:** Submit a Pull Request with:
- PR title: `[Paper] Author2025 - Short Description`
- PR body: Fill in the template (auto-populated)

### 2. Fixing Errors

If you find incorrect links, wrong venue/year, or typos:

```bash
git checkout -b fix/description-of-fix
```

Submit a PR with title: `[Fix] Description of correction`

### 3. Suggesting a New Paradigm Category

If you believe a paper doesn't fit existing categories, open an **Issue** first:
- Title: `[Category] Proposed: Category Name`
- Body: Explain why existing categories don't cover this approach, provide ≥3 example papers

### 4. Updating Research Gaps

Research gaps in `README.md` are living annotations. To update:
- If a gap has been addressed by new work → submit a PR noting the paper and reducing impact rating
- If you identify a new gap → open an Issue with literature evidence

---

## PR Review Criteria

All PRs will be reviewed against these criteria:

| Criterion | Requirement |
|-----------|-------------|
| **Relevance** | Paper must use a generative MLLM (not CLIP-only) for industrial AD |
| **Venue quality** | Peer-reviewed preferred (CVPR, ICCV, ECCV, NeurIPS, ICLR, ICML, AAAI, IJCAI, ACM MM, or top journals). arXiv accepted if ≥10 citations or from a recognized lab |
| **Completeness** | All table columns filled (use `—` for unavailable info) |
| **Accuracy** | Links verified, venue/year correct |
| **Formatting** | Follows the exact table format of the section |
| **No duplicates** | Paper not already listed |

---

## Commit Message Convention

```
[Paper] Add AnomalyGPT (AAAI 2024) to MLLM-based section
[Fix] Correct AnomalyCLIP code link
[Dataset] Add Real-IAD to established datasets
[Category] Add RL+VLM paradigm section
[Meta] Update methodology.md with new selection criteria
[Docs] Fix typo in CONTRIBUTING.md
```

---

## Code of Conduct

- Be respectful and constructive in issues and PR discussions
- Do not submit self-promotional content without genuine relevance
- Credit original authors — always link to the official paper and code
- When in doubt about scope, open an issue to discuss before submitting a PR

---

## What NOT to Submit

- ❌ Crawler scripts, data scraping code, or automation tools
- ❌ Executable code of any kind (this repo is markdown + images only)
- ❌ Papers without public preprints (i.e., no accessible PDF)
- ❌ Duplicate entries already covered in the list
- ❌ Marketing materials or product announcements

---

## Questions?

Open an issue with the `[Question]` tag, and we'll respond as soon as possible.

Thank you for helping build this resource for the MLLM × IAD research community! 🙏
