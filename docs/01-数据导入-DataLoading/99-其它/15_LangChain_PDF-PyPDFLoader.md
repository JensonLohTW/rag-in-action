## 總覽

對應：`15_LangChain_PDF-PyPDFLoader.py`。以 `PyPDFLoader` → 分塊 → `FAISS` → `RetrievalQA`，提供多問題查詢示例。

---

## 流程圖

```mermaid
flowchart TD
  A[PyPDFLoader] --> B[TextSplitter]
  B --> C[FAISS]
  C --> D[RetrievalQA]
  D --> E[invoke(query...)]
```

---

## 關鍵點總結

- **多輪示例**：便於測試檢索與回答表現。


