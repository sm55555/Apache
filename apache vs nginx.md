# apache vs nginx

apache가 검색량이 및 자료도 더 많다고 한다.(2021년 12월 20일 기준)

![image](https://user-images.githubusercontent.com/38831314/146679655-2c1ba44a-f765-41a6-918d-5f663bce081c.png)


## apache

Apache는 Client 요청을 받으면 MPM(Multi Processing Module : 다중처리모듈)이라는 방식으로 요청을 처리하며 대표적으로 Prefork와 Work방식이 있다.

### Prefork MPM

![image](https://user-images.githubusercontent.com/38831314/146679126-a0fd032a-05cd-48e8-9f01-340cf13fe4da.png)

실행중인 프로세스를 복제되어 처리가 된다. 각 프로세스는 한번에 한 연결만 처리하고 요청량이 많아질수록 프로세스는 증가하지만 복제시 메모리영역까지 복제되어 동작하므로 프로세스간 메모리 공유가 없어 안정적이라 볼수 있다.

-> 커넥션 수가 곧 프로세스 수 성능이 필요한 PHP에 사용된다.

### Worker MPM

![image](https://user-images.githubusercontent.com/38831314/146679183-2f314867-1f01-402b-8b33-01b993f5267a.png)

Prefork 동작방식이 1개의 프로세스가 1개의 스레드로 처리가 되었다면 Worker 동작방식은 1개의 프로세스가 각각 여러 쓰레드를 사용하게 된다. 쓰레드간의 메모리를 공유하며 PreFork방식보다 메모리를 덜 사용하는 장점이 있다.

![image](https://user-images.githubusercontent.com/38831314/146679278-8b717705-6f14-4c2a-9f0c-5b847f3b8c40.png)

### apache의 한계

클라이언트 접속마다 Process 혹은 Thread 를 생성하는 구조이며 1만 클라이언트로부터 동시접속 요청이 들어온다면 CPU 와 메모리 사용이 증가하고 추가적인 Process/Tread 생성비용이 드는 등 대용량 요청(대략 1만정도)에서 한계를 보임


### MPM 확인 방법

httpd -V" 또는 "httpd -l" 명령어로 확인

![image](https://user-images.githubusercontent.com/38831314/146679759-0be44bb8-034b-4295-b8ab-30a6dcdf2d9d.png)


## nginx

Nginx 는 Event-Driven 방식으로 동작한다. 한 개 또는 고정된 프로세스만 생성 하고, 그 프로세스 내부에서 비동기 방식으로 효율적으로 작업을 처리한다. 따라서 동시 접속 요청이 많아도 Process 또는 Thread 생성 비용이 존재하지 않는다.
Event-Driven(비동기로 효율적인 방식으로 task를 처리)

![image](https://user-images.githubusercontent.com/38831314/146679439-f7d6c441-c095-4dfa-b726-fdc10aa5fa5c.png)





