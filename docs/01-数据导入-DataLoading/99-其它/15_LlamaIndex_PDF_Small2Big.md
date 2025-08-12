## 總覽

對應：`15_LlamaIndex_PDF_Small2Big.py`。LlamaIndex：`PDFReader` + `SentenceWindowNodeParser` 構建「句窗」節點，並用 `MetadataReplacementPostProcessor` 回填上下文窗口，提升回答可讀性。

---

## 流程圖

```mermaid
flowchart TD
  A[PDFReader.load_data] --> B[SentenceWindowNodeParser(window=3)]
  B --> C[VectorStoreIndex(nodes)]
  C --> D[as_query_engine(similarity_top_k=3, MetadataReplacementPostProcessor)]
  D --> E[query → 回答 + window]
```

---

## 關鍵點總結

- **句窗技巧**：提供鄰近句上下文，提升與表格/段落的對齊度。


