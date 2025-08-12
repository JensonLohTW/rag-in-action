## 總覽

對應：`04-LangChain-为代码分块.py`。使用語言感知的代碼分塊（`from_language(Language.PYTHON)`）保留語法結構邊界。

---

## 流程圖

```mermaid
flowchart TD
  A[選語言 → get_separators_for_language] --> B[RecursiveCharacterTextSplitter.from_language]
  B --> C[create_documents([CODE])]
  C --> D[print 代碼塊]
```

---

## 關鍵點總結

- **語法友好**：避免在中途斷開語句或區塊，利於後續代碼檢索/理解。


