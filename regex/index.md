---
layout: default
title: Regex
---

**Change extension of all scss files to css**

```bash
for f in *.scss; do git mv -- "$f" "${f%.scss}.css"; done;
```

**Change extension of all css files to scss**

```bash
for f in *.css; do git mv -- "$f" "${f%.css}.scss"; done;
```
