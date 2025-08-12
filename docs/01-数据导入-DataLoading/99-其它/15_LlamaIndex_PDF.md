## 總覽

對應：`15_LlamaIndex_PDF.py`。用 `PDFReader` 直接讀入 → `VectorStoreIndex.from_documents` → `as_query_engine` 問答，並打印檢索片段。

---

## 流程圖

```mermaid
flowchart TD
  A[PDFReader.load_data] --> B[VectorStoreIndex.from_documents]
  B --> C[as_query_engine(similarity_top_k=3)]
  C --> D[query → 回答]
  D --> E[print 檢索片段]
```

---

## 關鍵點總結

- **標準管線**：最小 LlamaIndex PDF 問答流程。


