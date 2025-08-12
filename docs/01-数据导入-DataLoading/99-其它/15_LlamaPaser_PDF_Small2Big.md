## 總覽

對應：`15_LlamaPaser_PDF_Small2Big.py`。結合 `LlamaParse` 與 `SentenceWindowNodeParser` 的「小到大」策略：先以句窗建立豐富上下文，再以節點索引/檢索問答。

---

## 流程圖

```mermaid
flowchart TD
  A[LlamaParse(markdown)] --> B[SentenceWindowNodeParser(window=3)]
  B --> C[VectorStoreIndex(nodes)]
  C --> D[as_query_engine(similarity_top_k=3)]
  D --> E[query → 回答 + window]
```

---

## 關鍵點總結

- **上下文完整**：句窗保留前後語境，增強可讀性與準確性。


