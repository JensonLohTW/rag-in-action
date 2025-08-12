## 總覽

對應：`混合检索/Milvus+BGE-M3混合检索-v3-重排.py`。在混合檢索基礎上，加入 RRF 重排（或 WeightedRanker）作為融合策略變體，對比稀疏/密集/混合效果。

---

## 流程圖

```mermaid
flowchart TD
  A[準備 docs/向量] --> B[建 schema + index]
  B --> C[插入批次]
  C --> D[dense_req + sparse_req]
  D --> E[hybrid_search(RRFRanker or WeightedRanker)]
  E --> F[輸出對比結果]
```

---

## 關鍵點總結

- **融合策略**：RRF 對排序列穩健，Weighted 可按場景調權重。


