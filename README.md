# 傳播觀察誌 Media Insight Wiki

一個以繁體中文整理傳播理論、媒體案例與研究方法的知識網站。這個專案除了呈現網頁，也示範如何透過 `AGENTS.md` 建立一套可重複使用的 AI 協作規則。

## 專案特色

- **可延伸的文章資料庫：** 文章集中在 `data/articles.js`，共用 `article.html` 模板自動呈現。
- **一致的內容格式：** 每篇文章包含摘要、分類、閱讀時間、段落與參考資料。
- **原生前端：** 使用 HTML、CSS、JavaScript，不需要安裝套件或執行建置程序。
- **適合 GitHub Pages：** 使用相對路徑，可直接部署為靜態網站。
- **AI 開發規則：** `AGENTS.md` 記錄專案目的、檔案結構、視覺規範、內容格式與 AI 工作流程。

## 專案結構

```text
media-insight-wiki/
├── AGENTS.md
├── README.md
├── index.html
├── article.html
├── about.html
├── 404.html
├── data/articles.js
└── assets/
    ├── css/style.css
    └── js/
        ├── app.js
        └── article.js
```

## 本機預覽

最簡單的方式是直接用瀏覽器開啟 `index.html`。若瀏覽器因本機檔案安全限制而無法載入資料，也可以在專案資料夾執行：

```bash
python -m http.server 8000
```

再開啟 <http://localhost:8000>。

## 如何新增一篇文章

1. 閱讀 `AGENTS.md` 的「新增文章的固定格式」。
2. 開啟 `data/articles.js`。
3. 在 `ARTICLES` 陣列中新增一筆文章物件，設定唯一的 `slug`。
4. 按照既有內容規範撰寫摘要、段落與參考資料。
5. 儲存後，首頁會自動顯示新文章；文章網址格式為 `article.html?slug=你的-slug`。
6. 檢查文章內容、參考資料與手機版呈現。

新增文章不需要建立新的 HTML 頁面，也不需要複製版型。這是本專案可重複擴充的核心設計。

## AI 協作方式

使用 AI 編輯本專案時，先要求 AI 閱讀 `AGENTS.md` 與 `README.md`。例如：

> 請先閱讀 AGENTS.md。依照既有文章格式，在「理論」分類新增一篇「涵化理論」文章。請只修改必要檔案，沿用現有文章模板，提供可追溯的參考資料，並依照完成前檢查清單檢查。

## 發布到 GitHub Pages

1. 在 GitHub 建立一個新的 Repository，例如 `media-insight-wiki`。
2. 將本資料夾內的所有檔案上傳至 Repository 根目錄（不要只上傳 ZIP）。
3. 開啟 Repository 的 **Settings → Pages**。
4. 在 **Build and deployment** 中選擇 **Deploy from a branch**。
5. Branch 選 `main`，資料夾選 `/(root)`，按下 Save。
6. 等待 GitHub Pages 完成部署，再由 Pages 設定頁取得公開網址。

若 Repository 名稱為 `media-insight-wiki`，網址通常會是 `https://你的GitHub帳號.github.io/media-insight-wiki/`。請以 GitHub Pages 頁面實際顯示的網址為準。

## 內容與引用聲明

網站中的理論介紹以文末列出的學術文獻為依據。新增現實案例或統計資料時，必須補上事件年份、資料發布單位與原始來源；假設情境需明確標示。本站內容為學習筆記，不取代原始論文或正式研究。
