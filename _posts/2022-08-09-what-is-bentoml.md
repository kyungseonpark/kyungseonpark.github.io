---
layout: post
read_time: true
show_date: true
title: What is BentoML?
date: 2022-08-08 12:29:12 -0600
description: description about BentoML.
img: posts/cover/bento.jpg
tags: [bentoml]
author: Kyungseon Park
github: kyungseonpark
toc: yes
---

# What is BentoML?

🔗 <a href="https://docs.bentoml.org/en/latest/index.html">https://docs.bentoml.org/en/latest/index.html</a>

BentoML은 ML모델을 제공하기 위한 오픈소스 프레임워크입니다.

- ML모델을 제품화하는것을 가속화합니다.
- ML모델을 프로덕션하는것을 표준화할 수 있게 합니다.
- 안정적이고 확장 가능한 고성능 모델을 제공할 수 있게 합니다.
- 유연한 MLOps 플랫폼을 제공합니다.



## 간단한 정의

> ***BentoML = ML+ FastAPI + Docker 입니다. 🍱***

![Getting Started with Docker & Fast API 🚀🚀 - DEV Community](../assets/img/posts/2022-08-09-start-to-bentoml/l4jt274288k241g94r66.png)

우리가 생각할 수 있는 모델(ML/DL)을 컨테이너화(Docerize) 합니다. 근데 FastAPI로 Back-end End-point를 곁들인.

<img src="../assets/img/posts/2022-08-09-start-to-bentoml/img.png" alt="휴먼강록체, 근데 이제 ~를 곁들인" style="zoom:50%;" />

### Docker가 있어서 BentoML이 갖는 장점

- Docker Daemon이 있으면 어디서든 Server로서 운용할 수 있다.
- BentoML의 배포가 빨라지고 쉽게 표준화 할 수 있다.
- 같은 모델을 여러개 띄워 확장성을 쉽게 넓힐 수 있다. (like Scale-Out)
- 리소스 사용량 체크가 쉬움.

### FastAPI가 있어서 BentoML이 갖는 장점

- 쉬운 API 추가
- 쉬운 API 사용
- 쉬운 마이그레이션
- 쉬운 보안 적용
- Customize가 쉬워짐.



# BentoML에서 배포할 수 있는 프레임워크

BentoML에서 배포 가능한 ML/DL framework는? 🔗 <a href="https://docs.bentoml.org/en/latest/frameworks/index.html">출처</a>

- CatBoost
- XGBoost
- LightGBM
- MLflow
- ONNX
- Sklearn

- Keras
- Tensorflow
- Pytorch
- fast.ai

- Custom Model
  - Picklable Model (pickle로 압축 및 저장할 수 있는 모델)

> 그냥 너가 다룰 수 있는 모델은 다 배포 할 수 있게 해줄게!
>
> 라는 마인드인것 같네요.

<a href="https://github.com/bentoml/BentoML/tree/main/examples">관련 예제들</a>들도 github을 통해 공유하고 있으니, 다뤄봅시다. 



# 마무리 글.

ML기반의 AutoML 프레임워크도 다루고있으니, 예를 들면 H2O. (현재 정식 지원은 안합니다.)

잘 정제된 데이터(Tabluar type)만 있으면 이걸로 모델을 배포할 수 있도록 토이프로젝트를 해볼까 합니다. 재밌을것 같지 않아유?

<img src="../assets/img/posts/2022-08-09-what-is-bentoml/VD13652524_w640.jpg" alt="백종원의 3대 천왕 : 하니, 라면 먹방하며 깨알 같은 백종원 흉내 “재밌네” : SBS" style="zoom: 33%;" />

