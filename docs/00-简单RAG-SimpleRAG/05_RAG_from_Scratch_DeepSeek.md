## 總覽

本文件對應：`00-简单RAG-SimpleRAG/05_RAG_from_Scratch_DeepSeek.py`。

與 Claude 版本相同思路：SentenceTransformer 嵌入 + FAISS 檢索，唯生成端改為 DeepSeek（OpenAI 相容 SDK）。

---

## 流程圖

```mermaid
flowchart TD
  A[原始文本] --> B[SentenceTransformer 向量化]
  B --> C[FAISS 建索引]
  C --> D[查詢向量化]
  D --> E[FAISS.search 取 Top-k]
  E --> F[構建提示]
  F --> G[OpenAI(client=DeepSeek) chat.completions]
  G --> H[print]
```

---

## 分步講解

- 生成端：`OpenAI(api_key=ENV DEEPSEEK_API_KEY, base_url=https://api.deepseek.com/v1)` → `chat.completions.create(model="deepseek-chat", ...)`。

---

## 關鍵點總結

- **相容協議**：以 OpenAI SDK 調用 DeepSeek。
- **替換容易**：只需切換最終生成步驟。


