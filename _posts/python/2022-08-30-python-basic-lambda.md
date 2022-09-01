---
layout: post
read_time: true
show_date: true
title: python basic, 이름 없는 함수 lambda
date: 2022-08-28 12:29:12 -0600
description: python basic, lambda description
img: posts/cover/python.webp
tags: [python]
author: Kyungseon Park
github: kyungseonpark/
toc: yes
---

# 간단 설명

- 이름을 지을 필요없는 **간단한 함수**
- **함수**이기 때문에 인자(Argument)를 넣을 수 있다.
- 한줄로 표현가능한 함수 ➡️ 코드가 간결해진다.

# 간단 예시

```python
# x를 넣어 x의 제곱을 만드는 함수
def square(x):
  return x**2
```

```python
# x 제곱
square = lambda x:x**2
```

위에 경우는 둘 다 아래와같이 출력됩니다.

```python
output = square(3)
print(output)

##output
## 9
```

# if 문을 사용한 함수를 lambda함수로 만들기

```python
# 이거 짝수인지 판별해줘
def is_even_num(x):
  if x%2 == 0:
    return True
  else:
    return False
```

```python
# 이거 짝수?
is_even = lambda x: True if x%2==0 else False
```

# map이랑 같이 사용해보기

```python
def square(x):
  return x**2

numbers = [1,2,3,4]

squared_numbers = list(map(square, numbers))
print(squared_numbers)

## output
## 1,4,9,16
```

```python
numbers = [1,2,3,4]
squared_numbers = list(map(lambda x:x**2, numbers))
print(squared_numbers)

## output
## 1,4,9,16
```

# filter랑 같이 사용해보기

```python
def is_even_num(x):
  if x%2 == 0:
    return True
  else:
    return False
      
numbers = [1,2,3,4]

even_numbers = list(filter(is_even_num, numbers))
print(even_numbers)

## output
## 2, 4
```

```python
is_even = lambda x: True if x%2==0 else False
numbers = [1,2,3,4]
even_numbers = list(filter(is_even, numbers))
print(even_numbers)

## output
## 2, 4
```

# 마무리

이정도만 알아도 **lambda** 뚝딱입니다.

<img src="../../assets/img/posts/2022-08-30-python-basic-lambda/output_1337252815.jpg" alt="뚝딱이 짤 모음 1탄 : 네이버 블로그" style="zoom:50%;" />