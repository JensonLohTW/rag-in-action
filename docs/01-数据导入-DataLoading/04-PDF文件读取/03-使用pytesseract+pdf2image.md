## 總覽

對應：`03-使用pytesseract+pdf2image.py`。對掃描型/圖片型 PDF，先轉圖片再用 OCR（`pytesseract`）提取中文文本。

---

## 流程圖

```mermaid
flowchart TD
  A[convert_from_path(PDF)] --> B[for 每頁 → PNG]
  B --> C[pytesseract.image_to_string(lang=chi_sim)]
  C --> D[print 每頁文本]
```

---

## 關鍵點總結

- **適用場景**：掃描件、無文本層 PDF。
- **系統依賴**：需安裝 Tesseract 及中文語料。


