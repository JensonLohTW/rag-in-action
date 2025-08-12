### 總覽
本範例在多查詢分解上進一步自訂提示與輸出解析器：強制 LLM 產出「每行一問」的多視角子查詢，並用 `LineListOutputParser` 可靠解析後交由 `MultiQueryRetriever` 使用。

### 流程圖
```mermaid
flowchart TD
  D[載入/分塊/嵌入 → Chroma] --> V
  Q[原始查詢] --> P[自訂 Prompt: 5 個不同角度]
  P --> LLM[ChatDeepSeek]
  LLM --> PARSER[LineListOutputParser]
  PARSER --> MQR[MultiQueryRetriever(llm_chain=..., parser_key="lines")]
  MQR --> DOCS[合併後相關文檔]
```

### 分步講解
- 自訂輸出解析器
  - `LineListOutputParser.parse`：按行切分並過濾空行，得到子查詢清單。

- 自訂提示
  - 要求從不同維度（技能、戰鬥、裝備等）給出 5 條子查詢，提升互補性。

- 檢索器組裝
  - 以 `llm_chain = QUERY_PROMPT | llm | output_parser` 鏈式輸出清單。
  - `MultiQueryRetriever(retriever=..., llm_chain=..., parser_key="lines")` 使用解析結果。

### 關鍵點總結
- **輸出可預期**：自訂解析器讓 LLM 輸出更穩定可用。
- **易調參**：可調整子查詢數量與維度，兼顧成本與覆蓋。
- **與 HyDE/重寫互補**：在檢索前可疊加重寫或 HyDE 以進一步增強召回。


