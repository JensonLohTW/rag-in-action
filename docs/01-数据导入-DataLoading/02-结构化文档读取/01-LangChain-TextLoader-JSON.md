## 總覽

對應：`01-LangChain-TextLoader-JSON.py`。示例用 `TextLoader` 直接讀取 JSON 檔，作為純文本載入為 `Document` 列表（不做結構解析）。

---

## 流程圖

```mermaid
flowchart TD
  A[設定 JSON 檔路徑] --> B[TextLoader(file_path)]
  B --> C[load() → List[Document]]
  C --> D[print/後續處理]
```

---

## 分步講解

- `TextLoader`：按純文本方式載入 `.json`，適合快速查看或後續自定義解析。
- 若需欄位級抽取，建議改用 `JSONLoader` 搭配 `jq_schema`。

---

## 關鍵點總結

- **快速入門**：最小成本載入 JSON 內容。
- **局限**：不做結構抽取；需要欄位抽取時選擇 `JSONLoader`。


