### 總覽
將 `db_description.yaml`（欄位級/表級語義描述）嵌入後寫入 Milvus 的 `dbdesc_knowledge` 集合。這些文字描述能補充 DDL 無法清楚表達的業務語義，提升 Text2SQL 的可解釋性與正確性。

### 流程圖
```mermaid
flowchart TD
  YAML[讀取 db_description.yaml] --> EXP[展平為 (table, column, desc)]
  EXP --> EMB[OpenAIEmbeddingFunction]
  EMB --> SCHEMA[Collection: id/vector/table_name/column_name/description]
  SCHEMA --> IDX[AUTOINDEX(COSINE)]
  IDX --> INS[insert]
  INS --> DONE[Milvus: dbdesc_knowledge]
```

### 分步講解
- 讀 YAML，展平成欄位級記錄清單。
- 以 OpenAI 向量化描述文本，插入集合。

### 關鍵點總結
- **集合名**：`dbdesc_knowledge`。
- **語義補充**：與 DDL 和 Q2SQL 共同構成 Text2SQL 的三類關鍵知識源。


