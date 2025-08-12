## 總覽

本文件對應：`00-简单RAG-SimpleRAG/03_LangChain_LCEL_RAG_v1.py`。

示例用 LCEL（LangChain Expression Language）構建 RAG 管道：向量檢索 → 提示 → OpenAI Chat → 文字解析。

---

## 流程圖

```mermaid
flowchart TD
  A[WebBaseLoader] --> B[TextSplitter]
  B --> C[OpenAIEmbeddings]
  C --> D[InMemoryVectorStore]
  D --> E[vectorstore.as_retriever(k=3)]
  E --> F[組裝 LCEL 鏈: {context, question} | prompt | ChatOpenAI | StrOutputParser]
  F --> G[invoke(question) → print]
```

---

## 分步講解

- LCEL 鏈：
  - `{"context": retriever | merge, "question": RunnablePassthrough()}`
  - `| prompt | llm | StrOutputParser()`

---

## 關鍵點總結

- **可觀察性**：可在每一步插入 debug/打印查看輸入輸出。
- **模組化**：檢索、提示、LLM、解析四段清晰解耦。


