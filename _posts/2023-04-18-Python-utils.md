---
title: Python utils tricks
categories: ["usage"]
tags: ["python"]
---

## time

```py
from datetime import datetime, timedelta, timezone
import time

'get readable_time or timestamp'
readable_time_without_timezone = datetime.utcnow()
# 2023-05-14 15:10:37.228020
readable_time_without_timezone_with_offset = datetime.now()
'''
# I'm in `+08:00` timezone
# this `datetime` object doesn't contain timezone info
# it can't do math with `datetime` objects contain timezone info
'''
# 2023-05-14 23:10:37.228020
readable_time = datetime.now(timezone(timedelta(hours=8)))
# 2023-05-14 23:10:37.228020+08:00
timestamp = time.time()
# 1684077037.22802
print(readable_time_without_timezone)
print(readable_time_without_timezone_with_offset)
print(readable_time)
print(timestamp)

'readable_time <-> timestamp'
readable_time_without_timezone_with_offset = datetime.fromtimestamp(timestamp)
'''
# I'm in `+08:00` timezone
# this `datetime` object doesn't contain timezone info
# it can't do math with `datetime` objects contain timezone info
'''
# 2023-05-14 23:10:37.228020
readable_time = datetime.fromtimestamp(timestamp, timezone(timedelta(hours=8)))
# 2023-05-14 23:10:37.228020+08:00
timestamp = datetime.timestamp(readable_time)
# 1684077037.22802
print(readable_time_without_timezone_with_offset)
print(readable_time)
print(timestamp)
print(readable_time_without_timezone_with_offset - datetime.utcnow())
# 8:00:00.000001
print(type(readable_time_without_timezone_with_offset - datetime.utcnow()))
# <class 'datetime.timedelta'>
print(readable_time - datetime.fromtimestamp(timestamp, timezone(timedelta(hours=0))))
'2023-05-14 23:10:37.228020+08:00 - 2023-05-14 15:10:37.228020+00:00'
# 0:00:00
```

### Summary
- `datetime without timezone` can only do math with `datetime without timezone`.
- `datetime with timezone` can only do math with `datetime with timezone`.
- the math result is `timedelta` object.
- `datetime without timezone` and `datetime with timezone` are all `datetime` object.