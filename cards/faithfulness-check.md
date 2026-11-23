# Prompt Injection 簡報逐頁稿 Faithfulness 審查

## 審查範圍

只對照 `cards/slide-script.md`、`cards/index.md` 與 `cards/card-01.md` 至 `cards/card-08.md`。未查閱原始 PDF、Wiki 或其他外部資料。以下「來源支持」表示主張在所列 Evidence Cards 中有對應內容。

| Slide | Faithfulness | Source Alignment | Evidence Boundary | 教學清楚度 | 問題 |
|---|---|---|---|---|---|
| 1 | 通過 | 通過 | 通過 | 通過 | 定義與郵件助理例子均對應 EC-01；講者稿明確說明郵件例子是 AgentDojo 測試情境。 |
| 2 | 通過 | 通過 | 通過 | 通過 | 指令與資料難以區分的原因對應 EC-02；未加入模型內部機制的新結論。 |
| 3 | 通過 | 通過 | 通過 | 通過 | Direct／Indirect 的來源入口差異與來源用語差異均保留，符合 EC-03、EC-04。 |
| 4 | 通過 | 通過 | 通過 | 通過 | 四類風險與論文例子對應 EC-05；分類差異及測試／示範情境限制有提醒。 |
| 5 | 通過 | 通過 | 通過 | 通過 | Structured Queries／StruQ 與 Spotlighting 概念、三種做法及適用限制對應 EC-06；未宣稱普遍有效。 |
| 6 | 通過 | 通過 | 通過 | 通過 | Tool filtering、detector、Prompt sandwiching 對應 EC-06／EC-07；Least Privilege 保留資料不足。 |
| 7 | 通過 | 通過 | 通過 | 通過 | 聚焦方法本身的質性限制，未列實驗分數；與 Slide 8 的實驗解讀分工清楚。 |
| 8 | 通過 | 通過 | 通過 | 通過 | 聚焦測試情境與數值解讀；AgentDojo 約 7.5%（正文敘述）與 6.84%（Table 5）分開呈現，未合併。 |
| 9 | 通過 | 通過 | 通過 | 通過 | 保留「資料不足／尚無定論」，明確不把它改寫成已證明完全防禦不可能。 |

## Known Constraints 核對

- **Direct／Indirect 分類差異：** 已保留於 Slide 3 的注意事項及講者稿。
- **S4（OWASP）：** 未用作投影片主張或頁底來源。
- **AgentDojo 約 7.5% 與 6.84%：** Slide 8 標示為正文敘述與 Table 5 的不同位置，沒有合併成單一數字。
- **Least Privilege：** Slide 6 保留「資料不足」，並提醒不可直接等同 tool filtering。
- **能否完全防禦：** Slide 9 保留「資料不足／尚無定論」。
- **未宣稱不可能：** Slide 9 明確禁止把資料不足改寫成「已證明完全防禦不可能」。
- **Slide 7／8 分工：** Slide 7 討論各方法的質性適用條件與限制，不列數值；Slide 8 說明實驗數字的模型／任務／benchmark 範圍及如何保留數值差異，未重複上一頁的限制清單。

### 必須修正

無。未發現影響來源忠實性、證據邊界或結論正確性的問題。

### 建議修正

- Slide 7 的第四點同時提到 Tool filtering、detector 與 StruQ；若版面擁擠，可在製作投影片時縮短文字或改用表格，保留逐頁稿的細節即可。
- Slide 8 若採用比較表，建議清楚標示「正文敘述」與「Table 5」為不同來源位置，避免視覺上看成同一項結果的兩種等價呈現。

### Overall Result

PASS：全部重要檢查通過，可進入 HTML 階段
