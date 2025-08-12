### 總覽
使用 Transformers 直接載入 `Qwen3-0.6B` 小模型，透過 `device_map="auto"` 自動分配設備，完成最小可行的推理（生成回覆）。

### 流程圖
```mermaid
flowchart TD
  M[AutoModelForCausalLM.from_pretrained\nQwen/Qwen3-0.6B] & T[AutoTokenizer.from_pretrained] --> IN[Tokenizer(prompt)]
  IN --> GEN[model.generate(max_new_tokens, temperature, top_p)]
  GEN --> DEC[tokenizer.decode]
  DEC --> OUT[輸出回覆]
```

### 分步講解
- 載入模型與分詞器：`trust_remote_code=True` 以支援官方自定義實作。
- 構造提示：簡單中文問候作為示例。
- 生成：`do_sample=True`、`temperature=0.7`、`top_p=0.9` 控制多樣性與流暢度。
- 解碼：`skip_special_tokens=True` 取得可讀文本。

### 關鍵點總結
- **設備自動映射**：`device_map="auto"` 可自動將權重分配到可用 GPU/CPU。
- **小模型上手快**：便於 Demo 與快速驗證，之後可替換為更大參數量模型。
- **溫度/Top-p**：主要控制生成的隨機性與多樣性。


