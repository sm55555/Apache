# apache rotatelogs 설정 방법


월별 로그파일 생성 스크립트

```
#!/bin/bash


TDATE1=`date +%Y%m --date '1 months ago'`
TDATE2=`date +%Y-%m --date '1 months ago'`

cd $1
pwd
mkdir $TDATE1
mv *$TDATE1* $TDATE1
mv *$TDATE2* $TDATE1

```


아파치가 설치 되면서 자동으로 rotatelogs 깔림

```
[root@linux-1 ~]# which rotatelogs
/usr/sbin/rotatelogs
```

apache rotatelogs 설정

```
# /etc/httpd/conf.d/vhost.conf
<VirtualHost *:80>
        ServerName a.tistory.com
        DocumentRoot /home/www/doc_1
        ErrorLog "|/usr/sbin/rotatelogs /var/log/httpd/a.tistory-error_log.%y%m%d_%H 3600 +540"
        CustomLog "|/usr/sbin/rotatelogs /var/log/httpd/a.tistory-access_log.%y%m%d_%H 3600 +540" combined
</VirtualHost>
```

완료
