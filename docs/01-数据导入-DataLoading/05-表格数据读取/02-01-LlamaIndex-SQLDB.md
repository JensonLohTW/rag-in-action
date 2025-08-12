## 總覽

對應：`02-01-LlamaIndex-SQLDB.py`。示例用 `DatabaseReader` 連接 MySQL，執行 SQL 並將結果轉為 LlamaIndex `Document`。

---

## 流程圖

```mermaid
flowchart TD
  A[配置 DB 連線參數] --> B[DatabaseReader(...)]
  B --> C[load_data(query=SQL)]
  C --> D[List[Document]]
  D --> E[print 結果]
```

---

## 關鍵點總結

- **關聯數據**：結構化資料可直接納入 RAG 流中。
- **安全性**：避免直連生產庫；建議只讀權限與必要字段。


