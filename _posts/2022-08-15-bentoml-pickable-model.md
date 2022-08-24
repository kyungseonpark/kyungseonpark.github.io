---
layout: post
read_time: true
show_date: true
title: BentoML Custom model, Pickleable Model
date: 2022-08-15 12:29:12 -0600
description: BentoML tutorial
img: posts/cover/bento.webp
tags: [bentoml]
author: Kyungseon Park
github: kyungseonpark/MLops-BentoML
toc: yes
---

# Pickle?

![피클 가지고 놀기 : 네이버 블로그](/Users/kyungseon/Library/CloudStorage/OneDrive-에이젠글로벌/kyungseonpark.github.io/assets/img/posts/2022-08-15-bentoml-pickable-model/sponge_pickle.png)

python 자체에서도 흔하게 쓰이는지는 모르겠으나, ML/DL을 하다보면 쉽게 접할 수 있는 압축 확장자이다.

ML을 쉽게 접할 수 있는 Sklearn에서도 지원하고 DL을 쉽게 접할 수 있는 Tensorflow에서도 쉽게 접할 수 있다.

이런 pickle파일을 BentoML🍱에서도 지원하고 있기 때문에 우리는 pickle로 저장할 수 있는 모델이라면 쉽게 묶어서 구현할 수 있을 것이다.

다시 말해서, Tensorflow, sklearn, xgboost 다 pickle로 저장해서 pickle파일을 API로 던져서 컨테이너화(Containerize)된 Docker Image를 얻도록 구현할 생각이다.

# BentoML, Custom Model

🔗<a href="https://docs.bentoml.org/en/latest/frameworks/picklable.html">https://docs.bentoml.org/en/latest/frameworks/picklable.html</a>

예제는 이미 공식 문서에 잘 서술되어 있다.

# 전략 설정

**📡어떻게 pickle파일을 api로 전송해서 BentoML로 할 것인가?**

```py
loaded_model = bentoml.picklable_model.load_model("my_python_model:latest")
```



[진행중]
