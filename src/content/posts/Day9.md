---
title: Day9 屠龍者終有一天要屠龍
date: 2026-05-27
excerpt: 終於初次見面的Vue.js 
image: /images/image6.jpg
tags: [Vue.js, ref, directives, v-if, v-for, v-on, v-bind, v-model]
---
最近越來越覺得時間不太夠用，不知道班上的其他人是不是也有一樣的感覺。

每天上課都在學新的東西，課後的休息時間又忍不住吸收很多 AI 相關的知識；下課回家後，還要複習、整理筆記，順便維護這個部落格。基本上只要時間允許，不管多晚，我都還是會擠出一點時間運動一下。

雖然真的很累、很忙，但也有一種「我還活著」的忙碌感。

不知道大家有沒有看過《葬送的芙莉蓮》。主角一行人中有一位戰士叫修塔爾克，他每天都不斷修練。村裡的人們一直依靠著他強大的實力，認為他能保護村子，避免巨龍帶來災難。

但其實修塔爾克自己也很害怕。

他明知道惡龍就在那裡，卻始終不敢真正向前討伐，只能一直停留在原地，日復一日地劈砍同一座大山。直到那座山都被他劈成兩半，他依然沒有鼓起勇氣面對惡龍。

直到芙莉蓮出現，把害怕戰鬥的修塔爾克推上了戰場。

原本以為那會是一場驚心動魄的對決，結果，那位一直懷疑自己的強大戰士，只用一刀就結束了戰鬥。

## 終於初次見面的 Vue.js
前面幾天大多都在補 JavaScript、Git、測試之類的基礎，今天終於開始碰到前端框架 Vue.js。  
老實說剛開始看到 `createApp`、`ref`、`v-if`、`v-for` 這些東西，會有一種「怎麼又多一套語法」的感覺。

但整理完課程內容後，Vue 想解決的事情其實可以先濃縮成一句話：

**Vue 讓你專心改資料，畫面會跟著資料自動更新。**

以前用原生 JavaScript 寫互動時，常常要自己找 DOM、綁事件、改資料，最後還要手動把新的資料塞回畫面。  
Vue 則是把「資料」和「畫面」綁在一起，只要資料變了，畫面就會跟著更新，這也是我目前覺得最重要的觀念。

## Vue 想解決什麼問題?
在進 Vue 之前，課程先複習了 HTML、CSS、JavaScript 的分工：

<ul>
  <li>HTML 負責畫面結構</li>
  <li>CSS 負責外觀樣式</li>
  <li>JavaScript 負責互動邏輯</li>
</ul>

如果是傳統寫法，要做一個計數器，大概會經歷這些步驟：

1. 用 `querySelector` 找到畫面上的元素。
2. 用 `addEventListener` 綁定按鈕事件。
3. 點擊後讓 `count++`。
4. 再用 `textContent` 手動更新畫面。

這樣寫當然可以，但當畫面變複雜、資料變多時，就很容易變成到處都在找 DOM、改 DOM。  
Vue 的想法比較像是：我們先把資料準備好，畫面要顯示什麼就從資料來，事件發生時也是改資料，剩下的畫面更新交給 Vue 處理。

## 建立 Vue App 的基本流程
入門時可以先用 CDN 建立最小的 Vue App，不需要馬上開一個完整專案。

```html
<div id="app">
  {{ message }}
</div>

<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script src="./main.js"></script>
```

```js
const { createApp, ref } = Vue

createApp({
  setup() {
    const message = ref('Hello Vue!')

    return {
      message
    }
  }
}).mount('#app')
```

這段流程可以拆成幾個重點：

<ul>
  <li>`createApp()` 建立 Vue 應用程式</li>
  <li>`setup()` 裡面放資料和方法</li>
  <li>`return` 出去的東西，template 才能使用</li>
  <li>`mount('#app')` 把 Vue 掛到 HTML 的 `#app` 上</li>
</ul>

如果要建立正式專案，之後就會用 Vite：

```bash
npm create vue@latest
npm install
npm run dev
```

目前先知道 `npm run dev` 是開發時啟動網站，`npm run build` 是打包正式版本就夠了。

## ref()：讓資料變成響應式
Vue 裡很常看到 `ref()`，它的用途是建立響應式資料。  
所謂響應式，可以先理解成：資料改變時，畫面也會自動跟著改變。

```js
const count = ref(0)

const add = () => {
  count.value++
}
```

這裡有一個初學者很容易卡住的地方：  
在 JavaScript 裡讀取或修改 `ref` 的值，要用 `.value`。

```js
count.value++
```

但是在 HTML template 裡顯示時，不用寫 `.value`：

```html
<p>{{ count }}</p>
<button @click="add">+1</button>
```

也就是說：

| 使用位置 | 寫法 |
|---|---|
| JavaScript 裡讀取 / 修改 | `count.value` |
| HTML template 裡顯示 | `{{ count }}` |

這個規則先記起來，後面看到 Vue 範例會順很多。

## 從原生 JS 到 Vue 的差異
用計數器來看會最明顯。

原生 JavaScript 可能會這樣寫：

```js
const countElement = document.querySelector('.count')
const button = document.querySelector('.clickButton')

let count = 0

button.addEventListener('click', () => {
  count++
  countElement.textContent = count
})
```

Vue 的寫法則是先準備資料和方法：

