### 總覽
透過 LlamaIndex 的 `OpenAIPydanticProgram` 直接讓 LLM 生成 Pydantic v2 模型實例（如 `CodeAnalysis`），省去手寫解析邏輯，實現端到端的結構化輸出。

### 流程圖
```mermaid
flowchart TD
  SCHEMA[Pydantic 模型定義\nCodeIssue/CodeAnalysis] --> PROG[OpenAIPydanticProgram.from_defaults\noutput_cls=CodeAnalysis]
  CODE[輸入代碼] --> PROG
  PROG --> OBJ[分析報告(模型實例)]
```

### 分步講解
- 定義模型：包含 `issues/recommendations/overall_quality` 等欄位描述。
- Program：指定 `output_cls` 與 `prompt_template_str`，打包調用邏輯。
- 調用：`analysis = program(code=sample_code)` 直接返回類型安全的結果。

### 關鍵點總結
- **零解析成本**：不再手寫 JSON 解析 → Pydantic 的轉換邏輯。
- **型別安全**：欄位缺失或類型不符會在模型層報錯。
- **可擴展**：替換 `output_cls` 即可面向不同業務的結構化任務。


