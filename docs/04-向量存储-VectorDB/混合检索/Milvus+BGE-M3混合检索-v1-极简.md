## 總覽

對應：`混合检索/Milvus+BGE-M3混合检索-v1-极简.py`。用 BGE-M3 生成稀疏+密集向量，建立 `SPARSE_INVERTED_INDEX` 與 `AUTOINDEX`，並用 `hybrid_search(WeightedRanker)` 進行混合檢索。

---

## 流程圖

```mermaid
flowchart TD
  A[讀 JSON → 構建 docs/metadata] --> B[BGEM3EmbeddingFunction → {dense,sparse}]
  B --> C[建 schema: sparse_vector + dense_vector]
  C --> D[create_index(SPARSE_INVERTED_INDEX, AUTOINDEX)]
  D --> E[insert 批次]
  E --> F[dense_req + sparse_req]
  F --> G[hybrid_search(WeightedRanker)]
```

---

## 關鍵點總結

- **權重融合**：以加權方式融合稀疏/密集結果。


