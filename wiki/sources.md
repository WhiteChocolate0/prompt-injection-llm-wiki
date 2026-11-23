# 來源目錄與 ingest 檢核

## 檢核規則

每批來源須確認正文可讀、來源身分可核對、引用可定位、內容足以支援預定章節。任何一項不通過，就先停在該批修正，不進入後續 Wiki 整理。詳見 [`../AGENTS.md`](../AGENTS.md)。

## 目前工作區來源

六份 PDF 已逐一嘗試透過 PDFKit 擷取正文。Batch 1–3 只採用正文清晰可讀、且能逐頁核對的來源（S1、S2、S3、S5、S6）；S4 的文字擷取字符間距錯亂，三批均未引用，待修復或取得可讀版本後再檢核。主張均須逐項對應具體段落／頁碼。

| 來源 ID | 工作區檔名 | 正文可讀 | 可供核對的 Wiki 區塊 |
|---|---|---|---|
| S1 | `2026 Systematic Literature Review.pdf` | 是，PDF pp. 3、5 可讀 | Batch 1：3；Batch 2：4、5 |
| S2 | `AgentDojo.pdf` | 是，PDF pp. 1–2、6、8–9、20 可讀 | Batch 1：1、2、3；Batch 2：4、5；Batch 3：6 |
| S3 | `Greshake et al. — Indirect Prompt Injection.pdf` | 是，PDF pp. 1–3、9 可讀 | Batch 1：1、3；Batch 2：4 |
| S4 | `OWASP LLM01-2026 Prompt Injection.pdf` | **暫不通過**：抽取文字字符間距錯亂 | Batch 1–3 均不引用；修復後再檢核 |
| S5 | `Spotlighting.pdf` | 是，PDF pp. 1–6 可讀 | Batch 1：1、2、3；Batch 2：5；Batch 3：6 |
| S6 | `StruQ：Structured Queries.pdf` | 是，PDF pp. 1–2、7–8、10、14 可讀 | Batch 1：1、2；Batch 2：5；Batch 3：6 |

## 書目補全欄位

整理各主題頁時，依來源正文補全其書目資料，不得由檔名推測：

| 來源 ID | 正文標題 | 作者／機構 | 版本／日期 | DOI／URL（若有） | Wiki 引用定位 |
|---|---|---|---|---|---|
| S1 | A Systematic Literature Review on LLM Defenses Against Prompt Injection and Jailbreaking: Expanding NIST Taxonomy | 作者群見 PDF p. 1 | PDF p. 1 標示 2026-01-27 | 依正文補全 | Batch 1 p. 3；Batch 2 pp. 3、5 |
| S2 | AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents | Debenedetti et al. | arXiv v3，2024-11-24；NeurIPS 2024 | PDF p. 1 列出專案網址 | Batch 1 pp. 1–2；Batch 2 pp. 1–2、6、8–9、20；Batch 3 pp. 6、8–9、20 |
| S3 | Not What You’ve Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection | Greshake et al. | arXiv v2，2023-05-05；ACM CCS AISec ’23 | DOI: 10.1145/3605764.3623985 | Batch 1 pp. 1–3；Batch 2 pp. 1–3、9 |
| S4 | 待由可讀正文核對（目前僅有檔案名可供識別） | 待核對 | 待核對 | 待核對 | Batch 1–3 未引用；文字擷取待修復 |
| S5 | Defending Against Indirect Prompt Injection Attacks With Spotlighting | Hines et al. | arXiv v1，2024-03-20 | Microsoft／arXiv 資料見 PDF p. 1 | Batch 1 pp. 1–2；Batch 2 pp. 1–6；Batch 3 pp. 2–6 |
| S6 | StruQ: Defending Against Prompt Injection with Structured Queries | Chen et al. | arXiv v2，2024-09-25；USENIX Security 2025 | 依正文補全 | Batch 1 pp. 1–2；Batch 2 pp. 7–8、10、14；Batch 3 pp. 7–8、10、14 |

## 第 1 批使用範圍

本批整理主題 1–3。採用 S1、S2、S3、S5、S6；S4 暫緩，不以其正文作為依據。各主張的 PDF 定位已記在三個主題頁正文中。批次品質檢查見 [`batch-01-check.md`](batch-01-check.md)。

## 第 2 批使用範圍

本批整理主題 4–5。採用 S1、S2、S3、S5、S6；S4 仍暫緩。風險分類、測試案例與防禦成效均附 PDF 定位，並註明其分類或實驗範圍。批次品質檢查見 [`batch-02-check.md`](batch-02-check.md)。

## 第 3 批使用範圍

本批整理主題 6，並收斂索引與來源記錄。採用已可讀且先前已核對的 S2、S5、S6；S4 仍不可用且未引用。主張集中於各來源明確記載的適用範圍、限制、測試結果與取捨，不推導普遍性的完全防禦結論。批次品質檢查及全 Wiki 收斂檢查見 [`batch-03-check.md`](batch-03-check.md)。

