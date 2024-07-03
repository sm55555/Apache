1. vi /usr/local/apache/conf/httpd.conf 아파치 파일 수정 

```
<VirtualHost *:80>
  ServerNmae test.com:80
...
...
...
  CustomLog "|/usr/bin/logger -p local1.info -t httpd" combined
<VirtualHost>
```

2. rsyslog 클라이언트 설정

vi /etc/rsyslog.conf 파일 수정 
 
```
local1.*    /etc/httpd/logs/access.log
...
...
...
*.* @10.0.0.1:514           #=> 서버의 IP를 입력하고 UDP 포트를 입력한다.
```



