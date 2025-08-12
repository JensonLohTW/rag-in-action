### 總覽
Self-RAG 流程在標準 RAG 的基礎上增加了「檢索質量評估、幻覺檢查、答案有效性評估」等環節，形成一個可自我糾偏與反覆試探的生成閉環。

### 流程圖
```mermaid
flowchart TD
  URLS[WebBaseLoader 多URL] --> SPLIT[tiktoken splitter 250]
  SPLIT --> V[Chroma + OpenAIEmbeddings]
  Q[問題] --> RET[retriever.invoke]
  RET --> GRD1[檢索文檔相關性評分\nGradeDocuments]
  GRD1 -->|過濾| CTX[相關文檔]
  CTX --> GEN[RAG 生成]
  GEN --> GRD2[幻覺評分\nGradeHallucinations]
  GRD2 -->|是| GRD3[答案是否解決問題\nGradeAnswer]
  GRD3 -->|是| END((完成))
  GRD3 -->|否| REW[重寫問題] --> RET
  GRD2 -->|否| GEN
```

### 分步講解
- 向量庫：網頁內容 → tiktoken 切分（250）→ Chroma(OpenAIEmbeddings)。
- 檢索評分：`ChatOpenAI.with_structured_output(GradeDocuments)` 過濾不相關文檔。
- 生成：`hub.pull("rlm/rag-prompt") | ChatOpenAI | StrOutputParser`。
- 幻覺評估：`GradeHallucinations` 判斷生成是否基於文檔；若否，回到生成重試。
- 答案評估：`GradeAnswer` 若不滿足需求，進入問題重寫 → 再檢索 → 再生成。
- 編排：以 `langgraph` 將節點與條件邊構成工作流，直觀可觀測。

### 關鍵點總結
- **可觀測/可糾偏**：在生成前後插入評分器，顯著降低幻覺與無效回答。
- **成本權衡**：多輪評估與重試會增加延時與花費，需結合 SLA 設置迭代次數。


