---
title: 115 上 「 行動網頁製作與應用 」 第 1 次作業
description: 行動網頁製作與應用作業
pubDatetime: 2026-09-14
tags:
  - Learning
  - homework
  - html
  - javascript
featured: false
---
<div align="center">

## 國立空中大學 管理與資訊學系

### 115 上 「 行動網頁製作與應用 」 第 1 次作業題目

### 班別：ZZZ002班 學生姓名：張欣容 學號：115xxxxxx

</div>

#### 1. 請任意介紹 HTML的五種標籤，並說明各個標籤的用途 。 (30%)

`<h1>`：最大標題，標題大小有分為1~6個層級

`<p>`：Paragraph 段落，用來放一般文字內容

`<br>`：換行

`<img>`：圖片，完整寫法 -> `<img src="圖片連結" alt="替代文字">`

`alt`實務上很常會加，通常會加在有資訊價值、會影響內容理解的圖片

`<a>`：超連結，完整寫法 -> `<a href="網址">要顯示的文字</a>`

---

#### 2. 請簡述介紹 Javascript 中的物件表示式、方法與屬性，並舉例說明 。 (40%)

JavaScript 中的物件表示式是使用大括號 {} 建立物件的方式，物件裡面可以包含屬性與方法

- 物件：是什麼東西

- 屬性：有什麼資料

- 方法：可以做什麼

例如：

```Javascript

let person = {
  name: "小明",
  age: 18,
  hello: function() {
    alert("你好");
  }
};

```

`console.log(person.name);`

`person.hello();`

其中 person 是物件，name 和 age 是屬性，hello() 是方法。

---

#### 3. 什麼是 jQuery Mobile？它具有哪些特性 ？(30%)

**jQuery Mobile 是一套專門用來開發手機版網頁的前端 UI 框架**

他可以讓開發者使用 HTML、CSS 和 JavaScript 快速建立適合手機、平板等行動裝置操作的網站

- jQuery：簡化 JavaScript 操作

- jQuery Mobile：提供適合手機操作的按鈕、表單、選單及頁面切換效果。

**jQuery Mobile 特性：**

1. 支援跨平台，像是安卓或是蘋果瀏覽器

2. 響應式，能配合不同裝置的螢幕尺寸調整網頁排版

3. 支援觸控的操作，方便使用者操作

4. 容易學也容易開發

5. 提供豐富的 UI 元件

6. 支援 HTML5 ，可以減少很多複雜的code

---

[給開發者的WEB技術文件-HTML](https://developer.mozilla.org/zh-TW/docs/Web/HTML)