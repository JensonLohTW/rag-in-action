## 總覽

對應：`07-使用Unstructured_v1.py`。示例用 `unstructured.partition.text.partition_text` 解析純文本為結構化元素，並展示元素與元資料。

---

## 流程圖

```mermaid
flowchart TD
  A[選擇文本檔] --> B[partition_text(file_path)]
  B --> C[List[Element]]
  C --> D[遍歷 element 與 metadata]
  D --> E[print 結構化資訊]
```

---

## 分步講解

- `partition_text` 輸出元素物件，帶型別與豐富元資料，可供後續清洗、抽取與分段。

---

## 關鍵點總結

- **結構化增益**：比簡單讀檔更易於後續檢索與提示工程。
- **可視化**：打印元素類型與元資料以理解資料形態。


