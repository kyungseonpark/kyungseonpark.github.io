---
layout: post
read_time: true
show_date: true
title: Apple Silicon M2, install Feast
date: 2022-08-04 01:29:12 -0600
description: install feast at M2
img: posts/cover/feast.png
tags: [feast]
author: Kyungseon Park
github: kyungseonpark
toc: yes
---

# 영롱한 내 맥북 에어 M2, 근데 애물단지 옷을 입은.

개인적으로 사용하던 한성게이밍노트북은 사실상 노트북이 아니다. 들고 다닐수 있는 데스크탑이다. 벽돌무게의 어댑터를 가방에 넣느라면 차량없이는 이동을 포기해야한다.

그래서 맥북 에어를 개인용으로 사서 공부를 하겠노라라는 다짐을 몇번이곤 했다. 하지만 M1을 2022년에 와서 산다는 것은 테크충인 내게 용납할 수 없었다. 그래서 얼마전 기다리고 기다리던 MacBook Air M2를 구매했다.

<img src="../assets/img/posts/2022-08-05-install-feast-m2/image-20220805223139652.png" alt="image-20220805223139652" style="zoom:67%;" />

아주 영롱해....이뻐...지문 잘뭍어....잭꽂을때 코팅까질까 무서워....

# 설치를 해야 Feast를 개발하고 공부하지

회사에서 받은 맥북은 운좋게도(?) intel mac 2019를 받아서 패키지 설치하는데 애로사항이 전혀 없었다.

![편안 짤과 움짤 모음 - 짤봇](../assets/img/posts/2022-08-05-install-feast-m2/Vgvs95YpK.jpeg)

근데 이놈의 M2, Apple Silicon은 개복치다. 패키치 설치만 할려치면 Error, Error, Error.

<img src="../assets/img/posts/2022-08-05-install-feast-m2/before.jpg" alt="rajephon lab - 개비스콘 짤 생성기" style="zoom:50%;" />

```dockerfile
pip install feast
```

를 실행하면....

```shell
	Using cached feast-0.23.0.tar.gz (3.0 MB)
	Installing build dependencies ...
```

이 무한으로 돌면서 CPU사용량이 99%을 찍고 공포 분위기를 조성한다.

이글을 쓰면서도 이 설치가 성공할지 모른다. 우선 해봤던 짓을 기록하면서 혹시나 찾아와서 읽는 분들의 시간을 아껴주고자 한다.

# How to run Feast on M1

:link:  <a href="https://github.com/feast-dev/feast/issues/2105/">https://github.com/feast-dev/feast/issues/2105</a>

m1 install feast 뭐 이런 검색어로 입력하면 처음 나오는 페이지. Feast 개발팀의 GitHub 이슈 페이지다. m1에서 되는지는 나는 모르겠고 m2는 안됑...

# 가상환경 문제인가?

Python의 친구 Anaconda로 가상환경을 구성해서 그런건가....혹시나해서 venv로 해서 해봤다. 안됑....

# Requirement를 직접 설치해보자

:link: <a href="https://github.com/feast-dev/feast/tree/v0.23-branch/sdk/python/requirements">https://github.com/feast-dev/feast/tree/v0.23-branch/sdk/python/requirements</a>

현재 2022년 8월 5일 기준 v0.23-branch가 최종 배포판이며 requirement에서 뭐가 문제인지 찾아보고자 하는 접근방법이다.

## py3.8-requirements.txt

우선 py3.8-requirements.txt를 설치한다. 혹시 모를 분들을 위해 명령어를 알려주자면

```
pip install -r py3.8-requirements.txt
```

근데 분명 에러가 날거다. 그래야 내가 덜 억울하다. grpcio 설치하는데 에러가 날거다.

:link: <a href="https://anaconda.org/conda-forge/grpcio">https://anaconda.org/conda-forge/grpcio</a>

conda로 설치해보자.

```shell
conda install -c conda-forge grpcio==1.47.0
```

으로 한스텝 넘어가보자.

<img src="../assets/img/posts/2022-08-05-install-feast-m2/img.jpg" alt="위대한 개츠비' 디카프리오가 건배하던 와인, 대체 뭘까요?" style="zoom:33%;" />

pip install -r py3.8-requirements.txt를 반복하면서 설치가 안되는 패키지는 이런식으로 찾아가면서 설치해보자...

(이렇게까지 해야하나 싶기도 하고....VM 올려서 해볼까 하기도하고...오기가 생기더라구요.)

## py3.8-ci-requirements.txt

``` shell
pip install -r py3.8-ci-requirements.txt
```

### mysqlclient Error

subprocess-exited-with-error

```shell
Collecting mysqlclient==2.1.1
  Using cached mysqlclient-2.1.1.tar.gz (88 kB)
  Preparing metadata (setup.py) ... error
  error: subprocess-exited-with-error

  × python setup.py egg_info did not run successfully.
  │ exit code: 1
  ╰─> [16 lines of output]
      /bin/sh: mysql_config: command not found
      /bin/sh: mariadb_config: command not found
      /bin/sh: mysql_config: command not found
      Traceback (most recent call last):
        File "<string>", line 2, in <module>
        File "<pip-setuptools-caller>", line 34, in <module>
        File "/private/var/folders/kz/yd1mgyyj2g75szh6mm6tf84w0000gn/T/pip-install-dc0brsrm/mysqlclient_633d10bc039844e28e1af5bad2d4d7c4/setup.py", line 15, in <module>
          metadata, options = get_config()
        File "/private/var/folders/kz/yd1mgyyj2g75szh6mm6tf84w0000gn/T/pip-install-dc0brsrm/mysqlclient_633d10bc039844e28e1af5bad2d4d7c4/setup_posix.py", line 70, in get_config
          libs = mysql_config("libs")
        File "/private/var/folders/kz/yd1mgyyj2g75szh6mm6tf84w0000gn/T/pip-install-dc0brsrm/mysqlclient_633d10bc039844e28e1af5bad2d4d7c4/setup_posix.py", line 31, in mysql_config
          raise OSError("{} not found".format(_mysql_config_path))
      OSError: mysql_config not found
      mysql_config --version
      mariadb_config --version
      mysql_config --libs
      [end of output]

  note: This error originates from a subprocess, and is likely not a problem with pip.
error: metadata-generation-failed

× Encountered error while generating package metadata.
╰─> See above for output.

note: This is an issue with the package mentioned above, not pip.
hint: See above for details.
```

가 뜨네....

:link: <a href="https://velog.io/@max9106/mac%EC%97%90-MySQL-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0-4ck17gzjk3">https://velog.io/@max9106/mac%EC%97%90-MySQL-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0-4ck17gzjk3</a> 를 참고하여

```shell
brew update
brew install cask
brew install mysql
```

mac OS에 mysql을 설치해준다. 그리고

```shell
pip install mysqlclient==2.1.1
```

가 설치된다.....ㅠㅠ

### psycopg2-binary Error

subprocess-exited-with-error

:link: <a href="https://github.com/psycopg/psycopg2/issues/1200">https://github.com/psycopg/psycopg2/issues/1200</a>

```shell
export LDFLAGS="-L/usr/local/opt/openssl/lib"
export CPPFLAGS="-I/usr/local/opt/openssl/include"
```

```shell
brew install postgres
pip install psycopg2
pip install psycopg2-binary==2.9.3
```

### gracious-tools Error

```shell
pip install grpcio-tools
```

하면 그냥 설치된다.



> ㅠㅠㅠ 아직도 진행중이다 도와주십쇼.