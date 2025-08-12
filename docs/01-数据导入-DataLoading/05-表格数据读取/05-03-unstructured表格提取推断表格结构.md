## 總覽

對應：`05-03-unstructured表格提取推断表格结构.py`。在 `partition_pdf` 中開啟 `infer_table_structure=True`，並列印父節點與前置鄰近元素作為上下文。

---

## 流程圖

```mermaid
flowchart TD
  A[partition_pdf(file_path, infer_table_structure=True)] --> B[elements]
  B --> C[過濾 Table → print metadata/text]
  C --> D[parent_id 映射 → 父節點資訊]
  C --> E[索引映射 → 表格前 N 個元素內容]
```

---

## 關鍵點總結

- **結構推斷**：提升表格重建的完整度。
- **脈絡保留**：父節點與前後文可輔助問答準確性。


