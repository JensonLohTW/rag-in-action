### 總覽
Adaptive RAG：先做查詢路由（向量庫 or Web 搜索），檢索後以 LLM 對文檔過濾，生成後做幻覺與回答完整性評分，根據評分選擇「重試/重寫/結束」，形成可適配的動態閉環。

### 流程圖
```mermaid
flowchart TD
  Q[問題] --> ROUTE[RouteQuery vectorstore|web_search]
  ROUTE -->|vectorstore| RET[向量檢索]
  ROUTE -->|web_search| WEB[網路搜索]
  RET --> FILTER[LLM 文檔過濾 yes/no]
  FILTER -->|有文檔| GEN[RAG 生成]
  FILTER -->|無文檔| REW[重寫問題]
  WEB --> GEN
  GEN --> GRADE[幻覺/回答質量評分]
  GRADE -->|retry| GEN
  GRADE -->|rewrite| REW
  GRADE -->|end| END((完成))
  REW --> RET
```

### 分步講解
- 路由：`with_structured_output(RouteQuery)` 產出資料源標識，保證可解析。
- 檢索與過濾：檢索後按 `yes/no` 過濾無關文檔，避免幻覺。
- 生成與評估：`hallu/answer` 兩評分器決定後續流向（重試/重寫/結束）。

### 關鍵點總結
- **可適配**：對未知問題可自動外搜；對檢索質量差自動重寫。
- **可觀測**：以圖工作流呈現決策路徑與狀態，便於灰度與觀測。


