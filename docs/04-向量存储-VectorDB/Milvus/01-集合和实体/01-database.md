## 總覽

對應：`Milvus/01-集合和实体/01-database.py`。展示 Milvus 資料庫（database）層級操作：連線、建立/列出/描述/修改屬性、切換、刪除。

---

## 流程圖

```mermaid
flowchart TD
  A[MilvusClient(uri, token)] --> B[create_database(my_database_1)]
  B --> C[create_database(my_database_2, properties.replica=3)]
  C --> D[list_databases / describe_database(default)]
  D --> E[alter_database_properties(max.collections=10)]
  E --> F[drop_database_properties(max.collections)]
  F --> G[use_database(my_database_2)]
  G --> H[drop_database(my_database_2)]
  H --> I[drop_database(my_database_1)]
```

---

## 關鍵點總結

- **賬號/位址**：`uri`、`token`（預設 `root:Milvus`）。
- **屬性管理**：可設副本數、最大集合數等。
- **操作順序**：刪庫前需確保已清空集合。


