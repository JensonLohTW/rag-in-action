## 總覽

本文件對應：`00-简单RAG-SimpleRAG/05_RAG_from_Scratch_Ollama.py`。

與 Claude/DeepSeek 版本一致：SentenceTransformer 嵌入 + FAISS 檢索，生成端改為本地 Ollama（Python 客戶端）。

---

## 流程圖

```mermaid
flowchart TD
  A[原始文本] --> B[SentenceTransformer 向量化]
  B --> C[FAISS 建索引]
  C --> D[查詢向量化]
  D --> E[FAISS.search 取 Top-k]
  E --> F[構建提示]
  F --> G[ollama.chat(model=ENV OLLAMA_MODEL)]
  G --> H[print]
```

---

## 分步講解

- 生成端：`from ollama import chat`，以本地模型（由 `OLLAMA_MODEL` 指定）生成最終回答。

---

## 關鍵點總結

- **完全離線**：搭配本地嵌入可無網運行。
- **工程透明**：每一步可替換與觀察。


