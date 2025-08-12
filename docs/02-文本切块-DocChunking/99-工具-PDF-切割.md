## 總覽

對應：`99-工具-PDF-切割.py`。輔助工具：從 PDF 中抽取指定頁碼，輸出新 PDF 供後續處理或示例使用。

---

## 流程圖

```mermaid
flowchart TD
  A[PdfReader(pdf)] --> B[遍歷 page_numbers → writer.add_page]
  B --> C[writer.write(output_path)]
  C --> D[print 成功資訊]
```

---

## 關鍵點總結

- **資料準備**：快速取樣長 PDF 的局部頁面。


