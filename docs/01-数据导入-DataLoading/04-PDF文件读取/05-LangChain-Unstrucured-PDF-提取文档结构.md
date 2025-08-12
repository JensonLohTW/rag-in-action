## 總覽

對應：`05-LangChain-Unstrucured-PDF-提取文档结构.py`。用 `UnstructuredLoader` 解析 PDF，並基於 `category/coordinates` 提取結構與版面資訊。

---

## 流程圖

```mermaid
flowchart TD
  A[UnstructuredLoader(file_path, strategy=hi_res, coordinates=True)] --> B[lazy_load → List[Document]]
  B --> C[extract_basic_structure(docs)]
  B --> D[analyze_layout(docs)]
  C --> E[按類型彙總內容]
  D --> F[版面尺寸/元素座標/排序]
```

---

## 關鍵點總結

- **高分辨率策略**：獲取座標與元素類別，利於版面理解。
- **結構萃取**：可按 `Title/Text/Image/Table` 分桶，做主題/表格抽取。


