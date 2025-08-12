## 總覽

本文件對應：`00-简单RAG-SimpleRAG/02_03_LangChain_OpenAI_Model.py`。

以 OpenAI 的 `OpenAIEmbeddings` + `ChatOpenAI(gpt-3.5-turbo)` 完成最小 RAG：抓取 → 分塊 → 嵌入 → 內存向量庫 → 檢索 → 生成。

---

## 流程圖

```mermaid
flowchart TD
  A[WebBaseLoader] --> B[TextSplitter]
  B --> C[OpenAIEmbeddings]
  C --> D[InMemoryVectorStore]
  D --> E[similarity_search]
  E --> F[ChatPromptTemplate]
  F --> G[ChatOpenAI(gpt-3.5-turbo)]
  G --> H[print(answer.content)]
```

---

## 分步講解

- 嵌入：`OpenAIEmbeddings()`；生成：`ChatOpenAI(model="gpt-3.5-turbo")`。
- 其餘處理（抓取、分塊、檢索、提示）與其他 LangChain 例子相同。

---

## 關鍵點總結

- **官方路徑**：完全基於 OpenAI 產品棧。
- **替換容易**：後續可切換至 DeepSeek/Ollama/HF 以對比效果與成本。


