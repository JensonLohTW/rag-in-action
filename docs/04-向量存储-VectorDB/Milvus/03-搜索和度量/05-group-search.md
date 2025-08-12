## 總覽

對應：`Milvus/03-搜索和度量/05-group-search.py`。分組搜索：按 `group_by_field` 聚合相似結果，支援 `group_size` 與 `strict_group_size` 控制每組返回數量。

---

## 流程圖

```mermaid
flowchart TD
  A[insert + index + load] --> B[search(group_by_field=docId, limit)]
  B --> C[search(group_size=2, strict_group_size=True)]
```

---

## 關鍵點總結

- **去重**：以文檔粒度聚合近鄰，避免一篇文檔佔滿結果。


