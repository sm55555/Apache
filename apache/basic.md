# apache
enviroment : amazon linux 2 (centOS)

## 1. How to install apache web server (using yum)

~~~
sudo yum install httpd -y

sudo systemctl start httpd

sudo systemctl status httpd

sudo systemctl stop httpd
~~~

you have to open 80 port using Security Group in AWS

```
you can use this command
systemctl status httpd
service httpd status	
httpd --k
httpd -k start
httpd -k graceful : 기존 접속은 두고 접속된 커넥션은 두고 설정파일 호출 후 재실행
apachectl configtest : Apache conf 검증
```

### Main directory

~~~
content directory : cd /etc/html/www
~~~


## 2. How to install apache web server (not using yum)

you need make, complier to install apache

##### install Lasted Version
~~~
yum -y install gcc gcc-c++ (yum list | grep gcc)

cd /usr/local/src
wget http://ftp.neowiz.com/apache/httpd/httpd-2.4.38.tar.bz2
wget http://ftp.neowiz.com/apache/apr/apr-1.6.5.tar.bz2
wget http://ftp.neowiz.com/apache/apr/apr-util-1.6.1.tar.bz2
wget http://downloads.sourceforge.net/project/pcre/pcre/8.41/pcre-8.41.tar.bz2

tar xvf apr-1.6.5.tar.bz2
tar xvf apr-util-1.6.1.tar.bz2
tar xvf httpd-2.4.38.tar.bz2
tar xvf pcre-8.41.tar.bz2
mv apr-1.6.5 ./httpd-2.4.38/srclib/apr
mv apr-util-1.6.1 ./httpd-2.4.38/srclib/apr-util
~~~
if not downloaded, check version and URL at http://ftp.neowiz.com/apache/httpd

##### install pcre

~~~
cd /usr/local/src/pcre-8.41
./configure
make
make install
~~~

~~~
[root@web01 ~]# cd /usr/local/src/pcre-8.33
[root@web01 pcre-8.33]# ./configure
... (생략)
    Link pcretest with libreadline .. : no
    Valgrind support ................ : no
    Code coverage ................... : no
~~~

~~~
[root@web01 pcre-8.33]# make
... (생략)
  CXX      pcre_stringpiece_unittest-pcre_stringpiece_unittest.o
  CXXLD    pcre_stringpiece_unittest
make[1]: Leaving directory `/usr/local/src/pcre-8.33'
~~~

~~~
[root@web01 pcre-8.33]# make install
make[3]: Leaving directory `/usr/local/src/pcre-8.33'
make[2]: Leaving directory `/usr/local/src/pcre-8.33'
make[1]: Leaving directory `/usr/local/src/pcre-8.33'
~~~

##### install apache

-> --prefix=/usr/local/apache2 means your apache homefolder

~~~
cd /usr/local/src/httpd-2.4.38
./configure --prefix=/usr/local/apache2 --with-included-apr
make
make install
~~~

~~~
[root@web01 pcre-8.33]# cd /usr/local/src/httpd-2.4.20
[root@web01 httpd-2.4.20]# ./configure --prefix=/usr/local/apache2 --with-included-apr
... (생략)
config.status: creating build/config_vars.sh
config.status: creating include/ap_config_auto.h
config.status: executing default commands
~~~

-> if the error "configure: error: Cannot use an external APR-util with the bundled APR error occurred" appears 

* ./configure --prefix=/usr/local/apache2 --with-included-apr

-> if the error "configure: error: pcre-config for libpcre not found. PCRE is required and available from" appears 

* yum install pcre-devel


~~~
[root@web01 httpd-2.4.20]# make
... (생략)
make[2]: Leaving directory `/usr/local/src/httpd-2.4.20/support'

make[1]: Leaving directory `/usr/local/src/httpd-2.4.20'
~~~

-> if the error "xml/apr_xml.c:35:10: fatal error: expat.h: No such file or directory #include <expat.h>..." appears

* yum install expat-devel

* make clean (compile initialize)

* make

-> if the error "collect2: error: ld returned 1 exit status" appears

* ./configure --prefix=/usr/local/apache2 --with-included-apr

* make clean (compile initialize)

* make

~~~
[root@web01 httpd-2.4.20]# make install
... (생략)
mkdir /usr/local/apache2/man/man8
mkdir /usr/local/apache2/manual
make[1]: Leaving directory `/usr/local/src/httpd-2.4.20'
~~~

##### start apache

~~~
cd /usr/local/apache2/bin
./httpd -k start
./httpd --k  (status check)
./httpd -k stop
./httpd -k restart
~~~

~~~
[root@web ~]# /usr/local/apache2/bin/httpd -k start
[root@web ~]# ps -ef | grep httpd | grep -v grep
root     35683     1  0 17:09 ?        00:00:00 /usr/local/apache2/bin/httpd -k start
daemon   35684 35683  0 17:09 ?        00:00:00 /usr/local/apache2/bin/httpd -k start
daemon   35685 35683  0 17:09 ?        00:00:00 /usr/local/apache2/bin/httpd -k start
daemon   35686 35683  0 17:09 ?        00:00:00 /usr/local/apache2/bin/httpd -k start
~~~

~~~
[root@web ~]# netstat -anp | grep httpd
tcp        0      0 :::80                       :::*                        LISTEN      35683/httpd
~~~

~~~
[root@web01 ~]# curl http://127.0.0.1
<html><body><h1>It works!</h1></body></html>
~~~

## 3. Web Source 

httpd.conf

```
DocumentRoot "/data/was/apps/resources"
```

## 4.The number of people who use apache 

check port !

```
netstat -nap | grep :80 | grep ESTABLISHED | wc -l
```
