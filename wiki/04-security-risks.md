# 4. Prompt Injection 可能造成哪些安全風險？

Prompt Injection 的後果要看模型能讀取哪些資料、能呼叫哪些工具，以及應用如何處理模型輸出。本頁先列來源明確提出的風險類型，再把論文中的測試情境與實際事件區分開來。

## 來源採用的風險分類

Systematic Literature Review 轉述 NIST 的分類，按攻擊者想影響的系統目標分成四類。這是「攻擊目標」分類，不等同於以下論文逐一實驗驗證的結果。（S1，PDF p. 3）

| 分類 | 初學者版說明 | 來源支持的例子或範圍 |
|---|---|---|
| **Availability breakdown**（可用性受損） | 讓模型或系統無法穩定、及時地提供服務。 | NIST 分類的定義；Greshake et al. 將 denial of service 列為 Indirect Prompt Injection 可能造成的影響。（S1，PDF p. 3；S3，PDF p. 2） |
| **Integrity violation**（完整性遭破壞） | 讓模型偏離原本用途，產生符合攻擊者意圖的輸出。 | NIST 分類的定義；Greshake et al. 展示要求模型產生錯誤摘要的攻擊示例。（S1，PDF p. 3；S3，PDF p. 9） |
| **Privacy compromise**（隱私受損） | 未授權取得系統中的機密資料或使用者資料。 | NIST 分類的定義；AgentDojo 的郵件任務包含攻擊者試圖取得使用者郵件的測試情境。（S1，PDF p. 3；S2，PDF p. 2，Figure 1） |
| **Misuse enablement**（促成不當使用） | 繞過系統防護，讓模型產生原本要被防止的有害內容。 | NIST 分類的定義。（S1，PDF p. 3） |

## 論文討論的其他可能後果

- **未授權工具操作或執行程式：** AgentDojo 指出，成功攻擊可能讓外部攻擊者藉模型代表使用者採取行動，並將資料外洩、執行任意程式碼列為可能後果。（S2，PDF p. 1）這是論文對風險的說明，不代表該文的所有測試都執行了任意程式碼。
- **資料外洩、遠端控制或持續影響：** Greshake et al. 將資料竊取、遠端控制及 denial of service 列為 Indirect Prompt Injection 的影響，並在論文中展示攻擊流程。（S3，PDF pp. 1–2）
- **錯誤或被操控的摘要：** Greshake et al. 描述讓 Bing Chat 搜尋／摘要功能產生錯誤摘要的示例。（S3，PDF p. 9）

## 如何理解證據範圍

AgentDojo 是動態代理人測試環境，首版包含 97 項任務與 629 個安全測試案例；郵件外洩例子是其中的測試情境。（S2，PDF pp. 1–2）Greshake et al. 報告其示範涵蓋合成應用及 Bing Chat 等測試對象。（S3，PDF p. 1）因此本頁呈現的是來源中的分類、風險分析及測試／示範案例，不把它們改寫成已在一般使用情境普遍發生的實際事件。

## 來源分類的差異

Systematic Literature Review 轉述的 NIST 框架按 Availability、Integrity、Privacy、Misuse 等攻擊目標分類；Greshake et al. 則以其 Indirect Prompt Injection 威脅分析列出資料蒐集、入侵、詐騙、惡意程式、內容操控與可用性等類別。（S1，PDF p. 3；S3，PDF pp. 2–3）兩者分類目的與粒度不同，Wiki 分開呈現，不合併成單一清單。

## 主要資料來源

Systematic Literature Review（S1，PDF p. 3）；AgentDojo（S2，PDF pp. 1–2）；Greshake et al.（S3，PDF pp. 1–3、9）。
