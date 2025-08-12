### 總覽
使用 Pydantic v1 驗證與序列化資料模型，示例以 `User` 結構做欄位校驗、默認值生成與 JSON/字典輸出，作為後續結構化生成的對照基礎。

### 流程圖
```mermaid
flowchart TD
  DATA[原始資料字典] --> VAL[User(**data) 驗證]
  VAL --> OK[模型實例]
  OK --> DUMP[user.model_dump / model_dump_json]
```

### 分步講解
- 欄位約束：`min_length/max_length/pattern/range` 等。
- 默認：`created_at` 使用 `default_factory=datetime.now`。
- 輸出：`model_dump` 與 `model_dump_json`。

### 關鍵點總結
- **先驗約束**：在進 LLM 前先做資料質量保證能減少錯誤擴散。
- **與 LLM 結合**：可搭配 JSON 輸出後再以 Pydantic 校驗。


