# 6. 為什麼目前仍無法完全防禦？

## 初學者版說明

目前可讀來源呈現的是：各種方法能在特定設計或測試中降低部分攻擊成功，但每種方法都有適用條件或已觀察到的限制。這些來源不足以證明「所有 Prompt Injection 都不可能被防禦」，也不足以證明存在一種適用於所有 LLM、RAG 或 Agent 系統的完整解法。因此，本頁整理來源明確記錄的限制，不把它們延伸成普遍定律。（S2，PDF pp. 9、20；S5，PDF pp. 4–6；S6，PDF pp. 10、14）

## 為什麼單一防禦方法可能不足？

來源展示的限制各不相同，並非一項統一的失效原因：

- **指令與資料的界線可能被混淆：** Spotlighting 的實驗指出，單靠 system prompt 提醒或文件界定符可能不足；如果攻擊者能仿造界定符，就可能混淆模型。（S5，PDF pp. 4、6）
- **方法可能有特定輸入條件：** 靜態 Datamarking 若只標記空格，可能漏掉沒有空格的攻擊文字；Spotlighting 論文因此提出可考慮動態改變標記及位置。（S5，PDF p. 6）
- **模型與任務能力會影響可用性：** Encoding 要求模型解碼輸入；Spotlighting 論文指出較弱模型可能在下游任務表現下降，也可能解碼錯誤或產生幻覺。（S5，PDF p. 5）
- **防禦未必涵蓋其他攻擊類型：** StruQ 作者說明其方法不適用於開放式多輪聊天，且不是為 jailbreak 或 data extraction 設計；其結果表中的 GCG 最佳化攻擊仍有非零成功率。（S6，PDF pp. 10、14）

以上是來源對各方法的具體限制，不代表所有系統都會遇到完全相同的問題。

## 方法的適用範圍與限制

| 方法 | 來源明確描述的適用情境 | 已知限制／測試結果 | 來源與範圍 |
|---|---|---|---|
| **Structured Queries（StruQ）** | 由開發者透過 API 或 library 呼叫、能分開任務 prompt 與輸入 data 的程式化應用。 | 不適用開放式多輪聊天，也未設計來防禦 jailbreak、data extraction 等攻擊；GCG 結果仍非零，強最佳化攻擊的防禦仍是作者指出的開放問題。 | S6，PDF pp. 7–8、10、14；StruQ 論文的設計與測試範圍。 |
| **Spotlighting：Delimiting** | 能在輸入中圈出外部文件的摘要或問答流程。 | 只靠提示或界定符的效果有限；若攻擊者知道標記，可嘗試在文件中插入相同標記。 | S5，PDF pp. 2–4、6；該論文的實驗及分析。 |
| **Spotlighting：Datamarking** | 外部文字可被轉換標記，且模型仍能完成預定語言任務。 | 僅靜態替換空格可能漏掉無空格攻擊文字；論文提出動態標記／位置作為方向。 | S5，PDF pp. 3、5–6；該論文的分析。 |
| **Spotlighting：Encoding** | 模型能可靠解碼，且特定下游任務已驗證可用。 | 較弱模型可能任務表現下降、解碼錯誤或幻覺；成效須在實際模型和任務確認。 | S5，PDF pp. 3、5；該論文的模型與任務測試。 |
| **Tool filtering** | 能在讀取不可信資料前，預先選定完成任務所需工具的 Agent 流程。 | 若工具需求要看回傳結果才知道，難以事先篩選；若正常任務與攻擊能用相同工具，篩選無法區分。AgentDojo 報告此限制出現在其 17% 測試案例。 | S2，PDF pp. 8–9；AgentDojo 測試案例。 |
| **Prompt injection detector** | 可在代理人處理工具輸出前檢查內容的 tool-calling 流程。 | AgentDojo 的 BERT detector 出現 false positives 並降低正常任務 utility。其 GPT-4o 測試中 targeted ASR 為 7.95%、benign utility 為 41.49%；no defense 對照值為 57.69% 與 69.0%。 | S2，PDF pp. 8–9、20，Table 5；AgentDojo 指定配置。 |
| **Prompt sandwiching** | 每次工具呼叫後都能重新附上使用者任務的代理人流程。 | AgentDojo 作者認為它不太可能抵抗自適應攻擊；GPT-4o 測試中的 targeted ASR 為 27.82%，no defense 為 57.69%。 | S2，PDF pp. 8–9、20，Table 5；AgentDojo 指定配置。 |

上述 AgentDojo 數值只描述該 benchmark、模型和配置。該論文 p. 9 對 tool filter 的文字敘述約為 7.5%，Table 5 則為 6.84%；兩個數字在此分開保留，不自行選定或合併。（S2，PDF pp. 9、20）Spotlighting 論文與 AgentDojo 的測試任務、模型及防禦配置也不同，結果不可視為同一基準直接比較。（S2，PDF pp. 8、20；S5，PDF pp. 4–5）

## 是否存在 trade-off？

在 AgentDojo 的測試中，detector 降低攻擊成功率的同時，也因 false positives 使 benign utility 低於 no defense 對照組。這是該測試設定中可觀察到的安全與正常任務效用取捨，不代表每種 detector、模型或部署方式都會有相同幅度。（S2，PDF pp. 9、20，Table 5）

Spotlighting 論文則指出 Encoding 可能影響較弱模型的下游任務表現；該來源支持「需考量解碼能力與任務表現」這項限制，但本批資料不足以將其量化成與安全成效對稱的 trade-off。（S5，PDF p. 5）

## 哪些結論仍受測試環境限制？

- AgentDojo 的 ASR、benign utility 與 17% 限制比例是其 benchmark 中的觀察，不可直接推論其他 Agent 或所有工具使用情境。（S2，PDF pp. 6、9、20）
- Spotlighting 的 ASR 數值來自該論文指定模型、摘要／問答任務及攻擊設定；論文也說明模型能力會影響解碼和任務結果。（S5，PDF pp. 4–6）
- StruQ 的結論受其程式化應用設計和論文測試攻擊範圍限制；作者明確指出開放式多輪聊天及其他攻擊類型不在其方法適用範圍內。（S6，PDF pp. 7–8、10、14）
- **「是否存在能完全防禦所有 Prompt Injection 的方法」：資料不足／尚無定論。** 本批來源指出多種方法的具體限制及部分未解問題，但不足以證明一個涵蓋所有 LLM、RAG、Agent、任務和攻擊者能力的普遍結論。此處不把單篇論文的實驗直接泛化。（S2，PDF pp. 9、20；S5，PDF pp. 4–6；S6，PDF pp. 10、14）
- **Least Privilege：資料不足。** 已核對的來源沒有提供足夠內容作為本頁比較其定義、適用情境或成效的依據；不能只因 tool filtering 涉及工具選擇，就把兩個術語視為相同。（S2，PDF pp. 8–9）

## 主要資料來源

AgentDojo（S2，PDF pp. 6、8–9、20）；Spotlighting（S5，PDF pp. 2–6）；StruQ（S6，PDF pp. 7–8、10、14）。本頁沒有使用 S4。
