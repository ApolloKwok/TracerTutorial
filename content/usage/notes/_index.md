---
title: Notes
weight: 4
---

Unexplained norms below must be confusing to tyros. Just obey them!
* Always inject with `prival val x get() = ...`.

* `Kotlin Native` and `Kotlin JS` are not supported. Because they lack `context receiver` which is
essential in this tool.

* Syntax `T & Any` is not allowed until ksp version `1.8.0-1.0.9`. In old versions, you could
annotate those traceable properties or super types with `@Tracer.Omit` to omit them in the trace.

* `Tracer` is compatible with `ksp 1.7.0-1.0.6` at least. Although mostly it works well with
`ksp`, you'd better try to make your `ksp plugin` in a high stable version, since `ksp api` is not
stable and many bugs are fixed every version.

* Java files are forbidden to use `Tracer`, because I don't want to spend time analyzing those
outdated things. But it's absolutely safe to reference `java classes and functions` in `kotlin` 
files with `tracer`.

*, Few generated types fail code inspection, mostly because of the imperfect authoritative type
inference system. Find their corresponding source properties or super types, then use another type
or annotate them with`@Tracer.Omitted`.
e.g.: todo

*, 如果 super abstract class 和 self 均有 Root /Nodes 标记，那么 super abstract class 中最好不要 override self

4, 解释 common type 的标准  
5, alias type 中带 * 可能会因为 multi-bounds 导致结果不准确  
9, 对于带泛型 / open / abstract class, 因为复用率高，不会从 property type trace, 对于会被多次构造的 class，应让 programmer
尽量少去探索次内部的东西