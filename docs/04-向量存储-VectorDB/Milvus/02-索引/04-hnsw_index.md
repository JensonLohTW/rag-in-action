## 總覽

對應：`Milvus/02-索引/04-hnsw_index.py`。HNSW 小世界圖索引，主要參數 `M`（每節點連邊數）與 `efConstruction`（建索引時候選表大小），查詢時 `ef`。

---

## 流程圖

```mermaid
flowchart TD
  A[insert vectors] --> B[prepare_index_params → HNSW(M, efConstruction)]
  B --> C[create_index]
  C --> D[load]
  D --> E[search(params.ef)]
```

---

## 關鍵點總結

- **吞吐/延遲**：M、ef/efConstruction 調大精度↑延遲↑記憶體↑。


