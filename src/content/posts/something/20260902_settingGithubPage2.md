--- 
title: 不繼承自訂網域與GitHub Page設定
description: 如何在GitHub Page設定網域
pubDatetime: 2026-09-02
tags:
  - Note
  - GitHub
  - GitHub Page
  - Domain 
featured: False
---

續前篇是暫時用繼承的，但是我其實想不使用繼承

我想讓網頁自己獨立一個子網域

---

我目前還沒開始建立，但可以先做個紀錄，一步一步建立

整個結構需要調整成：

```
C:\blog
│
├─ src/
├─ public/
├─ astro.config.ts
│
├─ root-site/
│   └─ index.html        ← 網域首頁，可做可不做
│
└─ Build 後
    site/
    ├─ index.html
    │
    └─ blog/
        ├─ index.html
        ├─ _astro/
        └─ posts/
```

S