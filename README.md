# TaskMaster - 個人任務管理系統

一個簡單的任務管理應用程式，展示 Claude Code 自定義指令的實際應用。

> **Ch10 專案成果**
> 本專案在 Ch09 以 `/auto-fix` 完成模組化重構的基礎上，進一步整合 GitHub Actions，讓 Claude Code 能直接在 GitHub 的 Issue 與 PR 中協作。

---

## 🎯 專案進度

### Ch09
- ✅ 建立本地 Claude Code 自定義指令
- ✅ 實作自動化 Git 工作流程
- ✅ 使用 `/auto-fix` 完成專案重構
- ✅ 中文化提交訊息規範

### Ch10（目前）
- ✅ 整合 Claude Code GitHub Actions（`.github/workflows/claude.yml`、`claude-code-review.yml`）
- ✅ 在 Issue / PR 中透過 `@claude` 觸發自動協作
- 🔜 將互動式自定義指令調整為可在 GitHub 環境運作

---

## 📋 功能特色

- 桌面 GUI 介面 (Tkinter)
- Web API 服務 (Flask)
- SQLite 資料庫
- 任務管理 (新增、檢視、更新、刪除)
- 任務統計 (`/api/stats`)
- GitHub 上以 `@claude` 協作

---

## 🚀 快速開始

```bash
# 安裝套件
uv sync

# 啟動 GUI
uv run python main.py gui

# 啟動 API (http://127.0.0.1:5000)
uv run python main.py api
# 或
uv run python main.py web

# 檢查資料庫狀態
uv run python main.py check

# 備份資料庫
uv run python main.py backup

# 顯示完整說明
uv run python main.py help

# 或執行獨立的 Web 應用 (api_server.py)
uv run python api_server.py
```

也可使用 `pip install -r requirements.txt` 安裝套件。

---

## 🤖 Claude Code 自定義指令

本專案的核心特色是整合了 Claude Code 自定義指令：

### 可用指令

- `/auto-fix` - 自動規劃、實作、提交的完整工作流程
- `/pack-zh` - 中文互動式 Git 提交流程
- `/commit-rules` - Git 提交訊息規範

### 指令檔案位置

```
.claude/
└── commands/
    ├── auto-fix.md       # 自動修復流程
    ├── pack-zh.md        # 中文提交指令
    ├── pack-basic.md     # 基礎提交流程
    ├── pack-direct.md    # 強制執行提交
    └── commit-rules.md   # 提交訊息規範
```

**注意：互動式指令（需等待使用者回覆）無法直接在 GitHub Actions 中運作，在 GitHub 上使用時需調整為非互動流程。**

---

## 🐙 GitHub 協作（Ch10）

在 Issue 或 PR 的內容／留言中提及 `@claude` 並描述需求，Claude 會自動分析、修改程式碼、推送到 `claude/` 分支並回覆進度。

- `.github/workflows/claude.yml` - 回應 `@claude` 提及
- `.github/workflows/claude-code-review.yml` - PR 自動審查

---

## 🏗️ 專案架構

```
F5757_ch10/
├── main.py          # 程式入口點（gui / api / web / check / backup / help）
├── database.py      # 資料庫管理
├── task_gui.py      # GUI 介面 (Tkinter / customtkinter)
├── api_server.py    # Flask Web 與 API 服務
├── config.py        # 設定檔（可由環境變數覆寫）
├── utils.py         # 工具函式
├── check_db.py      # 資料庫檢查
├── templates/       # HTML 模板
├── static/          # CSS / JS
├── log_history/     # 歷次 PROGRESS 紀錄
├── .claude/         # Claude Code 自定義指令
└── .github/         # GitHub Actions 工作流程
```

---

## 💻 技術棧

- Python 3.11+
- Tkinter (GUI)
- Flask (Web / API)
- SQLite (資料庫)
- Claude Code 自定義指令與 GitHub Actions

---

## 📝 授權

本專案僅供學習與練習使用。
