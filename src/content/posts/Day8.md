---
title: Day8  一個人可以走得很快，一群人可以走得很遠
date: 2026-05-26
excerpt: TDD 測試驅動開發
image: /images/image16.png
tags: [jest, 3A原則, TDD, jest]
---
最近專案差不多要開始了，一群人浩浩蕩蕩地到處亂跑，一下打羽球、一下匹克球、一下棒球
，在不然就是看電影，暫時還感受不出緊張的氛圍，算是苦中作樂嗎?
但內心緊張焦慮的心情，確實放鬆許多，雖然我自己部落格和複習的進度小落後，哈哈
我猜大家何嘗不是這種心情，恨不得把自己關在小房間連續24小時都做研究和開發，追趕進度。
也許很快，但我猜也走不遠。


## TDD(Test-Driven Development) 測試驅動開發是什麼?
TDD 的核心思想很簡單：先寫測試，再寫程式碼。而不是先實作功能再補測試，是讓測試來「驅動」開發方向。  
三個階段的意義：
<ul>
    <li>紅燈：先思考「這個功能應該有什麼」，把預期行為寫成測試。此時測試一定失敗（因為功能還不存在）。</li>
    <li>綠燈：寫「剛好夠」讓測試通過的程式碼，不多不少。</li>
    <li>重構：在測試保護下，安心整理程式碼的結構、命名、消除重複，不改變行為。</li>
</ul>

## 測試環境簡介
```bash
mkdir TDDtestdemo && cd TDDtestdemo #先開啟專案 並進入
npm install -D jest #安裝測試套件
```
## 設定npm腳本(Scripts)

```bash
{ 
  "scripts": {
        "test": "node --disable-warning=ExperimentalWarning  
        --experimental-vm-modules node_modules/jest/bin/jest.js"
  },
   "type": "module",
  "devDependencies": {
    "jest": "^30.4.2"}}
```

 
## 測試程式碼實例
<mark>溫度轉換公式(華氏轉攝氏)</mark>  
測試程式碼如下，輸入指令`npm run test`到終端機，一定會是壞的，因為f2c這個function還沒建立

```js
test('溫度轉換公式(華氏轉攝氏)', () => { 
  expect(f2c(150)).toBe(65.6) 
  expect(f2c(178)).toBe(81.1) 
})
```
## 建立實例
這部分再把前面還沒定義的函示建立出來，讓測試通過
```js
function f2c(t) {
  return Number((((t - 32) / 9) * 5).toFixed(1))
}
```

## 3A原則 ARRANGE、ACT、ASSERT
3A 原則是一種測試的最佳實踐方法，是指測試的目標是「實現」、「滿足」和「安全」的。
下面是一個測試的例子，執行下去也是壞的，因為沒有建立一個存錢功能的函式  
<mark>建立一個存錢功能</mark>

```js
test("可以存錢", () => {
  // 3A 原則
  // Arrange
  const account = new BankAccount(5)

  // Act
  account.deposit(10)

  // Assert
  expect(account.balance()).toBe(15)
})
```
下面的實例就是一個沒有任何內容，純粹有函式的程式碼，測試一樣會過，是偷工減料的版本
```js
class BankAccount {
  deposit() {}

  balance() {
    return 15
  }
}
```
這裡再將正確的功能全部補上
```js
class bankAccount {
  constructor(amount) {
    this.amount = mount
  }
  desposit(amount) {
    this.amount += amount
  }
  balance() {
    return this.amount
  }
}
```