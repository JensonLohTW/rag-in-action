## 總覽

對應：`01-openai-embedding-recomendation-system.py`。用 OpenAI 嵌入將遊戲描述向量化，構建使用者向量（對其評價過遊戲向量取平均），計算與目標遊戲的相似度，輸出最可能喜歡該遊戲的使用者。

---

## 流程圖

```mermaid
flowchart TD
  A[讀取 users.csv/遊戲描述.json] --> B[get_embedding(text-embedding-3-small)]
  B --> C[為每款遊戲建立向量]
  C --> D[按 user_id 聚合 → 均值向量]
  D --> E[cosine_similarity(user_vec, target_game_vec)]
  E --> F[排序 → TopN 使用者]
```

---

## 關鍵點總結

- **內容式推薦**：以描述語義相似度近似偏好。
- **特徵構建**：使用者向量=其歷史遊戲向量的平均值。


