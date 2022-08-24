---
layout: post
read_time: true
show_date: true
title: 일해라 .gitignore
date: 2022-08-24 12:29:12 -0600
description: Gitignore, go to work. 
img: posts/cover/git.webp
tags: [git]
author: Kyungseon Park
github: kyungseonpark/MLops-BentoML
toc: yes
---



Docker-compose up을 하고 볼륨을 잡고.

근데 볼륨은 github으로 올라가면 안된다.

```python
.volumes/
volumes/
```

![image-20220824223509804](../assets/img/posts/2022-08-24-go-to-work-gitignore/image-20220824223509804.png)

?

```shell
git add .
git commit -m "fix: blah blah"
```

해야되는데?

git cache를 날려버리자.

```shell
git rm -r -f --cached
git add .
git commit -m "fix: blah blah"
```

![편안 짤과 움짤 모음 - 짤봇](../assets/img/posts/2022-08-24-go-to-work-gitignore/Vgvs95YpK-1348249.jpeg)