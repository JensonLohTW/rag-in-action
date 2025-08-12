### 總覽
使用 `ContextualCompressionRetriever` 將「初檢索 + 壓縮/重排器」組合：先用 BM25 取回候選，再用 Cohere Rerank 作為壓縮器，僅保留與查詢最相關的片段，降低下游 LLM 的輸入負載。

### 流程圖
```mermaid
flowchart TD
  D[Documents] --> BM25[BM25 初檢索]
  Q[Query] --> BM25
  BM25 --> CCR[ContextualCompressionRetriever\n(base_compressor=CohereRerank)]
  CCR --> OUT[壓縮後的候選]
```

### 分步講解
- 候選取得：`BM25Retriever.from_documents(...).k=3`。
- 壓縮器：`CohereRerank(model="rerank-multilingual-v3.0")` 作為 `base_compressor`。
- 調用：`compression_retriever.invoke(query)` 返回精排且壓縮後的片段。

### 關鍵點總結
- **成本下降**：大幅減少 LLM 輸入長度。
- **易擴展**：可替換其他重排/摘要壓縮器。
- **工程提醒**：管理好 Cohere API Key；關注配額與費用。


