## 總覽

本文件對應：`00-简单RAG-SimpleRAG/04_LangGraph_RAG.py` 與 `04_LangGraph_RAG.ipynb`（筆記本邏輯相近）。

示例利用 LangGraph 將 RAG 流程拆分為檢索與生成兩個節點，嵌入採用 HF（BGE），生成使用 `ChatOpenAI(gpt-4)` 或其他可替換模型。

---

## 流程圖

```mermaid
flowchart TD
  A[WebBaseLoader] --> B[TextSplitter]
  B --> C[HF Embeddings]
  C --> D[InMemoryVectorStore]
  D --> E[StateGraph(State)]
  E --> F[retrieve(state)]
  F --> G[generate(state): ChatOpenAI]
  G --> H[graph.invoke({question}) → answer]
```

---

## 分步講解

- 狀態：`State{question, context, answer}`。
- 提示：從 LangChain Hub 拉取 `rlm/rag-prompt` 作為標準 RAG 提示。
- 生成：示例中以 `ChatOpenAI(model="gpt-4")`，亦可替換為 DeepSeek/Ollama。

---

## 關鍵點總結

- **可組合**：RAG 以節點組合，易於擴展（如重排、評估節點）。
- **模型可替換**：生成端可按需更換為本地或雲端模型。


