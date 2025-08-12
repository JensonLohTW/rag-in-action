## 總覽

對應：`04-BGE-M3.py`。演示 BGE-M3 同時輸出密集、稀疏與多向量（ColBERT）嵌入，便於後續混合檢索與多向量匹配。

---

## 流程圖

```mermaid
flowchart TD
  A[BGEM3FlagModel("BAAI/bge-m3")] --> B[encode(passage, return_dense/sparse/colbert)]
  B --> C[dense_vecs]
  B --> D[sparse lexical_weights]
  B --> E[colbert_vecs]
  C --> F[print 維度/示例]
  D --> F
  E --> F
```

---

## 關鍵點總結

- **多表徵**：一套模型同時支持多種檢索表徵，靈活組合。


