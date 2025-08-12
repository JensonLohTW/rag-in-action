## 總覽

本文件對應：`00-简单RAG-SimpleRAG/99_Testing.py`。

該腳本演示如何將 LlamaIndex 的 LLM 與嵌入模型切換到自定義 OpenAI 相容 API，並跑通最小 5 步流程：讀取 → 建索引 → 問答引擎 → 提問 → 輸出。

---

## 流程圖

```mermaid
flowchart TD
  A[配置 Settings.llm & Settings.embed_model (api_base, api_key, model)] --> B[讀取本地文檔]
  B --> C[VectorStoreIndex.from_documents]
  C --> D[index.as_query_engine]
  D --> E[query(問題)]
  E --> F[檢索 Top-k + 生成]
  F --> G[print 回答]
```

---

## 分步講解

- 以代碼方式配置全域 `Settings.llm` 與 `Settings.embed_model`，無需依賴環境變數。
- `try/except` 包裹讀檔，增強健壯性。
- 流程輸出提示（正在構建索引、引擎已創建等）便於排錯。

---

## 關鍵點總結

- **相容 API**：可切換到任意 OpenAI 相容供應商。
- **教學友好**：加入狀態輸出，易於理解與除錯。


