---
layout: post
read_time: true
show_date: true
title: Docker Volume 종류
date: 2022-08-10 01:29:12 -0600
description: kinds of docker-volume
img: posts/cover/docker.webp
tags: [docker]
author: Kyungseon Park
github: kyungseonpark/MLops-feast
toc: yes
---

🔗<a href="https://stackoverflow.com/questions/46166304/docker-compose-volumes-without-colon">Docker Volume 종류</a>

# Host Volumes

- Ex) ./host/path:/container/path
- Host에 존재하는 어떤 경로든 컨테이너에 볼륨 바인딩을 할 수 있습니다.
- uid/gid에 주의 해야 합니다.
  - host에서 먼저 생성하는 것을 권장합니다.
  - uid/gid를 따로 설정하지 않으면 Container는 root로 Directory를 생성하게 되므로 볼륨 삭제에 애를 먹을 수 있어요.

# Named Volumes

- Ex) created_name:/container/path
- 작성 파일에서 최상위 

# Anonymous Volumes

# tmpfs

