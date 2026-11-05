# 小四數學挑戰 · P.4 Maths Quiz

一個單檔 HTML 問答遊戲，題目取材自 `Sources questions` 內四份小四數學試卷
（4001、4002、4003、4004），共 **90 題**。

開啟 `index.html` 即可遊玩 — 毋須安裝、毋須網絡、沒有任何外部連結。

---

## 遊戲功能

| | |
|---|---|
| 範疇選擇 | 全部 / 數的運算 / 因數與倍數 / 應用題 / 度量 / 圖形 / 方向 / 數據處理 |
| 題數 | 10、20、30 或全部 |
| 計分 | 答對 10 分，連擊額外加分（最高 +10），連擊斷了歸零 |
| 即時回饋 | 顯示正確答案並附**解題說明** |
| 錯題回顧 | 完場後列出所有答錯的題目、你的答案、正確答案與解釋 |
| 最佳紀錄 | 以 `localStorage` 分範疇記錄最高分 |
| 操作 | 滑鼠／觸控，或鍵盤 <kbd>1</kbd>–<kbd>4</kbd> 作答、<kbd>Enter</kbd> 下一題 |
| 其他 | 每次隨機抽題並打亂選項次序；手機／平板／電腦自適應；內建音效（WebAudio，無音檔） |

---

## 上載到 GitHub Pages

只需要 **`index.html`** 一個檔案。

1. 在 GitHub 新建一個 repository（例如 `p4-maths-quiz`），勾選 *Public*。
2. 上載 `index.html` 到 repository 根目錄
   （網頁介面：**Add file → Upload files**，拖入後 **Commit changes**）。
3. 進入 **Settings → Pages**：
   - **Source** 選 `Deploy from a branch`
   - **Branch** 選 `main`、資料夾 `/ (root)`，按 **Save**。
4. 等 1–2 分鐘，網址會是：

   ```
   https://<你的帳號>.github.io/<repository 名稱>/
   ```

> 用 Git 指令的話：
> ```bash
> git init
> git add index.html
> git commit -m "Add P.4 maths quiz game"
> git branch -M main
> git remote add origin https://github.com/<你的帳號>/<repo>.git
> git push -u origin main
> ```

---

## 修改題目

題庫與版面是分開的，方便日後增減題目：

```
questions.js    題庫（唯一的題目來源）
template.html   版面與遊戲邏輯
build.js        把題庫注入版面，產生 index.html
```

改完 `questions.js` 後執行：

```bash
node build.js
```

就會重新產生 `index.html`。

### 題目格式

```js
{
  c:'calc',                    // 範疇 calc/num/word/measure/shape/direction/data
  s:'4001',                    // 來源試卷
  q:'25 × 32 × 4 = ?',         // 題目（可用 HTML）
  t:'<table>…</table>',        // 選填：附表
  o:['3200','320','800','2800'],// 四個選項
  a:0,                         // 正確選項的索引（0 = 第一個）
  e:'25 × 4 = 100，100 × 32 = 3200。'   // 解題說明
}
```

遊戲會自動打亂選項次序，所以 `a` 只需對應 `o` 陣列的原始位置。

---

## 題目分佈

| 範疇 | 題數 |
|---|---|
| 應用題 | 30 |
| 數的運算 | 16 |
| 因數與倍數 | 14 |
| 度量 | 14 |
| 圖形 | 7 |
| 數據處理 | 7 |
| 方向 | 2 |
| **合計** | **90** |

| 來源試卷 | 題數 |
|---|---|
| 4001 | 14 |
| 4002 | 18 |
| 4003 | 27 |
| 4004 | 31 |

---

## 備註

- 原試卷中**必須看圖才能作答**的題目（釘板作圖、溫氏圖、平面圖、拼砌圖形、象形統計圖等）
  未有收錄，或已改寫成可用文字／表格完整表達的版本，以確保每題都能獨立作答。
- 所有可計算的答案已用程式獨立覆核過一次。
