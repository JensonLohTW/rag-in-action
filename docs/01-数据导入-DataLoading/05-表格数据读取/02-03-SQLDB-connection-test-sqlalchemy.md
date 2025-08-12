## 總覽

對應：`02-03-SQLDB-connection-test-sqlalchemy.py`。用 `SQLAlchemy` 測試連接並以 `pandas` 輸出查詢結果。

---

## 流程圖

```mermaid
flowchart TD
  A[create_engine(mysql+pymysql://...)] --> B[engine.connect()]
  B --> C[execute(text(SELECT ...))]
  C --> D[pd.DataFrame(result.fetchall(), columns=result.keys())]
  D --> E[print]
```

---

## 關鍵點總結

- **工程化**：ORM/連線池等能力便於擴展。


