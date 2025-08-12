## 總覽

對應：`05-01-Unstrutured-简单示例.py`。用 `UnstructuredLoader` 解析網頁為多類元素，並輸出前 5 條。

---

## 流程圖

```mermaid
flowchart TD
  A[設定 URL] --> B[UnstructuredLoader(web_url)]
  B --> C[load() → List[Document]]
  C --> D[print 前N條 category:content]
```

---

## 分步講解

- `UnstructuredLoader`：比 `WebBaseLoader` 解析粒度更細，含 `category`（Title/Text/Image/Table...）。

---

## 關鍵點總結

- **結構化維度**：可用 `metadata["category"]` 做後續分組與抽取。


