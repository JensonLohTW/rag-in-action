## 總覽

對應：`01-用LangChain读入txt文件.py`。示例演示如何用 `TextLoader` 讀取單個 `.txt` 文件為 `Document` 列表。

---

## 流程圖

```mermaid
flowchart TD
  A[定位腳本目錄] --> B[拼接相對路徑到目標txt]
  B --> C[TextLoader(file_path)]
  C --> D[loader.load() → List[Document]]
  D --> E[print/後續處理]
```

---

## 分步講解

- 路徑處理：以 `os.path.dirname(__file__)` 取得腳本目錄，拼接相對路徑到 `90-文档-Data/黑悟空/设定.txt`。
- 文檔導入：`TextLoader(file_dir).load()` 輸出 `List[Document]`。

---

## 關鍵點總結

- **可移植**：相對路徑拼接避免硬編碼。
- **標準化**：輸出即為 LangChain `Document`，方便後續分塊與索引。


