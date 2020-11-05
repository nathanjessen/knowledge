---
layout: default
title: Font Loading API
parent: Font
---

- [Font Loading API](https://drafts.csswg.org/css-font-loading)
- [CanIUse](http://caniuse.com/#feat=font-loading)

```JS
if("fontDisplay" in document.body.style === false) {
  if ("fonts" in document) {
    document.fonts.load("1em Open Sans Regular");
    document.fonts.ready.then(function(fontFaceSet) {
      document.documentElement.className += " fonts-loaded";
    });
  }
}
```
