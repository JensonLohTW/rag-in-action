## 總覽

本文件對應：`00-简单RAG-SimpleRAG/03_LangChain_LCEL_RAG_v3.py`。

在 v1 基礎上，將 LLM 改為 `ChatDeepSeek`（或其他），其餘流程保持不變：抓取 → 分塊 → 嵌入（OpenAIEmbeddings）→ 內存向量庫 → 檢索 → LCEL 鏈。

---

## 流程圖

```mermaid
flowchart TD
  A[WebBaseLoader] --> B[TextSplitter]
  B --> C[OpenAIEmbeddings]
  C --> D[InMemoryVectorStore]
  D --> E[Retriever(k=3)]
  E --> F[LCEL: {context, question} | prompt | ChatDeepSeek | StrOutputParser]
  F --> G[invoke(question)]
```

---

## 分步講解

- 生成模型：`ChatDeepSeek(model="deepseek-chat")`。
- 其他步驟與 v1 類似：重點仍是 LCEL 的模組化與可替換性。

---

## 關鍵點總結

- **靈活性**：LLM/Embeddings/向量庫皆可替換。
- **模式一致**：維持相同 LCEL 拼裝方式，便於教學對比。


