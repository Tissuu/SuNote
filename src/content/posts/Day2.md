---
title: Day2 我愛程式碼程式是我爸
date: 2026-05-19
excerpt: 陣列操作（filter、展開運算子）、時間換算（Math.floor、取餘數、padStart）
image: /images/image1.png
tags: [filter(), 展開運算子, Math.floor(), padStart(), String(), 樣板字面字串, ]
---

    結果最近被AI成功吸引注意力，隔了快一個禮拜才又打開個筆記兼部落格(笑)。  
    不知道AI浪潮下的工程師的未來是如何呢?  
    訪間出現各種AI花里胡哨的用法，看得我是暈頭轉向，但同時又樂在其中，最大的原因就是不像傳統的coding比較枯燥乏味，馬上就會有成就感。  
    這情況就跟現在大家都在看短影音一樣如初一撤;作為觀眾們是享受多巴胺爆發式的快感，而內容創作者則是靠著超高效率的內容產出，無情地收割著名氣與流量。  
    無關對錯想當觀眾或是創作者都無訪，因為也許兩邊都不會贏來最美好的結局，但我認為如果想要當創作者，前期還是要回歸本質，並且重在產出Just do it


## 題目3:完成函數的內容，把陣列裡的 0 都移到最後面
```js
let list = [false, 1, 0, -1, 2, 0, 1, 3, "a"];
```

我的做法是先把陣列分成有0，和沒有0的兩組  
接著再用展開運算子合併兩個陣列呼叫印出就可以了

```js
function moveZerosToEnd(arr) {
    const zeros = arr.filter(element => element = = = 0);
    const nonZeros = arr.filter(element => element ! = = 0);
    return combinedArray = [...nonZeros, ...zeros];
    return combinedArray
}
let result = moveZerosToEnd(list);
console.log(result);
```


## 題目4：完成函數的內容，把傳進去的秒數以下的時間格式
## EX: ``` console.log(timeConverter(3600)) => 01:00:00```  ```console.log(timeConverter(90)) => 00:01:30```

用簡單算數把秒數換算成分、時，然後丟進STring.padStart()裡面讓他補0
```js
function humanReadableTimer(seconds) {
  const hour = Math.floor(seconds/3600)
  const minute = Math.floor((seconds % 3600)/60)  
  const sec = seconds % 60 
  const printhour = String(hour).padStart(2, "0")
  const printmin = String(minute).padStart(2,"0")
  const printsec = String(sec).padStart(2,"0")
  return `${printhour}:${printmin}:${printsec}`
}
```
另外可以補充的是關於```Math.floor()```、```String.padStart()```、```String()``` 與樣板字面值各種語法的用法之後再一併整理到語法知識站作補充。