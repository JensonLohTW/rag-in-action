## 總覽

對應：`05-用LlamaIndex-加载目录文档.py`。使用 `SimpleDirectoryReader` 載入整個資料夾或單檔，輸出為 LlamaIndex `Document`。

---

## 流程圖

```mermaid
flowchart TD
  A[選擇資料夾或單檔] --> B[SimpleDirectoryReader(...).load_data()]
  B --> C[List[Document]]
  C --> D[print 範例/數量]
```

---

## 分步講解

- 目錄導入：`SimpleDirectoryReader("90-文档-Data/黑悟空")`。
- 單檔導入：`SimpleDirectoryReader(input_files=[...])`。

---

## 關鍵點總結

- **與 LangChain 對照**：這裡輸出的 `Document` 為 LlamaIndex 版本，欄位命名略有不同（`text`）。
- **後續可接**：索引構建（`VectorStoreIndex`）與問答。


