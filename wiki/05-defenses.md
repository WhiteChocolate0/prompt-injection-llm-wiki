# 5. 常見防禦方式

目前來源介紹的防禦方式各有適用條件。下列方法可降低特定測試情境中的攻擊成功率，但不能只憑一個實驗結果推論在所有模型、任務或部署環境都有效。**ASR** 是 Attack Success Rate（攻擊成功率）；AgentDojo 將 targeted ASR 定義為測試案例中攻擊者目標達成的比例，並把 benign utility 定義為未受攻擊時模型完成使用者任務的比例。（S2，PDF p. 6）

## 1. Structured Queries（StruQ）

- **方法名稱：** Structured Queries；StruQ 是 Chen et al. 實作此方向的系統。
- **核心概念：** 把 prompt（應遵循的指令）和 data（待處理內容）分開編碼；StruQ 使用安全前端與特殊分隔符，並以 structured instruction tuning 訓練模型只遵從 prompt 部分的指令。（S6，PDF pp. 7–8）
- **適用情境：** 由開發者透過 API 或 library 呼叫模型的程式化應用，能明確分開任務指令和輸入資料。（S6，PDF pp. 7、14）
- **已知限制：** 作者指出 StruQ 不適用於開放式多輪聊天；它也不是用來防禦 jailbreak、data extraction 等其他攻擊。結果表顯示 GCG 等最佳化攻擊仍有非零成功率；作者表示如何防禦強最佳化攻擊仍是開放問題。（S6，PDF pp. 10、14）

## 2. Spotlighting

Spotlighting 是以輸入轉換提供資料來源線索，幫助模型分辨外部文件和使用者指令。原論文提出三種做法，主要針對 Indirect Prompt Injection。（S5，PDF pp. 1–3）

### 2.1 Delimiting（加界定符）

- **核心概念：** 在外部文件前後加上特殊標記，並在 system prompt 說明文件內容不可當成新指令。（S5，PDF pp. 2–3）
- **適用情境：** 可在輸入中清楚圈出文件區塊的摘要或問答任務。（S5，PDF pp. 2–3）
- **已知限制：** Spotlighting 的實驗顯示，只靠 system prompt 提醒效果有限；若攻擊者知道標記方式，可能在文件內插入相同界定符以混淆模型，因此作者不建議單獨依賴此法。（S5，PDF pp. 4、6）

### 2.2 Datamarking（資料標記）

- **核心概念：** 在文件文字中反覆插入標記，例如用特殊符號取代空格，讓模型持續看到該段是外部文件。（S5，PDF p. 3）
- **適用情境：** 原文內容可接受標記轉換，而且模型仍能完成摘要、問答等下游語言任務。（S5，PDF pp. 3、5）
- **已知限制：** 靜態地只替換空格可能無法標記沒有空格的攻擊文字。論文建議考慮動態改變標記及其插入位置。（S5，PDF p. 6）

### 2.3 Encoding（編碼）

- **核心概念：** 將外部文字轉成 Base64、ROT13 或 binary 等形式，並要求模型解碼、處理內容，但不要遵循其中的命令。（S5，PDF p. 3）
- **適用情境：** 模型有能力可靠地解碼輸入，且實際任務已測試確認可用。（S5，PDF pp. 3、5）
- **已知限制：** 論文指出較弱模型在解碼後的任務表現可能下降，亦可能出現解碼錯誤或幻覺；作者建議只在適當模型上使用並按實際情境驗證。（S5，PDF p. 5）

**Spotlighting 的實驗結果要按設定解讀：** 原論文在 GPT-3.5-Turbo 的文件摘要任務中，報告 Datamarking 將 ASR 從約 50% 降到 3% 以下；Encoding 在其摘要任務報告 0%，在問答任務報告 1.8%。（S5，PDF pp. 4–5）這些數字是該論文指定模型與任務的測試結果，不是所有情境都能達到的保證。較新的實驗室（AgentDojo）中，僅用界定符時攻擊仍成功；該測試配置和 Spotlighting 論文不同，不能直接把兩組結果當成同一基準比較。（S2，PDF pp. 8、20；S5，PDF pp. 4–5）

