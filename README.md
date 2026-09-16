# PlayShield 網站

靜態介紹頁，用 GitHub Pages 託管。頁面：首頁、服務政策、隱私權政策、Support。

## 發布到 GitHub Pages

1. 在 GitHub 新建公開儲存庫（例如 `PlayShield_website`），把這個資料夾推上去。
2. 打開儲存庫 **Settings → Pages**。
3. Source 選 **Deploy from a branch**，Branch 選 `main`、資料夾選 `/ (root)`，儲存。
4. 數分鐘後可先用 `https://<你的帳號>.github.io/PlayShield_website/` 預覽。若儲存庫名稱是 `<帳號>.github.io`，則會出現在網域根目錄。

App Store 的隱私權政策 URL 填：

`https://你的網域/privacy.html`

或尚未綁網域時：

`https://<你的帳號>.github.io/PlayShield_website/privacy.html`

## 用 GoDaddy 網域指向 GitHub

把 `你的網域.com` 換成實際網域，把 `YOURUSER` 換成 GitHub 使用者名稱或 Organization。

### 1. 在儲存庫根目錄新增 `CNAME` 檔

檔案沒有副檔名，內容只有一行：

```
你的網域.com
```

推送後，GitHub Pages 會讀取這個檔。

### 2. GitHub 後台

Settings → Pages → Custom domain 填入同一個網域，儲存。DNS 生效後再勾選 **Enforce HTTPS**。

### 3. GoDaddy DNS

登入 GoDaddy → 該網域 → **DNS**。刪掉會衝突的舊 `A` / `CNAME`（例如 GoDaddy 預設停駐頁、舊主機）。然後新增：

| 類型 | 名稱 | 資料 | TTL |
|------|------|------|-----|
| A | `@` | `185.199.108.153` | 600 秒 |
| A | `@` | `185.199.109.153` | 600 秒 |
| A | `@` | `185.199.110.153` | 600 秒 |
| A | `@` | `185.199.111.153` | 600 秒 |
| CNAME | `www` | `YOURUSER.github.io` | 600 秒 |

不要把 `www` 指到 GoDaddy 的停駐主機。IPv6 可加（非必須）：

| 類型 | 名稱 | 資料 |
|------|------|------|
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |

### 4. 等 DNS 傳播

通常數分鐘到數小時。用 `dig 你的網域.com` 確認 A 紀錄已是上面四個 IP。HTTPS 憑證要等 GitHub 核發完成才能勾 Enforce HTTPS。

客服信箱：`jason@kosbrohter.com`
