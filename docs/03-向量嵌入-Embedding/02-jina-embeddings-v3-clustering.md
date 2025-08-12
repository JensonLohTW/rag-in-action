## 總覽

對應：`02-jina-embeddings-v3-clustering.py`。使用 Jina Embeddings API 對描述向量化，並用 `KMeans` 分群以觀察主題聚類。

---

## 流程圖

```mermaid
flowchart TD
  A[讀取 description.csv] --> B[POST /v1/embeddings (model=jina-embeddings-v3)]
  B --> C[embeddings ← data]
  C --> D[KMeans.fit_predict]
  D --> E[打印 Cluster 標籤與樣本]
```

---

## 關鍵點總結

- **聚類探索**：檢視描述語義分佈與主題。


