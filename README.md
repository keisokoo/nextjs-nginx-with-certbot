# next.js-nginx-docker-compose-with-letsencrypt

인증서 자동화를 포함한 next.js nginx 배포를 위한 docker-compose 설정

## domain 및 email 변경 필요

### init-letsencrypt.sh

example.org -> domain 변경  
example@example.com -> email 변경

### app.conf

example.org -> domain 변경

## deploy

docker설치
docker-compose설치
1 ~ 4번까지 실행
이후에는 2, 4번만 실행

1. 네트워크 생성, 이미 생성되어 있다면 생략 가능. 필요하지 않다면 docker-compose.prod.yml에서 network 설정 삭제

```
docker network create my_network
```

2. next.js 변경시 마다 빌드

```
docker-compose --build
```

3. 최초 실행시에만 실행. 이후에는 생략 가능.  
   루트가 아니라면 권한을 부여해야함  
   chmod +x init-letsencrypt.sh

```
./init-letsencrypt.sh
```

4. 실행

```
docker-compose up
```

## references from

https://github.com/wmnnd/nginx-certbot  
https://github.com/vercel/next.js/tree/canary/examples/with-docker-compose
