---
Date: Jun 3, 2018
Topic: pip
---

# pip3 ImportError: cannot import name main

## Problem

After upgrade to pip 10, pip refuses to start and raise this error instead:

```
Traceback (most recent call last):
  File "/usr/bin/pip3", line 7 in <module>
    from pip import main
ImportError: cannot import name 'main'
```

## Solutions

No idea what's going on. But here comes a temporary solution:

1. Modify `/usr/bin/pip3`

   ```
   from pip._internal import main
   ```

## Related Links

* After pip 10 upgrade ... #5240: https://github.com/pypa/pip/issues/5240
