---
title: "使用 GVM 管理 go 版本"
date: 2018-06-25T14:54:21+08:00
slug: gvm-go-version
draft: false
categories:
  - golang
tags:
  - golang
---

GVM 是一套管理 golang 版本的套件，類似於 nodeJS / nvm。

<!--more-->

## 安裝 GVM

```
bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)
```

安裝之後應該會在 bashrc 下加入 source 的指令，如果安裝完還是找不到 gvm 指令就需要檢查一下這塊。

```
source "/Users/<username>/.gvm/scripts/gvm"
```

## 首次使用 GVM

使用 GVM 安裝 Go1.4 與之後版本。go1.4 版本之後使用 go 對自己編譯，因此沒有安裝 go 的狀況下之後的版本都是無法編譯的。

```
gvm install go1.4 --binary # 直接安裝 binary
gvm use go1.4 # 使用 go1.4 的環境
export GOROOTBOOTSTRAP=$GOROOT # 設定 $GOROOTBOOTSTRAP
gvm install go1.10.3 # 安裝 Go go1.10.3
Installing go1.10.3...
```

```
gvm install go1.4 --binary
gvm use go1.4
export GOROOTBOOTSTRAP=$GOROOT
gvm install go1.10.3
```

## 常用指令

```
gvm list	- 列出全部已經安裝的版本
gvm listall	- 列出線上可安裝版本
gvm use		- 切換使用特定版本
```

## ref

<https://github.com/moovweb/gvm>  
<https://blog.longwin.com.tw/2016/11/golang-gvm-go-version-manager-install-2016/>
