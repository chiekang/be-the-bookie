# Be the Bookie 莊家模擬器

輔仁大學 FMGB 全英課（Financial Markets and Global Business）的課堂互動遊戲。學生扮演莊家，自己決定客人怎麼押、莊家要抽多少，再看系統怎麼算出兩邊的賠率。

**線上玩：** https://chiekang.github.io/be-the-bookie/

[English](#english) | 中文

---

## 這個遊戲想教什麼

1. **莊家不用猜誰會贏。** 只要設定好賠率，不論哪一邊贏，莊家賺的錢都一樣。
2. **賠率是算出來的，不是亂開的。** 人多的一邊賠率低，人少的一邊賠率高。
3. **抽成要拿捏。** 抽太多，客人離開；抽太少，賺不到錢。
4. **莊家賺的是價差。** 這跟銀行外匯報價的買進價與賣出價是同一個道理，也是衍生性商品市場中做市商（market maker）的收入來源。

## 玩法

共 10 局，每局三步：

| 步驟 | 要做什麼 |
|---|---|
| 1. 客人怎麼押 | 場上有 100 位客人，每人押 $100，總投注 $10,000。拖動滑桿，決定幾人押紅、幾人押綠。 |
| 2. 你想抽多少 | 用「佛心 ↔ 黑心」滑桿，決定從總投注中留下多少錢。 |
| 3. 看賠率 | 系統算出紅、綠兩邊的小數賠率，並顯示每一步的算式。按下「開獎」。 |

開獎是電腦隨機抽，紅、綠各 50%。10 局結束後，系統依表現給一個稱號。

## 賠率怎麼算

只有兩條公式：

```
可分給贏家的錢 = 總投注 − 莊家抽的錢
賠率           = 可分給贏家的錢 ÷ 這一邊的投注額
```

**例子：** 70 人押紅、30 人押綠，莊家想抽 $500。

| | 計算 | 賠率 |
|---|---|---|
| 可分給贏家的錢 | $10,000 − $500 = $9,500 | |
| 紅色（押 $7,000） | $9,500 ÷ $7,000 | 1.35 |
| 綠色（押 $3,000） | $9,500 ÷ $3,000 | 3.16 |

**驗算：** 不論誰贏，莊家都賺 $500。
- 紅贏：收 $10,000，付 $7,000 × 1.357 ≈ $9,500，賺 $500
- 綠贏：收 $10,000，付 $3,000 × 3.167 ≈ $9,500，賺 $500

賠率畫面顯示到小數兩位，驗算時多算一位，所以用「≈」。

## 客人會不會離開

下一局的客人數，取決於這一局的抽成比例（抽成 ÷ 總投注）：

| 抽成比例 | 客人反應 |
|---|---|
| 5% 以下 | 客人帶朋友來，人數加 10%（最多 150 人） |
| 5% 到 10% | 人數不變 |
| 超過 10% | 開始流失，抽得越多、走得越多（單局最多流失 90%） |

客人少於 2 人時提早打烊。

## 結算稱號

| 稱號 | 條件（依序判斷） |
|---|---|
| 客人全跑光 | 最後客人少於 30 人 |
| 佛心莊家 | 平均抽成低於 3% |
| 黑心商人 | 平均抽成高於 15% |
| 剛剛好大師 | 10 局總獲利達 $8,000 以上 |
| 合格莊家 | 其他 |

## 課堂使用建議

這個遊戲接在「兩顆按鈕」故事的第二層（場外開賭）之後：

- 先讓學生玩 1 到 2 局，再請大家說說「你抽多少、為什麼」。
- 請抽成最高與最低的同學各分享他的客人人數變化。
- 收尾連到真實市場：買賣價差（bid-ask spread）、預測市場的價格與機率、莊家付不出錢時的交易對手風險。

## 使用方式

- **學生：** 用手機或電腦開啟上面的網址即可，不需登入，每個人各玩各的。
- **老師：** 把網址做成 QR code 放在投影片上。
- 遊戲紀錄只存在每個人自己的畫面，不會上傳，也不會有班級排行榜。

## 技術說明

單一檔案 `index.html`，沒有後端、沒有安裝步驟，只用到 Google Fonts。

在本機測試：直接用瀏覽器打開 `index.html`。

更新網站：修改 `index.html` 後推到 `main` 分支，GitHub Pages 會自動重新發佈。

---

## English

An in-class game for the Fu Jen FMGB course (Financial Markets and Global Business). You play the bookie: decide how customers bet, set how much you take, and see how the odds are calculated.

**Play:** https://chiekang.github.io/be-the-bookie/

### What it teaches

1. The bookie does not need to guess who wins. Set the odds right and the profit is the same either way.
2. Odds are calculated, not made up. The more crowded side pays less.
3. Greed has a cost. Take too much and customers leave.
4. The house earns the spread, the same idea as a bank's buy and sell prices for currencies, or a market maker's bid-ask spread.

### How to play

10 rounds. Each round has three steps:

1. **Split the customers.** 100 customers bet $100 each (total $10,000). Drag the slider to choose how many bet red and how many bet green.
2. **Set your take.** Use the Saint to Greedy slider to choose how much of the total bets you keep.
3. **Read the odds and spin.** The game shows the decimal odds for each side with every step of the math. The coin flip is random, 50% each.

### How the odds are calculated

```
Winners' pool = Total bets − House take
Odds          = Winners' pool ÷ Bets on that side
```

Example: 70 customers on red, 30 on green, house takes $500.

- Winners' pool = $10,000 − $500 = $9,500
- Red odds = $9,500 ÷ $7,000 = 1.35
- Green odds = $9,500 ÷ $3,000 = 3.16
- Whoever wins, the house earns $500.

### Customer rules

| House take (% of total bets) | Next round |
|---|---|
| 5% or less | Customers bring friends: +10% (max 150) |
| 5% to 10% | No change |
| Over 10% | Customers leave, more the greedier you are |

### Technical notes

One static file, `index.html`. No backend, no build step. Open it in a browser to test locally. Push to `main` and GitHub Pages republishes it.
