---
title: "第一次使用 Hugo 就上手"
date: 2017-07-05T12:35:25+08:00
categories:
  - golang
tags:
  - hugo
  - golang
slug: "first-hugo"
draft: false
---

Hugo 是一套生成靜態頁面的工具(static site generator)。利用 Markdown 將內容跟樣式外觀完整分開 ，再利用生成的靜態網頁直接發佈到 server 上。般來說 markdown 語法對應樣式種類會比較少，但是相對的也是幫助在寫作的時候專注在內容而不是樣式上。

<!--more-->

### 與動態的 blog 平台比較

##### 優點

1. 很容易對文章內容進行 git 版控 或是多人協作
2. 生成的靜態網頁瀏覽速度很快，也不需要對 server 系統依賴
3. 容易互相在 同類型的 靜態生成工具之間轉換，只要把 markdown 的文章內容帶著走就好了

##### 缺點

1. 需要熟悉 markdown , git
2. 通常不會有線上編輯模式或是管理平台
3. 如果想要取得流量或讀者留言需要註冊其他服務

## 第一次安裝

如果是 mac OS 只要執行

    brew install hugo

就可以直接安裝完成，之後進入選定好 儲存檔案的目錄下

    hugo new site <SiteName>

就會建立出預設的檔案目錄

### 建議第一篇 post

```
hugo new post/my-first-post.md
```

建立後的 md 檔案產生在 content/post 目錄

### 選擇 Theme

### 挑選寫作工具

### 常用指令

    //建立可以發佈的靜態檔案
    hugo
    // 建立 local 端 server 連同草稿
    hugo server --buildDrafts

---

Hugo 官網說明文件 <https://gohugo.io/overview/quickstart/>
