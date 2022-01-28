# MPM (Mulit Proceesing Module)

MPM에는 prefork, worker, event 방식이 있으며 event가 가장 효율적이다. prefork는 쓰레드를 지원하지 않는 어플리케이션을 사용하는 경우 쓰는데 메모리를 많이 먹는다. worker는 중간.



## 사용 MPM 버전 확인


```
[root@]# /Apache2.2.31/bin/apachectl -V | grep -i mpm
Server MPM:     Prefork
 -D APACHE_MPM_DIR="server/mpm/prefork"
```

### conf/extra/httpd-mpm.conf 위치에 MPM 설정 값이 있다.

```
# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>
```

