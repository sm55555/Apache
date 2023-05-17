

모든 트래픽을 S3 버킷으로 proxy_pass에 넣는다. IAM Role 필요, Bucket 컨텐츠만 볼 수 있다.
Html이 Bucket에 있어도 거기 내부에 있는 s3 콘텐츠는 못읽는다 생각해봐..

이렇게 되면

https://192.168.0.1/test.jpg라고 브라우저가 하면 -> 서버는 proxy로 넘겨서 s3콘텐츠를 볼 수 있다.


```nginx
location / {
  proxy_pass https://test.s3.ap-northeast-2.amazonaws.com
}
```
