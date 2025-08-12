### 總覽
在 v1 基礎上增加 Prompt 錨點（以 `SQL:` 結尾）與更嚴格的結構，降低 LLM 產生多餘文本的機率；執行失敗時打印錯誤。此版本在大多數情況下可穩定產生可執行 SQL。

### 流程圖
```mermaid
flowchart TD
  RAG[檢索: DDL/Q2SQL/字段描述] --> P[組裝 Prompt (以 SQL: 結尾)]
  P --> LLM[openai.chat.completions]
  LLM --> SQL[純 SQL 字串]
  SQL --> EXE[SQLAlchemy 執行]
  EXE --> OUT[結果 或 錯誤]
```

### 分步講解
- 與 v1 相同的三路檢索，Prompt 結尾加上 `SQL:` 作為強提示。
- 生成 SQL 後直接執行，打印列名與資料列。

### 關鍵點總結
- **錨點效果**：`SQL:` 能明顯降低代碼塊或解釋性文字。
- **限制**：仍未內建錯誤自動修復；遇語法錯誤需人工介入或升級到 v3。


