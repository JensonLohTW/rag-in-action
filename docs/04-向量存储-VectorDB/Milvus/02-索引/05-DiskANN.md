## 總覽

對應：`Milvus/02-索引/05-DiskANN.py`。DiskANN 適合超大資料集，部分索引駐磁碟；查詢時可調 `search_list` 等參數。

---

## 流程圖

```mermaid
flowchart TD
  A[create_collection/insert] --> B[prepare_index_params → DISKANN]
  B --> C[create_index]
  C --> D[load]
  D --> E[search(params.search_list)]
```

---

## 關鍵點總結

- **大規模**：磁碟友好，適用百萬/億級向量。