## 3. Tool filtering（工具篩選／限制工具）

- **方法名稱：** AgentDojo 稱為 tool filter，是一種簡單的 isolation（隔離）方式。（S2，PDF p. 8）
- **核心概念：** 在讀取不可信資料前，先選出完成使用者任務需要的工具，執行時不開放其他工具。例如，只需讀郵件摘要時可先限制代理人使用讀取工具。（S2，PDF p. 9）
- **適用情境：** 使用者任務所需工具可以事先規劃，而且攻擊目標需要額外權限的工具時，例如正當任務只需讀取、攻擊目標卻要寄出郵件。（S2，PDF p. 9）
- **已知限制：** 若下一步要用哪些工具取決於工具回傳結果，便難以事先篩選；若正當任務與攻擊都能使用同一批工具，也無法靠篩選分開。AgentDojo 指出這種限制出現在其 17% 測試案例中。（S2，PDF p. 9）
- **實驗成效範圍：** AgentDojo 的 GPT-4o 設定下，Table 5 報告 tool filter 的 targeted ASR 為 6.84%，no defense 為 57.69%。（S2，PDF p. 20，Table 5）同一論文 p. 9 的文字敘述約寫 7.5%；本 Wiki 保留兩處數值差異，不自行合併。這只表示該基準中的結果。

## 4. Prompt injection detector（注入偵測器）

- **核心概念：** AgentDojo 使用 BERT classifier 檢查每次 tool call 的輸出，若偵測到 prompt injection 就中止代理人。（S2，PDF p. 8）
- **適用情境：** 工具輸出可在交給代理人繼續處理前先行檢查的 tool-calling 系統。（S2，PDF p. 8）
- **已知限制：** 在 AgentDojo 測試中，detector 有過多 false positives，降低了正常任務的 utility。（S2，PDF p. 9）GPT-4o 的該組測試中 targeted ASR 為 7.95%，但 benign utility 為 41.49%；no defense 分別為 57.69% 與 69.0%。（S2，PDF p. 20，Table 5）這是同一實驗設定下的取捨，不代表其他偵測器或模型的結果。

## 5. Prompt sandwiching（重申使用者指令）

- **核心概念：** 每次工具呼叫後，再重複一次使用者原本的任務指令。（S2，PDF p. 8）
- **適用情境：** 每次工具回應後都能重新附上使用者任務的代理人流程。（S2，PDF p. 8）
- **已知限制：** AgentDojo 作者認為此法可能擋住其所測攻擊，但不太可能抵抗自適應攻擊；例如外部指令要求模型忽略之後重複的指令。（S2，PDF p. 9）GPT-4o 該組測試的 targeted ASR 是 27.82%，no defense 是 57.69%。（S2，PDF p. 20，Table 5）

## 本批資料不足的術語

**Least Privilege：資料不足。** 本批可讀來源沒有提供足以直接對應此術語的定義和完整操作說明。AgentDojo 的 tool filtering 是來源明載、在基準中測試的方法；本頁不把它直接改稱 Least Privilege。（S2，PDF pp. 8–9）

Systematic Literature Review 也把「分隔可信／不可信資料」及「過濾第三方內容中的指令」列為針對 Indirect Prompt Injection 的防禦方向，但該回顧在概述處未提供兩者足以逐項比較的實作步驟或獨立成效數據。（S1，PDF p. 5）需更詳細介紹時，應回到其引用的原始研究逐一核對。

## 主要資料來源

StruQ（S6，PDF pp. 7–8、10、14）；Spotlighting（S5，PDF pp. 1–6）；AgentDojo（S2，PDF pp. 8–9、20）；Systematic Literature Review（S1，PDF p. 5）。
