---
created: 2026-06-17
last-modified: 2026-06-18
tags: [n8n, learning-track, overview, automation]
status: in-progress
---

# n8n — Learning Track Overview

## Goal
掌握 n8n workflow automation，作為建構 AI 驅動自動化系統的基礎技能。

### 3 個月目標
- 理解所有核心 node 類型
- 建立複雜的多步驟 workflows
- 學會 debug workflow 失敗
- 用「workflow 思維」而非 code 思維

### 6 個月目標
- n8n + Claude Code 混合 AI workflows
- 建立可重用 workflow templates
- 透過 n8n 理解 API 設計

## 待學的概念
- [ ] **Nodes & Connections** — Workflow 的基本構件
- [ ] **Data Flow** — 資料如何在 nodes 之間流動
- [ ] **HTTP Nodes** — API 互動
- [ ] **Webhook Nodes** — 從外部來源接收資料
- [ ] **Conditional Logic** — 讓 workflow 有智慧
- [ ] **Error Handling** — 失敗時怎麼辦
- [ ] **Variables & Expressions** — 處理資料
- [ ] **Integration Patterns** — 常見 workflow 結構

## 學習策略
從最少的 nodes 開始：**HTTP、Webhook、If、Merge**。
其他 nodes 都是這四個的變形。一旦理解資料流，新 nodes 就變簡單。

## 開放問題
- Webhook node 為什麼需要 test URL？
- 如何在不 deploy 的情況下測試 webhook？
- n8n 可以純本地跑嗎？

## 里程碑
- Week 1-2：理解基礎（nodes、connections、data flow）
- Week 3-4：建立第一個真實 workflow（email → Obsidian）
- Week 5-6：整合外部 APIs
- Week 7-8：結合 Claude Code 做 AI workflows

## Related Notes
（學習筆記會陸續在這個資料夾建立）
