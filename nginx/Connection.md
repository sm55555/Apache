## Connection 관련 이슈

```
Nginx Error: upstream prematurely closed connection while reading response header from upstream
```

기본은 timeout 120s

```
server {
    listen 8080;

    # Increase proxy timeout
    # ------------------------
    proxy_read_timeout 300;
    proxy_connect_timeout 300;
    proxy_send_timeout 300;
    # ------------------------
... 생략
```

Access 로그에서도 기존 성공 응답시간을 확인해야한다 !
