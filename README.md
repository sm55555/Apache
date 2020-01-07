# apache
enviroment : amazon linux 2

## 1. How to install apache web server (using yum)

~~~
sudo yum install httpd -y

sudo systemctl start httpd

sudo systemctl status httpd

sudo systemctl stop httpd
~~~

!!! you have to open 80 port using Security Group in AWS

* * *

### Main directory

~~~
content directory : cd /etc/html/www
~~~

* * *

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
mv apr-util-1.6.5 ./httpd-2.4.38/srclib/apr-util
~~~
if not downloaded, check version and URL at http://ftp.neowiz.com/apache/httpd

##### install pcre

~~~
cd /usr/local/src/pcre-8.41
./configure
make
make install
~~~

##### install apache

-> --prefix=/usr/local/apache2 means your apache homefolder

-> if configure: error: Cannot use an external APR-util with the bundled APR error occurred 

using ./configure --prefix=/usr/local/apache2 --with-included-apr

~~~
cd /usr/local/src/httpd-2.4.27
./configure --prefix=/usr/local/apache2
make
make install
~~~

##### start apache

~~~
cd /usr/local/apache2/bin
./httpd -k start
./httpd --k  (status check)
./httpd -k stop
./httpd -k restart
~~~


~~~linux
**[root@test pcre-8.33]#** cd /usr/local/src/httpd-2.4.20
**[root@test httpd-2.4.20]#** ./configure --prefix=/usr/local/apache2
... (생략)
config.status: creating build/config_vars.sh
config.status: creating include/ap_config_auto.h
config.status: executing default commands
~~~




