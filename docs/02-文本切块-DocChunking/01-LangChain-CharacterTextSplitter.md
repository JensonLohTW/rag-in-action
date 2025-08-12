## 總覽

對應：`01-LangChain-CharacterTextSplitter.py`。用固定長度字符分塊（`chunk_size`/`chunk_overlap`）對 `Document` 進行切分並打印結果。

---

## 流程圖

```mermaid
flowchart TD
  A[TextLoader → Documents] --> B[CharacterTextSplitter(chunk_size, overlap)]
  B --> C[split_documents → chunks]
  C --> D[print 內容與 metadata]
```

---

## 關鍵點總結

- **簡單可控**：固定長度，易於推理效能與 token 成本。


