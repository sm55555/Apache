### 1 yum 저장소에는 nginx 라이브러리가 없기 때문에 저장소를 추가

```
sudo vi /etc/yum.repos.d/nginx.repo
```

### 2 /etc/yum.repos.d 경로에 nginx.repo 파일을 추가하고 아래와 같이 작성

```
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=0
enabled=1
```

### 3 yum 설치

```
yum install -y nginx
```
