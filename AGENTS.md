# AGENTS.md — 傳播觀察誌｜Media Insight Wiki 開發與內容擴充規範

## 1. 專案目的與定位 (Project Overview)
本專案「傳播觀察誌（Media Insight Wiki）」旨在建立一個結構化、可持續擴充的傳播學知識庫網站。核心目標是將抽象的「傳播理論」與「媒體科技議題」，具體連結至「台灣在地實際案例」與「研究延伸提問」。所有協作的 AI Agent 在新增條目、調整版面或擴充功能時，必須嚴格遵守本文件定義之設計系統與資料結構規範。

## 2. 視覺風格與色彩規範 (Design System & Style Guide)
網站採知性、具紙本閱讀質感的「人文學術雜誌風（Editorial & Magazine Style）」。
- **字體規範**：主標題與卡片標題採用 `Noto Serif TC`（思源宋體），英文副標與裝飾編號採用 `Cormorant Garamond` 襯線斜體，內文採用 `Noto Sans TC`（思源黑體）。
- **色彩規範**：AI 修改或新增樣式時必須使用 `index.html` 中 `:root` 定義的莫蘭迪色系 CSS 變數，禁止硬編碼未定義之刺眼色彩：
  - 背景主色：`--bg-main: #F4F1EA`（溫暖燕麥紙張質感）
  - 卡片背景：`--card-bg: #FCFBF9`（奶油米白，搭配細邊框與硬陰影）
  - 主視覺色：`--primary: #1C1B18`（深炭黑，用於刊頭線條、主標題與選取狀態）
  - 強調點綴色：`--accent: #9E472A`（赤陶棕，用於英文副標與互動提示）
  - 三大分類專屬標籤色：
    - `theory`（傳播理論）：`--tag-theory: #3A5A78`（古典灰藍）
    - `issue`（媒體議題）：`--tag-issue: #6B5074`（煙燻梅紫）
    - `case`（台灣案例）：`--tag-case: #38665B`（深松石綠）

## 3. 檔案結構與命名規則 (File Structure & Naming)
本專案採用「單頁資料驅動架構（Single-Page Data-Driven Architecture）」以確保在 GitHub Pages 上零相依性且快速載入：
- `/AGENTS.md`：AI 開發與內容擴充規範文件（本檔案）。
- `/index.html`：主應用程式，包含響應式雜誌排版、分類篩選器、關鍵字搜尋引擎、詳情檢視視窗（Modal）以及核心資料庫陣列 `WIKI_ENTRIES`。
- 若未來拆分獨立文章頁面，檔案須存放於 `/entries/` 目錄下，並依 `entry-XXX.html` 格式命名（例如 `entry-007.html`）。

## 4. 頁面結構規範 (Page Architecture)
網頁由上而下固定包含四個核心區塊，AI 修改時不得破壞此 DOM 階層結構：
1. **Header 雜誌刊頭區**：展示刊頭資訊列（Masthead Bar）、中英文主視覺標題、專案定位說明與目前收錄條目統計。
2. **Control Bar 檢索與分類列**：提供「全部條目」、「傳播理論」、「媒體議題」、「台灣案例」四個切換按鈕，以及支援標題、英文專有名詞與標籤檢索的即時搜尋框。
3. **Insight Card Grid 條目卡片網格**：以 CSS Grid 呈現知識卡片，每張卡片顯示分類標籤、序號、中英文標題、核心摘要與關鍵字 Hashtags。
4. **Article Modal 深度閱讀視窗**：點擊任一卡片後彈出，固定依序呈現三個結構化段落：「Ⅰ. 核心概念與理論解析」、「Ⅱ. 台灣實際案例對照」、「Ⅲ. 研究觀察與延伸提問」。

## 5. 新增內容之標準格式 (Content Addition Schema)
當使用者要求 AI「新增一筆傳播理論、議題或案例」時，AI **不需修改 HTML 結構**，只需在 `index.html` 底部 `<script>` 的 `const WIKI_ENTRIES` 陣列中，嚴格依循以下 JSON Schema 新增一筆資料物件：

{
  id: "entry-XXX",              // 必填：3位數遞增編號，如 "entry-007"
  category: "theory",           // 必填：僅限 "theory" | "issue" | "case"
  categoryLabel: "傳播理論",     // 必填：對應 category 之中文名稱（傳播理論 / 媒體議題 / 台灣案例）
  title: "中文條目標題",         // 必填：簡潔明確的主標題
  enTitle: "English Term",      // 必填：對應之英文學術專有名詞或概念名稱
  keywords: ["標籤1", "標籤2"],  // 必填：2~4 個核心關鍵字陣列
  summary: "外層卡片摘要...",    // 必填：45 字以內的一句話核心定義，顯示於卡片列表
  coreConcept: "核心概念解析...", // 必填：點擊展開後的第一段，說明理論內涵或議題背景（約 80-150 字）
  taiwanCase: "台灣案例對照...", // 必填：點擊展開後的第二段，必須舉出台灣本土具體媒體現象或實例（約 80-150 字）
  reflection: "研究觀察提問..."  // 必填：點擊展開後的第三段，提出可供量化或質化研究延伸探討的問題（約 50-100 字）
}

## 6. AI 撰寫與維護守則 (Strict Rules for AI Agents)
1. **學術誠實原則**：提及理論與學者時必須確保真實可查證，嚴禁杜撰不存在的文獻、年代或研究數據。
2. **在地化連結強制要求**：任何新增的西方傳播理論，都必須在 `taiwanCase` 欄位中轉化並對照至台灣當代的社群、新聞或消費傳播情境。
3. **維持單一檔案純淨度**：禁止引入外部大型 JS/CSS 框架，確保單一 `index.html` 即可獨立運作。
