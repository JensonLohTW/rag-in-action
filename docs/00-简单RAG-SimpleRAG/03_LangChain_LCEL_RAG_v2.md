## 總覽

本文件對應：`00-简单RAG-SimpleRAG/03_LangChain_LCEL_RAG_v2.py`。

在 v1 基礎上，將 LLM 改為 DeepSeek（`ChatDeepSeek`），同時演示了各階段中間結果的打印，有助於教學與除錯。

---

## 流程圖

```mermaid
flowchart TD
  A[WebBaseLoader] --> B[TextSplitter]
  B --> C[OpenAIEmbeddings]
  C --> D[InMemoryVectorStore]
  D --> E[Retriever(k=3)]
  E --> F[LCEL: {context, question} | prompt | ChatDeepSeek | StrOutputParser]
  F --> G[演示各階段中間結果 & invoke(question)]
```

---

## 分步講解

- 差異點：`ChatDeepSeek(model="deepseek-chat", api_key=ENV)`。
- 教學性：列印檢索器輸出、合併文本、提示輸出、LLM 輸出、最終解析輸出。

---

## 關鍵點總結

- **可替換 LLM**：保留相同 LCEL 結構，替換模型即可。
- **可觀察**：中間態輸出便於學習與調參。


