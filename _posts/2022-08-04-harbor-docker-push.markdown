---
layout: post
read_time: true
show_date: true
title: Harbor(Cloud, Server)에 Docker Push(Upload)
date: 2022-08-03 01:29:12 -0600
description: harbor, docker image push
img: posts/cover/docker.webp
tags: [docker]
author: Kyungseon Park
github: kyungseonpark
toc: yes
---

# 1. docker file로 Custom Image 생성

```dockerfile
# Dockerfile-feast
FROM python:3.10
RUN pip install --upgrade pip
RUN pip install 'feast[redis]'
```

docker run 해도 되는데 다른거(환경변수 포트 등등...)설정하기 귀찮으니까 compose로 실행하면서 docker file이 잘 돌아가는지 확인한다.

```yaml
version: "2.4"
services:
  feast_local:
    build:
      context: .
      dockerfile: Dockerfile-feast
    environment:
      TZ: "Asia/Seoul"
    restart: always
    ports:
      - "6566:7000"
    tty: true
```



# 2. docker image tagging

Docker image를 태깅(tagging)해서 이미지 이름을 재정의해준다.

```shell
docker tag ${local_image_name} ${harbor_address}/${harbor_project}/${harbor_image_name}:${tag}

# example
docker tag feast_test_feast:latest harbor.add/harbor_pro/feast:latest
```



# 3. docker image push

```shell
docker push ${harbor_address}/${harbor_project}/${harbor_image_name}:${tag}

#example
docker push harbor.add/harbor_pro/feast:latest
```

이제 밀어넣으면 된다. 당연히 클라우드 접근권한도 있어야겠죠?

docker login이 먼저.