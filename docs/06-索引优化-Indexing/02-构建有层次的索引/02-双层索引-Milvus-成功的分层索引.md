### 總覽
與「不成熟版」相比，該方案將 details 集合簡化為整表文本 `content`，避免行級欄位解析帶來的 brittle。第一層仍用 summary 精準定位表名，第二層在限定表名下以整表文本向量檢索，顯著提升穩定性。

### 流程圖
```mermaid
flowchart TD
  XLS[Excel 多 Sheet] --> SUM_EMB[encode(sheet_name)]
  XLS --> TBL_TXT[df.to_string → encode(content)]
  SUM_EMB --> C1[Milvus: billionaires_summary]
  TBL_TXT --> C2[Milvus: billionaires_details(content)]
  Q[Query] --> L1[summary search]
  L1 --> FT[filter table_name]
  FT --> L2[details search top1]
  L2 --> PROMPT[構造上下文]
  PROMPT --> LLM[DeepSeek 回答]
```

### 分步講解
- summary：僅存 `table_name`（降低 schema 複雜度）。
- details：存整表 `content` 字串並向量化（避免列名對齊問題）。
- 檢索：summary→details，兩次搜索皆用 COSINE；`nprobe=10`。

### 關鍵點總結
- **穩定性大幅提升**：避免對列名、資料清洗的強依賴。
- **可壓縮**：可對整表文本先經 LLM 生成摘要再入庫，節省向量維度與存儲。


