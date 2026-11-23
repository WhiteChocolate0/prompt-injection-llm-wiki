# 第 1 批檢查紀錄

## 批次範圍

主題：Prompt Injection 基本概念、LLM 對 Prompt Injection 的易受影響原因、Direct Prompt Injection 與 Indirect Prompt Injection 的差異。

本批採用正文可讀且可核對的來源：S1、S2、S3、S5、S6。S4 的文字擷取出現字符間距錯亂，暫不引用，列為待修復來源；本批不使用 S4 作為主張依據，也不根據其檔案名稱推定正文內容。

## 檢查結果

| 檢查項目 | 結果 | 說明 |
|---|---|---|
| 來源正文可讀 | 通過 | PDFKit 可讀取本批五份採用來源正文，並逐頁檢視引用頁面：S1 p. 3；S2 pp. 1–2；S3 pp. 1–3；S5 pp. 1–2；S6 pp. 1–2。S4 擷取文字字符間距錯亂，已排除並記錄待修復。 |
| 主張與來源對應 | 通過 | 三個主題所需內容均有來源支持；各段主張附來源 ID 與 PDF 頁碼；例子標示為來源測試情境或教學化轉述，未發現內容缺口需推測填補。 |
| 引用可核對 | 通過 | 引用所列頁碼均在相應 PDF 範圍內，且正文頁面包含對應定義、說明或分類。未把檔名當作內容證據。 |
| 初學者可讀性 | 通過 | 使用簡明定義與郵件助理例子，先解釋核心差異，再列來源說法。 |
| 術語一致性 | 通過 | 使用 Prompt Injection、Direct Prompt Injection、Indirect Prompt Injection、LLM、Prompt 等原文術語，中文解釋保持一致。 |
| 來源衝突是否標示 | 通過 | 並列 AgentDojo、Systematic Literature Review（轉述 NIST）及 Spotlighting 的分類用語；標明 NIST 用語範圍差異與 jailbreaking 分類差異。 |
| 是否有未核實內容 | 無 | 重要主張均附正文頁碼；教學例子標明其性質；未採用無法正常讀取的 S4。 |

## 來源核對摘要

- **Prompt Injection 基本概念：** AgentDojo PDF p. 1 說明第三方資料中的惡意指令及工具代理風險；StruQ PDF pp. 1–2 說明資料中夾帶指令可使模型偏離原應用任務；Greshake et al. PDF pp. 1–3 說明檢索內容可間接控制整合式應用。
- **易受影響原因：** AgentDojo PDF p. 1、StruQ PDF pp. 1–2、Spotlighting PDF p. 1 均談到模型難以區分指令與資料，角度各自保留。
- **Direct／Indirect 差異：** AgentDojo PDF p. 2；Systematic Literature Review PDF p. 3（含其對 NIST 術語的註記）；Spotlighting PDF p. 2；Greshake et al. PDF pp. 1–3。

## 批次決策

本批使用來源通過可讀性、主張對應、引用可核對及內容充分性檢查，已完成指定三個主題。S4 不納入本批，須先修復文字擷取或取得可正常閱讀版本，再另行檢核；在完成檢核前不得引用 S4。
