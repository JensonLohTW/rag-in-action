## 總覽

對應：`06-01-llamaparser提取PDF表格.py`。以 `LlamaParse` 解析 PDF 並結合 LlamaIndex 節點/檢索器與重排，對財報類 PDF 問答。

---

## 流程圖

```mermaid
flowchart TD
  A[LlamaParse(result_type=markdown).load_data(PDF)] --> B[MarkdownElementNodeParser 拆節點]
  B --> C[VectorStoreIndex(text_nodes + index_nodes)]
  C --> D[QueryEngine(similarity_top_k, reranker=BAAI/bge-reranker-large)]
  D --> E[query → print 回答與來源]
```

---

## 關鍵點總結

- **表格友好**：LlamaParse 對複雜排版與表格重建表現較好。
- **重排加持**：引入重排器提升對齊度與可讀性。


