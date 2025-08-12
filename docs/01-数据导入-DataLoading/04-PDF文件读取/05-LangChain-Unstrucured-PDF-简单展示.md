## 總覽

對應：`05-LangChain-Unstrucured-PDF-简单展示.py`。用 `UnstructuredLoader` 解析 PDF 並簡單打印內容。

---

## 流程圖

```mermaid
flowchart TD
  A[UnstructuredLoader(file_path, strategy=hi_res)] --> B[lazy_load → List[Document]]
  B --> C[print(docs)]
```

---

## 關鍵點總結

- **入門範例**：快速看到解析輸出的基礎結構。


