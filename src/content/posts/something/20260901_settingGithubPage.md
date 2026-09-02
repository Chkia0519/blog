--- 
title: 自訂網域與GitHub Page設定
description: 如何在GitHub Page設定網域
pubDatetime: 2026-09-01
tags:
  - Note
  - GitHub
  - GitHub Page
  - Domain 
featured: False
---

前幾天買了個自訂網域要套用到現在的Blog網址上

我在[cloudflare](https://domains.cloudflare.com/)購買的

在設定上有點兒問題，所以問了GPT要怎麼設定

原來GitHub Page可以繼承自訂網域，超酷ㄉ


> [!TIP] GitHub 官方機制：
> 
> 如果你的使用者 Pages(使用者名稱.github.io)使用自訂網域
> 
> 那同帳號底下的 Project Pages 會自動保留 Repository 名稱當路徑

---

首先建立一個 GitHub Repository，名稱一定要完全是：

`Chkia0519.github.io`  使用者名稱.github.io

我先在裡面放個個index.html，之後再想想要補甚麼

要進到 Setting -> Page -> Custom domain

Custom domain 輸入自訂網域後，要到購買網域的地方設定DNS

這樣子之後有放在github page上但未設定網域的網頁

預設就會是我在`Chkia0519.github.io`裡設定的自訂網域

---

設定DNS

GitHub Pages 官方目前提供的 IPv4 位址：

| Type | Name | Content |
| ------ | ------ | ------ |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |

自己的網域：
| Type | Name | Content |
| ------ | ------ | ------ |
| CNAME | www | Chkia0519.github.io(使用者名稱.github.io) |
| CNAME | learning-blog(自訂子網域) | Chkia0519.github.io(使用者名稱.github.io) |

如果後續有再新增其他的自訂子網域也需要再設定DNS~

---

那因為我今天設定繼承自己的子網域，所以我Astor就有一些資料要改

`astro.config.ts`：

```
site: "https://learning-blog.chkia.dev",
base: "/blog",
```
site = 網域

base = 網域後面的固定路徑

因為我想留著 `/blog`，所以 base 的部分就沒有改，只改 site 的網址


`astro-paper.config.ts`：

```
url: "https://learning-blog.chkia.dev/blog",
```

`astro-paper.config.ts`裡的url是給 AstroPaper 主題看的正式網址

所以就直接填完整網址就好

---

目前這篇是暫時用繼承的，但是我其實想不使用繼承

不然每一個開頭都是`learning-blog.chkia.dev/`

目前是因為卡在HTML跟CSS，所以暫時用繼承的

我想讓網頁自己獨立一個子網域

---