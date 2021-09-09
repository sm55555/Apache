## 암호걸려 있는 인증서 처리방법

1. 먼저 인증서에 비밀번호 걸려 있는지 확인 

### httpd-ssl.conf 파일

```cmd

<VirtualHost *:[SSL 적용 포트 (ex : 443)]>
    DocumentRoot [http 설정과 동일한 디렉토리]
    ServerName [해당 서버의 도메인 (ex : guide.kicassl.com)]
    ServerAdmin [서버 관리자 정보 (ex : webmaster @ kicassl.com)]
    ErrorLog [에러로그를 저장할 경로]/ssl_error_log
    TransferLog [에러로그를 저장할 경로]/ssl_access_log
    ......
    SSLEngine On 
    #설명 : 발급받은 인증서 경로와 파일명을 지정합니다.
    SSLCertificateFile “경로/인증서파일” [ex : 도메인명_cert.pem]
    ......
    SSLCertificateKeyFile “경로/개인키파일” [ex : 도메인명_key.pem]
    ......
    SSLCertificateChainFile “경로/Chain_RootCA_Bundle.crt”
    ......
</VirtualHost>

```

```cmd
SSLPassPhraseDialog builtin -> 기동 시 비밀번호 입력해야함
SSLPassPhraseDialog exec:/web/Apache2.2.31/conf/ssl_passwd.sh -> ssl_passwd.sh로 실행 파일 권한 확인
```
### ssl_passwd.sh (파일 권한 700) 내용(패스워드가 1234)인 경우

```cmd
#!/bin/sh

echo "1234"
```



