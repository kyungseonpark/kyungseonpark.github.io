---
title: "Feast, Online Store에 바로 데이터 넣기"
date: 2022-07-29
img: posts/20210402/post7-header.webp
tags: [feast, mlops]
category: Feast
author: Kyungseon Park
description: "feast."
---

# 1안, use PushSource

[Push](https://docs.feast.dev/reference/data-sources/push)

## Define a push Source

```python
from feast import PushSource, ValueType, BigQuerySource
from feast import FeatureView, Feature, Field
from feast.types import Int64

"""

"""
push_source = PushSource(
    name="push_source",
    batch_source=BigQuerySource(table="test.test"),
)

fv = FeatureView(
    name="feature view",
    entities=["user_id"],
    schema=[Field(name="life_time_value", dtype=Int64)],
    source=push_source,
)
```

## Pushing Data

```python
from feast import FeatureStore
import pandas as pd

fs = FeatureStore(...)
feature_data_frame = pd.DataFrame()
fs.push("push_source_name", feature_data_frame)
```

# 2안, FeatureStore.write_to_online_store 메소드

[Feast Python API Documentation - Feast documentation](https://rtd.feast.dev/en/latest/index.html#feast.feature_store.FeatureStore.write_to_online_store)