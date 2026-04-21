# 02 · 外部編輯器設定

當你要貼入大段文字或用語音輸入時，終端機會截斷內容。
設定外部編輯器之後，按 `Ctrl+G` 就能開啟編輯視窗，打完再送出。

---

## Mac 推薦：CotEditor（免費）

### Step 1：安裝 CotEditor
前往 Mac App Store 搜尋「CotEditor」，下載安裝（免費）。

### Step 2：安裝 CLI 指令
打開 CotEditor → 左上角選單 **CotEditor** → **Settings**（`Cmd+,`）
→ General → 滾到最下面 → 點選 **Install `cot` command to /usr/local/bin**

確認安裝成功：
```bash
which cot
# 應該顯示：/usr/local/bin/cot
```

### Step 3：建立 Wrapper Script
```bash
mkdir -p ~/.local/bin && cat > ~/.local/bin/cot-editor << 'SCRIPT'
#!/bin/bash
cot --wait "$@" 2>/dev/null
exit 0
SCRIPT
chmod +x ~/.local/bin/cot-editor
```

### Step 4：設定環境變數
```bash
grep -q 'HOME/.local/bin' ~/.zshrc || echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
grep -q 'EDITOR=' ~/.zshrc || echo "export EDITOR='cot-editor'" >> ~/.zshrc
source ~/.zshrc
```

確認設定成功：
```bash
echo $EDITOR
# 應該顯示：cot-editor
```

### Step 5：測試
1. 啟動 Claude Code（輸入 `hi`）
2. 按 `Ctrl+G`
3. CotEditor 開啟 → 打字
4. `Cmd+S` 儲存 → `Cmd+W` 關閉
5. 內容出現在輸入框 = 成功 ✅

---

## 其他編輯器選項

| 編輯器 | 指令 |
|--------|------|
| VS Code | `export EDITOR='code --wait'` |
| Cursor | `export EDITOR='cursor --wait'` |
| Vim | `export EDITOR='vim'` |

---

© Bizkit · sulli-bizkit｜保留所有權利

本文件由 Bizkit 原創製作，未經授權禁止轉載、複製或商業使用。

- IG：https://www.instagram.com/sulli_bizkit/
- Threads：https://www.threads.com/@sulli_bizkit
- GitHub：https://github.com/sulli-bizkit/claude-code-setup
- 服務詳情：（即將公開）
