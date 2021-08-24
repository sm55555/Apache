웹서버의 DocumentRoot 경로 하단에 심볼릭 링크로 연결된 디렉토리가 있을 때,
해당 URL 경로에 접근 시 'HTTP 403 권한 없음' 오류가 발생 하는 경우가 있습니다.
apache의 error log를 살펴 보면 심볼릭 링크에 access가 불가능하다는 메세지가 발생 합니다.

[error] [client 111.111.111.111] Symbolic link not allowed or link target not accessible: /home/user/test

위와 같은 에러가 발생할 경우 다음 항목을 확인해 보아야 합니다.

### 1. httpd.conf 내 해당 Directory 설정에 FollowSymLinks 옵션이 들어가 있는지

<Directory "/home/user">
    Options FollowSymLinks  <----------
</Directory>

### 2. 심볼릭 링크 파일의 소유권 확인

심볼릭 링크 파일 자체의 소유권이 실제 디렉토리 및 파일과 다를 때 권한 문제가 발생할 수 있습니다.

이 경우, chown -h 명령으로 심볼릭 링크 파일의 소유권을 변경해 주어야 합니다.
