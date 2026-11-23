# 3. Direct Prompt Injection 與 Indirect Prompt Injection 的差異

## 入門比較

最容易理解的差別是：**惡意指令是由使用者直接送進來，還是藏在模型受命讀取的其他資料裡。**

| 比較項目 | Direct Prompt Injection | Indirect Prompt Injection |
|---|---|---|
| 指令從哪裡進入 | 主要使用者直接透過 query／input 傳入 | 外部來源或第三方資料被模型取回、讀取或放入上下文，例如網頁、郵件或文件 |
| 使用者是否直接提供攻擊指令 | 主要使用者直接輸入 query；AgentDojo 描述為使用者輸入覆蓋 system prompt | 使用者可能沒有提供，也沒有看到其中的指令 |
| 初學者例子 | 使用者在聊天中直接寫入企圖蓋過原任務的命令 | 使用者請助理摘要網頁；網頁內藏著企圖改變助理行為的命令 |
| 本批來源 | AgentDojo（S2，PDF p. 2）；Systematic Literature Review（S1，PDF p. 3） | AgentDojo（S2，PDF pp. 1–2）；Greshake et al.（S3，PDF pp. 1–3）；Systematic Literature Review（S1，PDF p. 3）；Spotlighting（S5，PDF pp. 1–2） |

## 來源分類差異

- **AgentDojo** 把 Direct 描述為使用者輸入覆蓋 system prompt；Indirect 則是模型取回的第三方資料中含有指令。（S2，PDF p. 2）
- **Systematic Literature Review 對 NIST 分類的轉述**以攻擊者身分及來源區分：Direct 由主要使用者透過 query 發動；Indirect 由非主要使用者改動外部資訊來源，再讓內容進入模型上下文。（S1，PDF p. 3）該回顧並註明 NIST 在不同段落對「direct prompting attack」和「direct prompt injection」的用語範圍並非完全一致：部分段落互換使用，另有段落把 Direct Prompt Injection 說成 Direct Prompting Attack 的子類。（S1，PDF p. 3，註 1）
- **Spotlighting** 將較常見的直接使用者輸入稱為 User Prompt Injection Attack，並說此類常被稱作 jailbreaking；Systematic Literature Review 對 NIST 分類的轉述則把 jailbreaking 視為 Direct Prompting Attack 的子類。此處保留兩來源的用語差異，不將其合併為唯一分類。（S5，PDF p. 2；S1，PDF p. 3）
- **Greshake et al.** 著重於整合式應用的遠端攻擊：攻擊者把指令放在可能被檢索的資料中，資料一旦被讀入，就可能間接控制模型。（S3，PDF pp. 1–3）此描述聚焦 Indirect Prompt Injection，並非該文對 Direct 的完整分類。（單一來源觀點）

## 主要資料來源

AgentDojo（S2，PDF pp. 1–2）；A Systematic Literature Review on LLM Defenses Against Prompt Injection and Jailbreaking: Expanding NIST Taxonomy（S1，PDF p. 3）；Spotlighting（S5，PDF pp. 1–2）；Greshake et al., *Not What You’ve Signed Up For*（S3，PDF pp. 1–3）。

