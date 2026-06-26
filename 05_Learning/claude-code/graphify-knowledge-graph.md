---
created: 2026-06-17
last-modified: 2026-06-17
tags: [claude-code, graphify, knowledge-graph, codebase-analysis, tools]
status: in-progress
related: [[building-first-skill]], [[obsidian-vault-setup-principles]]
source: "Personal Discovery — hands-on session with TradingAgents codebase"
---

# Graphify — Codebase Knowledge Graph Tool

## What This Is
`/graphify` 是一個 Claude Code skill，把任何資料夾（程式碼、文件、圖片、影片）轉成一個可以查詢的知識圖譜。輸出是互動式 HTML、graph.json、還有 GRAPH_REPORT.md。

## Why It Matters
以前你看一個陌生的 codebase 需要自己一個一個讀檔案。有了 graphify，你能在幾分鐘內看到：
- 哪些函數是「God Nodes」（連接最多地方的核心）
- 哪些社群（communities）代表一個功能區域
- 意外的連結（跨模組的隱性依賴）

這就像是在進電影院之前先拿到一張場景結構圖。

## How It Works

### 整體流程（Pipeline）
```
1. 偵測檔案 (detect)
2. AST 結構提取（程式碼 → 函數/類/邊）
3. 語義提取（LLM subagents → 概念/關係）
4. 合併兩者 → graph
5. 分群 (cluster) → communities
6. 標記 communities → 人類可讀名稱
7. 輸出 HTML + JSON + 報告
```

### 快速開始
```bash
/graphify                        # 對當前資料夾建圖
/graphify <路徑>                  # 對特定資料夾
/graphify query "你的問題"        # 直接查詢已建好的圖
```

### 輸出位置
```
graphify-out/
├── graph.html        ← 在瀏覽器開，可互動
├── graph.json        ← 原始資料
├── GRAPH_REPORT.md   ← 文字報告（God Nodes, 驚喜連結, 建議問題）
└── cache/            ← 快取，下次更快
```

## My First Run — TradingAgents Codebase

**日期**: 2026-06-17  
**對象**: `TradingAgents-main by Yijia Xiao`（143個檔案，126個 .py）

### 結果數字
- **節點**: 1,527 個
- **邊**: 2,944 條
- **社群**: 109 個
- **AST 提取**: 1,447 節點 / 3,256 邊（自動，免費）
- **語意提取**: 265 節點 / 267 邊（6個 LLM subagents 並行）

### God Nodes（核心抽象）
| 節點 | 邊數 | 意義 |
|------|------|------|
| `TradingAgentsGraph` | 41 | 整個系統的入口點 |
| `make_log()` | 40 | 記憶系統核心 |
| `route_to_vendor()` | 38 | 所有資料來源的路由器 |
| `BaseLLMClient` | 36 | LLM 層的抽象基礎 |

### 驚喜發現
- `polymarket.py` 有一個**自我循環 import**（唯一的 import cycle）
- 評分詞彙（`parse_rating`）同時被記憶系統、信號處理器、研究員管理器、投資組合管理器共用 — 隱性耦合，看 code 很難發現
- 測試輔助函數 `_no_data()` 直接引用了 `NoMarketDataError`，測試與錯誤分類之間的耦合比看起來更深

## Key Concepts

### God Nodes
連邊最多的節點。這些是你**最不應該隨便改動**的函數/類。也是理解一個系統最快的入口。

### Communities（社群）
Graphify 用圖論演算法把節點自動分群。每群大概對應一個功能模組。標記名稱是 Claude 看節點內容後命名的。

### Cohesion Score
每個 community 的內聚力分數（0-1）。分數低表示這群節點其實沒那麼緊密 — 可能是人為的模組邊界，不是真實的邏輯邊界。

### 快取機制
第一次跑很慢（需要 LLM 提取語義）。之後用 `--update` 只重新提取改過的檔案。快取存在 `graphify-out/cache/`。

### EXTRACTED vs INFERRED vs AMBIGUOUS
每條邊都有信心標籤：
- **EXTRACTED** = 原始碼裡明確寫出來的關係（import, call）
- **INFERRED** = LLM 合理推斷的關係（共享資料結構、功能對齊）
- **AMBIGUOUS** = 不確定，標記等人工確認

## When to Use This
- **接觸新 codebase** — 建圖後先讀報告，再讀程式碼
- **debug 神秘 bug** — 用 `graphify query "bug 描述"` 找相關節點
- **重構前** — 確認哪些節點是核心，哪些 community 邊界不清晰
- **學習開源專案** — 先看架構再看細節

## Common Mistakes

- **對很大的資料夾跑** — 超過 500 個檔案或 200 萬字要先選子資料夾
- **忘記 `--update` 快取** — 每次重跑都重新提取很慢（用 `graphify-out/.graphify_root` 記住路徑）
- **把 graph.html 和 graph.json 一起 commit** — 這些是生成物，通常應該加入 `.gitignore`

## Related Concepts
[[building-first-skill]] — graphify 本身也是一個 skill，理解 skill 架構有助於理解它的觸發機制  
[[obsidian-vault-setup-principles]] — 知識圖譜的概念和 Obsidian 的連結思維是同一種模式

## Next Steps
- [ ] 對 Louis-Brain vault 本身跑 graphify（看自己的知識結構）
- [ ] 試 `graphify query "如何 X"` 查詢工作流程
- [ ] 探索 `--update` 增量更新
- [ ] 考慮在新 codebase 時把 graphify 作為第一步 SOP
