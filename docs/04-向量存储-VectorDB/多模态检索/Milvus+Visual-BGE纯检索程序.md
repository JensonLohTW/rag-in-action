## 總覽

對應：`多模态检索/Milvus+Visual-BGE纯检索程序.py`。將檢索與可視化封裝為 `MilvusSearcher`/`visualize_results`，僅依賴已建好的 Milvus 圖像庫進行查詢（可選過濾條件）。

---

## 流程圖

```mermaid
flowchart TD
  A[WukongEncoder.encode_query] --> B[MilvusSearcher.search(filter可選)]
  B --> C[print_results]
  B --> D[visualize_results]
```

---

## 關鍵點總結

- **組件化**：檢索器/可視化獨立，便於整合到 Web/服務。


