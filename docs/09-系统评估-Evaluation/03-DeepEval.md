### 總覽
以 DeepEval 定義單條 LLM 測試案例（TestCase），並度量 Contextual Precision 與 Answer Relevancy 兩項分數，形成極簡但實用的單元級評測。

### 流程圖
```mermaid
flowchart TD
  TC[LLMTestCase(input, actual_output, expected_output, retrieval_context)] --> M1[ContextualPrecisionMetric.measure]
  TC --> M2[AnswerRelevancyMetric.measure]
  M1 & M2 --> S[score]
```

### 分步講解
- 測試案例：包括輸入、實際輸出、期望輸出與檢索上下文。
- 指標：
  - Contextual Precision：回答是否嚴格基於檢索上下文。
  - Answer Relevancy：回答與問題的相關性。
- 輸出：兩個分數便於快速比較不同實作或 prompt 的變更影響。

### 關鍵點總結
- **輕量化**：適合在 CI 中做冒煙測或回歸對比。
- **可擴充**：DeepEval 還提供更多指標與 Dataset 支援，可逐步引入。


