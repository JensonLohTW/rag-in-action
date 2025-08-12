## 總覽

對應：`06-LlamaIndex-构建Document对象.py`。示例手動構造 LlamaIndex `Document`（`text` + `metadata`）。

---

## 流程圖

```mermaid
flowchart TD
  A[準備文本與元資料] --> B[llama_index.core.Document(text=..., metadata=...)]
  B --> C[List[Document]]
  C --> D[print metadata]
```

---

## 分步講解

- 欄位與 LangChain 的 `Document` 略有差異，注意使用對應屬性（如 `text`）。

---

## 關鍵點總結

- **結構化**：便於後續索引與檢索。
- **可擴展**：自定義豐富的 `metadata` 支援多維檢索。


