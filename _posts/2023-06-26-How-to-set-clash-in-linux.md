---
title: How to setup clash in linux
categories: ["howto"]
tags: ["linux"]
---

# Setup clash

## Download clash

- [github clash](https://github.com/Dreamacro/clash/releases)

```sh
wget -O clash.gz https://github.com/Dreamacro/clash/releases/download/v1.16.0/clash-linux-amd64-v1.16.0.gz
```

## Unzip clash

```sh
gzip -f clash.gz -d
```

## make it executable

```sh
chmod +x clash
```

## init clash

```sh
./clash
```

it will generate a config file named `config.yaml` in `~/.config/clash/` directory

## close clash

Press `Ctrl + C` to close clash

## modify config file

```sh
wget -U "Mozilla/6.0" -O ~/.config/clash/config.yaml  你的Clash订阅链接网址
```

## start clash

```sh
./clash
```

## set proxy

open a new terminal

```sh
export http_proxy=http://127.0.0.1:7890
export https_proxy=http://127.0.0.1:7890
```

## verify proxy in use

make a get request before and after set proxy

```sh
curl https://httpbin.org/ip
```

# References

- [tutorial in Chinese](https://fanqiang.gitbook.io/fanqiang/linux)
