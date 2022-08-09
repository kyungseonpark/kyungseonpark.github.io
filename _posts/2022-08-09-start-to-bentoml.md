---
layout: post
read_time: true
show_date: true
title: BentoML 예제로 다뤄보기.
date: 2022-08-08 12:29:12 -0600
description: BentoML tutorial
img: posts/cover/bento.jpg
tags: [bentoml]
author: Kyungseon Park
github: kyungseonpark
toc: yes
---

# 이글의 목적

🔗 https://docs.bentoml.org/en/latest/tutorial.html

튜토리얼도 굉장히 쉽게 구성되어 있어서...이 글이 필요할까 싶어요.

그래도 나도 정리할겸. 내가 다뤄본 경험도 넣을겸. 써볼까합니다.

튜토리얼로도 충분히 이해가 될만한 수준이라면 보지마요 부끄러워요.

sklearn에서 제공하는 <a href="https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_breast_cancer.html#sklearn.datasets.load_breast_cancer">breast_cancer</a>를 이용하여 Batch Prediction(여러 Row를 한방에 예측해줭.)을 제공하는 API를 만들어 볼거에요.



# BentoML 설치

2022년 8월 9일 기준 1.0.3 버전이 배포되어있습니다.

```shell
pip install --upgrade pip
pip install bentoml
```

로 설치해봅시다.



# 모델 학습하기

xgboost로 심장병(Breast Cancer) 이진분류모델(Binary Classification Model) 생성하기

```python
# BentoML 가져와
import bentoml

from xgboost as xgb
# Toy Dataset 가져와
from sklearn import datasets

# Breast Cancer 데이터셋 가져오기.
breast_cancer = datasets.load_breast_cancer()
X, y = breast_cancer.data, breast_cancer.target
```

```python
# 학습된 xgb 모델 만들기.
xgb_clf = xgb.DMatrix(X, label=y)
param = {"max_depth": 3, "eta": 0.3, "objective": "multi:softprob", "num_class": 2}
fitted_clf = xgb.train(param, xgb_clf)
```



TBA
