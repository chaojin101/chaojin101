---
title: How to set clash in linux
categories: ["howto"]
tags: ["linux"]
---

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
