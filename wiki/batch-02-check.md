# 第 2 批檢查紀錄

## 批次範圍

主題：「Prompt Injection 的安全風險與常見防禦方式」，更新 `04-security-risks.md` 和 `05-defenses.md`。

本批採用可讀且可核對的來源 S1、S2、S3、S5、S6。S4 仍因文字擷取字符間距錯亂而排除，未用作任何主張依據。檢核及引用位置已更新到 `sources.md`。

## 檢查結果

| 檢查項目 | 結果 | 說明 |
|---|---|---|
| 來源正文可讀 | 通過 | 逐頁讀取本批使用頁面：S1 pp. 3、5；S2 pp. 1–2、6、8–9、20；S3 pp. 1–3、9；S5 pp. 1–6；S6 pp. 7–8、10、14。S4 未使用，維持待修復狀態。 |
| 主張與來源對應 | 通過 | 風險分類、測試例子及各防禦方法均附來源 ID 與頁碼；不同防禦效果與限制依來源分開記錄。Least Privilege 已標示資料不足，未自行定義。 |
| 引用可核對 | 通過 | 所列 PDF 頁碼含對應分類、方法描述、實驗結果或限制；AgentDojo 的 tool filter 敘述與表格數字差異（約 7.5% vs. 6.84%）明確標示。 |
| 初學者可讀性 | 通過 | 使用四類簡明風險說明和每種防禦的核心概念、適用情境及限制，並說明 benchmark／論文示例不是普遍實際事件。 |
| 術語一致性 | 通過 | 保留並一致使用 Availability breakdown、Integrity violation、Privacy compromise、Misuse enablement、Structured Queries、Spotlighting、Datamarking、Encoding、tool filtering、ASR 等術語。 |
| 來源衝突已標示 | 通過 | 分開說明 NIST 目標分類與 Greshake et al. 威脅分類；並列 Spotlighting 與 AgentDojo 不同測試設定的效果，及 AgentDojo 同篇論文文字與表格的 tool-filter 數值差異。 |
| 未核實內容 | 無 | 沒有使用 S4 或以檔名推測正文；所有實驗成效均限定在來源所述設定，缺乏來源的 Least Privilege 以「資料不足」標示。 |

## 來源核對摘要

- **風險分類：** Systematic Literature Review PDF p. 3 對 NIST 的四類攻擊目標作定義；Greshake et al. PDF pp. 2–3 以 Indirect Prompt Injection 威脅分類呈現其風險類別。
- **風險例子及證據範圍：** AgentDojo PDF pp. 1–2 包含潛在後果及其郵件外洩 benchmark 情境；Greshake et al. PDF p. 1 說明其合成應用及 Bing Chat 示範，PDF p. 9 包含錯誤摘要攻擊示例。
- **防禦方法：** StruQ PDF pp. 7–8、10、14；Spotlighting PDF pp. 1–6；AgentDojo PDF pp. 8–9、20；Systematic Literature Review PDF p. 5。

## 批次決策

重要檢查均通過，本批指定頁面已更新。S4 尚未修復前仍不可引用。Least Privilege 在目前可讀來源中缺乏足夠正文支持，已留作資料缺口；若之後需納入其定義或建議，須先 ingest 並核對可讀來源。
