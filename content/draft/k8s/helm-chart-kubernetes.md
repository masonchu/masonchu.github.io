---
title: "Helm Kubernetes 管理工具"
date: 2018-08-23T14:30:14+08:00
draft: true
---
kubernetes 本身已經將安裝流程簡化，共用的設定也可以抽出到 config-map。但是不同服務之間還是有相依性設定需要人工介入，這時候就是可以利用 Helm 的時候了。

## TL;DR
安裝 helm
```
brew install kubernetes-helm
```
在 kubernetes cluster 初始化 helm
```
helm init
```
確認 helm 狀態
```
helm version
```
應該會顯示 client & server 版本狀況
```
Client: &version.Version{SemVer:"v2.9.1", GitCommit:"20adb27c7c5868466912eebdf6664e7390ebe710", GitTreeState:"clean"}
Server: &version.Version{SemVer:"v2.9.1", GitCommit:"20adb27c7c5868466912eebdf6664e7390ebe710", GitTreeState:"clean"}
```
## ref