### 總覽
藉由 `response_format={type: 'json_object'}` 強制模型輸出符合 JSON 的內容，避免再做脆弱的純文本解析。

### 流程圖
```mermaid
flowchart TD
  SYS[system 說明 JSON 輸出示例] & USR[user 含問答文本] --> CALL[DeepSeek chat.completions]
  CALL --> JSON[response.message.content(JSON)]
  JSON --> LOAD[json.loads]
```

### 分步講解
- 客戶端：`OpenAI(base_url=https://api.deepseek.com)`；設置 `DEEPSEEK_API_KEY`。
- 請求：攜帶 `response_format={'type': 'json_object'}`。
- 解析：`json.loads(message.content)` 直接獲得字典結構。

### 關鍵點總結
- **避免幻覺格式**：在模型層要求輸出 JSON，可靠性更高。
- **仍需校驗**：可加 schema 校驗（如 `pydantic`）確保字段完整。


