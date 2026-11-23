# Evidence Card 07

- **Card ID：** EC-07
- **教學主題：** 防禦方法的限制
- **核心主張：** Wiki 所整理的限制包括：界定符可能被仿造、靜態標記可能漏掉無空格文字、Encoding 可能影響較弱模型的任務表現、tool filtering 可能受工具需求或共享工具限制、detector 可能有 false positives；StruQ 也有明確適用範圍及未解攻擊。（S5，PDF pp. 4–6；S2，PDF pp. 9、20；S6，PDF pp. 10、14）
- **簡短初學者解釋：** 防禦方法不是萬用開關：有些依賴資料格式或模型能力，有些可能誤擋正常任務，另一些只適合特定系統設計。
- **對應 Wiki 頁面：** `wiki/05-defenses.md`；統整：`wiki/06-defense-limitations.md`
- **來源 ID：** S2、S5、S6
- **PDF 頁碼：** S2 pp. 9、20；S5 pp. 4–6；S6 pp. 10、14
- **可用於哪一頁簡報：** 第 7 頁：防禦的適用範圍與限制
- **限制 / 不可過度延伸的地方：** 每一限制須連同原方法及來源測試情境呈現；AgentDojo 的數據屬其 benchmark 配置。tool filter 在該文 p. 9 的文字敘述約 7.5%，Table 5 為 6.84%，兩者須保留差異。
