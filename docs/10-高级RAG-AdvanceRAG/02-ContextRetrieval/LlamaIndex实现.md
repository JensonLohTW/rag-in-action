### 總覽
基於 LlamaIndex 實作 Contextual Retrieval：為每個文本塊生成「上下文描述/擴寫」版本，並與常規（原始塊）檢索做對比；同時支持 Embedding、BM25、以及融合後經 CohereRerank 的混合檢索，最後用 `RetrieverEvaluator` 評估 MRR/HitRate。

### 流程圖
```mermaid
flowchart TD
  DOC[原文檔] --> SPLIT[SentenceSplitter]
  SPLIT --> NODES[原始節點]
  NODES --> CTX[生成 contextualized nodes\nmetadata.generated_context]
  NODES --> IDX1[Embedding/BM25 檢索器]
  CTX --> IDX2[Contextual Embedding/BM25 檢索器]
  IDX1 & IDX2 --> RERANK[CohereRerank 可選]
  QA[EmbeddingQAFinetuneDataset] --> EVAL[RetrieverEvaluator(mrr/hit_rate)]
  RERANK --> EVAL
```

### 分步講解
- 節點構建：`SentenceSplitter(256/50)` 產生 `nodes`；基於原文模擬 `generated_context` 並複製到 `metadata` 形成 `nodes_contextual`。
- 檢索器組合：Embedding、BM25、Hybrid(Embedding+BM25+Rerank) 各對應 contextual 與非 contextual 雙版本。
- 評估：以 `EmbeddingQAFinetuneDataset` 構造 QA 數據，`RetrieverEvaluator.from_metric_names(["mrr","hit_rate"])` 非同步評分。

### 關鍵點總結
- **上下文填充**：緩解切塊語義孤立；常帶來 MRR/HitRate 提升。
- **混合檢索**：關鍵詞與語義互補，再配重排更穩健。
- **健壯性**：對節點過少時做 top_k 調整與樣本節點補齊，避免評測失效。


