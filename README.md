# Mini Meihua v0.1｜梅花易數・一事一問（小六太乙）

由「梅花觀象」v1.3.1 改作的可內嵌簡約版，介面沿用 Mini Runes。單檔 `index.html`，無外部依賴、無 localStorage。

## 部署與內嵌
放進 Workers 靜態資產（與 mini-runes 同層，例：`/mini-meihua/index.html`），WordPress 用 iframe：

```html
<iframe src="https://mini-heping.nakaiwen.workers.dev/mini-meihua/"
        style="width:100%;height:1400px;border:0"
        allow="clipboard-write" loading="lazy" title="Mini Meihua 梅花易數"></iframe>
```
`allow="clipboard-write"` 讓「複製解讀提示」在 iframe 內走正式剪貼簿；沒加也有 execCommand 與手動選取兩層退路。

## 與原工具的差別
- 保留：此刻（年月日時）／隨機（1–960）／數字三種起卦；本互變卦、動爻爻辭與變卦同位爻、體用、白話線索；AI 解讀提示（溫柔／平實）。
- 拿掉：PWA、觀察紀錄與回填、JSON 匯出匯入、指定日期、子初換日選項（固定 00:00 換日）。
- 起卦引擎：engine.js v1.3.1 原檔內嵌，一字未改。

## 開機自測（L-008）
- 引擎：26 組卦序錨點＋64 格排列檢查＋八純卦名＋八卦卦畫＋6 組數字起卦＋爻辭索引＋提示組裝。不過 → 鎖起卦鍵。
- 時間：6 組農曆／時間起卦（含閏月、跨年、子初、1900／2100 兩端），錨點取自原引擎實算並經 lunar-javascript 交叉核對。不過或瀏覽器不支援農曆 → 只停用「此刻起卦」，隨機／數字照常。
- 已做破壞測試：改卦序一格、兩格互換、改卦名、改爻辭，皆被攔下。

## 可調
- 卦象說明卡預設顯示；要像 Mini Runes 一樣只留 AI 面板，在 `#cards` 加 `class="hidden"`。

## 待辦
- 中／EN 切換（Mini Runes 有，本版未做）。
- 未在實體 iPhone／Android 與 WordPress iframe 內實測。
