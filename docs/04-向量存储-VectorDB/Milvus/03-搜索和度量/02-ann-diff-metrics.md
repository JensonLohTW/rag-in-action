## 總覽

對應：`Milvus/03-搜索和度量/02-ann-diff-metrics.py`。比較 L2/IP/COSINE 三種度量下的索引與搜索差異；COSINE 需向量正規化。

---

## 流程圖

```mermaid
flowchart TD
  A[prepare data] --> B[for metric in {L2,IP,COSINE}: create_collection(metric)]
  B --> C[insert + create_index(metric)]
  C --> D[load]
  D --> E[search(單向量/批量)]
```

---

## 關鍵點總結

- **度量選擇**：
  - L2：歐式距離，連續數據常用
  - IP：內積，未正規化向量
  - COSINE：方向相似性，建議先 normalize


