### 總覽
在 SQLite 中建立兩張示例表：`scenic_spots`（景區信息）與 `city_info`（城市信息），並插入若干樣例資料，作為 Text2SQL 教學測試庫。

### 流程圖
```mermaid
flowchart TD
  CONN[sqlite3.connect] --> CT1[CREATE TABLE scenic_spots]
  CONN --> CT2[CREATE TABLE city_info]
  CT1 --> INS1[插入樣例景區]
  CT2 --> INS2[插入樣例城市]
  INS1 & INS2 --> COMMIT[commit & close]
```

### 分步講解
- 連線 `90-文档-Data/tourism.db` 或 `data/tourism.db` 後建立兩表（若不存在）。
- 以 `executemany` 插入多筆示例數據。
- 提交事務並關閉連線。

### 關鍵點總結
- **數據一致性**：景區表的 `city` 與城市表 `city_name` 相互關聯。
- **可擴充**：可加入更多列（如地理位置、票價）以測試複雜查詢。


