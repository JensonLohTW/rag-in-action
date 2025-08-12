## 總覽

對應：`99-使用Textract.py`。用 `textract.process` 直接抽取 PDF 文本，並簡述與 PyMuPDF/Unstructured 的優劣比較。

---

## 流程圖

```mermaid
flowchart TD
  A[textract.process(pdf)] --> B[bytes → str]
  B --> C[print]
```

---

## 關鍵點總結

- **快速**：多格式統一 API。
- **侷限**：只抽文本，無結構/元資料/圖片；對複雜版面支持較弱。


