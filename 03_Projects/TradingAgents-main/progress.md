## 2026-06-26
- 完成 TradingAgents UI/流程強化：落地 3-round 辯論配置（investment + risk）。
- 實作 Sentiment 自適應雙階段策略（先短版、可用時再補充），並加入 hard fallback，避免 sentiment 單點失敗中止整體分析。
- 強化 OpenAI-compatible client 的 transient retry/backoff，降低 Poe 連線波動影響。
- 更新環境設定與範例：輸出語言改為繁體中文、補齊 FRED_API_KEY 與相關參數說明。
- 驗證多組單元測試通過；端到端仍受上游 Poe 不穩定影響，需持續觀察。

Blockers:
- Poe 端偶發 `APIConnectionError` / `RemoteProtocolError`，即使有重試仍可能拖慢或中斷完整 E2E run。
