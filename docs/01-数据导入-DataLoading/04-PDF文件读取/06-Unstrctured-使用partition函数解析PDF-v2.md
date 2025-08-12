## 總覽

對應：`06-Unstrctured-使用partition函数解析PDF-v2.py`。在 v1 基礎上，統計 `elements` 類型分佈並打印詳細內容。

---

## 流程圖

```mermaid
flowchart TD
  A[partition(filename, content_type=PDF)] --> B[List[Element]]
  B --> C[統計各類型數量]
  B --> D[print 詳細內容]
```

---

## 關鍵點總結

- **數量分佈**：理解文檔元素型別構成，指導後續處理策略。


