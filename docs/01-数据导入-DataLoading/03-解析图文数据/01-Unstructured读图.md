## 總覽

對應：`01-Unstructured读图.py`。用 `UnstructuredImageLoader` 讀取圖片並轉為 `Document`。

---

## 流程圖

```mermaid
flowchart TD
  A[設定圖片路徑] --> B[UnstructuredImageLoader(image_path)]
  B --> C[load() → List[Document]]
  C --> D[print]
```

---

## 關鍵點總結

- **圖像到文本**：提取圖像中的文字或描述，後續可索引檢索。


