# ss-translator

手機簡單的機器翻譯螢幕畫面內容日文變繁體中文版。
在 Android 手機上玩 SS（Sega Saturn）模擬器的秀逗魔導士遊戲時，自動辨識畫面上的日文對話，翻成台灣繁體中文，並附華曜版攻略本。

## 下載

到右邊的 **Releases** 下載最新的 `SS-Translator.apk` 安裝。
更新時如果顯示「簽章不符」或「無法安裝」，請先移除舊版再安裝（AI 金鑰要重新貼上）。

## ⚠ 使用前必看：模擬器設定

| 項目 | 設定 |
|---|---|
| 模擬器 | **Yaba Sanshiro 2**（Google Play 免費版，測試版本 1.20.x） |
| 遊戲 | SS「スレイヤーズろいやる」1 代、2 代 |
| 手機方向 | **直立**：遊戲畫面在上半部，下半部是 Yaba 的虛擬按鍵 |
| 輸入裝置 | 遊戲中按返回鍵叫出選單 → Player1 → **On-Screen Pad** |
| **VDP2 Compositing** | **Fast (legacy)**（一定要改） |
| Video Core | Vulkan |
| Rendering Resolution | Native |
| Filter | None |
| Aspect Ratio | Original |

### 為什麼一定要把 VDP2 Compositing 改成 Fast (legacy)

這款遊戲的對話字是**金色**，有些場景（例如バークランド的石階、石板路）背景也是金色。

- **Fast (legacy)**：對話字後面會出現一條**半透明深色底**，金色字很清楚，日文辨識不會漏字。
- **Accurate (per-pixel)**：沒有深色底，金色字直接疊在金色樓梯上，對話**開頭的兩三個字常常讀不到**（例如「ここが、バークランドって町ね」只讀到「バータランドはて町ね」）。

### VDP2 Compositing 設定步驟

1. 在 Yaba Sanshiro 2 選遊戲、按 **Play**，等遊戲畫面出來。
2. 按手機的 **返回** 鍵（或從螢幕邊緣往內滑的返回手勢），左邊會跳出遊戲選單（Exit、Open CD Tray、Reset、Action Replay Code、Settings、Save State、Load State…）。
3. 點選單裡的 **Settings**（齒輪圖示，在 Action Replay Code 下面那個）。
4. 進到 **Game Setting** 頁面，點 **VDP2 Compositing**。
5. 跳出「Choose VDP2 compositing method」，選 **Fast (legacy)**。
6. 確認 VDP2 Compositing 下面顯示 **Fast (legacy)**，按 **返回** 回到遊戲。
7. 檢查：對話字後面出現一條 **半透明深色底** 就成功了。如果沒出現，叫出選單 → **Exit** 結束遊戲，再重新開一次。

這個設定會保留，之後玩不用再改。

### 虛擬按鍵（On-Screen Pad）設定步驟

如果下半部沒有出現虛擬按鍵：遊戲中按 **返回** 叫出選單 → 拉到下面 **Player1** → 點目前的輸入裝置名稱 → 選 **On-Screen Pad** → **Ok**。

## 使用方法

1. 打開 App，依序按 ① 開啟「顯示在其他應用程式上層」權限、② 下載離線翻譯模型。
2. （選用）在 AI 設定貼上自己的 API 金鑰（例如 Google Gemini 免費額度），翻譯更準。
3. 按 ③ 啟動翻譯懸浮按鈕，再切到 Yaba Sanshiro 2 開始玩。
4. **先開好翻譯再進入對話**，每個場景的第一頁最準。
5. 長按懸浮球可調整翻譯範圍、翻譯方式、開啟攻略本。

## 診斷紀錄（開發用）

App 最下方有「儲存診斷紀錄」選項，預設關閉。打開後會把每一頁的截圖和辨識結果存到手機的「下載/SSDiag」資料夾，用來回報辨識問題。平常不用開。
