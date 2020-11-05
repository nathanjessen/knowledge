---
layout: default
title: Animation
parent: CSS
---

## Fill Mode

Pause at the end of the animation and do not reset to its default state, pre-animation.

```CSS
@keyframes slideIn {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(0); }
}

.slideIn {
  animation-name: slideIn;
  animation-duration: .25s;
  animation-fill-mode: forwards;
}
```
