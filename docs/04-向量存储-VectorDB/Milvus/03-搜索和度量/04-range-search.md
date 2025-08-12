## 總覽

對應：`Milvus/03-搜索和度量/04-range-search.py`。範圍搜索：指定 `radius` 與 `range_filter` 返回距離位於區間內的結果（對 L2：`range_filter < radius`）。

---

## 流程圖

```mermaid
flowchart TD
  A[load] --> B[search(params.radius, params.range_filter, limit)]
  B --> C[輸出帶 metadata 結果]
```

---

## 關鍵點總結

- **半徑/內圈**：`radius` 外圈、`range_filter` 內圈；結果在兩者之間。


