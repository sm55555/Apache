# HTTP to HTTPS Redirect

![image](https://user-images.githubusercontent.com/38831314/138405083-07d99855-4617-4f0b-93f4-66511dc422a0.png)

#### 1. server

코드가 작성되는 블록의 이름

#### 2. listen 80 default_server;

포트 번호는 80 http 포트이고 default_server는 서버 호스트네임
IPv4 HTTP 동작

#### 3. listen [::]:80 default_server;

IPv6 HTTP 동작

#### 4. SSL Redirect 설정

```
return 301 https://$host$request_uri;
```

예제 

test.com, www.test.com의 모든 HTTP 트래픽은 HTTPS로 리다이렉션 된다.

![image](https://user-images.githubusercontent.com/38831314/138405346-9308e612-b00e-4069-b23e-9ecb1e6fff3e.png)
