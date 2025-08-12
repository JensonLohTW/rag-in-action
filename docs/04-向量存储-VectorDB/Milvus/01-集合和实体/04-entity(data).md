## 總覽

對應：`Milvus/01-集合和实体/04-entity(data).py`。展示實體 CRUD 與查詢：insert/upsert/delete、load/flush、query、濾條件、QueryIterator 分頁。

---

## 流程圖

```mermaid
flowchart TD
  A[create_collection] --> B[insert 初始資料]
  B --> C[upsert 更新]
  C --> D[delete 刪除]
  D --> E[flush/load]
  E --> F[query(filter, output_fields)]
```

---

## 關鍵點總結

- **upsert**：存在即更新，不存在即插入。
- **Query vs Get**：`get` 按 ID 取；`query` 支援表達式與欄位投影。


