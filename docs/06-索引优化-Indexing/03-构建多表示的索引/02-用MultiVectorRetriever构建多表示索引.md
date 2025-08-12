### 總覽
利用 `MultiVectorRetriever` 為同一原文檔建立多個向量表示（如多段摘要），以 `id_key` 將多向量與原文關聯，檢索時先命中摘要向量，再從 `ByteStore` 取回對應原文，提升效率與覆蓋。

### 流程圖
```mermaid
flowchart TD
  WEB[WebBaseLoader] --> DOCS[Documents]
  DOCS --> SUM[LLM 批量摘要]
  SUM --> SDOCS[Summary Documents(doc_id)]
  SDOCS --> VEC[Chroma 向量庫]
  DOCS --> STORE[InMemoryByteStore(doc_id->原文)]
  VEC & STORE --> MVR[MultiVectorRetriever(id_key=doc_id)]
  Q[Query] --> MVR --> OUT[相關原文(經 doc_id 映射)]
```

### 分步講解
- 摘要生成：`ChatDeepSeek` 對 `docs` 逐份總結（`chain.batch`）。
- 多向量入庫：將 `summary_docs` 加入 `Chroma`；原文以 `doc_id` 存於 `ByteStore`。
- 檢索：`retriever.get_relevant_documents(query, n_results=1)` 返回與摘要綁定的原文。

### 關鍵點總結
- **多表示優勢**：對長文可建立多段摘要、標題、關鍵詞等多視角向量。
- **存取一致性**：確保 `id_key` 一致，避免摘要與原文錯綁。
- **擴展**：可對單文檔建立多語種表示以增強跨語檢索。


