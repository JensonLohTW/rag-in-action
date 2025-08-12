## 總覽

對應：`09-Parent-Child-Unstructured-LangChain.py`。用 `UnstructuredLoader` 解析 PDF，列印每頁元素細節與抽取 `Title` 列表，並以標題-正文關聯輸出。

---

## 流程圖

```mermaid
flowchart TD
  A[UnstructuredLoader(file_path, strategy=hi_res)] --> B[lazy_load → docs]
  B --> C[過濾 page==1 並列印元素細節]
  B --> D[收集 Title(第一頁)]
  B --> E[Title.parent_id 關聯 NarrativeText/Text]
  E --> F[輸出分組內容]
```

---

## 關鍵點總結

- **父子關係**：靠 `element_id/parent_id` 關聯標題與正文。
- **可擴展**：可視化渲染結合座標疊加。


