---
title: Python logging
tags: ["python"]
---

```py
import logging

logging.basicConfig(
    level=logging.DEBUG,
    format="%(asctime)s %(levelname)s %(message)s",
    datefmt="%Y-%m-%d %H:%M:%S",
    # filename="log.txt", # set this will log to file
)

logging.debug("This is a debug message")
logging.info("This is an info message")
logging.warning("This is a warning message")
logging.error("This is an error message")
logging.critical("This is a critical message")
```

```
2023-05-26 11:43:32 DEBUG This is a debug message
2023-05-26 11:43:32 INFO This is an info message
2023-05-26 11:43:32 WARNING This is a warning message
2023-05-26 11:43:32 ERROR This is an error message
2023-05-26 11:43:32 CRITICAL This is a critical message
```
