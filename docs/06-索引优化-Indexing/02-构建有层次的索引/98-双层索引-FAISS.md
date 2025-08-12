### 總覽
以本地 FAISS 搭建輕量雙層索引：第一層用描述向量定位年份，第二層用整表文本向量定位對應年度表格，最後將上下文交由 LLM 生成回答，避免外部向量庫依賴。

### 流程圖
```mermaid
flowchart TD
  DESCS[年份描述列表] --> E1[SentenceTransformer.encode]
  E1 --> F1[FAISS IndexFlatL2(desc)]
  XLS[Excel 多 Sheet] --> TBLTXT[df.to_string]
  TBLTXT --> E2[encode]
  E2 --> F2[FAISS IndexFlatL2(table)]
  Q[Query] --> S1[desc_index.search k=1]
  S1 --> S2[table_index.search k=1]
  S2 --> PROMPT[構造上下文]
  PROMPT --> LLM[DeepSeek 回答]
```

### 分步講解
- 建兩個 FAISS 索引：年份描述與整表文本，維度取自同一 encoder。
- 查詢：先年描述匹配 → 再表文本匹配 → 組裝 prompt → LLM 回答。

### 關鍵點總結
- **本地化**：無 Milvus 依賴，便於快速試驗。
- **注意**：示例中以硬編碼鍵名選表，實務中應建立穩健的 sheet 名對齊策略。


