### 總覽
將相似案例作為 Few-Shot 參照，指導 LLM 生成與示例同構的分析報告格式；先用向量召回最接近的示例，再將其與當前輸入拼接到提示中。

### 流程圖
```mermaid
flowchart TD
  EX[示例語料] --> V[FAISS 向量庫]
  CUR[當前問題] --> SRCH[similarity_search(k=1)]
  SRCH --> FS[取最相似示例]
  FS & CUR --> PROMPT[Few-Shot 模板]
  PROMPT --> LLM[OpenAI]
  LLM --> OUT[分析報告]
```

### 分步講解
- 建庫：將 `examples.context` 建為向量索引。
- 檢索：對當前輸入檢索最相似示例，抽取 `context/answer`。
- 模板：將示例放入模板前半段，再放入當前輸入，要求「按相同格式輸出」。

### 關鍵點總結
- **對齊格式**：Few-Shot 能顯著穩定輸出結構與風格。
- **語料質量**：示例要高質與多樣；相似性越高，遷移越好。


