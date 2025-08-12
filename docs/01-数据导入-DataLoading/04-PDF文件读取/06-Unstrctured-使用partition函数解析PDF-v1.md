## 總覽

對應：`06-Unstrctured-使用partition函数解析PDF-v1.py`。用 `unstructured.partition.auto.partition(content_type=application/pdf)` 解析 PDF 並打印元素類型與內容。

---

## 流程圖

```mermaid
flowchart TD
  A[partition(filename, content_type=application/pdf)] --> B[List[Element]]
  B --> C[print 前N個元素類型/內容]
```

---

## 關鍵點總結

- **自動分段**：快速獲得元素級文本。


