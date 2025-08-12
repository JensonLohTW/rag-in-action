### 總覽
使用 `LlamaParse` 將 PDF 解析為 Markdown，配合 `MarkdownElementNodeParser` 生成「文本節點 + 結構化索引節點」，同時構建 raw 與 recursive 兩種索引，疊加 `FlagEmbeddingReranker` 進行重排，對比檢索效果。

### 流程圖
```mermaid
flowchart TD
  PDF[PDF] --> LP[LlamaParse → Markdown]
  LP --> MNP[MarkdownElementNodeParser]
  MNP --> TN[text_nodes] & IN[index_nodes]
  TN & IN --> RIDX[VectorStoreIndex (recursive)]
  LP --> RIDX2[VectorStoreIndex (raw)]
  RER[FlagEmbeddingReranker] --> RIDX & RIDX2
  Q[Query] --> QE1[raw_query_engine] & QE2[recursive_query_engine]
```

### 分步講解
- 解析：`LlamaParse(result_type="markdown").load_data(...)`。
- 節點化：`MarkdownElementNodeParser(...).get_nodes_from_documents` → `get_nodes_and_objects`。
- 構建索引：`recursive_index`（text+index nodes）與 `raw_index`（原文）。
- 重排：`FlagEmbeddingReranker(model=BAAI/bge-reranker-large, top_n=5)`。
- 查詢：比較兩種引擎在相同問題下檢索與回答差異。

### 關鍵點總結
- **結構理解**：IndexNode 對章節/表格等結構敏感，便於精準路由。
- **重排收益**：對多段命中時能顯著改善最終排序。
- **成本**：高精度解析與重排會增加延時，按需開啟。


