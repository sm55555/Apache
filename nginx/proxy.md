### 구조 

<img width="482" alt="image" src="https://github.com/sm55555/WEB/assets/38831314/b7af3752-335e-404a-9a85-fe9ce9e85f69">

예를들어서 Private에 있는 172.20.1.1 서버가 curl -v 127.50.1.1:3200을 통해서 바깥 도메인인 naver.com 을 호출 할 수 있는 구조이다.
Public Subnet에 있는 127.50.1.1은 필요한 외부와 통신이 가능하다.

nginx.conf + Disable DNS Caching

```
  server{
    listen 3200
    server_name _;

    resolver 127.20.1.2 valid=5s; <- 해당 Ec2의 DNS 주소
    set $domain "https://naver.com"
    access_log /var/log/nginx/....

    location/ {
      proxy_pass $domain;
      proxy_set_header Upgrade $http_upgrade;
      proxy_set_header Connection "upgrade";
    }
  }
```

