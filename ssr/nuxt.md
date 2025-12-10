## Nuxt SSR Framework

## 最佳实践

### 1、接口请求优化

前提：Nuxt应用需要和后端服务在用一台机子或局域网中

SSR分为服务器渲染和客户端两种，那么在服务端时可直接通过本地127.0.0.1或局域网ip进行访问，防止https等其他网络开销

## 部署

### Nginx 配置

```nginx
server {
    listen 80;
    listen 443 ssl ;
    http2 on;
    server_name preview-SP-C;

    # ----------- SSL 配置 -----------
    ssl_certificate /www/server/panel/vhost/cert/preview-SP-C/fullchain.pem;
    ssl_certificate_key /www/server/panel/vhost/cert/preview-SP-C/privkey.pem;

    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers on;

    # HSTS（可选，不要删，只在确认 HTTPS 正常后开启）
    add_header Strict-Transport-Security "max-age=31536000" always;

    # ----------- 长连接优化 -----------
    keepalive_timeout 70;
    keepalive_requests 1000;

    # ----------- 强制 HTTPS -----------
    if ($scheme = http) {
        return 301 https://$host$request_uri;
    }

    # ----------- Nuxt 前端项目 4002 -----------
    location / {
        proxy_pass http://127.0.0.1:4002;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection $connection_upgrade;

        proxy_connect_timeout 30s;
        proxy_read_timeout 60s;
        proxy_send_timeout 30s;
    }
    location ~ ^/api/_nuxt_icon {
        proxy_pass http://127.0.0.1:4002;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header Origin $http_origin;        
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
    # ----------- 接口服务 8095 -----------
    location /api/ {
        proxy_pass http://127.0.0.1:8095;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        proxy_connect_timeout 30s;
        proxy_read_timeout 60s;
        proxy_send_timeout 30s;
    }

    # ----------- 日志 ----------
    access_log /www/wwwlogs/preview-SP-C.log;
    error_log  /www/wwwlogs/preview-SP-C.error.log;
}
```