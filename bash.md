---
layout: base
title: Bash scripting
---

```
# Mark as bash script:
#!/bin/bash

# Stop on errors:
set -e

# Current dir name:
${PWD##*/}

# Set env var:
ABC="123"; export ABC
```
