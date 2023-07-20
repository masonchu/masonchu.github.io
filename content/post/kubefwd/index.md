---
title: "kubefwd 好用的服務轉發工具"
date: 2023-07-20T16:20:26+08:00
categories:
  - kubernetes
tags:
  - golang
  - kubernetes
keywords:
  - tech
# thumbnailImage: images/cover/kubefwd.png
---

對於 Kubernetes 服務開發來說，在本地進行測試時候，會因為相依服務的問題比較繁瑣，或是在分階段偵錯遇到麻煩。kubefwd 可以將 Kubernetes 集群中的服務直接轉發到本地機器，不需要發佈到集群中。可以支援 ClusterIP、NodePort 或 LoadBalancer 不同服務，這樣可以在本地環境中進行測試和確認問題。

<!--more-->

對代碼進行修改，然後直接在本地運行測試。使用 kubefwd 的好處在於，避免擔心相依的服務，因為它們看起來就像在 Kubernetes 集群中運行一樣，我們可以通過 local 連線。加快整體的測試速度

## TD;LR

Brew 安裝

```
brew install txn2/tap/kubefwd
```

轉發特定標籤的服務

```
kubefwd svc -l <label-selector>
```

轉發 dev 命名空間至本地特定 hosts

```
kubefwd svc -n dev -d mason.dev
```

## reference

<https://github.com/txn2/kubefwd>
