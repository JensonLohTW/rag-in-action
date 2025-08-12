## 總覽

對應：`Milvus/a-working-sample.py`。端到端樣例：以 BGE 生成向量，設計欄位 Schema，建立自動索引，批量插入，再做語義檢索與條件查詢。

---

## 流程圖

```mermaid
flowchart TD
  A[準備資料 DataFrame] --> B[SentenceTransformerEmbeddingFunction → dim]
  B --> C[定義 FieldSchema 列表]
  C --> D[create_collection(schema)]
  D --> E[prepare_index_params(AUTOINDEX)]
  E --> F[create_index]
  F --> G[for row 生成 embedding + insert]
  G --> H[search(query_emb) / query(filter)]
```

---

## 關鍵點總結

- **AUTOINDEX**：讓 Milvus 自選索引策略，簡化調參。
- **實戰**：包含欄位設計、批量插入與查詢。


