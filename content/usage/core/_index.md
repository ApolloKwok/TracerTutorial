---
title: "Core"
weight: 1
---

in video  

1, 找生成的代码时不用 ` 开头  
2, val xx get() = 某个 tracerPro 前的修饰符只能为 private  
3, 如果一个类如果可能在 mallTracer 或者 out mallTracer 下，那么直接 @Nodes(Mall::class)  
4, 解释 common type 的标准  
5, alias type 中带 * 可能会因为 multi-bounds 导致结果不准确  
6, 因为每次输入_时出来的提示较多，所以建议在外部用 private val xx get()＝声明  
7, 用 get()= 不用 =，这样则不用关心其是否为 mutable  
8, 某些 property 会被忽略
9, 对于带泛型 / open / abstract class, 因为复用率高，不会从 property type trace, 对于会被多次构造的 class，应让 programmer
尽量少去探索次内部的东西