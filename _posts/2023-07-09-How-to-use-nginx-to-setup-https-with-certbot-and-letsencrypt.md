---
title: How to use nginx to setup https with certbot and let's encrypt
categories: ["nginx"]
---

# Install nginx

```sh
sudo apt update
sudo apt upgrade -y
sudo apt install nginx -y
```

press 'Enter' if it prompts to restart some program.

# Install certbot

I'm in Ubuntu 20.04, so I use snap to install certbot.

[certbot official instuctions](https://certbot.eff.org/instructions?ws=nginx&os=ubuntufocal)

```sh
sudo snap install core; sudo snap refresh core
sudo snap install --classic certbot
```

# Run certbot

```sh
sudo certbot --nginx
```

follow the instructions it prompts you.

If you only enter one domain, and not add server block for it, it will create two new server blocks in your `/etc/nginx/sites-available/default` file, one for port 80, one for port 443.

I will move these two server blocks to `/etc/nginx/sites-available/yourdomain.com` and configure it.
