### SSLHandshakeException

```
com.sun.jersey.api.client.ClientHandlerException: javax.net.ssl.SSLHandshakeException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target
```

위 이슈 발생 시

https://www.digicert.com/kb/ssl-support/pem-ssl-creation.htm

현재 테스트 서버 순서대로

최신 cert.pem 파일
최신 GEO-Chain.pem 파일
ROOT CA(?)로 추정됨.

![image](https://user-images.githubusercontent.com/38831314/134835692-53281b4c-5cd6-4a70-af8e-80359681a900.png)

Step 1) Certificate download

- 구매하신 인증서에 맞는 inermediate, Root CA 다운로드

Step 2) 하나의 파일로 만들기 : 이름은 테스트 서버 -> ssl-bundle.crt.pem

Step 3)  Web server에 bundle certificate 지정 -> conf에서 ssl_certificate,,, ssl-bundle.crt.pem 찾기 ..

Step 4) Web server 재시작
