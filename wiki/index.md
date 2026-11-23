# Prompt Injection Wiki

> 讀者：第一次接觸 Prompt Injection 的初學者。用途：課堂教學與自學。語言：繁體中文，保留重要英文專有名詞。

本 Wiki 以已 ingest 且正文可讀取的來源為依據。來源若無法讀取、引用無法回到正文，或對應章節內容不足，先停止該批資料整理並修正；不得以檔名推測或自行補寫結論。詳細流程見 [`../AGENTS.md`](../AGENTS.md)，來源及檢核紀錄見 [來源目錄](sources.md)。

## 主題頁

依序從定義、成因、攻擊類型讀起，再了解風險、防禦方式與防禦限制。六頁均已完成初步整理；各頁對來源不足之處另有標示。

| 順序 | Wiki 頁面 | 狀態 | 本頁簡介 |
|---|---|---|---|
| 1 | [Prompt Injection 是什麼？](01-what-is-prompt-injection.md) | 已整理 | 認識基本概念，並以外部資料中的指令說明入門例子。 |
| 2 | [為什麼 LLM 容易受到 Prompt Injection？](02-why-llms-are-vulnerable.md) | 已整理 | 說明模型輸入中「要遵循的指令」與「要處理的資料」可能難以區分。 |
| 3 | [Direct Prompt Injection 與 Indirect Prompt Injection 的差異](03-direct-vs-indirect.md) | 已整理 | 比較攻擊指令直接由使用者送入，或藏在模型讀取的外部資料中，並保留來源分類差異。 |
| 4 | [Prompt Injection 可能造成哪些安全風險？](04-security-risks.md) | 已整理 | 介紹來源採用的風險分類與論文案例，並註明實驗／示範的範圍。 |
| 5 | [常見防禦方式](05-defenses.md) | 已整理 | 介紹 Structured Queries、Spotlighting、tool filtering 等方法及其適用情境、限制。 |
| 6 | [為什麼目前仍無法完全防禦？](06-defense-limitations.md) | 已整理 | 綜整單一方法的限制、測試環境範圍、已觀察到的 trade-off 與尚未能下結論之處。 |

批次檢查紀錄：[第 1 批](batch-01-check.md)、[第 2 批](batch-02-check.md)、[第 3 批](batch-03-check.md)。來源及 ingest 狀態見 [來源目錄](sources.md)。

## 後續教學產出

- 課堂講義或簡報
- 初學者測驗或練習題

這些是 Wiki 的後續用途；本 Wiki 結構不包含 HTML 簡報。

