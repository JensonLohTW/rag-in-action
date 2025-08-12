### 總覽
使用 RAGAS 對 RAG 輸出的「忠實度」與「答案相關性」進行評估，並對比開源與 OpenAI 兩種 Embedding 在答案相關性上的差異。

### 流程圖
```mermaid
flowchart TD
  DATA[構造 Dataset(question/answer/contexts)] --> EVAL1[Faithfulness(llm)]
  DATA --> EVAL2[AnswerRelevancy(llm+embeddings)]
  EVAL2 -->|HuggingFaceEmbeddings\nvs OpenAIEmbeddings| CMP[分數對比]
```

### 分步講解
- LLM 包裝：`LangchainLLMWrapper(ChatOpenAI)` 供評估器使用。
- 數據：含 `question/answer/contexts`，轉 `Dataset.from_dict`。
- 忠實度：`Faithfulness(llm=...)` 僅依賴 LLM 將答案斷句驗證是否可由上下文推得。
- 相關性：`AnswerRelevancy(llm, embeddings)` 需 Embedding；示例比較 all-MiniLM-L6-v2 與 OpenAI 兩種嵌入。

### 關鍵點總結
- **度量互補**：忠實度衡量是否基於上下文；答案相關性衡量與問題的貼合度。
- **可替換嵌入**：透過 `LangchainEmbeddingsWrapper` 適配現有嵌入模型。
- **小樣本起步**：先以少量樣本走通流程，再擴充測試集並固化評估管線。


