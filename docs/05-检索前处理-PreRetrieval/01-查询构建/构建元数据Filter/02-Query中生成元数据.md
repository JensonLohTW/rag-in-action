### 總覽
演示 `SelfQueryRetriever`：LLM 根據自然語言查詢，自動推導對應的元數據過濾條件（如標題、作者、觀看數、發佈日期、時長等），並與語義相似度檢索結合，得到更精準的結果。

### 流程圖
```mermaid
flowchart TD
  U[視頻URL清單] --> Y[YoutubeLoader.add_video_info]
  Y --> VEC[HuggingFaceEmbeddings → Chroma]
  MF[AttributeInfo(字段描述)] --> SQ[SelfQueryRetriever.from_llM]
  LLM[ChatDeepSeek(temperature=0)] --> SQ
  Q[自然語言查詢] --> SQ
  SQ --> RET[帶過濾條件的檢索]
  RET --> DOCS[命中文檔]
```

### 分步講解
- 數據準備：批量加載若干 YouTube 視頻並構建向量庫（`BAAI/bge-small-zh` + `Chroma`）。
- 元數據定義：用 `AttributeInfo` 描述 `title/author/view_count/publish_date/length` 等字段。
- 自查詢檢索器：`SelfQueryRetriever.from_llm(...)` 將查詢語句 → 結構化 filter + 檢索詞。
- 查詢與輸出：對多個示例查詢執行 `retriever.invoke(query)`，列印匹配影片的信息。

### 關鍵點總結
- **語義+結構化**：同時利用語義相似度與結構化條件，顯著縮小候選集。
- **字段說明越清晰，效果越好**：`AttributeInfo.description` 有助 LLM 正確理解字段語義。
- **確定性輸出**：`temperature=0` 提升 filter 生成穩定性。


