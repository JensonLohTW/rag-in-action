## 總覽

對應：`05-01-unstructured表格提取.py`。用 `unstructured.partition.pdf.partition_pdf` 提取表格元素與父節點資訊。

---

## 流程圖

```mermaid
flowchart TD
  A[partition_pdf(file_path)] --> B[elements]
  B --> C[過濾 category==Table]
  C --> D[打印 element.metadata / element.text]
```

---

## 關鍵點總結

- **元素級**：以表格作為一級元素，保留元資料便於回溯。


