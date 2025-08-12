## 總覽

對應：`04-LangChain-为代码普通分块.py`。用通用分塊器對代碼做固定長度切分，作為與語言感知分塊的對照。

---

## 流程圖

```mermaid
flowchart TD
  A[定義 CODE 字串] --> B[RecursiveCharacterTextSplitter(chunk_size, overlap)]
  B --> C[create_documents([CODE])]
  C --> D[print 代碼塊]
```

---

## 關鍵點總結

- **對照組**：便於比較語法感知分塊對檢索與生成效果的影響。


