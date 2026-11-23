# Prompt Injection 教學簡報 Evidence Cards

本目錄的 Evidence Cards 只抽取目前通過三批檢查的 Wiki 內容，作為後續簡報大綱與逐頁撰稿的唯一知識依據。卡片中的來源 ID 與 PDF 頁碼沿用 Wiki 引用定位；後續撰稿不得跳過 Wiki 直接加入其他來源或研究結論。S4 未通過正文擷取核對，因此未納入。

## 卡片索引

| 順序 | Card ID | 教學主題 | 對應 Wiki 頁面 | 建議簡報位置 |
|---|---|---|---|---|
| 1 | [EC-01](card-01.md) | Prompt Injection 是什麼？ | `wiki/01-what-is-prompt-injection.md` | 第 1 頁 |
| 2 | [EC-02](card-02.md) | 為什麼 LLM 容易受到 Prompt Injection？ | `wiki/02-why-llms-are-vulnerable.md` | 第 2 頁 |
| 3 | [EC-03](card-03.md) | Direct Prompt Injection | `wiki/03-direct-vs-indirect.md` | 第 3 頁 |
| 4 | [EC-04](card-04.md) | Indirect Prompt Injection | `wiki/03-direct-vs-indirect.md`、`wiki/01-what-is-prompt-injection.md` | 第 3–4 頁 |
| 5 | [EC-05](card-05.md) | Prompt Injection 的安全風險 | `wiki/04-security-risks.md` | 第 5 頁 |
| 6 | [EC-06](card-06.md) | 常見防禦方法 | `wiki/05-defenses.md` | 第 6 頁，可拆頁 |
| 7 | [EC-07](card-07.md) | 防禦方法的限制 | `wiki/05-defenses.md`、`wiki/06-defense-limitations.md` | 第 7 頁 |
| 8 | [EC-08](card-08.md) | 為什麼目前不能宣稱已能完全防禦？ | `wiki/06-defense-limitations.md` | 第 8 頁 |

## 撰稿時必須保留

- Direct／Indirect 的來源分類用語差異（EC-03、EC-04）。
- 風險分類、測試案例與實際事件之間的證據邊界（EC-05）。
- 防禦成效只對應來源中的模型、任務與 benchmark；AgentDojo tool-filter 數值差異（EC-06、EC-07）。
- 「能否完全防禦」維持資料不足／尚無定論，不可改寫成已證明不可能或已經可完全防禦（EC-08）。
