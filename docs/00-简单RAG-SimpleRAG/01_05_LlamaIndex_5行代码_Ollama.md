## 總覽

本文件對應：`00-简单RAG-SimpleRAG/01_05_LlamaIndex_5行代码_Ollama.py`。

示例使用 HuggingFace 中文嵌入模型 `BAAI/bge-small-zh` 進行本地嵌入，並以 Ollama 本地 LLM（如 `qwen:7b`）生成答案，無需雲端 API 金鑰。

---

## 流程圖

```mermaid
flowchart TD
  A[啟動腳本] --> B[load_dotenv 載入 OLLAMA_MODEL]
  B --> C[初始化 HF 嵌入 BAAI/bge-small-zh]
  C --> D[初始化 Ollama LLM]
  D --> E[讀取本地檔 SimpleDirectoryReader]
  E --> F[VectorStoreIndex.from_documents(documents, embed_model)]
  F --> G[index.as_query_engine(llm=llm)]
  G --> H[query(問題) → 檢索 Top-k]
  H --> I[Ollama 生成回答]
  I --> J[print 輸出]
```

---

## 分步講解

- 本地嵌入：`HuggingFaceEmbedding("BAAI/bge-small-zh")` 對文本向量化。
- 本地生成：`Ollama(model=os.getenv("OLLAMA_MODEL"))` 使用本地模型推理。
- 問答流程：載入文本 → 構建索引 → 檢索 → 生成 → 輸出。

---

## 關鍵點總結

- **離線友好**：嵌入與生成皆可本地完成。
- **可替換性**：更換 `OLLAMA_MODEL` 即可切換不同本地模型。
- **一致流程**：與其他 LlamaIndex 例子流程一致，便於對比學習。


