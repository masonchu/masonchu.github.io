---
title: "在本機安裝 Minikube"
date: 2018-07-03T09:56:18+08:00
slug: install-minikube-locally
# thumbnailImagePosition: left
# thumbnailImage: images/kubernetes/minikube.png
draft: false
categories:
  - kubernetes
tags:
  - kubernetes
---

minikube 是 kubernetes 社群推出的的一個輕量型工具，用於在本地端建置模擬 kubernetes 功能。

<!--more-->

minikube 支援以下幾種 vm driver。

1. virtualbox(預設值)
2. vmwarefusion
3. kvm2
4. kvm
5. hyperkit

> 後續內容預設使用 macOS + virtualbox。

## 安裝 VM

## 安裝 kubectl

```text
brew install kubernetes-cli
```

確定安裝版本

```text
kubectl version
```

> 如果還沒有啟動 Minikube 這時候會出現 The connection to the server localhost:8080 was refused 的訊息。

## 安裝 minikube

```text
curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.28.0/minikube-darwin-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```

也可以使用 homebrew 安裝

```text
brew cask install minikube
```

### 啟動 minikube

```
minikube start
```

> 如果是第一次啟動，這時候會自動下載 Minikube ISO & kubelet & kubeadm

```
minikube start --kubernetes-version v1.10.0
```

### 啟動 Minikube 儀表板

```
minikube dashboard
```

![minikube dashboard](/images/kubernetes/minikube-dashboard.png)

## 部署到 Docker Image Minikube

用 echoserver 建立一個測試 deploy

```text
kubectl run hello-minikube --image=gcr.io/google_containers/echoserver:1.4 --port=8080
```

將資源暴露為新的 Kubernetes Service

```text
kubectl expose deployment hello-minikube --type=NodePort
```

這時候可以取得 service url，從 url 就可以看到 service 回應。

```text
minikube service hello-minikube --url
```

當建立 pods 的時候如果有發生 `Insufficient memory / CPU` 的錯誤，可以試著給 minikube 更多資源。

```text
minikube stop && minikube start --cpus 4 --memory 8192
```

<!-- >這並不代表 service 這樣做就可以對外公開，而是只有在 minikube 上面本機檢視。 -->

## reference

<https://kubernetes.io/docs/setup/minikube/#minikube-features>

怎麼暴露本機服務給 minikube
<https://blog.fraq.io/tech/exposing-local-services-to-minikube/>
