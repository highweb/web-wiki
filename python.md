---
layout: base
title: Python cheatsheet
---


## dict

Initialize or modify dict value:
```
book = {'title': 'Game of Thrones'}
book.setdefault('authors', []).append('George R.R. Martin')
# {'authors': ['George R.R. Martin'], 'title': 'Game of Thrones'}
```


## set

Intersect two sets:
```
set(['w', 5, 7]) & set([7, 9, 'w'])
# set(['w', 7])
```
