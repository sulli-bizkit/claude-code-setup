# MCP 工具安裝說明

MCP（Model Context Protocol）讓 Claude Code 直接連接你每天在用的工具。

---

## 安裝前準備

確認你已經安裝 Claude Code：
```bash
npm install -g @anthropic-ai/claude-code
```

---

## 推薦安裝的 MCP 工具

### 1. Notion MCP
讓 Claude 直接讀寫你的 Notion workspace。
```bash
claude mcp add notion-mcp
```

### 2. Gmail MCP
讓 Claude 幫你整理和搜尋信件。
```bash
claude mcp add gmail
```

### 3. Google Calendar MCP
讓 Claude 查看和管理你的行事曆。
```bash
claude mcp add google-calendar
```

### 4. Filesystem MCP
讓 Claude 存取你指定的資料夾。
```bash
claude mcp add filesystem --scope user
```

### 5. Firecrawl MCP（競品研究用）
讓 Claude 抓取公開網頁內容。
```bash
claude mcp add firecrawl
```

### 6. Playwright MCP（進階自動化）
讓 Claude 操作瀏覽器，處理需要登入的頁面。
```bash
claude mcp add playwright
```

---

## 確認安裝成功

```bash
claude mcp list
```

看到你安裝的工具名稱出現即代表成功。

---

## 需要幫助？

遇到問題可以參考 [Claude Code 官方文件](https://docs.anthropic.com/claude-code)
