# server status

- 아파치 웹서버를 사용시 관리자는 서버의 부하가 얼마나 걸리고 있는지 모니터링이 필요합니다. 리눅스 쉘 상태에서 확인이 가능하지만, 웹으로 할 수 있는 방법을 알려드립니다.

1. 별도의 설치 없이 httpd.conf 파일에 아래의 내용을 추가합니다.


```
<Location /server-status>
SetHandler server-status
order allow,deny
allow from all
allow from [.도메인주소]
</Location>
```

이 후 아파치 재시작

```
/usr/local/apache2/bin/apachectl restart
```

2. 웹페이지에서 정상적으로 상태가 나타나는지 확인
: 아래와 같은 형식으로 웹 브라우저에 입력하면 아래 그림과 같은 화면을 볼 수 있습니다.

	<img width="100%" height="100%" src="https://user-images.githubusercontent.com/38831314/102948558-8139c080-4509-11eb-8fc4-5ac4ceba7573.PNG">
