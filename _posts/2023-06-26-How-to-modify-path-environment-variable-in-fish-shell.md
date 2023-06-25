---
title: How to modify path environment variable in fish shell
categories: ["howto"]
tags: ["linux"]
---

# Set path environment variable permanently

```sh
set -U fish_user_paths /usr/local/bin $fish_user_paths
```

This will prepend /usr/local/bin permanently to your path, and will affect the current session and all future instances too because the -U argument will make the variable universal.

# Links

- [stackoverflow](https://stackoverflow.com/questions/26208231/modifying-path-with-fish-shell)
