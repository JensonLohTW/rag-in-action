### 總覽
使用 LlamaIndex 原生評測框架對兩種檢索策略（Sentence Window vs Base）進行對比：從 PDF 構建索引、準備評測數據集（QR pairs），並以 Correctness/Faithfulness/Relevancy/SemanticSimilarity 批量評分輸出結果表。

### 流程圖
```mermaid
flowchart TD
  PDF[讀入 PDF] --> PARSE[SentenceSplitter/WindowNodeParser]
  PARSE --> IDX1[VectorStoreIndex(nodes)]
  PARSE --> IDX2[VectorStoreIndex(base_nodes)]
  IDX1 --> QE1[SentenceWindow QueryEngine]
  IDX2 --> QE2[Base QueryEngine]
  GEN[QueryResponseDataset(load/generate)] --> BATCH[BatchEvalRunner]
  QE1 & QE2 & GEN --> EVAL[aevaluate_responses]
  EVAL --> DF[get_results_df]
```

### 分步講解
- 索引：同時構建 `SentenceWindow` 與 `Base` 兩種索引與查詢引擎。
- 數據：`QueryResponseDataset`（可由 `DatasetGenerator` 生成）提供問題與參考答案。
- 評測：配置四類 Evaluator，並對兩路引擎輸出批量評測、生成結果 DataFrame。

### 關鍵點總結
- **方法對比**：量化上下文窗口（窗口替換）對回答品質的提升幅度。
- **可擴展**：可替換文檔源、引擎參數與評測指標，形成 A/B 實驗。


