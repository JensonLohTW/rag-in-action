## 總覽

對應：`多模态检索/Milvus+Visual-BGE多模态检索-中文.py`。以 Visualized-BGE 生成圖像/圖文嵌入，存入 Milvus 本地 DB，支持圖+文查詢、多欄位輸出與可視化拼圖。

---

## 流程圖

```mermaid
flowchart TD
  A[WukongDataset 讀入 metadata.json] --> B[WukongEncoder.encode_image]
  B --> C[create_collection(dimension=emb_dim, enable_dynamic_field)]
  C --> D[insert {vector + metadata}]
  D --> E[encode_query(image,text)]
  E --> F[search(params=COSINE, nprobe/radius/range_filter)]
  F --> G[visualize_results]
```

---

## 關鍵點總結

- **多模態**：純圖/圖+文兩種檢索入口。
- **可視化**：網格展示檢索結果，疊加分數。


