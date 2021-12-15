### wsadmin 명령어

ci -s    (지금 접속한 사용자)
```
       Clients  Unique IPs  Dropped
       -------  ----------  -------
HTH 0        2           1        0
  All        2           1        0
```

사용자에 따라서 아래 옵션이 넉넉해야한다.
max user processes
open files                      (-n) 1048576

```
webtob5@tmax-6cb761eb:/home/webtob5/webtob/config>ulimit -a
core file size          (blocks, -c) unlimited
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 385571
max locked memory       (kbytes, -l) 16384
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1048576
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 4096
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```
  
