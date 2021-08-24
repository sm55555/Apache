### Apache와 Tomcat 설치

* Apache

```
$ wget http://apache.tt.co.kr//httpd/httpd-2.4.39.tar.gz
$ tar -zxvf httpd-2.4.39.tar.gz
$ ./configure --prefix=/home/~~~/apache
$ make && make install
$ cd /home/~~~/apache/bin
$ sudo chown root:계정명 httpd
$ sudo chmod +s httpd
$ vi /home/~~~/apache/conf/httpd.conf
User 계정명
Grop 계정명
$ /home/~~~/apache/bin/apachectl start ← 실행
```
서버 ip 확인

* Tomcat

```
$ wget http://mirror.apache-kr.org/tomcat/tomcat-8/v8.5.43/bin/apache-tomcat-8.5.43.tar.gz
$ tar -zxvf apache-tomcat-8.5.43.tar.gz
$ /home/apache-tomcat-8.5.43/bin/start.sh ← 실행
```

Tomcat의 기본 http 포트인 8080으로 접속 확인

### Apache와 Tomcat 연동하기

(여기선 mod_jk 방식과 mod_proxy 방식 중 mod_jk로 한다.)

* mod_jk 설치 

```
$ wget http://apache.tt.co.kr/tomcat/tomcat-connectors/jk/tomcat-connectors-1.2.46-src.tar.gz
$ tar -zxvf tomcat-connectors-1.2.46-src.tar.gz
$ cd tomcat-connectors-1.2.46-src/native
$ ./configure --with-apxs=/home/~~~/apache/bin/apxs
$ make && make install
$ /home/~~~/apache/modules 하위에 mod_jk.so가 생김
```

mod_jk 를 활용하면 AJP라는 통신으로 아파치와 Tomcat이 연동되는데 Tomcat의 기본 AJP 포트는 8009번임을 알고 다음처럼 설정

* apache/conf/workers.properties

```
worker.list=tomcat1
worker.tomcat1.port=8009
worker.tomcat1.host=localhost
worker.tomcat1.type=ajp13
worker.tomcat1.lbfactor=1
```

* apache/conf/httpd.conf

```
LoadModule jk_module modules/mod_jk.so
<IfModule jk_module>
    JkWorkersFile    conf/workers.properties
    JkLogFile        logs/mod_jk.log
    JkLogLevel       info
    JkMount /* 	tomcat1
</IfModule>
```

이렇게 하고서 Apache와 Tomcat을 재시작 후에 서버의 ip로 접속해보면 (별도의 port 없이) Tomcat 설정 페이지로 랜딩
