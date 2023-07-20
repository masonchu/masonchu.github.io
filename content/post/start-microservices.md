---
menuTitle: "microservices"
title: "開始微服務架構"
date: 2018-06-29T11:03:34+08:00
slug: start-microservices
categories:
  - microservice
tags:
  - microservice
draft: false
---

決定系統往微服務架構前進。

<!--more-->

## 前置作業

開始進行 microservices 至少要具備的基本建設。

### 開發相關配置

1. 服務發現 service discovery
   1. k8s
   2. etcd
   3. consul
   4. zookeeper
   5. Netflix/eureka
2. 事件訊息 (非同步訊息) event sourcing messaging
   1. kafka
   2. NSQ
3. 訊息傳遞(同步訊息) transport
   1. grpc
   2. thrift
   3. http
4. 系統監控 monitor
   1. metrics
   2. Prometheus
   3. Grafana
5. 斷路器 Circuit Breaker
6. Health Check
7. 紀錄追蹤 Log Tracking
   1. opentracing
   2. zipkin
   3. Elasticsearch
   4. Stackdriver
8. Auth

### Devops

1. CI / CD
2. Docker
3. k8s

## golang 相關套件

1. go-kit <https://github.com/go-kit/kit>
2. go-micro <https://github.com/micro/go-micro>
3. gizmo <https://github.com/nytimes/gizmo>
4. rpcx <https://github.com/smallnest/rpcx>

## 造成延伸問題

microservices solve organizational problems  
microservices cause technical problems

## ref

Go + Microservices = Go Kit [I] - Peter Bourgon, Go Kit <https://www.youtube.com/watch?v=NX0sHF8ZZgw>  
微服務基礎建設 - Service Discovery <http://columns.chicken-house.net/2017/12/31/microservice9-servicediscovery/>

