---
title: "安裝 Caddy Webserver"
date: 2018-07-04T17:08:27+08:00
draft: true
---
Caddy 在目前的版本商用授權已經不支援免費版本了，但是幸好的是 source code 授權沒有更動，如果從 source code 直接編譯可以避免掉授權問題。

## 1. 從 source code 建置 Caddy

```
go get github.com/mholt/caddy/caddy
```

```
cd $GOPATH/src/github.com/mholt/caddy
```
```
git checkout -b "adding_plugins" "v0.10.12"
```

```
go install github.com/mholt/caddy/caddy
```

## 安裝 Caddy

複製 Caddy 執行檔到 `/user/local/bin`

```
sudo cp $GOPATH/bin/caddy /usr/local/bin/
```
設定 Caddy 執行權限
```
sudo chown root:root /usr/local/bin/caddy
```
```
sudo chmod 755 /usr/local/bin/caddy
```
```
sudo setcap 'cap_net_bind_service=+ep' /usr/local/bin/caddy
```
建立 Caddy 預設設定檔放置目錄
```
sudo mkdir /etc/caddy
```
```
sudo chown -R root:www-data /etc/caddy
```
設定 TLS 相關目錄，讓 Caddy 可以啟用 Let's Encrypt 自動更新 SSL 功能
```
sudo mkdir /etc/ssl/caddy
sudo chown -R root:www-data /etc/ssl/caddy
```
```
sudo chmod 0770 /etc/ssl/caddy
```
建立 Caddy 設定檔
```
sudo touch /etc/caddy/Caddyfile
```
安裝 service 將 service 檔案複製到 systemd 目錄下。
```
sudo cp $GOPATH/src/github.com/mholt/caddy/dist/init/linux-systemd/caddy.service /etc/systemd/system/
```
設定只有 root 才能編輯這個檔案
```
sudo chmod 644 /etc/systemd/system/caddy.service
```

## 啟動 caddy server
```
sudo systemctl start caddy
sudo systemctl status caddy
```

## Caddy 相關設定


```
# Should work on all Debian based distros with systemd; tested on Ubuntu 16.04+.
# This will by default install all plugins; you can customize this behavior on line 6. Selecting too many plugins can cause issues when downloading. 
# Run as root (or sudo before every line) please. Note this is not designed to be run automatically; I recommend executing this line by line.

apt install curl
curl https://getcaddy.com | bash -s personal dns,docker,dyndns,hook.service,http.authz,http.awses,http.awslambda,http.cache,http.cgi,http.cors,http.datadog,http.expires,http.filemanager,http.filter,http.forwardproxy,http.geoip,http.git,http.gopkg,http.grpc,http.hugo,http.ipfilter,http.jekyll,http.jwt,http.locale,http.login,http.mailout,http.minify,http.nobots,http.prometheus,http.proxyprotocol,http.ratelimit,http.realip,http.reauth,http.restic,http.upload,http.webdav,net,tls.dns.auroradns,tls.dns.azure,tls.dns.cloudflare,tls.dns.cloudxns,tls.dns.digitalocean,tls.dns.dnsimple,tls.dns.dnsmadeeasy,tls.dns.dnspod,tls.dns.dyn,tls.dns.exoscale,tls.dns.gandi,tls.dns.gandiv5,tls.dns.godaddy,tls.dns.googlecloud,tls.dns.lightsail,tls.dns.linode,tls.dns.namecheap,tls.dns.ns1,tls.dns.otc,tls.dns.ovh,tls.dns.powerdns,tls.dns.rackspace,tls.dns.rfc2136,tls.dns.route53,tls.dns.vultr
sudo chown root:root /usr/local/bin/caddy
sudo chmod 755 /usr/local/bin/caddy
sudo setcap 'cap_net_bind_service=+eip' /usr/local/bin/caddy
sudo mkdir -p /etc/caddy
sudo chown -R root:www-data /etc/caddy
sudo mkdir -p /etc/ssl/caddy
sudo chown -R www-data:root /etc/ssl/caddy
sudo chmod 770 /etc/ssl/caddy
sudo touch /etc/caddy/Caddyfile
sudo mkdir -p /var/www
sudo chown www-data:www-data /var/www
sudo chmod 755 /var/www
curl -L https://github.com/mholt/caddy/raw/master/dist/init/linux-systemd/caddy.service | sudo sed "s/;CapabilityBoundingSet/CapabilityBoundingSet/" | sudo sed "s/;AmbientCapabilities/AmbientCapabilities/" | sudo sed "s/;NoNewPrivileges/NoNewPrivileges/" | sudo tee /etc/systemd/system/caddy.service
sudo chown root:root /etc/systemd/system/caddy.service
sudo chmod 744 /etc/systemd/system/caddy.service
sudo systemctl daemon-reload
sudo systemctl enable caddy.service

# If you need caddy to be up now:
# systemctl start caddy.service

# if you need QUIC protocol:
# 1. edit /etc/systemd/system/caddy.service, write " -quic" (without quotes) to the end of the line ExecStart
# 2. systemctl daemon-reload
# 3. systemctl restart caddy
```

## ref
<https://github.com/mholt/caddy/#install>
<https://www.digitalocean.com/community/tutorials/how-to-host-a-website-with-caddy-on-ubuntu-16-04>
