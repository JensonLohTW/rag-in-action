## 總覽

對應：`02-LangChain-RecursiveharacterTextSplitter.py`。使用遞歸字符分塊，按多級分隔符（段落/句號/逗號/空格）優先匹配切分，盡量保持語義完整。
 
---

## 流程圖

```mermaid
flowchart TD
  A[TextLoader → Documents] --> B[RecursiveCharacterTextSplitter(separators)]
  B --> C[split_documents → chunks]
  C --> D[print]
```

---

## 關鍵點總結

- **語義友好**：先大後小的分隔符保證自然邊界優先。


