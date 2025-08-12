## 總覽

本文件對應：`00-简单RAG-SimpleRAG/02_02_LangChain_DeepSeek_Model_v2.py`。

與 v1 類似，但生成模型改用 `ChatOpenAI` 並指定 `base_url=https://api.deepseek.com/v1`，以 OpenAI 相容協議調用 DeepSeek。

---

## 流程圖

```mermaid
flowchart TD
  A[WebBaseLoader] --> B[TextSplitter]
  B --> C[HF Embeddings]
  C --> D[InMemoryVectorStore]
  D --> E[similarity_search]
  E --> F[ChatPromptTemplate]
  F --> G[ChatOpenAI(base_url=DeepSeek) 生成]
  G --> H[print]
```

---

## 分步講解

- 主要差異：`ChatOpenAI(model="deepseek-reasoner", base_url=..., api_key=ENV)`。
- 其餘流程（抓取、分塊、嵌入、檢索、提示）與 v1 保持一致。

---

## 關鍵點總結

- **相容協議**：透過 OpenAI 標準介面使用 DeepSeek。
- **可移植性**：僅替換 LLM 實例，其他模組不變。


