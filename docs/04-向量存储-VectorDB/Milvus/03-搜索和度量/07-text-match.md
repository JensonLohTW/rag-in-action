## 總覽

對應：`Milvus/03-搜索和度量/07-text-match.py`。在向量檢索同時，對文本欄位啟用 `enable_analyzer`/`enable_match`，支持 `TEXT_MATCH(field, 'q1 q2')` 文本匹配過濾。

---

## 流程圖

```mermaid
flowchart TD
  A[schema.add_field(text, enable_analyzer, enable_match)] --> B[insert + index]
  B --> C[search(output_fields=[text])]
  C --> D[search(filter=TEXT_MATCH(text,'...'))]
```

---

## 關鍵點總結

- **文本匹配**：支援基本關鍵詞配對；與向量結果結合輸出。


