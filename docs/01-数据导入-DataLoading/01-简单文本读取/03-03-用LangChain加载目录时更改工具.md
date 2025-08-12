## 總覽

對應：`03-03-用LangChain加载目录时更改工具.py`。示例用 `loader_cls=TextLoader` 覆蓋 `DirectoryLoader` 的預設加載器，只處理文本類型。

---

## 流程圖

```mermaid
flowchart TD
  A[定位 data_dir] --> B[DirectoryLoader(loader_cls=TextLoader, glob=**/*.md)]
  B --> C[load → List[Document]]
  C --> D[print 內容片段]
```

---

## 分步講解

- 指定 `loader_cls` 可以避免 `unstructured` 解析二進位格式造成的報錯/性能問題。

---

## 關鍵點總結

- **精準控制**：僅以文本加載器處理選定類型。
- **更穩定**：降低混合格式導致的依賴與錯誤風險。


