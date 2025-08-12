## 總覽

本文件對應：`00-简单RAG-SimpleRAG/04_LangGraph_RAG_Ollama.py`。

示例用 LangGraph 定義狀態機式 RAG：檢索節點 → 生成節點；嵌入使用 HF（BGE），生成使用 `ChatOllama` 本地推理。

---

## 流程圖

```mermaid
flowchart TD
  A[WebBaseLoader] --> B[TextSplitter]
  B --> C[HF Embeddings]
  C --> D[InMemoryVectorStore]
  D --> E[StateGraph(State)]
  E --> F[retrieve(state): similarity_search]
  F --> G[generate(state): ChatOllama(messages)]
  G --> H[graph.invoke({question}) → answer]
```

---

## 分步講解

- 狀態定義：`TypedDict State{question, context, answer}`。
- 檢索步：`vector_store.similarity_search()` 將結果放入 `context`。
- 生成步：格式化提示，`ChatOllama(model=ENV OLLAMA_MODEL)` 生成文本。
- 圖編譯：`StateGraph(State).add_sequence([retrieve, generate]).compile()`。

---

## 關鍵點總結

- **可視化與編排**：用流程圖方式表達 RAG 節點。
- **本地化**：HF 向量 + Ollama 生成，離線友好。


