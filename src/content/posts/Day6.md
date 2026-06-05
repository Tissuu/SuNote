---
title: Day6 有時候傻傻地上班反而是逃避生活的一種方式
date: 2026-05-23
excerpt: 題目做不完 
image: /images/image13.png
tags: [split(), indexOf(), Math.max(), reduce(), map(), Array.from()]
---

不知道從什麼時候開始，不管是從小認識到大的朋友，還是出社會後才認識的人，聊天的話題總離不開「工作」。
這其實也不是什麼壞事。畢竟除非家裡有礦，否則工作幾乎會佔據我們人生大部分的時間。
只是我開始忍不住思考：「工作」這個詞，對我們來說究竟代表什麼？
如果把「工作」換成英文，其實會聯想到很多不同的單字，而每個單字背後，都帶著不太一樣的意義。
<ol> <li><strong>work</strong>：在物理學中代表「做功」，意味著投入能量後產生結果。</li> <li><strong>job</strong>：受僱於某個單位或機構的職務與任務。</li> <li><strong>career</strong>：職涯，代表長時間累積而成的人生道路。</li> <li><strong>vocation</strong>：在宗教裡譯為「聖召」，也可以理解為願意全心投入的「天職」。</li> <li><strong>profession</strong>：需要專業技術與知識的工作。</li> </ol>
最近剛好處在人生轉職的階段，因此多了不少時間和許久未見的朋友聊天。也發現，到了這個年紀，不管是從小一起長大的朋友，還是出社會後認識的人，大家聊著聊著，最後總會回到「工作」這個話題。
但有趣的是，大家聊的早已不只是薪水、工時或升遷，而是開始思考：「工作的意義到底是什麼？」
也因為這些對話，我才意識到——
既然我們總把工作視為一輩子的事，那麼當我們開始認真探討工作的時候，其實某種程度上，也是在討論人生的意義。


## 題目8:傳入一字串，計算得分最高的字 英文字母 a 得 1 分、b 得 2 分、c 得 3 分，以此類推,所有傳入的字都是小寫。
## EX :```console.log(highestScoreWord("sit down please")); // 印出 please```
定義一個函數"highestScoreWord",傳入的值為input,先把傳入的字串用split(" ")分割成陣列   
Array.from() 將陣列轉成字串, map() 把字母轉成ASCII碼(), reduce() 累加值  
用Math.max()取得最大值, indexOf() 選得對應的單字 最後回傳印出  
流程:  
字串 → 拆成單字 → 每個單字計分 → 找最高分 → 回傳對應單字
```js 
function highestScoreWord(input) {
    const words = input.split(" ")
     const scores = words.map(word =>{
      return Array.from(word)
                  .map(letter => letter.charCodeAt(0)-96)
                  .reduce((acc, arc) => acc+ arc, 0)
  })
    const topScore = Math.max(...scores)
    const index = scores.indexOf(topScore)
    return words[index]
}
```

## 題目9: 移除網址中的錨點（Anchor）
<strong>補充說明:通常錨點網址會在一班網址上加上```#```與錨點名稱</strong>
用split() 把井字號分割成陣列,回傳第一個元素

```js
function removeAnchor(url) {
  const remove = url.split("#")
  return remove[0]
}
```
Ans: ```https://example.com#section1``` → ```https://example.com```
     ```https://example.com#section1#section2``` → ```https://example.com#section1```
























