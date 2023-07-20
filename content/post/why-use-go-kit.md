---
title: "microservices 套件(1) - go-kit"
date: 2017-07-05T15:52:11+08:00
slug: why-use-go-kit
categories:
  - golang
tags:
  - microservice
  - golang
draft: true
---

<!-- ![](/images/go-kit microservices.png){: width=50 } -->

## 什麼是 go-kit

go-kit 是一套 golang 針對 microservices 架構開發的 toolkit，目的在於建立 go-kit 能成為 golang 在 microservices 框架下的標準 library (注意不是 framework) 讓開發的時候只需要專注在商業邏輯 上，而 microservices 不同協定下的問題就可以直接 引用 go-kit 來處理。

<!--more-->

> 作者 Peter Bourgon 在 SoundCloud 的時候發現，雖然公司內部專案已經有很多使用 go 開發，但是往往 在建立新專案的時候，go 不會被選擇到，而是使用 scala / ruby，原因是由於 library 不足 。造成在使用 go 的時候 許多看似共通的問題還是要從頭開始造輪子。因而催生了 go-kit 這個 專案。

go-kit 是 golang 類似的套件中，最早開始被關注的，後來的類似套件或多或少 都參考了其中一部分的概念，尤其是在 transport / endpoint。

## go-kit 已經做到了些什麼

## go-kit 還沒有做到什麼

- 除了 RPC 之外的訊息傳遞支援

## ref

最终，为什么选择 go-kit <https://www.jianshu.com/p/0c34a75569b1>  
Why I Recommend to Avoid Using the go-kit Library <https://gist.github.com/posener/330c2b08aaefdea6f900ff0543773b2e>  
Peter Bourgon 谈使用 Go 和“Go kit”构建微服务 <http://www.infoq.com/cn/news/2015/09/microservices-with-go-kit>  
Go + Microservices = Go Kit [I] - Peter Bourgon, Go Kit <https://www.youtube.com/watch?v=NX0sHF8ZZgw>  
Discussion: package pubsub <https://github.com/go-kit/kit/issues/295>
