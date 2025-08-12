## 總覽

對應：`02-使用PyMuPDF.py`。用 `pymupdf`（`fitz`）細粒度提取文本、圖片、連結、頁面尺寸與元資料。

---

## 流程圖

```mermaid
flowchart TD
  A[open(pdf)] --> B[for page in doc]
  B --> C[get_text / get_images / get_links]
  C --> D[print 內容與統計]
```

---

## 關鍵點總結

- **控制力強**：獲取底層版面信息，便於自定義處理。
- **需取捨**：結構理解需自行實作或結合其他庫。


