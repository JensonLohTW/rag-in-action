## 總覽

對應：`04-LangChain-UnstructuredMarkdownLoader.py`。用 `UnstructuredMarkdownLoader` 讀取 Markdown；`mode="elements"` 可輸出多個元素。

---

## 流程圖

```mermaid
flowchart TD
  A[設定 markdown 路徑] --> B[UnstructuredMarkdownLoader(...)]
  B --> C[load → List[Document] or elements]
  C --> D[print 內容/元素數量]
```

---

## 分步講解

- `mode="elements"` 會將同一 Markdown 分解成多個元素，每個成為一則 `Document`。

---

## 關鍵點總結

- **細粒度**：更適合後續按照標題/段落做檢索。


