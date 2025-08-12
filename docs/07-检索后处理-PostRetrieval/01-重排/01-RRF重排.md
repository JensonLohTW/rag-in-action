### 總覽
RRF（Reciprocal Rank Fusion）用於融合「多查詢、多路檢索」的結果，最終以 1/(rank+k) 的方式累積各候選文檔的分數，得到更穩健的排序。此範例：對每個使用者問題先用 LLM 生成多個不同視角的查詢，逐一在向量庫檢索，最後以 RRF 做融合，展示 Top-N 結果。

### 流程圖
```mermaid
flowchart TD
  D[PDF/TXT 載入] --> S[RecursiveCharacterTextSplitter]
  S --> V[Chroma 向量庫]
  Q[原始問題] --> GQ[LLM 生成多視角查詢]
  GQ --> R1[逐查詢檢索]
  R1 --> F[RRF 融合 1/(rank+k)]
  F --> TOP[最終排序 TopK]
```

### 分步講解
- 文檔處理：讀取 `90-文档-Data/山西文旅` 下 PDF/TXT，分塊（300/50），入 Chroma。
- 多查詢生成：`ChatPromptTemplate` + `ChatDeepSeek` 生成 4 條不同角度子查詢。
- 檢索：對每條子查詢做向量檢索，得到多個候選列表。
- 融合：自實作 `reciprocal_rank_fusion(results, k=60)` 將多列表融合排序。

### 關鍵點總結
- **穩健性**：多視角查詢 + RRF 可顯著降低單一查詢偏差。
- **k 參數**：控制不同排名差距，常見經驗值 60，可視資料調整。
- **可搭配**：RRF 後可再接交叉編碼器或重排 API 進一步精排。


