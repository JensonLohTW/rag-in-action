## 總覽

對應：`Milvus/02-索引/01-milvus_flat_index.py`。流程：建 schema/集合 → 插入向量 → 建 FLAT 索引（暴力掃描）→ load → 搜索。

---

## 流程圖

```mermaid
flowchart TD
  A[MilvusClient] --> B[create_schema + add_field(vector)]
  B --> C[create_collection]
  C --> D[insert N vectors]
  D --> E[prepare_index_params → FLAT]
  E --> F[create_index + describe/list]
  F --> G[load_collection → search]
```

---

## 關鍵點總結

- **FLAT**：精度最高，延遲最高；小資料或校驗基準用。


