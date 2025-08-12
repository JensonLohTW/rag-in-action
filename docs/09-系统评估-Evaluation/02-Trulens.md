### 總覽
使用 TruLens 對 RAG 應用進行可觀測與評估：通過 `@instrument` 標記檢索與生成步驟，並以 Feedback 函數評估 Groundedness、Answer Relevance、Context Relevance，最後生成 leaderboard 結果。

### 流程圖
```mermaid
flowchart TD
  VEC[Chroma 向量庫] --> RET[RAG.retrieve]
  RET --> GEN[RAG.generate_completion]
  Q[Query] --> RET
  RET & GEN --> APP[TruApp(app, feedbacks)]
  APP --> RUN[with TruApp as recording]
  RUN --> LB[TruSession.get_leaderboard]
```

### 分步講解
- 可觀測：以 `@instrument` 裝飾 `retrieve/generate/query`，自動記錄輸入輸出與執行訊息。
- Provider：`TruLensOpenAI(gpt-4)` 作為評估裁判（以 CoT 理由計分）。
- 指標：
  - Groundedness：答案是否基於檢索上下文（on retrieve.rets and on_output）。
  - Answer Relevance：答案與問題是否相關（on_input 和 on_output）。
  - Context Relevance：檢索到的每個上下文是否與問題相關，並聚合平均。
- 看板：`TruSession(database_redact_keys=True)` 初始化並 `get_leaderboard()` 查看平均分。

### 關鍵點總結
- **鏈路可見**：可回放每次 query 的完整調用鏈與分數。
- **對比實驗**：適合比較不同提示/模型/檢索策略版本的效果差異。


