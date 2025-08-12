## 總覽

對應：`15_LlamaParse_PDF no_Rerank.py`。以 `LlamaParse` 解析 → `MarkdownElementNodeParser` 節點化 → 構建 `VectorStoreIndex` 與兩種 Query Engine（raw/recursive），不啟用重排。

---

## 流程圖

```mermaid
flowchart TD
  A[LlamaParse → Documents(markdown)] --> B[MarkdownElementNodeParser → nodes]
  B --> C[VectorStoreIndex(text_nodes + index_nodes)]
  C --> D[raw_query_engine / recursive_query_engine]
  D --> E[query → 對比結果]
```

---

## 關鍵點總結

- **對照實驗**：不加重排觀察檢索與回答差異。


