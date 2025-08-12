### 總覽
使用 DeepSeek（OpenAI 兼容 API）的 `tools` 參數定義函數，驅動模型主動產生 `tool_calls`，並實現一次「函數調用 → 工具返回 → 最終回覆」的閉環。

### 流程圖
```mermaid
flowchart TD
  TOOLS[tools: get_weather 定義(JSON Schema)] --> CHAT[chat.completions]
  Q[User 問天氣] --> CHAT --> MSG1[message.tool_calls]
  MSG1 --> TOOL[執行 get_weather]
  TOOL --> MSG2[role=tool 回傳結果]
  MSG2 --> CHAT --> FINAL[最終自然語言回覆]
```

### 分步講解
- 工具宣告：`type=function`，用 JSON Schema 定義 `parameters` 與 `required`。
- 首輪回應：模型返回 `message.tool_calls`，包含函數名與結構化參數。
- 工具執行：外部執行並以 `role=tool, tool_call_id` 將結果回注。
- 二輪生成：模型結合上下文輸出最後回覆。

### 關鍵點總結
- **標準化**：與 OpenAI Function/Tool Calling 一致，易於兼容。
- **安全性**：請對工具請求做白名單與參數驗證。


