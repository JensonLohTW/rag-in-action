## 總覽

對應：`Milvus/02-索引/02-ivf_flat_index.py`。IVF_FLAT = 倒排簇中心 + 簇內暴力掃描；需設置 `nlist`，查詢時設 `nprobe`。

---

## 流程圖

```mermaid
flowchart TD
  A[insert vectors] --> B[prepare_index_params → IVF_FLAT(nlist)]
  B --> C[create_index]
  C --> D[load]
  D --> E[search(params.nprobe)]
```

---

## 關鍵點總結

- **取捨**：`nlist` 越大、`nprobe` 越大，精度↑延遲↑。


