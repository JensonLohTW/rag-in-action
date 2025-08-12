### 總覽
ColBERT 採用「後期交互」策略：先分別對查詢與文檔做 token 級嵌入，查詢時只需編碼 Q，並在向量空間以 MaxSim 等操作進行精細匹配，平衡效率與精度，適合大規模檢索的重排/召回增強。

### 流程圖
```mermaid
flowchart TD
  Q[Query] --> EQ[Encoder→token embeddings]
  D[Documents] --> ED[Encoder→token embeddings(可預計算)]
  EQ & ED --> INT[後期交互 MaxSim/平均池化(示例)]
  INT --> S[相似度分數]
  S --> R[重排]
```

### 分步講解
- 模型：示例用 `bert-base-uncased`；實務建議用專門微調的 `colbertv2` 等。
- 編碼：保留所有 token 的 `last_hidden_state`，而非僅 [CLS]。
- 相似度：示例為平均池化近似，完整 ColBERT 使用 MaxSim 聚合。

### 關鍵點總結
- **可預計算**：文檔端預編碼，查詢時低延遲。
- **精細交互**：token 級匹配優於純句向量相似度。
- **實務建議**：使用原生 ColBERT 庫與索引器以獲得最佳性能。


