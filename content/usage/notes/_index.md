---
title: Notes
weight: 4
---

* `Kotlin Native` and `Kotlin JS` are not supported. Because they lack `context receiver` which is
  essential in this tool.

* Always inject like `prival val x get() = _X`. Just obey it which is confusing to tyros but 
  automatically understandable when you get familiar.

* `Tracer` is compatible with `ksp 1.7.0-1.0.6` at least. Although mostly it works well with
`ksp`, you'd better try to make your `ksp plugin` in a high stable version, since `ksp api` is not
stable and many bugs are fixed every version.

* Java files are forbidden to use `Tracer`, because I don't want to spend time analyzing those
outdated things. But it's absolutely safe to reference `java classes and functions` in kotlin files.

*, Few generated types fail code inspection, mostly because of the imperfect authoritative type
inference system. Find their corresponding source properties or super types, then use another type
or annotate them with`@Tracer.Omitted`.
e.g.: todo

*, 如果 super abstract class 和 self 均有 Root /Nodes 标记，那么 super abstract class 中最好不要 override self

5, alias type 中带 * 可能会因为 multi-bounds 导致结果不准确  
