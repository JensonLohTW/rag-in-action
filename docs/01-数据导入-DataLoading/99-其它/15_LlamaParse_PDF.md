## 總覽

對應：`15_LlamaParse_PDF.py`。在 `LlamaParse` + `MarkdownElementNodeParser` 基礎上，引入 `FlagEmbeddingReranker(BAAI/bge-reranker-large)` 提升檢索質量，對比 raw 與 recursive 兩種引擎。

---

## 流程圖

```mermaid
flowchart TD
  A[LlamaParse(markdown)] --> B[MarkdownElementNodeParser → nodes]
  B --> C[VectorStoreIndex(text_nodes + index_nodes)]
  C --> D[as_query_engine(node_postprocessors=[reranker])]
  D --> E[query → 回答 + 來源片段]
```

---

## 關鍵點總結

- **重排**：大幅提升檢索段落與問題的相似度。
- **工程建議**：視資料量與場景調整 `top_n`、`similarity_top_k`。


