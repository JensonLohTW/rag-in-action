## 總覽

對應：`02-构建LangChain Document对象.py`。示例手動構造 `Document` 列表並附帶 `metadata`。

---

## 流程圖

```mermaid
flowchart TD
  A[準備原始文本與元資料] --> B[構造 Document(page_content, metadata)]
  B --> C[組裝為 List[Document]]
  C --> D[print/後續處理]
```

---

## 分步講解

- `Document` 欄位：
  - `page_content`：文本內容
  - `metadata`：任意鍵值對（如來源檔名、作者等）

---

## 關鍵點總結

- **結構化**：統一文本與元資料格式，方便分塊、檢索與追溯。
- **靈活性**：適用於來自 API、DB 或自定義來源的文本。


