---
title: Details
date: 2023-02-19T20:43:59+08:00
weight: 3
---

* Wildcard `*` would be converted to its bound, and with covariance if needed, like from 
  `List<*>` to `List‹Any？›` and from `Array<*>` to `Array‹↓Any？›`.
---
* Type aliases are always converted to its actual types.  
---
* Partial super types are traceable. including src klass 截止到 foreign module or Java\

*
截止探索 element 的条件\
tags.AllInternal\
tags.propertiesFullName\
Omit 的用法\
Tips 的用法 \
支持 var\