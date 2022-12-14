---
layout: post
read_time: true
show_date: true
title: What is BentoML?
date: 2022-08-07 12:29:12 -0600
description: description about BentoML.
img: posts/cover/bento.webp
tags: [bentoml]
author: Kyungseon Park
github: kyungseonpark/MLops-BentoML
toc: yes
---

# 1. What is BentoML?

๐ <a href="https://docs.bentoml.org/en/latest/index.html">https://docs.bentoml.org/en/latest/index.html</a>

BentoML์ ML๋ชจ๋ธ์ ์ ๊ณตํ๊ธฐ ์ํ ์คํ์์ค ํ๋ ์์ํฌ์๋๋ค.

- ML๋ชจ๋ธ์ ์ ํํํ๋๊ฒ์ ๊ฐ์ํํฉ๋๋ค.
- ML๋ชจ๋ธ์ ํ๋ก๋์ํ๋๊ฒ์ ํ์คํํ  ์ ์๊ฒ ํฉ๋๋ค.
- ์์ ์ ์ด๊ณ  ํ์ฅ ๊ฐ๋ฅํ ๊ณ ์ฑ๋ฅ ๋ชจ๋ธ์ ์ ๊ณตํ  ์ ์๊ฒ ํฉ๋๋ค.
- ์ ์ฐํ MLOps ํ๋ซํผ์ ์ ๊ณตํฉ๋๋ค.



## ๊ฐ๋จํ ์ ์

> ***BentoML = ML+ FastAPI + Docker ์๋๋ค. ๐ฑ***

![Getting Started with Docker & Fast API ๐๐ - DEV Community](../../assets/img/posts/2022-08-09-what-is-bentoml/l4jt274288k241g94r66.png)

์ฐ๋ฆฌ๊ฐ ์๊ฐํ  ์ ์๋ ๋ชจ๋ธ(ML/DL)์ ์ปจํ์ด๋ํ(Containerize) ํฉ๋๋ค. ๊ทผ๋ฐ FastAPI๋ก Back-end End-point๋ฅผ ๊ณ๋ค์ธ.

<img src="../../assets/img/posts/2022-08-09-what-is-bentoml/img.png" alt="ํด๋จผ๊ฐ๋ก์ฒด, ๊ทผ๋ฐ ์ด์  ~๋ฅผ ๊ณ๋ค์ธ" style="zoom:50%;" />



### Docker๊ฐ ์์ด์ BentoML์ด ๊ฐ๋ ์ฅ์ 

- Docker Daemon์ด ์์ผ๋ฉด ์ด๋์๋  Server๋ก์ ์ด์ฉํ  ์ ์๋ค.
- BentoML์ ๋ฐฐํฌ๊ฐ ๋นจ๋ผ์ง๊ณ  ์ฝ๊ฒ ํ์คํ ํ  ์ ์๋ค.
- ๊ฐ์ ๋ชจ๋ธ์ ์ฌ๋ฌ๊ฐ ๋์ ํ์ฅ์ฑ์ ์ฝ๊ฒ ๋ํ ์ ์๋ค. (Scale-Out)
- ๋ฆฌ์์ค ์ฌ์ฉ๋ ์ฒดํฌ๊ฐ ์ฌ์.



### FastAPI๊ฐ ์์ด์ BentoML์ด ๊ฐ๋ ์ฅ์ 

- ์ฌ์ด API ์ถ๊ฐ
- ์ฌ์ด API ์ฌ์ฉ
- ์ฌ์ด ๋ง์ด๊ทธ๋ ์ด์
- ์ฌ์ด ๋ณด์ ์ ์ฉ
- Customize๊ฐ ์ฌ์์ง.



# 2. BentoML์์ ๋ฐฐํฌํ  ์ ์๋ ํ๋ ์์ํฌ

BentoML์์ ๋ฐฐํฌ ๊ฐ๋ฅํ ML/DL framework๋? ๐ <a href="https://docs.bentoml.org/en/latest/frameworks/index.html">์ถ์ฒ</a>

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
  - Picklable Model (pickle๋ก ์์ถ ๋ฐ ์ ์ฅํ  ์ ์๋ ๋ชจ๋ธ)

> ๊ทธ๋ฅ ๋๊ฐ ๋ค๋ฃฐ ์ ์๋ ๋ชจ๋ธ์ ๋ค ๋ฐฐํฌ ํ  ์ ์๊ฒ ํด์ค๊ฒ!
>
> ๋ผ๋ ๋ง์ธ๋์ธ๊ฒ ๊ฐ๋ค์.

<a href="https://github.com/bentoml/BentoML/tree/main/examples">๊ด๋ จ ์์ ๋ค</a>๋ค๋ github์ ํตํด ๊ณต์ ํ๊ณ  ์์ผ๋, ๋ค๋ค๋ด์๋ค. 



# 3. ๋ง๋ฌด๋ฆฌ ๊ธ.

ML๊ธฐ๋ฐ์ AutoML ํ๋ ์์ํฌ๋ ๋ค๋ฃจ๊ณ ์์ผ๋, ์๋ฅผ ๋ค๋ฉด H2O. (ํ์ฌ ์ ์ ์ง์์ ์ํฉ๋๋ค.)

์ ์ ์ ๋ ๋ฐ์ดํฐ(Tabluar type)๋ง ์์ผ๋ฉด ์ด๊ฑธ๋ก ๋ชจ๋ธ์ ๋ฐฐํฌํ  ์ ์๋๋ก ํ ์ดํ๋ก์ ํธ๋ฅผ ํด๋ณผ๊น ํฉ๋๋ค. ์ฌ๋ฐ์๊ฒ ๊ฐ์ง ์์์ ?

<img src="../../assets/img/posts/2022-08-09-what-is-bentoml/VD13652524_w640.jpg" alt="๋ฐฑ์ข์์ 3๋ ์ฒ์ : ํ๋, ๋ผ๋ฉด ๋จน๋ฐฉํ๋ฉฐ ๊นจ์ ๊ฐ์ ๋ฐฑ์ข์ ํ๋ด โ์ฌ๋ฐ๋คโ : SBS" style="zoom: 33%;" />

