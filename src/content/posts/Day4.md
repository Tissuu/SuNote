---
title: Day4 排球是永遠向上看的運動 工程師則是永遠向前看
date: 2026-05-21
excerpt: 善用filter解題與問題拆解
image: /images/image15.png
tags: [String(), Array(), Number(), join(""), map(),sort(), ]
---
某科技公司又傳出裁員的消息，這不免讓人心中又多了一層焦慮。這個時代彷彿總是在殘酷地提醒我們：「你現在擁有的，隨時都有可能失去。」
但是，我們真的就此失去所有了嗎？
有在運動的人應該都很清楚，要成為職業球員有多麼困難，那絕對不是光靠天賦就能在球場上大殺四方的。既然如此，我們這些平凡人的努力，難道就毫無意義嗎？
我很喜歡《排球少年》裡的那句經典台詞：
「排球，是永遠向上看的運動。」  

而我想，工程師，則是永遠向前看的職業。
技術會淘汰、產業會變化、工具會更新，甚至昨天才挑燈夜戰學會的東西，明天可能就已經退出了主流。我們能做的，就是不斷地往前走、不斷地學習、不斷地去適應。
職涯就像一場高強度的球賽，只要我們還願意抬頭看著球，願意繼續向前奔跑——
那份心中的熱血，就永遠不會消失。

## 題目5:完成函數的內容，把傳進去的數字的每個位數平方之後組合在一起
## EX: ```console.log(squareDigits(387)); // 印出 96449      console.log(squareDigits(2112)); // 印出 4114```  
解題思路:  
1. 把傳進去的數字轉成字串
2. 把字串轉成陣列
3. 把陣列的每個元素平方
4. 把平方的結果組合在一起

```js   
function squareDigits(num){
    const str = String(num) 
    const arr = Array.from(str)
    const square = arr.map(element =>Number(element)**2)
     return Number(square.join(""))
}
```

## 題目6:找出在數字陣列裡跟其它元素不一樣的值
## EX ```console.log(findDifferent([1, 1, 1, 1, 3, 1, 1, 1]))// 印出 3```  
解題思路:先用```sort()``` 排序陣列，如此一來相異的值只會在首或尾  
排完之後就可以直接if else 判斷;如果陣列第一個值和第二個值不相等，則回傳第一個值;反之則回傳最後一個值
```js
function findDifferent(numbers) {
    const arr = numbers.sort()
    if (arr[0] !== arr[1]){
        return arr[0]
    } else {
        return arr[arr.length - 1]
    }
}
```

## 題目7: 在某個數字陣列裡，可能藏有某個不合群的奇數或偶數，試著找出它
## EX: ```console.log(findOddOne([2, 4, 0, 100, 4, 11, 2602, 36]))// 印出 11```
先設定 偶數和奇數的變數，用filter分別過濾出奇數和偶數
在用if else 判斷偶數陣列長度是否等於1，如果是則回傳偶數陣列的第一個值,反之則回傳奇數陣列的第一個值
```js
function findOddOne(numbers) {
    const even = numbers.filter(element => element % 2 ===0)
    const odd = numbers.filter(element => element % 2 !==1)
    if (odd.length === 1){
        return odd[0]
    }else {
        return evenp[0]
    }
}
