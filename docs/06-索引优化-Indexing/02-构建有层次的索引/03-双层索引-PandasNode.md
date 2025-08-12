### 總覽
以 LlamaIndex 的 `PandasQueryEngine` + `IndexNode` + `RecursiveRetriever` 實現「向量路由 → 表格引擎下鑽」：用向量索引命中表格摘要節點，再根據 `index_id` 路由到對應的 `PandasQueryEngine` 直接在 DataFrame 上作業，提升精確問答能力。

### 流程圖
```mermaid
flowchart TD
  XLS[Excel sheets] --> DF[to_string → Document]
  DF --> VIDX[VectorStoreIndex]
  XLS --> PQE[PandasQueryEngine per sheet]
  SUM[為每表生成摘要 IndexNode(pandas{i})] --> VIDX
  MAP[index_id → PQE] --> RR[RecursiveRetriever]
  Q[Query] --> RR --> R[命中 IndexNode 時下鑽 PQE]
  R --> A[答案]
```

### 分步講解
- 準備：為每個 sheet 生成 `Document` 與 `IndexNode(summary, index_id=pandas{i})`。
- 向量檢索：`VectorStoreIndex(documents + df_nodes)` → `as_retriever(k=1)`。
- 遞歸檢索：`RecursiveRetriever("vector", retriever_dict={...}, query_engine_dict={index_id: engine})`。
- 問答：`RetrieverQueryEngine.from_args(recursive_retriever, response_mode="compact")`。

### 關鍵點總結
- **專項路由**：表格問題以結構化引擎解決，優於單純文本生成。
- **擴展性**：可混入更多類型引擎（SQL、Graph），由 IndexNode 負責路由。


