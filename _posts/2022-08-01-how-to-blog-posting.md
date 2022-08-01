---
layout: post
read_time: true
show_date: true
title: GitBlog 포스팅하는 방법
date: 2022-08-01 21:29:00 -0600
description: "post git-Blog"
tags: [gitblog, post]
author: Kyungseon Park
toc: yes
---

# 앞으로 블로그를 시작하기 위한 글.

 나는 Notion으로 블로그를 관리해보려고했다. oopy를 이용하면 호스팅도 굉장히 편했고 Notion의 강력한 임베딩 기능들은 굉장히 매력적이었다. 하지만 oopy구독비용+개인Host DNS비용까지 합하면 한달에 1만원을 사용하기에는 그만한 가치가 있나 생각하게되었다...

<img alt="흠터레스팅 짤 모음.jpg.gif : 클리앙" height="50%" src="../assets/img/posts/2022-08-01-how-to-blog-posting/d7798c12900cb.gif" width="50%"/>

 자기개발 비용이라고 생각할 수 있지만....닭강정 하나 사먹는게 더 좋아서 gitblog를 시작하게되었다. 근데 markdown으로 하려니 너무 어려워 정리해놓고 틈틈히 컨닝하면서 작성하기 위해 작성하는 글이다.

## 포스팅정보 정리(YAML)

```yaml
layout: post # 고정하면 됨. post layout을 사용하기 위함인듯.
read_time: true # 읽는시간, 몇분걸리나? 단어수로 추정하여 자동 계산.
show_date: true # 작성일자 보여줄거니?
title: GitBlog 포스팅하는 방법 # 포스팅 제목
date: 2022-08-01 21:29:00 -0600 # 포스팅의 작성 시간 뻥쳐도 모를듯.
img: posts/cover/typing_man.png # 커버이미지, 노션에서 이것도 너무 좋았는데 글쓰는데 고민할거리가 늘었다.
tags: [gitblog, post] # 카테고리 태그
Author: kyungseon park # 작성자(내이름)
gitHub: kyungseonpark # 깃헙 옵션 프로젝트관련글일때 레포 연결
toc: yes # Table of Contents
```

## 이미지 삽입

 Typora를 통해 작성할것같다. 이미지 저장폴더만 잘 지정해놓으면 알아서 잡힌다. 너무 편하다.

![신난다 > 짤투데이](../assets/img/posts/2022-08-01-how-to-blog-posting/1028612757_QXZ7yAY3_4da70b8eb1aaf0fe157b0fa73f607f4f8281da36.gif)

 블로그 꾸미느라 시간가는줄 몰랐다. 나의 섬세함을 한껏 뽐냈다.

```html
{: width="300" height="300")
{: width="100%" height="100%"}
```

만 기억하자 이미지 크기를 적당히 해서 혹시 모를 방문자를 당황시키기 말자.

## 코드 삽입

[```]따옴표 세개 입력하고 프로그래밍 언어 or html 입력해주면된다.

## 리스트 삽입

[-] 입력하고 띄어쓰기 하면

- 이런
- 애들이
- 삽입되고,

[1.] 입력하고 띄어쓰기 하면

1. 이런
2. 친구들이
3. 입력돼영

## 마무리

아무턴가네 맞든 말든 내가 공부하고 생각한 것들을 정리하며 쓸 생각이다.

<img alt="열심히 할테니 잘 부탁드린다는 자막의 펭수움짤" height="50%" src="../assets/img/posts/2022-08-01-how-to-blog-posting/995AE84A5E307BEA05-20220801215343225.png" width="50%"/>
