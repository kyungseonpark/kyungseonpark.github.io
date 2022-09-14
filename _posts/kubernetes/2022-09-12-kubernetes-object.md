---
layout: post
read_time: true
show_date: true
title: Kubernetes Object, k8s 오브젝트
date: 2022-09-10 12:29:12 -0600
description: k8s object
img: posts/cover/k8s.webp
tags: [kubernetes]
author: Kyungseon Park
github: kyungseonpark/
toc: yes
---

# 쿠버네티스 오브젝트란?

쿠버네티스 클러스터를 이용하여 어플리케이션(Application)을 배포하고 운영하기 위해 필요한 모든 쿠버네티스 리소스

# 쿠버네티스 오브젝트

- Pod
  - 어떤 어플리케이션
- ReplicaSet
  - 얼마나
- Node, Namespace
  - 어디에
- Deployment
  - 어떤 방식으로 배포할 것인가
- Service, Endpoints
  - 트래픽을 어떻게 로드밸런싱할 것인가

## Spec 필드

- Spec
  - 원하는 오브젝트 상태.
  - 선언할 수 있는 속성은 오브젝트 종류마다 다름.
  - <a href=https://kubernetes.io/docs/reference/kubernetes-api/>참고 링크 🔗</a>
- apiVersion
  - 오브젝트를 생성할 때 사용하는 API 버전
- kind
  - 생성하고자 하는 오브젝트 종류
- Metadata
  - 오브젝트를 구분 지을 수 있는 정보
  - Name, resourceVersion, labels, namespace 등등...

## Status 필드

- status
  1. 오브젝트가 k8s cluster에 생성
  2. k8s는 오브젝트 정보에 status 필드를 추가
  3. 현재 실행 중인 오브젝트의 상태 정보 전달

# 쿠버네티스가 갖는 목적

> 쿠버네티스가 달성해야할 목표 ➡️ **Spec**
>
> 오브젝트의 현재 상태 ➡️ **Status**

***Status가 Spec에 도달하도록 한다.***

1. 사용자가 k8s object yaml 파일을 작성 ➡️ Spec
2. K8s API를 이용하여 k8s에 생성을 요청한다.
3. k8s API Server가 오브젝트 파일의 spec 파일을 읽고 오브젝트를 생성한다.
4. k8s ControllerManager가 spec과 status를 비교하면서 계속 조정하고 상태를 업데이트
