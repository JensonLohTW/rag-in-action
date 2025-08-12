### 總覽
將 `q2sql_pairs.json`（自然語言問題與對應 SQL 範例對）嵌入後存入 Milvus 的 `q2sql_knowledge` 集合，作為案例檢索樣本，幫助 LLM 在生成 SQL 時對齊語料風格與正確性。

### 流程圖
```mermaid
flowchart TD
  JSON[讀取 q2sql_pairs.json] --> EMB[OpenAIEmbeddingFunction]
  EMB --> SCHEMA[Collection: id/vector/question/sql_text]
  SCHEMA --> IDX[AUTOINDEX(COSINE)]
  IDX --> INS[insert 批量插入]
  INS --> DONE[Milvus: q2sql_knowledge]
```

### 分步講解
- 對每條 `question` 計算向量；保留原始 `sql_text`。
- 定義集合與索引，插入 `{question, sql_text, vector}`。

### 關鍵點總結
- **案例驅動**：檢索到相似問句與標準 SQL 能顯著降低幻覺與語法錯誤。
- **資料質量**：樣本越貼近真實查詢場景，效果越好。


