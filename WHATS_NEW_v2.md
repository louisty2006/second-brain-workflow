# Second Brain v2.0 — 新功能介紹

## 為什麼要做這個？Pain Point

你有沒有這個經歷：

在 YouTube 看到一個厲害的開源工具、在 Threads 刷到一個很有用的教程、在 IG 看到一個設計靈感——然後 **save 了**。

然後就沒有然後了。

這些資源躺在你的「已儲存」裡面，慢慢消失。你根本沒有時間去翻，也記不起 save 過什麼。需要解決某個問題的時候，明明你 save 過相關的資源，但你找不到它。

**Save 完石沉大海，是所有人的問題。**

---

## v2.0 如何解決

這個版本在 Second Brain 加入了**資源儲存點**——一個真正可以被查詢、被利用的知識庫。

### `/stash` — 把資源存進去

貼一條 URL 給 Claude，它會：

1. **自動抓取內容**：標題、詳細說明（不是一句話帶過，是「這是什麼、做什麼、解決什麼問題」）
2. **智慧分類**：自動判斷應該放哪個分類——`ui-ux-design`、`dev-tools`、`knowledge-tools`、`coding`……不會粗暴地全塞進「IT」
3. **格式化儲存**：用 Obsidian callout 格式，有狀態（未讀／學習中／已用），有來源和日期

```
/stash https://github.com/某個很厲害的工具
```

30 秒，這個資源就被整理好、有詳細說明、放在正確的分類，不再石沉大海。

---

### `/tool` — 需要的時候找出來

當你在解決一個問題，想知道「我的資源庫裡有什麼可以幫我」：

```
/tool 我想建一個有好看 UI 的 dashboard
/tool 有沒有工具可以幫我自動化這個流程
```

Claude 會 deep search 你的資源庫，找出真正相關的資源，解釋為什麼這個資源能幫到你——**而且會優先推薦你還沒看過的**，幫你消化那些被遺忘的收藏。

---

### `/brain` 的升級

`/brain` 原本是你問任何問題，Claude 從 Second Brain 的角度回答。

現在，如果 `/brain` 判斷你的問題本質上是在找工具或資源，它會自動呼叫 `/tool` 幫你搜尋資源庫。你不需要記得要不要用 `/tool`——brain 會判斷。

---

## 視覺效果

資源在 Obsidian 裡長這樣：

```
> [!info] [OpenKnowledge — AI-native 開源知識庫](https://...)
> `#PKM` `#open-source` `#ai-search` · 未讀
> 來源: Threads · 加入: 2026-06-26
>
> 一個剛開源的個人知識管理平台，定位是 Obsidian / Notion 的替代品。
> 核心是把 AI-native 搜尋整合進知識庫，讓筆記可以被 AI agent 直接查詢。
```

有 Properties 面板、有彩色 callout block，不是一堆雜亂的純文字。

---

## 未來方向

目前 `/stash` 需要在電腦上開 Claude Code 才能用——但現實是大部分有趣的資源都是**在手機上發現的**。

**v3.x 計劃：多 device 全連結**

目標是讓 Second Brain 不只是一個電腦工具，而是真正的跨裝置知識系統：

- 📱 **iOS Share Sheet**：在手機上直接「分享」任何 link 到 Second Brain，不需要打開 app
- ⚡ **iPhone Shortcut**：一鍵把網頁、YouTube、IG post 送進資源庫
- 📥 **Inbox 自動匯入**：把 link 寄到特定 email，自動被分類存進 vault
- 🔄 **iCloud / Git 同步**：手機和電腦的 vault 實時同步，在任何裝置上都能查詢

**最終目標**：不管你在哪裡、用什麼裝置發現了有用的東西，Second Brain 都能收到——然後在你需要的時候，幫你找出來。

---

## 快速上手

```bash
# 存一個資源
/stash https://你看到的連結

# 找資源解決問題
/tool 我想做的事情

# 問 brain（會自動決定要不要用 /tool）
/brain 我最近在學 n8n，有什麼資源可以參考
```

---

*Second Brain v2.0 — 讓你 save 過的東西真正被用上*
