## 總覽

對應：`Milvus/03-搜索和度量/08-search-iter.py`。海量結果分批拉取：`search_iterator(batch_size, limit)` 逐批 `next()` 直到結束。

---

## 流程圖

```mermaid
flowchart TD
  A[load] --> B[search_iterator(batch_size, limit, output_fields)]
  B --> C[while (next) 收集結果]
  C --> D[close]
```

---

## 關鍵點總結

- **可擴展**：避免一次性載入過多結果至記憶體。


