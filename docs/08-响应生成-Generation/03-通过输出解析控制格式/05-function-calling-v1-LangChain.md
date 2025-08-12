### 總覽
以 LangChain 的 `bind_tools` 為 LLM 綁定 Pydantic 定義的工具（函數），觀察模型的工具調用決策與參數結構，作為函數調用（Tool Calling）的最小示例。

### 流程圖
```mermaid
flowchart TD
  DEF[Pydantic 工具定義 get_weather] --> BIND[llm.bind_tools([tool])]
  Q[Query] --> INV[llm_with_tools.invoke]
  INV --> RESP[AIMessage(tool_calls)]
  RESP --> PARSE[讀取 tool_calls 列表]
```

### 分步講解
- 工具定義：`get_weather(location:str, temperature:float)`。
- 綁定：`llm.bind_tools([get_weather])`。
- 請求：輸入「請告訴我上海的天氣」，模型可選擇觸發工具調用並生成參數。

### 關鍵點總結
- **結構化參數**：Pydantic 自帶類型校驗，避免錯參數。
- **閉環**：實務中需接上實際工具執行與二次回覆。


