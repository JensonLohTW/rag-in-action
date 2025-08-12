## 總覽

對應：`04-02-pdfplumber提取PDF表格并问答.py`。流程：提取表格 → 轉為 `Document` → 構建 `VectorStoreIndex` → 問答。

---

## 流程圖

```mermaid
flowchart TD
  A[pdfplumber.extract_table(s)] --> B[for table → DataFrame]
  B --> C[df.to_string → LlamaIndex Document]
  C --> D[VectorStoreIndex.from_documents]
  D --> E[index.as_query_engine → query]
```

---

## 關鍵點總結

- **表格即文本**：先轉文本後索引，簡單有效；可再配合表格結構化引擎優化。


