## 總覽

對應：`Milvus/02-索引/03-ivf_pq_index.py`。IVF_PQ = 倒排簇 + 產品量化壓縮；核心參數 `nlist`、`m`、`nbits`。

---

## 流程圖

```mermaid
flowchart TD
  A[insert vectors] --> B[prepare_index_params → IVF_PQ(nlist,m,nbits)]
  B --> C[create_index]
  C --> D[load]
  D --> E[search(params.nprobe)]
```

---

## 關鍵點總結

- **壓縮/效能**：PQ 降低存儲與計算成本；需權衡精度損失。


