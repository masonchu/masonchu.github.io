---
title: "安裝和啟用 NSQ 服務"
date: 2018-06-21T15:53:16+08:00
slug: install-and-start-nsq
categories:
- microservice
tags:
- microservice
- golang
draft: false
---
NSQ 是一套用 GO 開發的訊息傳遞系統。同樣角色時常拿來比較的對象是 rabbitMQ、kafka。
<!--more-->

<!-- # 使用 NSQ -->
## 安裝 NSQ 在本機測試環境
NSQ 本身有提供 brew / docker 版本。在這邊我是直接使用 github 原始碼下載編譯，注意 golang 1.7+ 並且已經有 dep 套件管理。在 test.sh 會執行 golang test & 編譯出所有的可執行檔。

### 下載 source code & 安裝相依性套件
```
git clone https://github.com/nsqio/nsq $GOPATH/src/github.com/nsqio/nsq
cd $GOPATH/src/github.com/nsqio/nsq
dep ensure
```
### 測試 & 編譯
```
./test.sh
```
<!-- ### 安裝到 $GOPATH/bin
```
go install ./apps/nsqlookupd
go install ./apps/nsqd
go install ./apps/nsqadmin
``` -->
### 安裝 NSQ
安裝至 /usr/local/bin 目錄
```
make install
```

### 依序啟動服務
nsqlookupd 預設監聽 http:4161 / tcp:4160，而 nsqd 啟動時自動到 nsqlookupd 註冊。
```
nsqlookupd
nsqd --lookupd-tcp-address=127.0.0.1:4160
nsqadmin --lookupd-http-address=127.0.0.1:4161
```

## 使用 go-nsq 發布與接受訊息

## 發佈環境配置
使用在 microservices 中時候，nsqd 建議並不是全部 services 共用，而是使用 sidecar 模式註冊到 nsqlookupd。 

在 nsq gitlab issue 中提到，建議在每個 node 都部署一個 nsqd 再註冊到一台或多台的 nsqlookup 中，這樣各自的 service 生產的訊息就通一推到各自的 sidecar，再由 nsqd 處理訊息這一段。   

> You may have your nsqds and nsqlookupds segregated so that all nodes are good candidates (we do this also), but this isn't a requirement. nsqlookupd can handle several nsqd "clusters" with distinct responsibilities, like a service discovery service.

 >When you get the nodes back you'll have to make a decision about which node you want to publish to. In our setup we either publish to localhost if nsqd is on the same box or a VIP.

<!-- ## 在 kubernete 上建立 nsq 服務

```
kubectl run nsqlookup --image=nsqio/nsq /nsqlookupd --port=4161
```
```
kubectl expose deployment nsqlookup --type=NodePort
```
```
kubectl run nsqadmin --image=nsqio/nsq /nsqadmin --lookupd-http-address=localhost:4161 --port:4171
```
10.96.49.165 -->
## ref
<https://nsq.io/deployment/production.html>  
<https://github.com/nsqio/go-nsq/issues/170>  
<https://segmentfault.com/a/1190000009194607>  
