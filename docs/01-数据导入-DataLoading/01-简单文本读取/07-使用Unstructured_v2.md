## 總覽

對應：`07-使用Unstructured_v2.py`。與 v1 類似，但展示以 `__dict__` 方式查看元素元資料。

---

## 流程圖

```mermaid
flowchart TD
  A[partition_text(file_path)] --> B[List[Element]]
  B --> C[for element: print 類型/文本]
  C --> D[print element.metadata.__dict__]
```

---

## 分步講解

- 元資料觀察方式不同：直接輸出 `metadata.__dict__`，便於一次性檢查所有欄位。

---

## 關鍵點總結

- **資料理解**：快速熟悉 unstructured 元資料結構。


