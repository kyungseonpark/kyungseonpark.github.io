---
layout: post
read_time: true
show_date: true
title: RestAPI로 받은 데이터(Json, Dict)를 DataFrame으로 만들기
date: 2022-09-05 01:15:15 -0600
description: RestAPI to spark.Dataframe
img: posts/cover/spark.webp
tags: [spark]
author: Kyungseon Park
github: kyungseonpark
toc: yes
---

# 사용한 라이브러리

```python
import os
import time

import pandas as pd

from datetime import datetime
from fastapi import FastAPI

from pydantic import BaseModel

class PredictionItem(BaseModel):
    data: dict
```

# dict → Json File → spark.DF

```python
@app.post("/prediction/")
async def post_prediction(api_body: PredictionItem):
  # ms단위로 파일명 작성하여 요청 겹치지 않게 처리
  now_time = datetime.now().strftime('%y%m%d_%H%M%S_%f')
  file_path = f'./json/{now_time}.json'
    with open(file_path, 'w') as f:
      json.dump(api_body.data, f)

  # json file을 읽어서 pySpark Dataframe으로 만들기
 	stream_data = SPARK_SESSION.read.json(file_path)
  
  # 파일 삭제
  os.remove(file_path)
```

```python
process time : 0.001686999999999994
```

# dict → spark.DF

```python
@app.post("/prediction/")
async def post_prediction(api_body: PredictionItem):
	# data = api_body.data
  # stream_data = SPARK_SESSION.createDataFrame([tuple(data.values())], tuple(data.keys()))
  stream_data = SPARK_SESSION.createDataFrame([api_body.data])
```

```python
process time : 0.005585999999999869
```

# 정리

왜 json file로 갔다가 읽는 것이 속도가 더 빠를까? (IO가 발생하는데도 말이다.)

아마도 Dataframe의 특징 때문인 것 같다.

```
- 구조화된(structed) 데이터 구조 : 앞서 언급한 것처럼, DataFrame은 구조화된 데이터를 다루기 쉽게 하기 위해 만들어진 데이터 구조 입니다. 이를 통해, 스파크 사용자는 SparkSQL 등을 통해 구조화된 데이터의 쿼리를 처리할 수 있습니다.
- GC(Garbeage Collection) 오버헤드 감소 : RDD는 데이터를 메모리에 저장합지만, DataFrame은 데이터를 오프-힙(gc의 영향을 받지 않는, 디스크가 아닌 RAM 영역) 영역에 저장합니다. 이를 통해 Garbage Collection의 오버헤드를 감소시켰습니다.
- 직렬화 오버헤드 감소 : DataFrame은 오프-힙 메모리를 사용한 직렬화를 통하여 오버헤드를 크게 감소시켰습니다.
- Flexibility & Scalability : DataFrame은 CSV, 카산드라(Cassandra) 등 다양한 형태의 데이터를 직접 지원합니다. 사용자 입장에서는 이를 통한 효율성이 매우 큽니다.
```

🔗: https://artist-developer.tistory.com/21 [개발자 김모씨의 성장 일기:티스토리]

Spark Dataframe을 생성하면서 오프힙 영역에 생성하게 되고 메모리에 새로운 공간을 만들고 저장하는데에 시간이 꽤나 소모된 것 같다.

하지만 이는 장시간 Dataframe을 핸들링하는데 처리속도에 이점을 주고 안정성을 제공한다.

그래서 RestAPI로 건바이건 실시간 처리하는데에 Spark Dataframe으로 생성하여 SparkSQL로 데이터를 조작할 계획이다.
