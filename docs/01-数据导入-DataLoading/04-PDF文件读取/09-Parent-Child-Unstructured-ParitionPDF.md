## 總覽

對應：`09-Parent-Child-Unstructured-ParitionPDF.py`。直接用 `unstructured.partition.pdf.partition_pdf` 解析 PDF，打印元素、元資料與父子關係，並按頁過濾與關聯輸出。

---

## 流程圖

```mermaid
flowchart TD
  A[partition_pdf(filename, strategy=hi_res)] --> B[elements]
  B --> C[檢視第一個元素細節 to_dict]
  B --> D[過濾 page==1 列印元素資訊]
  B --> E[收集 Title 並關聯 NarrativeText/Text]
  E --> F[輸出分組內容]
```

---

## 關鍵點總結

- **直接元素 API**：不經 LangChain 包裝，觀察 unstructured 原生結構。
- **父子關聯**：基於 `parent_id` 關聯段落到標題。


