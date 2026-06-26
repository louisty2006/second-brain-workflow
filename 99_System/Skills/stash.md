# /stash — 網絡資源儲存點

---
name: /stash
description: 把網絡資源 link 存進 04_Resources/ 並智慧分類
implemented: yes
phase: 2
---

## How to Use
```
/stash <貼上一條或多條 URL>
/stash <url> --note "一句簡介"
/stash <url> --cat dev-tools
```

## What it does
- 對每條 URL 試 WebFetch 抓標題 + 生成一句摘要 + 判斷來源。
- 抓不到（IG/Threads 常擋）→ 保留 link，問用戶簡介，沒給就標 `#待補`。
- 智慧分類後 append 到 `04_Resources/<分類>.md`，新分類就新建並更新 index.md。
- 禁止粗暴歸成「coding / IT」大筐；細分到 ui-ux-design / dev-tools / design 等。
- 結尾回報每條去了哪個分類。

詳見 `04_Resources/instructions.md`。Skill 本體：`~/.claude/skills/stash/SKILL.md`。
