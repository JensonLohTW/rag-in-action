### 總覽
CRAG（Corrective RAG）在傳統 RAG 上加入「檢索質量評估 + 自動校正」：若本地檢索文檔經 LLM 評分為不相關，則觸發「重寫查詢 → 網路搜索 → 再生成」的補救支路，顯著降低錯檢索導致的幻覺。

### 流程圖
```mermaid
flowchart TD
  WEBL[WebBaseLoader] --> SPLIT[RecursiveCharacterTextSplitter(tiktoken 250)]
  SPLIT --> V[Chroma + OpenAIEmbeddings]
  V --> RETR[retriever]
  Q[問題] --> RETR --> DOCS[候選文檔]
  DOCS --> GRADER[LLM 結構化評分 yes/no]
  GRADER -->|有相關| GEN[RAG 生成]
  GRADER -->|皆不相關| REW[LLM 重寫查詢] --> TAV[Tavily 搜索] --> MERGE[合併至 documents] --> GEN
```

### 分步講解
- 構建基礎檢索：網頁加載 → 分塊（tiktoken 250）→ Chroma + OpenAIEmbeddings → `retriever`。
- 文檔評分：`ChatOpenAI.with_structured_output(GradeDocuments)`，提示明確標準，輸出 `yes/no`。
- 生成鏈：`hub.pull("rlm/rag-prompt") | ChatOpenAI | StrOutputParser`。
- 補救分支：`question_rewriter`（gpt-4o）重寫後，用 `TavilySearchResults` 補充外部資訊再生成。
- 圖編排：以 `langgraph` 組成 `retrieve → grade → (generate | transform_query → web_search → generate)`。

### 關鍵點總結
- **自我糾錯**：檢索品質差時自動改寫與外搜，提升可靠性。
- **類狀態機**：用狀態圖清晰表達決策與數據流，易擴展觀測。
- **代價**：增加一次或多次 LLM 調用與外網請求，需平衡成本/延遲。


