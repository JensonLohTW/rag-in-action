## 總覽

對應：`Milvus/03-搜索和度量/01-basic-ann.py`。基礎 ANN 搜索：建立集合/索引 → 單向量/批量向量搜索 → 指定輸出欄位。

---

## 流程圖

```mermaid
flowchart TD
  A[create_collection + insert + create_index] --> B[load]
  B --> C[search(data=[vec], limit)]
  C --> D[search(data=[vecs], limit)]
  D --> E[search(..., output_fields=[color])]
```

---

## 關鍵點總結

- `output_fields` 可回傳 metadata 方便上層組裝答案。


