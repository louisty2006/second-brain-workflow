# 04_Resources — 網絡資源儲存點

收集從 YouTube / IG / Threads / GitHub / 文章等餵養進來的 link，智慧分類，避免石沉大海。
用 `/stash` 存、`/tool` 反向搜尋建議。

## 結構
```
04_Resources/
  index.md            ← 總覽：所有分類 + 數量 + 最後更新
  knowledge-tools.md
  coding.md
  ui-ux-design.md
  design.md
  dev-tools.md
  ...（分類隨需要有機新增，不預先全建）
```

## 分類規則
- Claude 依內容判斷分類，新主題就新建分類檔並在 index.md 登記。
- **禁止粗暴歸成「coding」或「IT」大筐。** 細分，例如：
  前端 UI 套件 → `ui-ux-design`；CLI/開發工具 → `dev-tools`；設計靈感 → `design`；
  PKM/知識管理 → `knowledge-tools`；framework/語言/演算法 → `coding`。

## 分類檔 frontmatter（每個分類檔頂部一次，不在每條 entry 重複）
```
---
tags: [resources, <分類名>]
created: YYYY-MM-DD
last-modified: YYYY-MM-DD
---
```

## Entry 格式（Obsidian callout，append-only，遵守 cow.md）
```
> [!info] [標題](url)
> `#子標籤` `#子標籤` · 未讀
> 來源: GitHub · 加入: YYYY-MM-DD
>
> 詳細說明（2–5句）：是什麼、做什麼、解決什麼問題、重點特性/適用場景。
> 寫到日後 /tool 搜尋時光看這段就知道能不能幫到忙。
```
- 狀態詞：`未讀 / 學習中 / 已用 / 已歸檔`，新加入預設 `未讀`。
- 永不覆寫；重複 link 提示已存在。有關聯的既有 note 用 `[[wikilink]]` 連起來。
- 每條 entry 之間空一行。

## index.md 格式
```
# 資源儲存點

| 分類 | 數量 | 最後更新 |
|------|------|----------|
| [knowledge-tools](knowledge-tools.md) | 1 | 2026-06-26 |
```
