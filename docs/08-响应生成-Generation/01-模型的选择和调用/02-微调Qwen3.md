### 總覽
基於 `Qwen3-0.6B` 的指令式微調示例：將 SQuAD 前 100 條樣本格式化為「問-上下文-答」文本，使用 `Trainer` 快速完成單輪訓練並輸出權重，最後做一次推理驗證。

### 流程圖
```mermaid
flowchart TD
  DS[load_dataset('squad')[:100]] --> MAP[格式化問答文本]
  MAP --> TOK[tokenizer(..., max_length=512, padding, truncation)]
  TOK --> TRAIN[Trainer(model, TrainingArguments, DataCollator)]
  TRAIN --> SAVE[save_model / save_pretrained]
  SAVE --> TEST[生成測試]
```

### 分步講解
- 數據準備：將 SQuAD 樣本映射為 `問題/上下文/回答` 單段文本。
- Tokenize：最大長度 512，批量處理，刪除原始欄位以加速訓練。
- 訓練：`fp16=True`，`per_device_train_batch_size=4`，`gradient_accumulation_steps=4`；適合單卡試跑。
- 保存與驗證：保存至 `./qwen3_finetuned`，再以簡短提示做生成測試。

### 關鍵點總結
- **小樣本起步**：便於走通流程；正式場景需清洗與擴充數據。
- **監督信號設計**：若是對話式任務，建議模板化對話格式以提升穩定度。
- **資源與時長**：依硬體調整 batch/accumulation/epoch；留意顯存。


