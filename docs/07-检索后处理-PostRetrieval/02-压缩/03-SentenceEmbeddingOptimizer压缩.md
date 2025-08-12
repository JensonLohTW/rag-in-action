### 總覽
LlamaIndex 的 `SentenceEmbeddingOptimizer` 在檢索後對節點集合做「相似度裁剪」：可按百分位或閾值刪除相似度過低的句子節點，降低輸入長度並去噪。

### 流程圖
```mermaid
flowchart TD
  D[Documents] --> IDX[VectorStoreIndex]
  Q[Query] --> QE1[as_query_engine()]
  Q --> QE2[as_query_engine(node_postprocessors=SEO)]
  IDX --> QE1 & QE2
  QE2 --> OUT[優化後答案]
```

### 分步講解
- 構建：`VectorStoreIndex.from_documents(SimpleDirectoryReader(...).load_data())`。
- 不優化：普通 `query_engine` 直接回答。
- 優化：`SentenceEmbeddingOptimizer(percentile_cutoff=0.5)` 或 `threshold_cutoff=0.7` 作為後處理器。

### 關鍵點總結
- **兩種裁剪**：百分位裁剪保留排名前 X%；閾值裁剪保留相似度高於閾值的節點。
- **實務**：先觀測再裁剪，避免過度壓縮導致信息缺失。


