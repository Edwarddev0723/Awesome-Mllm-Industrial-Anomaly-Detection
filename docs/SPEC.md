# Spec: Awesome MLLM Industrial Anomaly Detection — Repo 建置規格書

## 專案概述

建立一個 GitHub awesome list repo，聚焦在 **MLLM (Multimodal Large Language Model) × Industrial Anomaly Detection** 的交叉領域。
與現有 awesome list 的差異化定位：M-3LAB 做通用工業 AD，mala-lab 做通用 Foundation Model AD，
**本 repo 專注 MLLM（能接收影像並生成自然語言輸出的大型多模態模型）在工業場景的應用**，提供 paradigm-level 分類、研究缺口標註、雙語支援。

---

## Repo 結構

```
awesome-mllm-industrial-anomaly-detection/
├── README.md                  # 主文件：paper list + taxonomy + gaps
├── CONTRIBUTING.md            # PR 規則 & 投稿格式
├── methodology.md             # Paper selection 方法論
├── LICENSE                    # MIT License
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── add-paper.md       # Issue template: 推薦論文
│   │   └── report-error.md    # Issue template: 回報錯誤
│   └── PULL_REQUEST_TEMPLATE.md  # PR template
└── assets/
    ├── taxonomy.png           # 分類架構圖（手動製作 or Mermaid 轉圖）
    └── banner.png             # Repo banner（選用）
```

### 關鍵設計原則

1. **純靜態內容** — 不推爬蟲、不推可執行程式碼。Repo 內容僅有 `.md` 檔 + 圖片
2. **單人可維護** — 所有更新只需編輯 README.md，不需 build pipeline
3. **社群友善** — Issue/PR template 讓貢獻者容易參與

---

## 可以用 Vibe Coding Agent 完成嗎？

**可以，而且非常適合。** 以下是建議的 agent 工作流：

### Phase 1: Repo 骨架（Agent 直接完成）✅

| 任務 | Agent 可行性 | 說明 |
|------|-------------|------|
| 產生 README.md | ✅ 完全可行 | 本 spec 已提供完整版本 |
| 產生 CONTRIBUTING.md | ✅ 完全可行 | 本 spec 已提供完整版本 |
| 產生 methodology.md | ✅ 完全可行 | 本 spec 已提供完整版本 |
| 產生 LICENSE (MIT) | ✅ 完全可行 | 標準模板 |
| 產生 .github/ templates | ✅ 完全可行 | 標準 GitHub template |
| 初始化 git repo + push | ✅ 完全可行 | `git init` + `gh repo create` |

### Phase 2: 圖片資產（需要人工 or 輔助工具）⚠️

| 任務 | Agent 可行性 | 建議做法 |
|------|-------------|----------|
| taxonomy.png 分類圖 | ⚠️ 半自動 | Agent 產生 Mermaid code → 你用 mermaid.live 轉 PNG |
| banner.png | ❌ 需人工 | 用 Canva / Figma 簡單製作，或不放 |

### Phase 3: Paper List 擴充（Agent 高效輔助）✅

| 任務 | Agent 可行性 | 說明 |
|------|-------------|------|
| 搜尋新論文並格式化 | ✅ 完全可行 | 給 agent 關鍵字，自動搜尋 + 格式化成 table row |
| 驗證 code link 存活 | ✅ 完全可行 | Agent 可以 fetch URL 確認 200 |
| 分類到正確 paradigm | ✅ 完全可行 | Agent 讀 abstract 判斷分類 |
| 更新 research gaps | ⚠️ 需審核 | Agent 產出草稿，你做最終判斷 |

### 建議 Agent Prompt（給 Claude Code 或類似工具）

```
你是一個研究助理，負責維護 awesome-vlm-industrial-anomaly-detection repo。

任務：搜尋最近一個月的新論文，符合以下條件：
1. 使用 VLM/MLLM（CLIP, LLaVA, InternVL 等）
2. 應用於工業異常偵測（MVTec AD, VisA 等 dataset）
3. 發表在 CVPR/ICCV/ECCV/NeurIPS/ICLR/ICML/AAAI/IJCAI 或 arXiv

輸出格式：
| Paper Title | VENUE | YEAR | [code](URL) or — | Backbone | Dataset(s) | Key contribution (≤15 words) |

分類規則：
- CLIP alignment → Section 1
- MLLM reasoning → Section 2
- Text-guided synthesis → Section 3
- Training-free → Section 4
- RL-based → Section 5
```

---

## GitHub Repo 設定建議

| 設定項 | 建議值 |
|--------|--------|
| Repo name | `awesome-mllm-industrial-anomaly-detection` |
| Visibility | Public |
| License | MIT |
| Topics | `awesome-list`, `anomaly-detection`, `mllm`, `industrial-inspection`, `multimodal`, `llava`, `zero-shot`, `computer-vision` |
| Description | A curated list of MLLM approaches for industrial anomaly detection |
| Default branch | `main` |
| Branch protection | Optional: require PR review for `main` |

---

## 啟動 Checklist

- [ ] 用 agent 產生三個 .md 檔（已完成 ✅）
- [ ] 建立 GitHub repo
- [ ] Push README.md, CONTRIBUTING.md, methodology.md, LICENSE
- [ ] 建立 .github/ templates
- [ ] 製作 taxonomy.png（Mermaid → PNG）
- [ ] 設定 repo topics & description
- [ ] 提交到 [awesome list](https://github.com/sindresorhus/awesome) 審核（選用，需滿足其嚴格標準）
- [ ] 在相關社群分享（Twitter/X, Reddit r/MachineLearning, PTT ML 版）
- [ ] 設定月度維護 reminder

---

## 後續維護 SOP

1. **每週**：用 agent 搜尋新 arXiv 論文 → 格式化 → PR 到自己的 repo
2. **每月**：cross-check M-3LAB 和 mala-lab 的更新
3. **每季**：重新評估 research gaps，更新 methodology.md changelog
4. **每次大會後**：bulk add 該會議的相關論文（CVPR June, ICCV Oct, NeurIPS Dec, ICLR May, AAAI Feb）

---

## 預估時間

| 階段 | 時間 | 備註 |
|------|------|------|
| Phase 1: 骨架 + push | 30 min | 大部分已由 agent 完成 |
| Phase 2: 圖片 | 30 min | Mermaid 轉 PNG + optional banner |
| Phase 3: 首次擴充 | 1-2 hr | 用 agent 搜尋 + 人工審核 20-30 篇 |
| **Total MVP** | **~2.5 hr** | |

---

*Spec created: 2026-03-12*
