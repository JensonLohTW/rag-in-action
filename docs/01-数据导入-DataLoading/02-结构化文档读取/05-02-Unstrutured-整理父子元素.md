## 總覽

對應：`05-02-Unstrutured-整理父子元素.py`。示例解析網頁後，基於 `element_id/parent_id` 關係，整理父（Title/Table）與子（Text）元素。

---

## 流程圖

```mermaid
flowchart TD
  A[UnstructuredLoader(web_url)] --> B[List[Document]]
  B --> C[掃描: 若 category in {Title,Table} → parent_id = element_id]
  B --> D[掃描: 若 doc.metadata.parent_id == parent_id → append(child)]
  C --> E[輸出 (parent, child) 或平鋪]
  D --> E[輸出 (parent, child) 或平鋪]
```

---

## 分步講解

- 利用 `metadata["element_id"]` 與 `metadata["parent_id"]` 建立層級結構。
- 可選：只保留 `Title/Table` 及其下屬文本，便於主題抽取與表格關聯。

---

## 關鍵點總結

- **層級化**：有助於以章節或圖表為單位建立索引。
- **可擴展**：可進一步轉為節點圖（GraphRAG）。


