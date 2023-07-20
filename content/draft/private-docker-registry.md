---
title: "建立私有 docker registry"
date: 2018-07-04T11:41:27+08:00
draft: true
---
## 確認 docker 安裝
如果在這台機器上市第一次安裝 Docker CE 需要先設定 docker repository
```
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
```

```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
### INSTALL DOCKER CE
```
sudo apt-get update
sudo apt-get install docker-ce
```
## 建立 Docker registry
```
docker run -d -p 5000:5000 --restart always --name registry registry:2
```
### 建立 TLS 憑證

> In order to make your registry accessible to external hosts, you must first secure it using TLS.

設定完憑證之後的 docker repository 才能從遠端存取
```
> docker login [OPTIONS] [SERVER]

[OPTIONS]: 
-u username 
-p password
```
```
docker pull ubuntu:16.04
docker tag ubuntu:16.04 myregistrydomain.com/my-ubuntu
docker push myregistrydomain.com/my-ubuntu
docker pull myregistrydomain.com/my-ubuntu
```
<!-- ```
docker pull ubuntu:16.04
docker tag ubuntu:16.04 dr.cow.bet/test-ubuntu
docker push dr.cow.bet/test-ubuntu
docker pull dr.cow.bet/test-ubuntu
``` -->
```
docker image remove ubuntu:16.04
docker image remove myregistrydomain.com/my-ubuntu
```

## 安裝 Docker registry UI

使用 docker-registry-frontend 建立 docker repository UI。在這我直接安裝在同一台 server 上因此指定 host 是本機端，將 docker 內部 80 導向 host 的 8080 port
```
docker run -d -p 8080:80 \
-e ENV_DOCKER_REGISTRY_HOST=myregistrydomain.com \
-e ENV_DOCKER_REGISTRY_PORT=80 \
konradkleine/docker-registry-frontend:v2
``` 
<!-- docker run -d -p 8080:80 \
-e ENV_DOCKER_REGISTRY_HOST=localhost \
-e ENV_DOCKER_REGISTRY_PORT=5000 \
konradkleine/docker-registry-frontend:v2 -->
> 這邊呼叫的時候會遇到 Access-Control-Allow-Origin 的問題，我的做法是直接在 caddy 上面開啟
## ref
<https://docs.docker.com/registry/deploying/>
<https://kairen.github.io/2016/01/02/container/docker-registry/>
<https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-docker-registry-on-ubuntu-14-04>