vi /usr/local/apache/conf/httpd.conf 아파치 파일 수정 

```
ServerNmae test.com:80
CustomLog "|/usr/bin/logger -p local1.notice -t apache" combined 
ErrorLog "|/usr/bin/logger -p local1.notice -t apache" 
```
