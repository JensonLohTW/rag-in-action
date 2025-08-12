## 總覽

對應：`03-01-camelot提取PDF表格.py`。用 `camelot.read_pdf` 解析 PDF 表格，轉為 `DataFrame` 並保存 CSV。

---

## 流程圖

```mermaid
flowchart TD
  A[read_pdf(pdf, pages=all)] --> B[tables: List[Table]]
  B --> C[for table → table.df → DataFrame]
  C --> D[print/info]
  D --> E[to_csv]
```

---

## 關鍵點總結

- **版面要求**：Camelot 對表格線條與結構較敏感，適合規則表格。


