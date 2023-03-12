---
title: Expected optimization
weight: 8
---

`Tracer` is not perfect, but can be much optimized if the `IDE` and `Kotlin plugin` cooperate. 

1, Too many hints when you input Root/Nodes carrier and `.`

<img src=elements.png/>

(after the visibility, of functions with context receivers, is fixed -> new generated tracer
property would replace the receiver with context receiver. Then there wouldn't be redundant
hints.)

2, names may change with the structure.  
-> 新的变更名字模式，实际值为 contractedName_packageName(_levelTag)_containerName_propertyName。
根据当前的实际需要来显示。且后台给每个 context 分配出一套提示

3, 针对 property 重写问题，如
```kotlin
@Tracer.Root
class X : XTracer{
    abstract val j: J  
} 

@Tracer.Root
class XImpl : X(), XImplTracer{
    override val j: J = J()
}
```
结合2，如果有重写，则父类相应的 `val XTracer.j inline get() = ...` 不对 XImplTracer 可见

4, Implement tracer interfaces automatically.

5, Override and solve the conflict automatically.

6, 生成结构图

7, Let android lift restriction on property names.

8. incremental processing after `aware of generated code` is supported
    1. check name conflict of all files after `getAllFiles(truly: Boolean)` is supported