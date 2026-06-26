# Session Handoff — Progress & Context Memory

**Last Updated**: 2026-06-24
**Session Status**: VibeCode Translator MVP2.1 complete ✅ (on branch, not yet released)

## Active Project This Session

**`VibeCode Translator`** — `/Users/lautinyam/Documents/VibeCode Translator/`

macOS menu bar app：選取程式碼 → `Cmd+Ctrl+E` → AI 解釋，bubble 顯示結果。今日專注解決打包 `.app` 後全域快捷鍵完全失效的問題。

## What Was Completed (2026-06-24)

### 核心問題
`Cmd+Ctrl+E` 在 CLI（`./run.sh`）下正常，打包成 `.app` 後完全無反應。根因是 ad-hoc 簽名每次 rebuild 都換 binary hash，TCC 把 app 當新程式 → Accessibility 授權名存實亡。

### 三個方向，最終解法
1. **pynput (CGEventTap)** — 需 Accessibility，ad-hoc 簽名下授權失效 ❌
2. **NSEvent.addGlobalMonitorForEventsMatchingMask** — 同樣問題；過程中修了 3 個 app 死機 bug（runModal 阻塞、runloop 前註冊、Python GC 清 handler）；診斷 log 確認 `accessibility=False` ❌
3. **Carbon `RegisterEventHotKey` via ctypes** — 完全免 Accessibility ✅
   - 撞 3 次 ARM64 SIGSEGV：ctypes 64-bit 指標截斷（`restype` 預設 `c_int`、CDLL 每次取屬性是新 object、未設 `argtypes`）
   - 靠 crash report 暫存器值逐個定位截斷點

### 最終架構（MVP2.1）
- **Hotkey 偵測**：Carbon API（免 Accessibility）
- **文字擷取**：Cmd+C 模擬（首次缺權限時彈提示 + 自動開系統設定）
- **版本**：2.1.0
- **Branch**：`mvp2-carbon-hotkey`（已推 GitHub，最新 commit `ea45c34`）
- **DEVLOG.md**：完整 debug 歷程（中英雙語 + ASCII 流程圖）

### 收工清理（Ponytail review）
- 移除 `_log()` debug 函數及 8 個 call sites（-26 行）
- `_HotKeyID`、`_EventTypeSpec`、`_HANDLER_T` 移至 module 頂層
- Code 乾淨，無 blockers

## Open Items

- **尚未 merge / release**：`mvp2-carbon-hotkey` 還在 feature branch；GitHub 最新 release 仍是 **2.0.2**（hotkey 在打包版仍壞）
- **CHANGELOG** 尚無 2.1.0 條目
- 英文 README 仍未撰寫（repo 目前以繁中為主）

## Suggested Focus for Next Session

1. **Merge + release 2.1.0** — merge `mvp2-carbon-hotkey` → `main`，跑 `./release.sh 2.1.0`，讓同事下載的 `.app` 快捷鍵真正可用
2. **Smoke test 打包版** — `./build_app.sh` 後從 `dist/` 啟動，確認 hotkey + Cmd+C 擷取 + bubble 全流程
3. **英文 README**（可選）— 提高 GitHub 曝光，或先寫 2.1.0 release notes 說明 hotkey 修復

## Critical Files
- `app.py` — Carbon hotkey 實作 + Cmd+C 文字擷取
- `DEVLOG.md` — 完整 debug 歷程（下次遇到 ctypes/ARM64 問題先看這裡）
- `build_app.sh` / `release.sh` — 打包與發布流程
- `Louis-Brain/03_Projects/VibeCode Translator/progress.md` — 專案進度紀錄
