## 總覽

對應：`02-Unstructured读PPT.py`。示例使用 `unstructured.partition.ppt.partition_ppt` 解析 PPT 並轉為 `Document` 列表。

---

## 流程圖

```mermaid
flowchart TD
  A[設定 PPT 路徑] --> B[partition_ppt(filename)]
  B --> C[List[Element]]
  C --> D[轉為 List[Document]]
  D --> E[print 範例]
```

---

## 分步講解

- 需要系統安裝 `libreoffice` 提供 `soffice` 命令（處理 Office 轉換）。

---

## 關鍵點總結

- **Office 支援**：PPT 解析需額外系統依賴。
- **結構化**：輸出元素可攜帶元資料，利於追溯。


