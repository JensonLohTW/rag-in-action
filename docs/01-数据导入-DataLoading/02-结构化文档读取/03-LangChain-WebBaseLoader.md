## 總覽

對應：`03-LangChain-WebBaseLoader.py`。示例用 `WebBaseLoader` 抓取維基頁面，並用 `bs4.SoupStrainer` 僅解析主體內容 `#bodyContent`。

---

## 流程圖

```mermaid
flowchart TD
  A[設定 URL] --> B[WebBaseLoader(web_paths, bs_kwargs=parse_only=SoupStrainer(id=bodyContent))]
  B --> C[load() → List[Document]]
  C --> D[print metadata & page_content]
```

---

## 分步講解

- `bs_kwargs.parse_only`：過濾頁面非主體元素，減少噪音。
- 可選 `bs_get_text_kwargs` 控制文本拼接方式（分隔符/trim）。

---

## 關鍵點總結

- **定向抓取**：降低後續分塊與檢索負擔。
- **元資料**：保留來源網址等，便於可溯源。


