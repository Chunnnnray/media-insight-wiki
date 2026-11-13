# 傳播觀察誌｜Media Insight Wiki

一個以繁體中文整理「傳播理論」、「媒體議題」與「台灣實際案例」的互動式知識庫網站。本專案除了呈現人文雜誌風格的網頁成果，也示範如何透過 `AGENTS.md` 建立一套可重複使用、結構化的 AI 協作與擴充規則。

## 專案特色

- **模組化單頁資料架構**：所有知識條目集中管理於 `index.html` 內建的 `WIKI_ENTRIES` 資料陣列中，由前端渲染引擎自動生成卡片與彈出式深度閱讀視窗（Modal）。
- **一致的三段式分析脈絡**：每筆條目皆遵循固定結構，包含外層摘要、關鍵字標籤，以及內頁的「Ⅰ. 核心概念與理論解析」、「Ⅱ. 台灣實際案例對照」與「Ⅲ. 研究觀察與延伸提問」。
- **人文學術雜誌視覺設計**：採用 Google Fonts（思源宋體 `Noto Serif TC`、思源黑體与英文襯線體 `Cormorant Garamond`）搭配莫蘭迪色票，營造舒適的閱讀體驗。
- **零相依性原生前端**：使用純 HTML、CSS 與 Vanilla JavaScript 建置，無須安裝套件或執行建置程序，完美適配 GitHub Pages 靜態部署。
- **AI 開發規則驅動**：透過 `AGENTS.md` 明確規範專案定位、CSS 色彩變數、DOM 頁面結構與 JSON 資料欄位（Schema）。

## 專案結構

```text
media-insight-wiki/
├── AGENTS.md      # AI 協作規範（定義視覺色票、頁面結構與新增內容之 JSON Schema）
├── README.md      # 專案說明與操作指南
└── index.html     # 主應用程式（包含雜誌風 CSS 設計系統、檢索篩選邏輯與 WIKI_ENTRIES 資料庫）
本機預覽與線上瀏覽
線上瀏覽：直接開啟 GitHub Pages 網址 https://chunnnnray.github.io/media-insight-wiki/

本機預覽：下載 index.html 後，直接以任何現代瀏覽器雙擊開啟即可完整操作（支援分類篩選、即時關鍵字搜尋與點擊展開詳情視窗）。

如何透過 AI 新增一筆知識條目
請 AI 先閱讀專案根目錄下的 AGENTS.md（特別是第 5 節「新增內容之標準格式」）。

開啟 index.html，找到下方 <script> 區塊中的 const WIKI_ENTRIES 陣列。

依照固定 Schema 新增一筆條目物件（設定遞增之 id，如 entry-007，並填妥 category、title、enTitle、keywords、summary、coreConcept、taiwanCase、reflection）。

儲存並推播至 GitHub 後，網頁會自動渲染新卡片、套用對應分類標籤色，並將其納入搜尋與分類篩選系統中，無須修改任何 HTML 或 CSS 結構。

AI 協作提示詞範例 (Prompt Example)
使用 AI 擴充本專案時，可直接提供以下指令：

請先閱讀我的 AGENTS.md。依照第 5 節定義的 WIKI_ENTRIES JSON Schema，在「傳播理論 (theory)」分類下新增一筆關於「框架理論 (Framing Theory)」的條目（編號設為 entry-007）。請確保包含核心概念解析、台灣具體媒體案例對照，以及一個可供傳播研究延伸探討的提問。

內容與學術誠實聲明
本網站收錄之傳播理論與概念解析皆以真實可查證之經典文獻為基礎，並對照台灣當代傳播現象進行案例分析，作為個人學術研究與媒體觀察之數位筆記庫。
