## 總覽

對應：`Milvus/create_milvus_db.py`。以 BGE-M3 建 SNOMED 例子：讀 CSV → 生成嵌入 → 建集合與 AUTOINDEX → 分批插入 → 語義檢索與條件查詢。

---

## 流程圖

```mermaid
flowchart TD
  A[讀取 CSV] --> B[SentenceTransformerEmbeddingFunction(bge-m3)]
  B --> C[取樣獲 dim → 定義 FieldSchema]
  C --> D[create_collection]
  D --> E[prepare_index_params(AUTOINDEX, COSINE)]
  E --> F[create_index]
  F --> G[for batch 生成向量 + insert]
  G --> H[search(query_emb, output_fields)]
  G --> I[query(filter, output_fields)]
```

---

## 關鍵點總結

- **批處理**：大資料批次切片處理，避免 OOM。
- **欄位設計**：針對醫學概念保留多維 metadata。


