### 總覽
結合 `PyMuPDFReader` 讀取正文與 `camelot` 提取 PDF 表格，為每個表格建立 `PandasQueryEngine`，再以 LLM 生成表格摘要，與正文節點一起建索引並用 `RecursiveRetriever` 在命中表格節點時自動下鑽至對應的 `PandasQueryEngine`。

### 流程圖
```mermaid
flowchart TD
  PDF[PDF] --> TXT[PyMuPDFReader 文本]
  PDF --> TBL[camelot.read_pdf 抽表]
  TBL --> PQE[PandasQueryEngine per table]
  TBL --> SUM[LLM 生成表格摘要]
  TXT --> NODES[文本節點]
  SUM --> IN[IndexNode(pandas{i})]
  NODES & IN --> IDX[VectorStoreIndex]
  IDX --> RR[RecursiveRetriever(id→PQE)]
  Q[Query] --> RR --> A[回答]
```

### 分步講解
- 表格處理：`camelot.read_pdf(pages=...)` → 轉 DataFrame，建立 `PandasQueryEngine`。
- 摘要生成：將 `DataFrame.to_csv()` 餵給 LLM 生成一句話摘要，作為 `IndexNode` 文本。
- 召回與下鑽：檢索命中對應 `IndexNode` 時，`RecursiveRetriever` 轉交該表的 `PandasQueryEngine`。

### 關鍵點總結
- **多模態結構融合**：正文與表格各自最優處理路徑的整合。
- **路由清晰**：以 `index_id` 對齊查詢引擎，避免混淆。
- **注意**：表格解析易受版面影響，必要時校正表頭與欄位。


