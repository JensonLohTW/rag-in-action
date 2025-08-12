## 總覽

對應：`02-LangCHain-JSONLoader-JSON.py`。示例用 `JSONLoader` + `jq_schema` 從 JSON 中抽取特定欄位並轉為 `Document`。

---

## 流程圖

```mermaid
flowchart TD
  A[設定 JSON 檔路徑] --> B[JSONLoader(file_path, jq_schema, text_content=True)]
  B --> C[load() → List[Document]]
  C --> D[print 抽取結果]
```

---

## 分步講解

- `jq_schema`：使用 jq 表達式選取 JSON 節點（如主角與支援角色資訊）並格式化輸出。
- `text_content=True`：將選取內容填入 `page_content`。

---

## 關鍵點總結

- **結構抽取**：比 `TextLoader` 更適合面向欄位的載入。
- **靈活**：更改 `jq_schema` 即可調整抽取策略。


