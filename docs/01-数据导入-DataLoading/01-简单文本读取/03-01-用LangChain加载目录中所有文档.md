## 總覽

對應：`03-01-用LangChain加载目录中所有文档.py`。示例用 `DirectoryLoader` 載整個目錄，注意依賴 `unstructured`/`nltk` 的說明與常見錯誤處理。
 
---

## 流程圖

```mermaid
flowchart TD
  A[定位資料目錄] --> B[DirectoryLoader(data_dir)]
  B --> C[load() → List[Document]]
  C --> D[print 長度 & 範例] 
  D --> E[後續處理]
```

---

## 分步講解

- 解析複雜格式（pdf/jpg/pptx）時，`DirectoryLoader` 可能透過 `unstructured` 調用 `nltk`；需提前準備 `nltk` 資料包避免 `BadZipFile`。
- 若只需文字格式，可透過 `glob`/`loader_cls` 來篩選與替換載入器。

---

## 關鍵點總結

- **通用性**：單一入口載入混合格式目錄。
- **健壯性**：掌握 `unstructured` 與 `nltk` 依賴，有助於排錯。


