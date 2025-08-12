## 總覽

本文件對應：`00-简单RAG-SimpleRAG/02_05_LangChain_Ollama_Model.py`。

示例：抓取 → 分塊 → HF 嵌入 → 內存向量庫 → 檢索 → `ChatOllama` 本地生成。

---

## 流程圖

```mermaid
flowchart TD
  A[WebBaseLoader] --> B[TextSplitter]
  B --> C[HF Embeddings]
  C --> D[InMemoryVectorStore]
  D --> E[similarity_search]
  E --> F[ChatPromptTemplate]
  F --> G[ChatOllama 生成]
  G --> H[print(answer.content)]
```

---

## 分步講解

- 本地生成：`ChatOllama(model=ENV OLLAMA_MODEL)` 與本地 Ollama 伺服器對接。
- 其餘與 02 系列一致：抓取 → 分塊 → 嵌入 → 檢索 → 提示。

---

## 關鍵點總結

- **離線生成**：不依賴雲端 LLM。
- **靈活切換**：透過環境變數選擇不同本地模型。


