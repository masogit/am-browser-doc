# Appendix C - Asset Manager Browser sample deployment configuration and tuning for benchmark

#### Nginx Load Balancer (In front of Asset Manager Browser)

```
# AM Browser

# LB
upstream backend {

        least_conn;
         session_sticky cookie=connect.sid mode=prefix;

        server 16.16.16.1:8080 max_fails=3 fail_timeout=30s;
        server 16.16.16.2:8080 max_fails=3 fail_timeout=30s;
        server 16.16.16.3:8080 max_fails=3 fail_timeout=30s;
        server 16.16.16.4:8080 max_fails=3 fail_timeout=30s;

        check interval=3000 rise=2 fall=5 timeout=1000 type=http;
        check_keepalive_requests 100;
          check_http_send "HEAD /AMB HTTP/1.0\r\n\r\n";
        check_http_expect_alive http_2xx http_3xx;
}
server {
        listen       80;
        server_name  localhost;

        location / {
                session_sticky_hide_cookie upstream=backend;
                proxy_pass http://backend;
                root   html;
                index  index.html index.htm;

        }
        location /nginx_status {
          stub_status on;
          access_log   off;
          allow 1.1.1.1;
        }
        location /status {
            check_status;

            access_log   off;
            allow 1.1.1.1;
        }
      

        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
                root   html;
        }

}
```

#### Asset Manager Browser

Out of box configuration


#### Asset Manager Rest Server


Aamapi96.ini
```
 [Option]
/Advanced/CnxPoolMinSize=10
/Advanced/CnxPoolIdleSize=2048
/Advanced/CnxPoolMaxSize=2048
```

#### Nginx Load Balancer (In front of Asset Manager Rest Server)

```
# AM Rest Server

# LB
upstream backend {
        least_conn;
         session_sticky;
        server 16.16.16.1:10081 max_fails=3 fail_timeout=30s;
        server 16.16.16.2:10081 max_fails=3 fail_timeout=30s;
        server 16.16.16.3:10081 max_fails=3 fail_timeout=30s;
        server 16.16.16.4:10081 max_fails=3 fail_timeout=30s;
        server 16.16.16.1:10082 max_fails=3 fail_timeout=30s;
        server 16.16.16.2:10082 max_fails=3 fail_timeout=30s;
        server 16.16.16.3:10082 max_fails=3 fail_timeout=30s;
        server 16.16.16.4:10082 max_fails=3 fail_timeout=30s;
        check interval=3000 rise=2 fall=5 timeout=1000 type=http;
        check_keepalive_requests 100;
          check_http_send "HEAD / HTTP/1.0\r\n\r\n";
        check_http_expect_alive http_2xx http_3xx;
}
server {
        listen       80;
        server_name  localhost;



        location / {
                session_sticky_hide_cookie upstream=backend;
                proxy_pass http://backend;
                root   html;
                index  index.html index.htm;

        }
        location /nginx_status {
          stub_status on;
          access_log   off;
          allow 1.1.1.1;
        }
        location /status {
            check_status;

            access_log   off;
            allow 1.1.1.1;
        }
      

        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
                root   html;
        }

}
```


