---
title: DAY 1 從零開始的轉職生活
date: 2026-05-12
excerpt: 我是SuJ，素人一枚0學歷0背景，準備轉職成工程師的菜鳥，開始的第一天也不知道要記錄什麼技術的文章(我也還沒什麼技術)不如就把每天課堂出的題目記錄在這裡當複習吧
# image: /images/image2.png
tags: [sort() ,filter(), Compare Function, charCodeAt(), charAt()]
---



## 題目1:找出陣列裡最小的兩個值的總和

```js
const list1 = [19, 5, 42, 2, 77];
const list2 = [23, 15, 59, 4, 17];
```
根據題目的描述，我們要在一串陣列裡，找出2個最小的數，第一個陣列會是2+5=7 第二個陣列會是4+15=19
所以我的第一個想到的方法就是用`sort()`把陣列裡的值進行排序，排完之後再取排列在陣列前兩個值相加就可以了如下:
```js
function sumOfSmallestValues(arr) {
  const sorted = arr.sort((a, b) => a - b)
  return sorted[0] + sorted[1]
}
```
這裡可以對sort()額外補充: 
比較函數(compareFunction)是 JavaScript 中用於控制排序順序的重要工具，通常與數組的 .sort() 方法結合使用
a 和 b），並返回一個數字，該數字決定了這兩個參數的相對順序。 
 關於比較函數的重要概念:  
1.返回值規則：比較函數必須返回一個數字，該數字可正可負可零，具體表示如下:   
&emsp;&emsp;-如果返回負數，意味著 a 應該在 b 之前，即 a 排在 b 的前面。  
&emsp;&emsp;-如果返回零，意味著 a 和 b 位置相對不變，它們相等。                               
&emsp;&emsp;-如果返回正數，意味著 b 應該在 a 之前，即 b 排在 a 的前面。  
2.排序用途：比較函數通常與數組的 `.sort()` 方法一起使用，用於確定數組中元素的排序順序。 `.sort()` 方法會調用比較函數來決定元素的相對位置。  
3.升冪排序:如果比較函數返回的數字小於零，表示 a 應該在 b 之前，即 a 排在 b 的前面。 
4.降冪排序:如果比較函數返回的數字大於零，表示 b 應該在 a 之前，即 b 排在 a 的前面。  

## 題目2:請寫一小段程式，印出連續陣列裡缺少的字元  
```js
const chars1 = ["a", "b", "c", "d", "f", "g"];
const chars2 = ["O", "Q", "R", "S"];
```
所以我們的期望是印出 e 和 P，所以得出結論後可以先建立一個函式:

```js
function missingChar(chars) {
  // 實作程式碼
}

console.log(missingChar(chars1)); // 印出 e
console.log(missingChar(chars2)); // 印出 P
```

這裡的第一個想法是用 `charCodeAt()` 轉換成ASCII編碼值如下:
```js
const star = chars[0].charCodeAt(0)
const end = chars[chars.length-1].charCodeAt(0)
```
至於為什麼要抓出頭尾呢? 可以先思考一下為什麼~先接著寫下去
```js
const length = end - star + 1
```
原因是這樣就可以算出完整範圍應該有幾個字母，進而推算出缺少的字元  
再來就是產生完整範圍的陣列然後把他轉成ASCII編碼值
```js
const fullRange = Array.from({length}, (_, i) => star + i)
const current = chars.map(element => element.charCodeAt(0))
```
比較兩個陣列是否相等，比較後就可以得到缺少的字元  
最後過濾出來然後轉換回字母印出就大功告成
```js
return fullRange
  .filter(element => !current.includes(element))
  .map(element => String.fromCharCode(element))
  ```
完整流程
chars → 算範圍 → 產生完整ASCII → 比較 → 找出缺少的 → 轉回字母 → 印出
  
```js
 function missingChar(chars) {
  const star = chars[0].charCodeAt(0)
  const end = chars[chars.length-1].charCodeAt(0)
  const length = end - star + 1
  const fullRange = Array.from({length}, (_, i) => star + i)
  const current = chars.map(element => element.charCodeAt(0))
  
  return fullRange
    .filter(element => !current.includes(element))
    .map(element => String.fromCharCode(element))
}
console.log(missingChar(chars1)); // 印出 e
console.log(missingChar(chars2)); // 印出 P
```
















