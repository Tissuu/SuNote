---
title: Day10 看了兩天的vue, JS 還看得下去嗎?
date: 2026-05-30
excerpt: 題目練習基本語法
image: /images/day10-heat-js-diary.png
tags: [filter(), String(), map(), Array.from(), join(" "), find()]
---

最近天氣真的好熱，才剛進入六月，走在路上就已經覺得自己快要融化了。一看溫度，才發現室外早已高達 35 度以上；一進到室內，第一件事就是趕緊把冷氣再調低兩度。

這讓我想起小時候，中午常常跑到室外的籃球場打球。那時候也很熱，但似乎還不至於熱到快曬昏、曬傷，甚至擔心中暑的程度。可現在的天氣，只是在外面站個半小時，就已經讓人感覺快要撐不住。很難想像到了七月，路上會是什麼樣的光景。

這也讓我想到，以前很常聽到「碳排放」、「臭氧層破洞」以及「溫室效應」這些說法，但現在似乎比較少用同樣的方式來討論。後來我也聽過另一種完全不同的觀點，像是所謂「溫室效應大騙局」的說法。這類觀點大致認為，人類在工業革命之後排放的溫室氣體，相較於大自然本身所排放的量，幾乎可以說是微乎其微；也有人引用相關研究，主張氣候變化其實主要來自太陽週期，以及地球本身的自然循環，人類的力量並不足以改變整個地球環境。

當然，也有人認為，這類說法很容易導向各種陰謀論；甚至有人懷疑，這背後可能與石化產業供應鏈的利益有關，目的是削弱大眾對氣候變遷與減碳議題的重視。畢竟會參與這種會議的上流人物，可能也都是搭著私人飛機過去開會。

有時都會覺得，我們可能永遠無法掌握真理是什麼。但這並不會阻礙我們保持懷疑、持續思考，也不會阻礙我們追尋知識與理解世界的慾望。





## 題目10 把數字以 10 進位展開式呈現，數字均為大於 0 的正整數
## EX: ```9527 變成 "1000 x 9 + 100 x 5 + 10 x 2 + 7"```
這題我覺得好難想，所以我覺得先列流程比較好連結我需要用什麼語法  
轉字串 -> 拆陣列 -> map 算位數 -> filter 去掉 0 -> join 接起來

```js
function expandedForm(num) {
  const value = String(num) // 轉成字串
  const arr = Array.from(value) // 拆陣列
  const result = arr.map((element, index)=> {
  if (element === "0"){
    return null //如果是0就回傳null
  } 
  const place = 10**(arr.length-1-index)// 10的次方
  
  if (place ===1 ) {
    return element // 如果是1就直接回傳
  } else {
    return `${place} x ${element}`c// 如果不是1就回傳
  }
}).filter(element => element !== null)// 如果不是null就回傳
return result.join(" + ") // 接起來
} 
```
## 題目11 找出一個數字陣列裡，出現奇數次數的數字
## 範例：```[1, 1, 0]，`0` 只有出現 1 次```, ```[5, 5, 8, 8, 8, 4, 4]，`8` 出現了 3  次```
這題code比較短，但我覺得很有趣
find 逐一找數字 -> filter 算出現次數 -> length 拿次數 -> % 2 判斷奇數 -> return 結果
```js
function findOddElm(numbers) {
  const result = numbers.find(n => {
    const count = numbers.filter(element => element === n).length
    return count % 2 !== 0
  })

  return result
}
```
