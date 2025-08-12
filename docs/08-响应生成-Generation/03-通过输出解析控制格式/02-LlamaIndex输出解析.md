### 總覽
LlamaIndex 的 `get_response_synthesizer` 支援多種輸出模式：簡潔、精煉、表格、分點、時間線等；並可直接輸出為 Pydantic 模型，實現「可控格式化生成」。

### 流程圖
```mermaid
flowchart TD
  DOCS[SimpleDirectoryReader] --> IDX[VectorStoreIndex]
  IDX --> QE[as_query_engine(response_synthesizer)]
  QE --> OUT[多種格式輸出/結構化對象]
```

### 分步講解
- 定義結構：`GameInfo(BaseModel)` 作為結構化輸出類。
- 模式示例：
  - COMPACT：簡潔總結。
  - REFINE：輸出 `output_cls=GameInfo` 結構化結果。
  - TREE_SUMMARIZE：以 `summary_template` 產生表格格式。
  - COMPACT_ACCUMULATE：分點彙總，支援 `use_async=True`。
  - SIMPLE_SUMMARIZE：以時間線呈現故事線。

### 關鍵點總結
- **結構化優先**：直接輸出 Pydantic 物件，避免再解析。
- **模板控制**：配合 `PromptTemplate` 控制表格/分點/時間線等形態。


