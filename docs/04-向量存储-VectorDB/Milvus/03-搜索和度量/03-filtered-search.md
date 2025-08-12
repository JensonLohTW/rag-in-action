## 總覽

對應：`Milvus/03-搜索和度量/03-filtered-search.py`。演示基於表達式的過濾（`like`/比較）、以及 `hints: iterative_filter` 的迭代過濾方式。

---

## 流程圖

```mermaid
flowchart TD
  A[insert + create_index] --> B[load]
  B --> C[search(filter='color like "color_%" and likes>500')]
  C --> D[search(params.hints=iterative_filter, 同樣篩選)]
```

---

## 關鍵點總結

- **表達式**：支援 `like`、比較、in 等。
- **迭代過濾**：對大資料集過濾更高效。


