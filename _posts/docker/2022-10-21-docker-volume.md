---
layout: post
read_time: true
show_date: true
title: Docker Volume ์ข๋ฅ
date: 2022-08-10 01:29:12 -0600
description: kinds of docker-volume
img: posts/cover/docker.webp
tags: [docker]
author: Kyungseon Park
github: kyungseonpark/MLops-feast
toc: yes
---

๐<a href="https://stackoverflow.com/questions/46166304/docker-compose-volumes-without-colon">Docker Volume ์ข๋ฅ</a>

# Host Volumes

- Ex) ./host/path:/container/path
- Host์ ์กด์ฌํ๋ ์ด๋ค ๊ฒฝ๋ก๋  ์ปจํ์ด๋์ ๋ณผ๋ฅจ ๋ฐ์ธ๋ฉ์ ํ  ์ ์์ต๋๋ค.
- uid/gid์ ์ฃผ์ ํด์ผ ํฉ๋๋ค.
  - host์์ ๋จผ์  ์์ฑํ๋ ๊ฒ์ ๊ถ์ฅํฉ๋๋ค.
  - uid/gid๋ฅผ ๋ฐ๋ก ์ค์ ํ์ง ์์ผ๋ฉด Container๋ root๋ก Directory๋ฅผ ์์ฑํ๊ฒ ๋๋ฏ๋ก ๋ณผ๋ฅจ ์ญ์ ์ ์ ๋ฅผ ๋จน์ ์ ์์ด์.

# Named Volumes

- Ex) created_name:/container/path
- ์์ฑ ํ์ผ์์ ์ต์์ 

# Anonymous Volumes

# tmpfs

