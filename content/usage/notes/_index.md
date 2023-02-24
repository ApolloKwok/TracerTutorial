---
title: Notes
weight: 3
---

Unexplained norms below must be confusing to tyros. Just obey them!
1, Always inject with `prival val x get() = ...`.

1, `Kotlin Native` and `Kotlin JS` are not supported. Because they lack `context receiver` which is
essential in this tool.

2, If you are developing android, see [tracer extension on traditional android](https://github.com/ApolloKwok/TracerAndroidTraditional)
after you learned this.

3, Syntax `T & Any` is not allowed until ksp version `1.8.0-1.0.9`. In old versions, you could
annotate those traceable properties or super types with `@Tracer.Declare(false)` to omit them.

4, `Tracer` is compatible with `ksp 1.7.0-1.0.6` at least. Although mostly it works well with
`ksp`, you'd better try to make your `ksp plugin` in a high stable version, since `ksp api` is not
stable and many bugs are fixed every version.

5, Java files are forbidden to use `Tracer`, because I don't want to spend time analyzing those
outdated things. But it's absolutely safe to call `java classes and functions` in `kotlin` files
with `tracer`.

6, Few generated types fail code inspection, mostly because of the imperfect authoritative type
inference system. Find their corresponding source properties or super types, then use another type
or annotate them with`@Tracer.Declare(false)`.
e.g.: todo

7, 如果 super abstract class 和 self 均有 Root /Nodes 标记，那么 super abstract class 中最好不要 override self

4, 解释 common type 的标准  
5, alias type 中带 * 可能会因为 multi-bounds 导致结果不准确  
9, 对于带泛型 / open / abstract class, 因为复用率高，不会从 property type trace, 对于会被多次构造的 class，应让 programmer
尽量少去探索次内部的东西