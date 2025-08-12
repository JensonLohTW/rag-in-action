### 總覽
在執行前先連 Neo4j 動態獲取當前資料庫的「節點標籤、關係型別、各標籤的屬性」，將實際 Schema 組裝成描述，然後再請 LLM 產出 Cypher 查詢，顯著提高成功率。

### 流程圖
```mermaid
flowchart TD
  CONN[Neo4j 連線] --> INSPECT[db.labels / db.relationshipTypes / keys(n)]
  INSPECT --> DESC[拼裝實際 Schema 描述]
  Q[使用者問題] --> PROMPT
  DESC --> PROMPT[生成 Cypher 提示]
  PROMPT --> LLM[DeepSeek]
  LLM --> CYPHER[Cypher 字串]
  CYPHER --> RUN[Neo4j 執行]
  RUN --> RES[結果]
```

### 分步講解
- 以 Cypher 系統函數獲取標籤、關係、屬性鍵，動態構造 Schema 說明。
- 提示中強調關係方向與匹配方式（如 `HAS_DESCRIPTION` 必須 Concept → Description）。
- 生成的查詢在同一連線中執行並打印結果。

### 關鍵點總結
- **可靠性**：避免了手寫 Schema 與真實庫不一致的風險。
- **可移植**：換庫即可用，無需更新硬編碼描述。
- **最佳實踐**：對 Text2Cypher 類場景，動態 schema 探查是關鍵步驟。


