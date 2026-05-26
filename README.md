# RSV iPhone PWA

這是 RSV 交易判斷系統的 iPhone Web App / PWA 版本。它保留原有資料格式，並加入主畫面安裝、離線核心功能、App icons 和 service worker。

今日判斷主介面已拆成三段：`盤前計劃`、`盤中工作台`、`儲存判斷`。盤中工作台內再切換 `判斷流程` 與 `指標快填`，避免手機或桌面右欄一路拉長。

## 本地預覽

在此資料夾開 HTTP server：

```powershell
python -m http.server 4174 --bind 127.0.0.1
```

然後打開：

```text
http://127.0.0.1:4174/index.html
```

不要用 `file://` 測 PWA，因為 service worker 需要 HTTP/HTTPS 或 localhost。

## iPhone 加到主畫面

1. 用 iPhone Safari 打開部署後的網站。
2. 按分享按鈕。
3. 選「加入主畫面」。
4. 之後可像 App 一樣由主畫面打開。

## GitHub Pages 部署

把這個資料夾內的檔案放到 GitHub Pages repo 根目錄：

```text
index.html
manifest.webmanifest
sw.js
icons/
README.md
```

推上 GitHub 後，在 repo Settings 啟用 Pages。

## 資料

此版本沿用現有 localStorage keys：

- `rsvDecisionJournal.v1`
- `rsvDailyPlan.v1`
- `rsvTradingViewSettings.v1`
- `rsvLiveTradeMode.v1`

舊版資料可先從原網站匯出 JSON，再在此版本匯入。

## 離線限制

盤前計劃、快判、日誌和覆盤可離線使用。TradingView 官方圖表需要網絡；離線時會顯示提示，不會阻礙其他功能。
