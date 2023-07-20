---
title: "Cobra 強大的 Golang 命令列工具"
date: 2018-06-27T12:49:40+08:00
slug: golang-cobra
draft: false
categories:
- golang
tags:
- golang
---
Cobra 是一套可以快速可以快速建立 golang CLI 工具的套件。在 golang 的生態圈內到處都可以看到相關的痕跡。最有名的包含 docker, k8s 都使用 cobra 處理 CLI 介面。

<!--more-->

## 使用方法

### 安裝

如果已經準備好 go 的環境，只需要執行 go get 就可以將 cobra 加入安裝。

```code
go get -u github.com/spf13/cobra/cobra
```

### 建立根命令

```
cobra init
```
> 注意如果目錄下已經有檔案會出現 Cobra will not create a new project in a non empty directory，這時候新開目錄建立之後把全部資料移過來就可以。（需要修改 main.go import 路徑）

應該會建立以下檔案
+ cmd  
  root.go
+ main.go

```text
package main

func main() {
	cmd.Execute()
}
```

這時候只要執行 `go run main.go` 就會顯示 cobra 預設的 CLI 指令。

```text
A longer description that spans multiple lines and likely contains
examples and usage of using your application. For example:

Cobra is a CLI library for Go that empowers applications.
This application is a tool to generate the needed files
to quickly create a Cobra application.
```

### 加入額外命令

```text
cobra add <command name>
```

### 使用外部參數

預設使用 viper 套件處理環境變數。
## ref
<https://github.com/spf13/cobra>