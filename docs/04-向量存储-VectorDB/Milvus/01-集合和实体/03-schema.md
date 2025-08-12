## 總覽

對應：`Milvus/01-集合和实体/03-schema.py`。展示 Schema 定義：主鍵、密集/二進位向量欄位、各類標量欄位（字串、數值、布林、JSON、陣列）、動態欄位，並以 Schema 建集合。

---

## 流程圖

```mermaid
flowchart TD
  A[create_schema] --> B[add_field: id INT64 primary]
  B --> C[add_field: text_vector FLOAT_VECTOR(dim=768)]
  C --> D[add_field: image_vector BINARY_VECTOR(dim=256)]
  D --> E[add scalar fields: VARCHAR/INT/BOOL/JSON/ARRAY]
  E --> F[create_collection(schema)]
  F --> G[describe_collection]
  G --> H[drop_collection]
```

---

## 關鍵點總結

- **向量欄位**：維度需符合模型輸出（Binary 需 8 的倍數）。
- **陣列欄位**：需指定元素型別與容量限制。


