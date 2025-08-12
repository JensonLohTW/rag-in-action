## 總覽

本文件對應：`00-简单RAG-SimpleRAG/01_03_LlamaIndex_更换兼容OPENAI API的模型`。

示例透過 LlamaIndex 的 `Settings.llm` 與 `Settings.embed_model`，將 LLM 與嵌入模型切換到「OpenAI 相容」的第三方 API（自定義 `api_base` + `api_key`）。流程保持不變：讀取文檔 → 構建索引 → 問答引擎 → 檢索增強生成 → 輸出。

---

## 流程圖

```mermaid
flowchart TD
  A[啟動腳本] --> B[設定 Settings.llm/Settings.embed_model（自定義 api_base & api_key）]
  B --> C[SimpleDirectoryReader 載入本地檔]
  C --> D[VectorStoreIndex.from_documents(documents)]
  D --> E[index.as_query_engine()]
  E --> F[query(問題)]
  F --> G[檢索 Top-k]
  G --> H[LLM 生成回答]
  H --> I[print 輸出]
```

---

## 分步講解

- 自定義 API 端點
  - 設定 `Settings.llm = OpenAI(model, api_key, api_base)` 與 `Settings.embed_model = OpenAIEmbedding(model, api_key, api_base)`。
  - 之後建立索引與查詢都會使用這些全域設定。

- 讀取與索引
  - `SimpleDirectoryReader(...).load_data()` 讀取文本為 `Document` 列表。
  - `VectorStoreIndex.from_documents(documents)` 對文本分塊並嵌入向量，寫入內建向量庫。

- 查詢與生成
  - `index.as_query_engine()` 構建檢索 + 生成引擎。
  - `query_engine.query(question)` 相似度檢索後交由第三方相容的 OpenAI 介面生成。

---

## 關鍵點總結

- **相容 API**：以自定義 `api_base`/`api_key` 切換至第三方 OpenAI 相容服務。
- **全域設定**：`Settings.llm`、`Settings.embed_model` 影響後續索引與查詢。
- **主流程不變**：載入 → 索引 → 檢索 → 生成 → 輸出。


