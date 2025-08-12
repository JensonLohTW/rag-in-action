## 總覽

對應：`05-02-unstructured表格提取+上下文.py`。在表格元素外，追加上下文（前後鄰元素）以輔助解讀。

---

## 流程圖

```mermaid
flowchart TD
  A[partition_pdf(file_path)] --> B[elements]
  B --> C[過濾 Table]
  C --> D[查找 parent / 前後相鄰元素]
  D --> E[print 表格 + 上下文]
```

---

## 關鍵點總結

- **上下文意義**：表格常需標題或說明輔助理解。


