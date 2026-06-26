# VibeCode Translator — Progress

macOS menu bar app。highlight 任何 code → Shift+Cmd+E → 用 AI 解釋給非工程師聽。
Tech stack: Python, rumps, AppKit, pynput, Quartz, Anthropic/OpenAI SDK。
Folder: `/Users/lautinyam/Documents/VibeCode Translator`

**MVP 完成：2026-06-23** ✅

---

## 2026-06-23

**今日完成：**

*穩定性（上午）*
- Settings 視窗死機修復：blocking run loop 與 rumps 衝突 → 非阻塞式視窗
- Shift+Cmd+E：pynput 大小寫/cmd/shift 左右鍵匹配修復
- `CGEventCreateKeyboardEvent` 改用 Quartz
- 無限觸發 + pasteboard race → cooldown + Lock

*功能與 UX（下午）*
- `providers.py`：12 個 AI provider（含 OpenRouter、Ollama 等）
- 預設語言 English；可選 Model 欄位覆寫 provider 預設 model
- Settings：NSWindow + EditableTextField + Edit 選單，原生 copy/paste
- Modal save/cancel、啟動順序、Model 欄位焦點等 bug 修復
- Accessibility 引導與 `AXIsProcessTrusted` 檢測；Homebrew Python.app 授權後快捷鍵正常

**目前狀態：** App 可啟動、Settings 可貼上 API Key / Model、Cmd+Shift+E 可用。OpenRouter + 自訂 model 已可設定。

**目前狀態：** App 可啟動、Settings 可貼上 API Key / Model、Cmd+Shift+E 可用。OpenRouter + 自訂 model 已可設定。

**Blockers：**
- ~~無 git（純本地開發），版本控制待建立~~ → 已解決（見下方收工段）

---

## 2026-06-23（續）

**晚段修復：**
- `show_bubble` 主執行緒排程：`performSelectorOnMainThread_` 無法包 closure → 改用 `NSOperationQueue.mainQueue().addOperationWithBlock_()`，bubble 成功出現
- `_CloseDelegate` 重複定義 crash：class 定義在 `_show()` 內，每次呼叫都重新 define ObjC class → 移至 module 頂層，delegate reference 改用 `_close_delegates` dict 保活
- `NSPanel.hidesOnDeactivate` bug：bubble 在用戶點回 editor 時自動消失 → 加 `win.setHidesOnDeactivate_(False)`，bubble 現在浮著不消失直到手動關閉
- NSWindowWillCloseNotification debug instrumenting（已完成診斷，可移除）

**目前狀態：** Bubble 可正常顯示、停留、手動關閉。繁體中文與英文翻譯均測試成功。

---

## 2026-06-23（收工）

**改名 + 開源上線：**
- 全專案更名 VibeCode Reader → **VibeCode Translator**（`main.py`、`bubble.py`、`providers.py`、設定路徑）
- 設定檔遷移：`~/.vibecode_reader_settings.json` → `~/.vibecode_translator_settings.json`（向下相容）
- 撰寫詳細繁中 README（安裝、設定、12 Provider、macOS 權限、FAQ）
- 新增 `.gitignore`（保護 API Key 設定檔）
- Git 初始化 + 推送 GitHub：https://github.com/louisty2006/VibeCode_Translator

**目前狀態：** MVP 完成並開源。App 可啟動、快捷鍵可用、雙語翻譯正常、repo 已上線。

**Blockers：** 無


---

## 2026-06-24

**今日完成：MVP2.1 — 打包 app hotkey 修復**

整天解同一問題：`Cmd+Ctrl+E` CLI 正常，`.app` 完全無反應。

走過三個方向：
- `pynput (CGEventTap)` → 需 Accessibility，ad-hoc 簽名每次 rebuild 讓 TCC 授權失效 ❌
- `NSEvent.addGlobalMonitorForEventsMatchingMask` → 同樣需 Accessibility，根本相同 ❌
  - 過程中修了三個 app 死機：runModal 阻塞主線程、runloop 前註冊、Python GC 清 handler
  - 診斷 log 確認 `accessibility=False` → 換方向
- `Carbon RegisterEventHotKey via ctypes` → 免 Accessibility ✅
  - 撞 3 次 SIGSEGV：ctypes ARM64 64-bit 指標截斷
  - 每次靠 crash report 暫存器值定位截斷點

**最終架構：** Hotkey 偵測用 Carbon（免 Accessibility）；文字擷取用 Cmd+C 模擬，首次缺權限時引導開啟。

**版本：** 2.1.0，branch `mvp2-carbon-hotkey`，新增 DEVLOG.md

**Blockers：** 無


**收工補記（2026-06-24 晚）：**
- Ponytail review 後清理：移除 `_log()` debug 函數及所有 8 個 call sites（-26 行）
- `_HotKeyID`、`_EventTypeSpec`、`_HANDLER_T` 移至 module 頂層
- DEVLOG.md 改為中英雙語
- 最新 commit: `ea45c34`，branch: `mvp2-carbon-hotkey`

**今日最終狀態：** MVP2.1 完成，code 乾淨。
