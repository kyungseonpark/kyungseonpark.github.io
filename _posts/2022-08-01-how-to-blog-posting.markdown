---
layout: post
read_time: true
show_date: true
title: GitBlog 포스팅 Tips
date: 2022-08-01 12:29:12 -0600
description: post git-Blog
img: posts/cover/typing_man.jpg
tags: [gitblog]
author: Kyungseon Park
github: kyungseonpark
toc: yes
---

# 앞으로 블로그를 시작하기 위한 글.

 나는 Notion으로 블로그를 관리해보려고했다. oopy를 이용하면 호스팅도 굉장히 편했고 Notion의 강력한 임베딩 기능들은 굉장히 매력적이었다. 하지만 oopy구독비용+개인Host DNS비용까지 합하면 한달에 1만원을 사용하기에는 그만한 가치가 있나 생각하게되었다...

<img alt="흠터레스팅 짤 모음.jpg.gif : 클리앙" height="20%" src="../assets/img/posts/2022-08-01-how-to-blog-posting/heum_teresting.gif" width="20%"/>

 자기개발 비용이라고 생각할 수 있지만....닭강정 하나 사먹는게 더 좋아서 gitblog를 시작하게되었다. 근데 markdown으로 하려니 너무 어려워 정리해놓고 틈틈히 컨닝하면서 작성하기 위해 작성하는 글이다.

> 참고로 Jekyll을 사용해서 포스팅중입니다.

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

<img alt="신난다 &amp;gt; 짤투데이" height="50%" src="../assets/img/posts/2022-08-01-how-to-blog-posting/KKAA_KKAA.gif" width="50%"/>

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

## Web 임베딩 하기

Notion처럼 동영상(YouTube)이나 웹을 직접 화면에 넣기위해 사용하면 좋을것같다.

```html
<iframe src="https://kyungseonpark.github.io/" title="PKS Git-Blog" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```

```css
.page-content > iframe {
  position: relative;
  top: 5px;
  left: 0;
  width: 100%;
  height: 300px;
  border: none;
}
```

<iframe src="https://kyungseonpark.github.io/" title="PKS Git-Blog" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Web 북마크 생성하기

```html
<a href="https://kyungseonpark.github.io/">PKS Git-blog</a>
```

🔗 <a href="https://kyungseonpark.github.io/">PKS Git-blog</a>

## Emoji 사용하기

원본 Gemfile에

```ruby
source 'https://rubygems.org'

gem 'jekyll'

group :jekyll_plugins do
  gem "jekyll-paginate"
  gem "jekyll-feed"
  gem "jekyll-sitemap"
end
```

Gem 'jemoji'를 추가하고

```ruby
source 'https://rubygems.org'

gem 'jekyll'

group :jekyll_plugins do
  gem "jekyll-paginate"
  gem "jekyll-feed"
  gem "jekyll-sitemap"
  gem "jemoji" #여기요 여기.
end
```

_config.yml 파일에는

```yaml
plugins:
  - jemoji
```

를 추가하여 사용하면 된다.

하지만,

jemoji는 image 속성을 사용하기 때문에....내 테마에서는 적용이 잘 안되더라.

그래서 ctrl+cmd+space를 사용해서 그냥 이모지 입력해서 사용하는게 젤 편하더군요. 😂

## 마무리

아무턴가네 맞든 말든 내가 공부하고 생각한 것들을 정리하며 쓸 생각이다.

<img alt="열심히 할테니 잘 부탁드린다는 자막의 펭수움짤" height="50%" src="../assets/img/posts/2022-08-01-how-to-blog-posting/pengsu_nicetomeet.png" width="50%"/>
