## 總覽

對應：`03-04-用LangChain加载目录时跳过错误.py`。示例設置 `silent_errors=True`，在混合格式目錄下忽略無法解析的檔案（如圖片、PDF）。

---

## 流程圖

```mermaid
flowchart TD
  A[定位 data_dir] --> B[DirectoryLoader(silent_errors=True, loader_cls=TextLoader)]
  B --> C[load → List[Document]]
  C --> D[print 內容片段]
```

---

## 分步講解

- 錯誤韌性：跳過報錯檔案，最大化可用文本收集。

---

## 關鍵點總結

- **健壯**：大幅提升目錄導入容錯能力。
- **實用**：處理含圖片/二進位混合格式資料夾時尤為重要。


