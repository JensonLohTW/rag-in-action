## 總覽

對應：`01-使用PyPDF.py`。用 `PyPDFLoader` 逐頁載入 PDF 為 `Document` 列表並輸出內容。

---

## 流程圖

```mermaid
flowchart TD
  A[設定 PDF 路徑] --> B[PyPDFLoader(file_path)]
  B --> C[load() → pages: List[Document]]
  C --> D[print 頁數與內容]
```

---

## 關鍵點總結

- **快速與穩定**：官方 PDF 文本抽取器，適合純文本型 PDF。


