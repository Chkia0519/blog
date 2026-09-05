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

---

### 第一步

確認`astro.config.ts`、`astro-paper.config.ts`

裡面的資訊如果是我要指向的網址就OK

如果不是就需要更動

因我前一天已經有把這邊更動成我要的，所以今天就檢查就好

---

### 第二步

修改 GitHub Actions 的部署方式

要把整份的`deploy.yml`都改掉

```
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v7

      - name: Setup PNPM
        uses: pnpm/action-setup@v4
        with:
          version: 11.24.0

      - name: Setup Node
        uses: actions/setup-node@v6
        with:
          node-version: 22
          cache: pnpm

      - name: Install dependencies
        run: pnpm install --frozen-lockfile

      - name: Build Astro site
        run: pnpm build

      - name: Move site into /blog
        run: |
          mkdir -p site/blog
          cp -r dist/. site/blog/

      - name: Create root redirect
        run: |
          cat > site/index.html <<'EOF'
          <!doctype html>
          <html lang="zh-TW">
          <head>
            <meta charset="UTF-8">
            <meta http-equiv="refresh" content="0; url=/blog/">
            <title>Chkia 的學習部落格</title>
          </head>
          <body>
            <p>正在前往 <a href="/blog/">Chkia 的學習部落格</a>...</p>
          </body>
          </html>
          EOF

      - name: Upload GitHub Pages artifact
        uses: actions/upload-pages-artifact@v4
        with:
          path: site

  deploy:
    needs: build
    runs-on: ubuntu-latest

    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}

    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v5
```

底下這兩行很重要：

1. 
`mkdir -p site/blog` -> 建置`site/blog`這個資料夾

`mkdir`：make directory 創造資料夾

`-p`：如果上層資料夾不存在，就一起建立；如果資料夾已經存在，也不要報錯

2. 
`cp -r dist/. site/blog/` -> 把`dist`裡面所有建置完成的檔案，複製到`site/blog/`

`cp`：copy 複製

`-r`：recursive 遞迴複製 要加這個才可以把資料夾一起複製

因為我想要整個對應https://learning-blog.chkia.dev/blog/

所以就需要做這兩步，不然結構會對不上

再來就是`Create root redirect`這邊，是為了要讓index.html直接跳轉至/blog

---

### pnpm exec astro build


---

### 調整Settings

進到專案 -> Settings -> Page

Custom domain 這邊要改成`learning-blog.chkia.dev`

這樣我就可以不用利用`Chkia0519.github.io`來繼承了

---

真的還有好多要學的東西，學無止盡~~~

---