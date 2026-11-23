# Prompt Injection LLM Wiki

本 repository 收錄 Prompt Injection 教學作業的核心成果：繁體中文 Wiki、Evidence Cards、教學簡報大綱與逐頁稿、Faithfulness 審查、HTML 簡報，以及 Loop／Graph 工作流程圖。

## 從 Wiki 開始

- [Wiki 首頁與閱讀順序](wiki/index.md)
- [來源目錄與 ingest 檢核](wiki/sources.md)
- [Evidence Cards 索引](cards/index.md)
- [簡報大綱](cards/slide-outline.md)
- [簡報逐頁稿](cards/slide-script.md)
- [Faithfulness Check](cards/faithfulness-check.md)
- [HTML 簡報](slides/index.html)
- [Loop／Graph 工作流程](workflow/loop-graph.png)

## Wiki 內容

Wiki 以繁體中文介紹 Prompt Injection 的基本概念、易受影響原因、Direct／Indirect Prompt Injection、可能風險、防禦方式與防禦限制。各頁附來源 ID 與 PDF 頁碼；分批檢查紀錄位於 `wiki/batch-01-check.md` 至 `wiki/batch-03-check.md`。

原始 PDF 未放入 repository。來源名稱、書目與 Wiki 引用定位整理於 `wiki/sources.md`；其中 S4（OWASP）正文擷取仍未通過，因此沒有用於 Wiki 或簡報內容。

## 瀏覽 HTML 簡報

在瀏覽器開啟 `slides/index.html`，使用左右方向鍵或頁面按鈕切換 9 頁投影片。頁碼顯示於底部控制列，HTML 使用內嵌 CSS／JavaScript，不需連網載入外部資產。

`cards/render-check.md` 記錄 HTML 靜態檢查結果與尚未完成的視覺檢查：目前執行環境無法存取本機瀏覽器，因此尚未確認 9 頁的實際顯示狀態，不標示最終 PASS。

## 教學證據與限制

後續簡報只能以 Evidence Cards 為知識依據。來源分類差異、實驗情境限制、AgentDojo tool-filter 約 7.5% 與 Table 5 的 6.84% 差異，以及 `Least Privilege` 資料不足與「能否完全防禦」尚無定論，均需保留。
