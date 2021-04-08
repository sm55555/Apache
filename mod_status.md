# Server status

- 아파치 웹서버를 사용시 관리자는 서버의 부하가 얼마나 걸리고 있는지 모니터링이 필요합니다. 리눅스 쉘 상태에서 확인이 가능하지만, 웹으로 할 수 있는 방법입니다.

1. cd /usr/local/apache2/conf/httpd.conf

LoadModule status_module modules/mod_status.so 주석 제거

2. 별도의 설치 없이 httpd.conf 파일에 아래의 내용을 추가합니다.


```
<Location /server-status>
SetHandler server-status
order allow,deny
allow from all
allow from [.도메인주소]
</Location>
```

아파치 재시작

```
/usr/local/apache2/bin/apachectl restart
```

3. 웹페이지에서 정상적으로 상태가 나타나는지 확인
: 아래와 같은 형식으로 웹 브라우저에 입력하면 아래 그림과 같은 화면을 볼 수 있습니다.

<img width="70%" height="70%" src="https://user-images.githubusercontent.com/38831314/102948558-8139c080-4509-11eb-8fc4-5ac4ceba7573.PNG">

위의 내용을 주기적으로 갱신하려면 웹 브라우저에 아래와 같은 형식으로 입력하면 됩니다.
(단위는 “초” 입니다.)

http://도메인/server-status?refresh=5

추가적으로 위의 내용에 대한 설명은 아래와 같습니다.
 - Server Version : 아파치서버의 버전을 나타냄
 - Server Built : 아파치서버가 설치된 년, 월, 일, 시
 - Current Time : 현재 모니터링하는 년, 월, 일, 요일, 시간
 - Restart Time : 아파치서버가 재동작한 년, 월, 일, 요일, 시간
 - Parent Server Generation : 서버 부하방지을 위한 아파치서버 생성갯수 총서버 개수중 요구에 응하고 있는 서버의 개수와 놀고 있는 서버의 개수 Scoreboard Key 에 대한 정보
  - "-" : 응답을 하기 위해 대기중임을 나타냄
 - "S" : 시작되고 있음을 나타냄
 - "R" : 응답을 위해 요구사항을 해석하고 있음
 - "L" : 요구에 대한 응답을 하고 있음
 - "K" : 계속 연결 중
 - "D" : DNS서버에 요구도메인 검색 중
 - PID key : 프로세스정보를 보여줌
