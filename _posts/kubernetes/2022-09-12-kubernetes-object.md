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

쿠버네티스 클러스터를 이용하여 애플리케이션(Application)을 배포하고 운영하기 위해 필요한 모든 쿠버네티스 리소스

# 쿠버네티스 오브젝트

- Cluster
  - 컨테이너화된 애플리케이션을 실행하는 노드라고 하는 작업자 시스템 세트
  - 모든 클러스에는 하나 이상의 작업자 노드가 있음
  - 클러스터에는 클러스터를 관리하는 서비스를 실행하는 제어평면도 있음

- Node, Namespace
  - K8s는 컨테이너를 Pod를 그룹화하고 해당 Pod를 노드에서 실행하도록 할당하여 워크로드를 실행
  - 노드는 클러스터에 따라 가상 머신 or 물리적 머신 일 수 있음
  - 각 노드는 컨트롤 플레인에서 관리
  - Pod를 실행하는 데 필요한 서비스를 포함
  - 어디에 실행할거니? 할 때 고민할 부분
- Pod
  - 하나 이상의 컨테이너 그룹
  - Pod는 컨테이너를 실행하는 방법에 대한 사양인 PodSpec 파일에 의해 정의됨
  - Pod는 배포, 확장 및 복제를 위한 K8s 내의 기본 빌딩 블록
  - 어떤 애플리케이션? 할 때 고민할 부분

- Volume
  - 임시 볼륨
    - Pod의 애플리케이션은 공유 볼륨에 액세스하여 Pod에서 데이터 공유를 용이하게 하고 컨테이너 재시작 시 데이터 지속성을 제공
    - Pod가 더 이상 존재하지 않으면 K8s는 임시 볼륨을 삭제

  - 영구 볼륨
    - 영구 볼륨은 임시 볼륨과 유사하게 작동
    - 이를 사용하는 개별 Pod와 독립적인 수명 주기를 갖는다
    - 영구 볼륨은 클러스터 노드와 독립적인 저장소 하위 시스템에 의해 지원받음

- Service, Endpoints
  - 트래픽을 어떻게 로드밸런싱할 것인가?
  - K8s에서 서비스는 Pod의 논리적 모음이자 액세스 수단
  - 서비스는 사용 가능한 포드 세트로 지속적으로 업데이트 ➡️ Pod가 다른 포드를 추적할 필요가 없음
- Namespace
  - 동일한 물리적 클러스터가 지원하는 가상 클러스터
  - 물리적 클러스터는 서로 다른 네임스페이스에 있는 한 동일한 이름을 가진 리소스 보유
  - 네임스페이스는 동일한 클러스터를 사용하는 여러 팀이나 프로젝트가 있을때 유용함

- ReplicaSet
  - 지정된 시간에 특정 수의 Pod 복제본이 실행되고 있는지 확인

- Deployment
  - ReplicaSet 또는 개별 포드를 소유하고 관리
  - 배포에서 원하는 상태를 설명 ➡️ 클러스터의 실제 상태를 제어된 속도로 원하는 상태로 변경
  - 어떤 방식으로 배포할 것인가

- ConfigMap
  - 다른 K8s 개체에서 사용하는 Key-Value 쌍으로 기밀이 아닌 데이터를 저장하는 API 개체
  - 애플리케이션 코드에서 구성 데이터를 분리 가능하도록 함

- Secrets
  - 기밀 데이터 저장
  - 민감 정보에 대한 액세스를 제한
  - 선택적으로 켤 수 있음


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
