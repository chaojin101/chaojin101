---
title: How to set a simple reverse proxy with nginx
categories: ["nginx"]
---

# Add a new server block

```sh
sudo vim /etc/nginx/sites-enabled/yourdomain.com
```

# Add the following content

```sh
server {
    listen 80;
    listen [::]:80
    server_name yourdomain.com; # or _ if you want to listen to all domains
    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header X-Real-IP $remote_addr;
		proxy_set_header Host $http_host;
    }
}
```
