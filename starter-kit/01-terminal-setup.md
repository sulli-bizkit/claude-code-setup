# 01 · 終端機快速啟動設定

設定完成後，你只需要輸入 `hi` 就能啟動 Claude Code，畫面也不會閃爍。

---

## 設定 `hi` 快速指令

### Mac 用戶

**Option A：指定專案資料夾啟動**
```bash
echo "alias hi='cd ~/你的專案路徑 && CLAUDE_CODE_NO_FLICKER=1 claude'" >> ~/.zshrc && source ~/.zshrc
```

**Option B：直接在當前位置啟動**
```bash
echo "alias hi='CLAUDE_CODE_NO_FLICKER=1 claude'" >> ~/.zshrc && source ~/.zshrc
```

### Windows 用戶

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Add-Content $PROFILE "`nfunction hi { $env:CLAUDE_CODE_NO_FLICKER = '1'; claude @args }"
. $PROFILE
```

---

## 為什麼要開 NO_FLICKER？

| 沒開 | 開了之後 |
|------|---------|
| 畫面一直閃 | 畫面穩定，像在用 App |
| 無法用滑鼠滾動 | 可以滑鼠滾動和選取文字 |
| Page Up/Down 壞掉 | 正常運作 |
| 長對話容易當機 | 記憶體更穩定 |

---

## 選配：調整滾動速度

```bash
export CLAUDE_CODE_SCROLL_SPEED=3
```

數值範圍 1–20，預設建議用 3。

---

© Bizkit · sulli-bizkit｜保留所有權利

本文件由 Bizkit 原創製作，未經授權禁止轉載、複製或商業使用。

- IG：https://www.instagram.com/sulli_bizkit/
- Threads：https://www.threads.com/@sulli_bizkit
- GitHub：https://github.com/sulli-bizkit/claude-code-setup
- 服務詳情：（即將公開）
