---
title: 如何在VPS上安装shadowsocks
tags: server
abbrlink: 59811
date: 2019-05-24 22:09:05
---

要求:
- ubuntu 16.04 or above
- Python 3

## 1. 安装Shadowsocks
```bash
sudo apt install python3-pip
pip3 install https://github.com/shadowsocks/shadowsocks/archive/master.zip
```
<!-- more -->
## 2. 配置shadowsocks
```bash
sudo mkdir /etc/shadowsocks
sudo nano /etc/shadowsocks/config.json
```

 复制粘贴
```json
{
    "server":"::",
    "server_port":8388,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"mypassword",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}
```

## 3. 系统设置
```bash
sudo nano /etc/systemd/system/shadowsocks-server.service
```
 复制粘贴
```
[Unit]
Description=Shadowsocks Server
After=network.target

[Service]
ExecStart=/usr/local/bin/ssserver -c /etc/shadowsocks/config.json
Restart=on-abort

[Install]
WantedBy=multi-user.target
```

开启shadowsocks并设置开机自启动
```bash
sudo systemctl start shadowsocks-server
sudo systemctl enable shadowsocks-server
```


参考:
[Ubuntu 16.04下Shadowsocks服务器端安装及优化 - Penguin](https://www.polarxiong.com/archives/Ubuntu-16-04%E4%B8%8BShadowsocks%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%AB%AF%E5%AE%89%E8%A3%85%E5%8F%8A%E4%BC%98%E5%8C%96.html)
