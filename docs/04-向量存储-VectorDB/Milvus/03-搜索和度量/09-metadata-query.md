## 總覽

對應：`Milvus/03-搜索和度量/09-metadata-query.py`。展示 `get`（按 ID 取）與 `query`（條件查詢、投影、limit）與 `QueryIterator` 分頁查詢。

---

## 流程圖

```mermaid
flowchart TD
  A[insert + index + load] --> B[get(ids, output_fields)]
  B --> C[query(filter, output_fields, limit)]
  C --> D[Collection.query_iterator(batch_size, expr)]
```

---

## 關鍵點總結

- **查詢形態**：ID 精確查 vs 表達式條件檢索。
- **分頁**：`query_iterator` 逐批拉取避免 OOM。


