# AI助理完整安裝指南

預計時間：60–90 分鐘（由 Bizkit 遠端協助完成）

---

## Step 1：確認環境

**Mac 用戶：**
```bash
# 確認 Node.js 已安裝
node -v

# 若未安裝，先安裝 Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 再安裝 Node.js
brew install node
```

**Windows 用戶：**
前往 [nodejs.org](https://nodejs.org) 下載安裝包。

---

## Step 2：安裝 Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

確認安裝成功：
```bash
claude --version
```

---

## Step 3：登入 Claude 帳號

```bash
claude
```

第一次執行會引導你登入，用你的 Claude Pro/Max 帳號登入即可。

---

## Step 4：安裝 tmux（讓工作階段持續運作）

**Mac：**
```bash
brew install tmux
```

**Windows：**
使用 WSL 或略過此步驟。

---

## Step 5：放入你的 CLAUDE.md

將填好的 `base/CLAUDE.md` 放進你的主要工作資料夾：

```bash
# 例如放在 Desktop
cp base/CLAUDE.md ~/Desktop/CLAUDE.md
```

---

## Step 6：安裝 MCP 工具

參考 `base/mcp-setup.md`，依照你的需求安裝對應工具。

---

## Step 7：驗收測試

開啟 Claude Code，輸入「早安」，確認它能正確執行早安流程。

---

## 完成！

你的 AI 助理現在已經懂你了。
