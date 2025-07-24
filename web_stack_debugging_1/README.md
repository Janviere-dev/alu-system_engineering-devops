# 0-nginx_likes_port_80

## 🧩 Task Overview

This script ensures that Nginx is correctly installed and configured to listen on port 80 across all active IPv4 interfaces. It's designed to debug and fix issues where Nginx might fail to serve traffic on port 80 in an Ubuntu-based container.

## ✅ Requirements

- Ubuntu container environment
- Nginx must be installed, running, and accessible via port 80
- Configuration must support IPv4 traffic properly

## ⚙️ Script Details

**File:** `0-nginx_likes_port_80`

```bash
#!/bin/bash
# Minimal Bash script to install and configure Nginx to listen on port 80

apt-get update -y
apt-get install -y nginx

cat > /etc/nginx/sites-enabled/default <<EOF
server {
    listen 80 default_server;
    listen [::]:80 default_server ipv6only=on;

    root /var/www/html;
    index index.html index.htm;

    server_name _;

    location / {
        try_files \$uri \$uri/ =404;
    }
}
EOF

systemctl restart nginx

