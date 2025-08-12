### 總覽
RankLLM 以 LLM 作為重排器，透過 Prompt 引導模型對候選文檔排序，能處理更複雜的語義與推理關係，適合高精度場景，通常配合向量初檢索形成兩段式流程。

### 流程圖
```mermaid
flowchart TD
  D[切分後文檔塊] --> V[FAISS 檢索 Top-20]
  Q[Query] --> V
  V --> CC[ContextualCompressionRetriever\n(base_compressor=RankLLMRerank)]
  CC --> TOP[Top-N 精排結果]
```

### 分步講解
- 文檔處理：`TextLoader` → `RecursiveCharacterTextSplitter(500/100)`，添加 `id/chunk_size` 等元數據。
- 初檢索：`FAISS.from_documents(..., BAAI/bge-small-zh)` → `as_retriever(k=20)`。
- 重排：`RankLLMRerank(top_n=3, model="gpt", gpt_model="gpt-4o-mini")` 嵌入 `ContextualCompressionRetriever`。

### 關鍵點總結
- **高準確**：可提供排序理由與可解釋性。
- **成本高**：涉及 LLM 調用；對延時敏感場景需權衡。
- **最佳實踐**：控制候選集大小（如 Top-20）以平衡成本與效果。


