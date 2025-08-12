## 總覽

對應：`Milvus/01-集合和实体/02-collection.py`。演示 Collection 管理：新建/列出/描述、重命名、TTL 屬性、載入與釋放、Partition 管理、Alias 管理、刪除集合。

---

## 流程圖

```mermaid
flowchart TD
  A[連線 Milvus] --> B[create_collection(name, dimension)]
  B --> C[list_collections / describe_collection]
  C --> D[rename_collection]
  D --> E[alter_collection_properties(TTL)] --> F[drop_collection_properties(TTL)]
  F --> G[load_collection / release_collection]
  G --> H[Partition CRUD]
  H --> I[Alias CRUD]
  I --> J[drop_collection]
```

---

## 關鍵點總結

- **TTL**：`collection.ttl.seconds` 控制自動過期回收。
- **Partition**：按子集載入/釋放以節省記憶體。
- **Alias**：便於讀寫切換與灰度。


