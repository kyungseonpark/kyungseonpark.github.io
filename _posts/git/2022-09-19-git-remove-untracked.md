---
layout: post
read_time: true
show_date: true
title: git, remove untracked files
date: 2022-08-23 12:29:12 -0600
description: git, remove untracked files
img: posts/cover/git.webp
tags: [git]
author: Kyungseon Park
github: kyungseonpark
toc: yes
---

```she
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        __init__.py
```

```shell
git clean -f
```

git에서 untrackef files을 지우는 방법.

git pull하려는데 안되서 찾아본 내용.
