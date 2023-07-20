---
title: "Angular 容器化 kubernetes 安裝"
date: 2018-08-06T11:11:58+08:00
draft: true
---

## CDN 發佈設定

如果有使用到 cdn 加速會變得比較複雜，一般發佈我們都知道只要將 `ng build` 加入參數 `--deploy-url` 就可以指定 cdn 位置。但是這個參數需要在建置時期就代入，沒辦法在 build 產生 dist 之後才去變更。

## 修改根目錄 base href

## ref

https://github.com/angular/angular-cli/issues/4318  
https://medium.com/voobans-tech-stories/multiple-environments-with-angular-and-docker-2512e342ab5a

https://medium.com/@tiangolo/angular-in-docker-with-nginx-supporting-environments-built-with-multi-stage-docker-builds-bb9f1724e984