## 總覽

對應：`01-02-导入目录时指定CSVLoader.py`。示例以 `DirectoryLoader(glob=**/*.csv, loader_cls=CSVLoader)` 批量載入 CSV。

---

## 流程圖

```mermaid
flowchart TD
  A[DirectoryLoader(path, glob=**/*.csv, loader_cls=CSVLoader)] --> B[load → List[Document]]
  B --> C[print 統計與範例]
```

---

## 關鍵點總結

- **批處理**：目錄級別一次載入多個 CSV。
- **統一接口**：輸出為 `Document`，便於後續處理。


