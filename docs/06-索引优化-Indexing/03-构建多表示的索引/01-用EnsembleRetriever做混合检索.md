### 總覽
以 `EnsembleRetriever` 將 BM25 與向量檢索（FAISS）集成，通過權重融合兩路結果，並與純向量檢索對比檢索與問答效果，觀察混合檢索的穩健性提升。

### 流程圖
```mermaid
flowchart TD
  D1[system_docs] & D2[lore_docs] --> BM25[BM25Retriever(k=2)]
  D1 & D2 --> VEC[FAISS.from_texts + as_retriever(k=2)]
  BM25 & VEC --> ENS[EnsembleRetriever(weights=0.5/0.5)]
  Q[Query] --> ENS --> R1[候選文檔]
  Q --> VEC --> R2[候選文檔]
  LLM[DeepSeek] --> QA1[RetrievalQA(ENS)] & QA2[RetrievalQA(VEC)]
```

### 分步講解
- 兩路檢索器：`BM25Retriever` 與 `FAISS`（`HuggingFaceEmbeddings=BAAI/bge-small-zh`）。
- 集成檢索：`EnsembleRetriever(retrievers=[...], weights=[0.5,0.5])`。
- 問答對比：`RetrievalQA.from_chain_type(..., retriever=ensemble_retriever)` 與 `retriever=faiss_retriever`。

### 關鍵點總結
- **穩健性**：關鍵詞與語義雙保險，對長文本與術語場景更穩。
- **權重調參**：可按資料類型調整 BM25 與向量的占比。
- **可再疊加**：可在融合後再接重排器。


