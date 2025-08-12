### 總覽
將 `ddl_statements.yaml` 讀入並以 OpenAI 嵌入生成向量，建庫至 Milvus 的 `ddl_knowledge` 集合，供 Text2SQL 檢索時使用（基於結構定義的語義召回）。

### 流程圖
```mermaid
flowchart TD
  YAML[讀取 ddl_statements.yaml] --> EMB[OpenAIEmbeddingFunction]
  EMB --> SCHEMA[定義 Collection: id/vector/table_name/ddl_text]
  SCHEMA --> IDX[AUTOINDEX(COSINE)]
  IDX --> INS[insert 逐條插入]
  INS --> DONE[Milvus: ddl_knowledge]
```

### 分步講解
- 以 `model.dense.OpenAIEmbeddingFunction('text-embedding-3-large')` 計算文本向量。
- 動態計算 `vector_dim`，定義集合 schema 與索引。
- 將 `{table_name, ddl_text, vector}` 批量插入。

### 關鍵點總結
- **集合名**：`ddl_knowledge`。
- **索引**：`AUTOINDEX + COSINE`，適配 OpenAI 向量。
- **一致性**：DDL 文本應與當前線上資料庫版本對齊。


