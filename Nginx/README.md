# Nginx

### Api反向代理转发server
```config
    server {
        listen      80;
        server_name a.xx.com;

        access_log   /var/log/nginx/a_access.log main;
        error_log    /var/log/nginx/a_error.log;

        proxy_temp_path       /var/nginx/proxy_temp/ 1 2;
        fastcgi_temp_path     /var/nginx/fastcgi_temp/ 1 2;

        gzip                       on;
        gzip_vary                  on;
        gzip_proxied               any;
        gzip_min_length            1k;
        gzip_comp_level            3;
        gzip_types text/plain application/json application/x-javascript application/javascript text/css;

        location /api/v1/ {
            proxy_set_header Host $Host;
            proxy_pass_request_headers on;
            proxy_set_header X-Forwarded-Host $Host;
            proxy_set_header X-Forwarded-Proto $scheme;
            proxy_set_header X-Real-IP         $remote_addr;
            proxy_http_version 1.1;
            proxy_set_header Connection "";
            proxy_pass http://open_api_v1/;
        }
    }
```

### 转发适配规则
#### 带前缀转发
```config
location /api/v1/ {
            proxy_pass http://open_api_v1;
}
```
#### 不带前缀转发
与带前缀转发写法区别仅仅是一个`/`
```config
location /api/v1/ {
            proxy_pass http://open_api_v1/;
}
```

