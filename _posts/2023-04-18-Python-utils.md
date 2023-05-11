---
title: Python utils tricks
categories: ["usage"]
tags: ["python"]
---

# Get specific datetime with timezone

```py
from datetime import datetime, timedelta, timezone

def now():
    return datetime.now(timezone(timedelta(hours=8)))

print(now())
```

```sh
2023-04-18 12:47:16.030372+08:00
```
