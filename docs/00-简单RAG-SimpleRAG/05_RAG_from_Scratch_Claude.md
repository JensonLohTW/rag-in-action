## 總覽

本文件對應：`00-简单RAG-SimpleRAG/05_RAG_from_Scratch_Claude.py`。

示例「從零實作」RAG：
1) 以 `sentence-transformers` 生成文本與查詢向量；
2) 使用 FAISS 建立向量索引並檢索 Top-k；
3) 將檢索到的片段拼接入提示，交由 Claude API 生成答案。

---

## 流程圖

```mermaid
flowchart TD
  A[準備原始文本列表] --> B[SentenceTransformer.encode → 文檔向量]
  B --> C[FAISS IndexFlatL2.add]
  C --> D[encode 問題 → 查詢向量]
  D --> E[FAISS.search(k=3) → 取 Top-k 片段]
  E --> F[構建提示串接上下文]
  F --> G[Claude API 生成]
  G --> H[print]
```

---

## 分步講解

- 嵌入：`SentenceTransformer('all-MiniLM-L6-v2')`。
- 索引：`faiss.IndexFlatL2(dimension)`，小型示例適用。
- 生成：`anthropic.Anthropic(...).messages.create(model="claude-3-5-sonnet-20241022")`。

---

## 關鍵點總結

- **可控透明**：顯式管理每一步，便於理解與替換。
- **可移植**：可替換為任何嵌入與生成模型實作。


