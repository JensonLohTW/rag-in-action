## 總覽

對應：`05-LlamaIndex-语义分块.py`。使用 `SemanticSplitterNodeParser` 基於嵌入相似度自動決定切分邊界，並與 `SentenceSplitter` 對照。

---

## 流程圖

```mermaid
flowchart TD
  A[SimpleDirectoryReader.load_data(txt)] --> B[SemanticSplitter(buffer, percentile, embed_model)]
  B --> C[get_nodes_from_documents → semantic_nodes]
  A --> D[SentenceSplitter → base_nodes]
  C --> E[print 統計與內容]
  D --> E
```

---

## 關鍵點總結

- **語義分段**：自動對齊語意轉折處，常比固定長度更自然。
- **參數含義**：`buffer_size` 控制比較粒度；`breakpoint_percentile_threshold` 控制斷點嚴格度。


