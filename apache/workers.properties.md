### workers.properties

workers는 back-end에 위치한 각 Tomcat 인스턴스들을 가리킨다. 이 workers.properties 파일은 Apache HTTP Server에서 연결하고자 하는 Tomcat에 대한 정의 및 설정 파일이다. 

----일반 설정값----

worker.template.type 연결 프로토콜 설정 ajp13 

worker.template.lbfactor 로드 밸러스 설정 1

worker.template.socket_timeout 소켓 타임아웃 설정 60

worker.template.socket_keepalive 소켓 keepalive 활성화 true

worker.template.recovery_options 복구 옵션 설정 7

worker.template.ping_mode ping 모드 설정 A 

worker.template.ping_timeout ping 타임아웃 설정 10000

worker.template.connection_pool_szie 최대 WAS 커넥션 수 설정 64 

worker.template.connection_pool_minsizee 최소 WAS 커넥션 수 설정 32 

worker.template.onnection_pool_timeout 커넥션 연결 종료 후 재사용 대기 시간 60

### WAS 1,2번기 분기

```shell
worker.list=wlb

# configuration template
worker.template.type=ajp13
worker.template.maintain=30
worker.template.lbfactor=1
worker.template.socket_timeout=60
#worker.template.reply_timeout=60000
worker.template.socket_keepalive=true
worker.template.recovery_options=7
worker.template.ping_mode=A
worker.template.ping_timeout=10000

worker.template.connection_pool_timeout=60

# configuration was1
worker.was1.reference=worker.template
worker.was1.host=10.xxx.xx.10
worker.was1.port=9009

#configuration was2
worker.was2.reference=worker.template
worker.was2.host=10.xxx.xx.11
worker.was2.port=9009

# configuration loadbalancer
worker.wlb.type=lb
worker.wlb.retries=2
worker.wlb.method=Session
worker.wlb.sticky_session=True
worker.wlb.balance_workers=was1,was2

worker.jkstatus.type=status
```
