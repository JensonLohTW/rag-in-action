## 總覽

對應：`Milvus/03-搜索和度量/06-full-text-search-bm25-en.py`。英文明文與中文版本流程一致：定義 BM25 函數、倒排稀疏索引、插入文檔、以查詢字串直接搜索。

---

## 流程圖

```mermaid
flowchart TD
  A[create_schema(enable_analyzer, sparse field)] --> B[Function(BM25)]
  B --> C[SPARSE_INVERTED_INDEX(metric=BM25)]
  C --> D[create_collection + insert]
  D --> E[load → search(data=[query_text], anns_field=sparse)]
```

---

## 關鍵點總結

- **Equal steps**：與中文流程一致，注意英語語料與分詞配置。


