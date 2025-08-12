## 總覽

對應：`02-02-SQLDB-connection-test-pymysql.py`。用 `pymysql` 測試 MySQL 連接並查詢表 `game_scenes`。

---

## 流程圖

```mermaid
flowchart TD
  A[pymysql.connect(...)] --> B[cursor.execute(SELECT ...)]
  B --> C[fetchall → print]
  C --> D[close]
```

---

## 關鍵點總結

- **連通性驗證**：在引入 RAG 前先確認 DB 可用。