```js
const { createApp, ref } = Vue

createApp({
  setup() {
    const count = ref(0)

    const add = () => {
      count.value++
    }

    return { count, add }
  }
}).mount('.container')
```

再把資料和事件接到畫面上：

```html
<span>{{ count }}</span>
<button @click="add">+1</button>
```

兩種寫法最大的差異不是程式碼變短而已，而是思考方式不同。

| 原生 JS | Vue |
|---|---|
| 手動找 DOM | 直接宣告資料 |
| 手動更新畫面 | 畫面自動跟資料同步 |
| 邏輯容易散落 | 資料和方法集中在 `setup()` |

## Directives：Vue Template 的超能力
Directive 是 Vue template 裡的特殊指令，通常會用 `v-` 開頭。  
它可以讓 HTML 不只是靜態畫面，而是能根據資料顯示、隱藏、重複渲染、綁定事件或表單。

例如：

```html
<p v-if="isVisible">{{ message }}</p>
```

這行的意思是：當 `isVisible` 是 true 時，才顯示這段文字。

常見的 directives 有這些：

| 指令 | 用途 | 常用寫法 |
|---|---|---|
| `v-text` | 顯示純文字 | `<p v-text="name"></p>` |
| `v-html` | 插入 HTML | `<div v-html="content"></div>` |
| `v-if` | 條件成立才建立元素 | `<p v-if="ok">Hi</p>` |
| `v-show` | 用 CSS 顯示 / 隱藏 | `<p v-show="ok">Hi</p>` |
| `v-for` | 顯示列表 | `<li v-for="item in items" :key="item.id">` |
| `v-on` | 綁定事件 | `<button @click="add">` |
| `v-bind` | 綁定屬性 | `<img :src="url">` |
| `v-model` | 表單雙向綁定 | `<input v-model="name">` |

## 常見指令整理
`{{ }}` 是最常見的文字顯示方式，`v-text` 也可以顯示純文字。  
比較需要小心的是 `v-html`，因為它會把字串當成 HTML 插入，如果內容來自使用者輸入，就可能有安全風險。

```html
<p>{{ studentName }}</p>
<p v-text="studentName"></p>
<div v-html="welcomeMessage"></div>
```

`v-if` 和 `v-show` 都能控制顯示，但做法不一樣：

```html
<p v-if="isLoggedIn">歡迎回來</p>
<p v-else>請先登入</p>

<p v-show="isVisible">這段可以被顯示或隱藏</p>
```

| 項目 | `v-if` | `v-show` |
|---|---|---|
| 元素不存在時 | DOM 真的不在 | DOM 還在 |
| 切換方式 | 建立 / 移除 | CSS `display` |
| 適合情境 | 不常切換 | 常常切換 |

`v-for` 用來渲染列表，通常要搭配 `:key`：

```html
<ul>
  <li v-for="pet in pets" :key="pet.id">
    {{ pet.name }} - ${{ pet.price }}
  </li>
</ul>
```

```js
const pets = ref([
  { id: 1, name: '小貓', price: 300 },
  { id: 2, name: '小狗', price: 400 }
])
```

`:key` 就像是每一筆資料的身分證，讓 Vue 知道誰是誰。  
如果資料本身有 `id`，就優先用 `id`，不要一開始就偷懶全部用 index。

事件綁定可以用 `v-on`，更常見的是簡寫 `@`：

```html
<button v-on:click="add">+1</button>
<button @click="add">+1</button>
```

屬性綁定可以用 `v-bind`，簡寫是 `:`：

```html
<img v-bind:src="avatarUrl" v-bind:alt="userName">
<img :src="avatarUrl" :alt="userName">
```

綁定 class 和 style 也很常見：

```html
<button :class="{ active: selectedTheme === theme }">
  {{ theme }}
</button>

<div
  :style="{
    backgroundColor: selectedTheme,
    width: boxSize + 'px',
    height: boxSize + 'px'
  }"
></div>
```

最後是 `v-model`，它常用在表單，可以讓使用者輸入和 Vue 資料互相同步。

```html
<input v-model="character.name" type="text">
<p>名稱：{{ character.name }}</p>

<select v-model="character.class">
  <option value="wizard">法師</option>
  <option value="warrior">戰士</option>
</select>
```

```js
const character = ref({
  name: '',
  class: 'wizard',
  skills: []
})
```

常見簡寫可以整理成這樣：

| 完整寫法 | 簡寫 | 意思 |
|---|---|---|
| `v-on:click="add"` | `@click="add"` | 綁定事件 |
| `v-bind:src="url"` | `:src="url"` | 綁定屬性 |
| `v-bind:class="classes"` | `:class="classes"` | 綁定 class |
| `v-bind:style="styles"` | `:style="styles"` | 綁定 style |

## 今日小結
今天的內容雖然看起來很多，但主軸其實很單純：  
先用 `ref` 準備資料，再用 directives 把資料、事件、屬性和表單接到畫面上。

目前我覺得最重要的是先建立這個 Vue 思考方式：

1. 先準備資料。
2. 在 template 顯示資料。
3. 用 `@click`、`v-model` 這類指令改資料。
4. Vue 自動更新畫面。

所以學到這裡之後，至少已經可以看懂 Vue 最基本的寫法，也可以開始做一些小型互動功能。  
下一步就是多練幾次 `v-if`、`v-for`、`@click`、`:class` 和 `v-model`，把這些語法變成直覺。
