## 總覽

對應：`03_LlamaIndex-分块大小影响准确性.py`。在 LlamaIndex 中通過 `SentenceSplitter(chunk_size, chunk_overlap)` 調整切塊大小，觀察檢索準確性變化。

---

## 流程圖

```mermaid
flowchart TD
  A[PDFReader.load_data] --> B[Settings.node_parser=SentenceSplitter(chunk_size,...)]
  B --> C[VectorStoreIndex.from_documents]
  C --> D[as_query_engine(similarity_top_k=3)]
  D --> E[query → 回答 + 檢索片段]
```

---

## 關鍵點總結

- **切塊影響**：塊太大會稀釋相似度，塊太小會丟失上下文；需在任務與模型之間折中。


