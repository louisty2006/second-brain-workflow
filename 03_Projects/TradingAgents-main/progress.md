## 2026-06-26
重大里程碑：完成 MVP v1.0 並 push 上 GitHub（公開 repo `louisty2006/SU28-Trade-agent`，tag `mvp-v1.0`）。

上午（流程強化）：
- 落地辯論配置與 Sentiment 自適應雙階段（先短版、可用時補充）+ hard fallback。
- 強化 OpenAI-compatible client transient retry/backoff。
- 報告輸出改繁體中文，更新 .env / .env.example。

下午（修 bug + 選 model + 出版）：
- SSL 修復：新增 `dataflows/http_utils.py` 用 certifi CA bundle，修好 macOS `CERTIFICATE_VERIFY_FAILED`（reddit/stocktwits）。pyproject 加 certifi。
- 混合 LLM 架構：default_config + trading_graph 支援 per-model provider/backend_url（deep/quick 可用不同 provider）。
- Sentiment freetext-first 開關（`TRADINGAGENTS_SENTIMENT_FREETEXT_FIRST`），跳過 structured 加速。
- 辯論輪數改 1（debate + risk）。
- app.py 加每步「預計 vs 實際時間 + ETA」顯示。
- LLM 選型結論：OpenRouter 免費 model 撞 429（Market Analyst tool-call 階段必掛）；最終採 **全 Poe 一條龍**：quick=`gpt-4o-mini`、deep=`claude-haiku-4.5`。零 429、tool-call 驗證 OK。
- 成功 E2E：LYFT 長線分析 192s 跑完 7/7 步，成本約 $0.05–0.15/檔。
- 撰寫 MVP_v1.0.md（setup + LLM 注意事項 + 成本）、重寫精簡 README（含 model 選擇表 + token/成本預測）。
- 確認 .env（真實 key）未被 commit，repo 無洩漏個人資料。

Blockers:
- 無重大阻塞。FRED_API_KEY 未設（長線 macro 數據會 skip，非必要）。
- 註記：OpenRouter 免費 model 不適用於 tool-calling 工作流，已棄用。
