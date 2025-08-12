### 總覽
以 Milvus 構建「雙層檢索」：第一層用摘要向量快速定位表（年份/Sheet），第二層在該表的明細向量中檢索答案候選，最後將候選格式化後交由 LLM 生成答案。本版本將明細拆為多欄字段，結構依賴解析正確性，容錯較弱。

### 流程圖
```mermaid
flowchart TD
  XLS[Excel 多 Sheet] --> SUM_EMB[encode(sheet_name)]
  XLS --> DET_EMB[encode(row→detail_text)]
  SUM_EMB --> C1[Milvus: billionaires_summary]
  DET_EMB --> C2[Milvus: billionaires_details]
  Q[Query] --> L1[summary search top1]
  L1 --> FT[filter table_name]
  FT --> L2[details search topK]
  L2 --> PROMPT[構造上下文]
  PROMPT --> LLM[DeepSeek 回答]
```

### 分步講解
- 嵌入：`BAAI/bge-m3`（sentence-transformers）。
- 建庫：兩集合 `billionaires_summary`（表名摘要）與 `billionaires_details`（行級明細）。
- 索引：IVF_FLAT + COSINE；`nlist=1024`。
- 檢索：先 summary → 再 details（帶 `filter=table_name`）。
- 生成：將多條明細串成文字，交由 DeepSeek 生成自然語言回答。

### 關鍵點總結
- **不成熟點**：明細 schema 綁死，若列名變動易報錯；資料清洗成本高。
- **升級方向**：見 FAISS 版、v2 版（整表入庫）與 LlamaIndex 版（遞歸檢索）。


