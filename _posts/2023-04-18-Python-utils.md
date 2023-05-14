---
title: Python utils tricks
categories: ["usage"]
tags: ["python"]
---

## time

```py
from datetime import datetime, timedelta, timezone
import time

# get readable_time or timestamp
readable_time = datetime.now(timezone(timedelta(hours=8)))
# 2023-05-14 23:10:37.228020+08:00
timestamp = time.time()
# 1684077037.22802
print(readable_time)
print(timestamp)

# readable_time <-> timestamp
readable_time = datetime.fromtimestamp(timestamp, timezone(timedelta(hours=8)))
# 2023-05-14 23:10:37.228020+08:00
timestamp = datetime.timestamp(readable_time)
# 1684077037.22802
print(readable_time)
print(timestamp)
```
