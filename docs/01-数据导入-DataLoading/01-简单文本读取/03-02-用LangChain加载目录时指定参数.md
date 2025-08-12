## 總覽

對應：`03-02-用LangChain加载目录时指定参数.py`。示例在 `DirectoryLoader` 中指定 `glob`、多執行緒與進度條。

---

## 流程圖

```mermaid
flowchart TD
  A[定位 data_dir] --> B[DirectoryLoader(data_dir, glob, use_multithreading, show_progress)]
  B --> C[load() → List[Document]]
  C --> D[print 統計]
```

---

## 分步講解

- `glob`：僅匹配特定副檔名（如 `**/*.md`）。
- `use_multithreading`：提速載入，對 I/O 密集任務明顯。
- `show_progress`：顯示處理進度。

---

## 關鍵點總結

- **效率**：多執行緒 + 進度視覺化。
- **精確**：利用 `glob` 避免無用格式。


