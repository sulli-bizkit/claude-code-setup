# 03 · 保護機制設定

防止 Claude Code 不小心刪錯東西或執行危險指令。
三層保護，設定一次，永久生效。

---

## Layer 1：垃圾桶保護（rm 變成移到垃圾桶）

```bash
# 安裝 trash 工具
brew install trash

# 把 rm 指令改成移到垃圾桶
echo "alias rm='trash'" >> ~/.zshrc

# 保留真正刪除的指令（需要時才用）
echo "alias rm!='/bin/rm'" >> ~/.zshrc

source ~/.zshrc
```

> 之後輸入 `rm` 會移到垃圾桶，可以救回來。
> 真的要永久刪除才用 `rm!`。

---

## Layer 2：危險指令黑名單

先備份現有設定：
```bash
cp ~/.claude/settings.json ~/.claude/settings.json.backup.$(date +%Y%m%d-%H%M%S)
```

新增黑名單（擋掉 20 個高風險指令）：
```bash
brew install jq

jq '.permissions.deny += [
  "rm -rf", "rm -r", "rm -f", "rm -rf /", "rm -rf *",
  "sudo rm", "sudo dd", "chmod 777", "chmod -R 777",
  "git reset --hard", "git push --force", "git push -f",
  "git clean -fd", "git clean -f",
  "dd if=", "mkfs", "fdisk",
  "shutdown", "reboot",
  "truncate", "shred"
]' ~/.claude/settings.json > /tmp/settings_new.json && mv /tmp/settings_new.json ~/.claude/settings.json
```

重新啟動 Claude Code 讓設定生效。

---

## Layer 3：權限模式選擇

啟動 Claude Code 之後，你可以選擇以下模式：

| 模式 | 說明 | 適合情境 |
|------|------|---------|
| **Default** | 每次有風險操作都詢問你 | 日常使用，推薦 |
| **Accept Edits** | 自動接受文件編輯，其他仍詢問 | 大量寫作時 |
| **Plan** | 只規劃不執行，你確認後才動 | 重要任務前確認 |
| **Bypass** | 全部自動執行不詢問 | 非常熟悉後才用 |

---

## 確認三層都設定好了

```bash
# 確認 trash 安裝
type trash

# 確認 rm alias
alias rm

# 確認黑名單寫入
cat ~/.claude/settings.json | grep "deny"
```

三個都有回應 = 保護機制啟動完成 ✅

---

© Bizkit · sulli-bizkit｜保留所有權利

本文件由 Bizkit 原創製作，未經授權禁止轉載、複製或商業使用。

- IG：https://www.instagram.com/sulli_bizkit/
- Threads：https://www.threads.com/@sulli_bizkit
- GitHub：https://github.com/sulli-bizkit/claude-code-setup
- 服務詳情：（即將公開）
