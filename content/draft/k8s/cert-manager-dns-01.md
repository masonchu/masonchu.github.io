---
title: "Cert Manager 使用 DNS01 Challenge Provider"
date: 2019-01-29T15:48:00+08:00
draft: true
categories:
- kubernetes
tags:
- kubernetes
- letsencrypt
---
在這個範例中使用的是 GKE + Google CloudDNS + GoDaddy 環境，其他環境可以參考[DNS01 providers 支援清單](http://docs.cert-manager.io/en/latest/reference/issuers/acme/dns01/index.html#supported-dns01-providers)。

## ref
<http://docs.cert-manager.io/en/latest/reference/issuers/acme/dns01/index.html#supported-dns01-providers>