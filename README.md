# apache
enviroment : amazon linux 2

### 1. How to install apache web server (using yum)

~~~
sudo yum install httpd -y

sudo systemctl start httpd

sudo systemctl status httpd

sudo systemctl stop httpd
~~~

!!! you have to open 80 port using Security Group in AWS

* * *

### 2. Main directory

~~~
content directory : cd /etc/html/www
~~~

* * *

### 1. How to install apache web server (not using yum)

you need make, complier to install apache

~~~
yum -y install gcc gcc-c++

1. install Lasted Version
cd /usr/local/src
wget http://ftp.neowiz.com/apache/httpd/httpd-2.4.38.tar.bz2
wget http://ftp.neowiz.com/apache/apr/apr-1.6.5.tar.bz2
wget http://ftp.neowiz.com/apache/apr/apr-util-1.6.1.tar.bz2
wget http://downloads.sourceforge.net/project/pcre/pcre/8.41/pcre-8.41.tar.bz2
~~~
if not downloaded, check version and URL at http://ftp.neowiz.com/apache/httpd


