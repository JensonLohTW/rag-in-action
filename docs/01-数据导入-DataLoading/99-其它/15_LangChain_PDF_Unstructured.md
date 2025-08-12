## 總覽

對應：`15_LangChain_PDF_Unstructured.py`。以 `UnstructuredPDFLoader` → 分塊 → `FAISS` → `RetrievalQA` 構建 PDF 問答。

---

## 流程圖

```mermaid
flowchart TD
  A[UnstructuredPDFLoader] --> B[RecursiveCharacterTextSplitter]
  B --> C[FAISS.from_documents]
  C --> D[RetrievalQA(llm=ChatOpenAI, k=5)]
  D --> E[invoke(query) → result + sources]
```

---

## 關鍵點總結

- **端到端**：從解析到問答的完整範例。


