### 암호걸려 있는 인증서 처리방법

1. 먼저 인증서에 비밀번호 걸려 있는지 확인 

httpd-ssl.conf 파일

```cmd
SSLPassPhraseDialog builtin -> 기동 시 비밀번호 입력해야함
SSLPassPhraseDialog exec:/edi/web/Apache2.2.31/conf/ssl_passwd.sh -> ssl_passwd.sh 파일 권한 확인
```

ssl_passwd.sh 내용(패스워드가 1234)인 경우

```cmd
#!/bin/sh

echo "1234"
```



