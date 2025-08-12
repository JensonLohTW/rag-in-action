## 總覽

對應：`04-使用LlamaParser.py`。用 `LlamaParse` 將 PDF 解析為 Markdown，並透過 `MarkdownElementNodeParser` 拆分為節點。

---

## 流程圖

```mermaid
flowchart TD
  A[LlamaParse(result_type=markdown).load_data(PDF)] --> B[Documents]
  B --> C[MarkdownElementNodeParser.get_nodes_from_documents]
  C --> D[nodes]
  D --> E[print 節點]
```

---

## 關鍵點總結

- **結構化輸出**：Markdown 有利於節點拆分與層級理解。
- **前置**：需 `LLAMA_CLOUD_API_KEY`。


