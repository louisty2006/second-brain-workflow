# /tool — 資源儲存點 deep search

---
name: /tool
description: 針對想解決的問題，從 04_Resources/ deep search 建議工具/知識（read-only）
implemented: yes
phase: 2
---

## How to Use
```
/tool <我想解決的問題>
```

## What it does
- 讀 04_Resources/index.md 鎖定相關分類，再讀相關分類檔 deep search。
- 理解問題意圖（非關鍵字配對），建議 1–N 個資源並說明「為什麼能幫你」+ 連結。
- 優先浮出 `未讀` 資源並標出。
- 沒合適資源就明說，不幻覺。
- **Read-only，絕不改 vault。**

`/brain` 判斷到用戶在找工具/資源時可委派呼叫 `/tool`。
Skill 本體：`~/.claude/skills/tool/SKILL.md`。
