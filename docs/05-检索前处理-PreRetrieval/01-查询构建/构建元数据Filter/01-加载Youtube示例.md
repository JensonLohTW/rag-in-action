### 總覽
使用 `YoutubeLoader` 並開啟 `add_video_info=True`，將 YouTube 視頻的標題、作者、發佈日期、觀看數等元數據一併讀入，便於後續構建向量庫或基於元數據的檢索。

### 流程圖
```mermaid
flowchart TD
  U[YouTube URL] --> L[YoutubeLoader.add_video_info=True]
  L --> D[文檔列表 docs]
  D --> M[打印 docs[0].metadata]
```

### 分步講解
- 輸入：單一 YouTube 影片 URL。
- 加載：`YoutubeLoader.from_youtube_url(url, add_video_info=True).load()` 返回一組 `Document`。
- 輸出：直接打印第一個文檔的 `metadata` 字段，觀察包含的結構化信息。

### 關鍵點總結
- **add_video_info**：打開後會抓取影片標題、ID、作者、時長、觀看數等。
- **用途**：作為元數據欄位，可用於後續 `SelfQueryRetriever` 自動生成過濾條件。
- **風險**：YouTube 訪問可能受限；請處理網路超時與異常。


