## 總覽

對應：`04-01-pdfplumber提取PDF表格.py`。用 `pdfplumber` 遍歷頁面提取表格，轉為 `DataFrame` 並清理列名。

---

## 流程圖

```mermaid
flowchart TD
  A[pdfplumber.open] --> B[for page in pdf.pages]
  B --> C[page.extract_tables()]
  C --> D[for table → DataFrame]
  D --> E[清理首行為列名]
  E --> F[print]
```

---

## 關鍵點總結

- **實務友好**：對非規則表格也常有不錯效果，需後處理清洗。


