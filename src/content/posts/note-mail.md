---
title: mailto - 使用方式
description: mailto
pubDatetime: 2026-07-28
tags:
  - Learning
  - Note
featured: true
---

## 因為在調整這個網站的時候不小心把mailto刪掉而發現的事情

```
<a href="mailto:信箱">信箱</a>  ->一般常用範例

{ name: "mail",     url: "mailto:信箱" }  ->我是錯在這個

```
當使用者點擊連結就會自動開啟outlook或是其他可寄信的程式，且會將收件人帶入你輸入的信箱

我就是因為在調整的時候不小心刪掉，怎麼點都是error，才發現這件事


### URL Scheme 網址協定

URL Scheme 網址協定是**告訴瀏覽器「這個網址要怎麼處理」的一種格式。**

- mailto: mailto:信箱

- https: https:網址

- tel: tel:+880912345678 建議使用國際區碼

 >[!TIP] 一般會搭配 ```<a href> </a>``` 超連結來做使用

---

在查閱錯誤的時候也發現了這個網站是用JavaScript寫的，我錯的部分是物件導向的其中一項 :O
看來我也應該花一些時間來學一下了JavaScript了

