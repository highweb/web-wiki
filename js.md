---
layout: base
title: JavaScript cheatsheet
---

## Get query params:

```js
var urlParams = new URLSearchParams(window.location.search);

console.log(urlParams.get('action')); // "edit"
```

Source: https://davidwalsh.name/query-string-javascript

Polyfill: https://github.com/WebReflection/url-search-params
