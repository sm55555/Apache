# 조치 사항

httpd-default.conf 파일 수정 필요 

1. Apache 서버의 설정 중 KeepAlive 를 off로 설정.
2. MaxKeepAliveRequest 와 KeepAliveTimeout 값 을 적절하게 조절.
