# Evidence Card 06

- **Card ID：** EC-06
- **教學主題：** 常見防禦方法
- **核心主張：** 已通過 Wiki 整理的來源提出多種方向：Structured Queries 分開 prompt 與 data；Spotlighting 用 Delimiting、Datamarking、Encoding 提供資料來源線索；AgentDojo 測試 tool filtering、detector、prompt sandwiching。它們各有適用情境與限制。（S6，PDF pp. 7–8；S5，PDF pp. 2–6；S2，PDF pp. 8–9）
- **簡短初學者解釋：** 這些方法分別從區分指令與資料、標示外部資料、限制可用工具，或檢查工具回傳內容等角度處理問題。Wiki 只主張這些方法在來源描述的情境下被提出或測試。
- **對應 Wiki 頁面：** `wiki/05-defenses.md`
- **來源 ID：** S2、S5、S6；概覽補充：S1
- **PDF 頁碼：** S2 pp. 8–9、20；S5 pp. 2–6；S6 pp. 7–8、10、14；S1 p. 5
- **可用於哪一頁簡報：** 第 6 頁：防禦方法概覽（後續可拆成多頁）
- **限制 / 不可過度延伸的地方：** Spotlighting、AgentDojo、StruQ 的模型、任務和測試設定不同，成效不可跨設定直接比較或泛化至所有 LLM、RAG、Agent。Least Privilege 在 Wiki 中是資料不足；不得把 tool filtering 直接等同於 Least Privilege。
