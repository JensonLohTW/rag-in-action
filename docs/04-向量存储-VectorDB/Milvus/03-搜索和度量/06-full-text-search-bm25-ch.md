## 總覽

對應：`Milvus/03-搜索和度量/06-full-text-search-bm25-ch.py`。使用 Milvus 內建 BM25：在 schema 中啟用 `enable_analyzer` 與 `SPARSE_FLOAT_VECTOR`，定義 `FunctionType.BM25` 映射文字→稀疏向量，建立 `SPARSE_INVERTED_INDEX`，執行全文檢索。

---

## 流程圖

```mermaid
flowchart TD
  A[create_schema(enable_analyzer, sparse field)] --> B[add BM25 Function(text→sparse)]
  B --> C[prepare_index_params(SPARSE_INVERTED_INDEX,BM25)]
  C --> D[create_collection + insert 文本]
  D --> E[load → search(data=[query_text], anns_field=sparse)]
```

---

## 關鍵點總結

- **內建 BM25**：省去外部稀疏生成；支援中文分詞（需 analyzer）。


