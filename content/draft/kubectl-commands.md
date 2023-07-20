---
title: "認識 Kubectl 相關指令"
date: 2018-07-03T13:56:47+08:00
draft: true
weight: 30
# pre: "<b>2. </b>"
---

## 取得 k8s deployemnt & pods
```
kubectl get deploy,po
```
expose port
```
kubectl expose deployment hello-minikube --type=NodePort
```

```
curl $(minikube service nsq-lookup --url)
```