---
title: Notes
weight: 4
---

## Common
- `Kotlin Native` and `Kotlin JS` are not supported. Because they lack `context receiver` which is
  essential in this tool.

- Always inject like `prival val x get() = _X`. Just obey it which is confusing to tyros but 
  automatically understandable when you get familiar.

- `Tracer` is compatible with `ksp 1.7.0-1.0.6` at least. Although mostly it works well with
`ksp`, you'd better try to make your `ksp plugin` in a high stable version, since `ksp api` is not
stable and many bugs are fixed every version.

- Java files are forbidden to use `Tracer`, because I don't want to spend time analyzing those
outdated things. But it's absolutely safe to reference `java classes and functions` in kotlin files.     
<br>

## Rare  
{{< hint type=note >}}
Problems below are so unusual that you could read it later or when you get puzzled.
{{< /hint >}}

* Few generated types fail code inspection, mostly because of the imperfect authoritative type.
Use another source type or annotate them with `Tracer.Omit`. Unfortunately, I forget those rare 
cases which should be displayed here. 
---
* `*` in alias types are all shifted first and then converted, which, however, may be 
  **inaccurate**.  
  For source code
  ```kotlin
  interface A<T: Iterable<String>> 

  interface B<T: List<CharSequence>>

  typealias MyTypeAlias<T> = Pair<A<T>, B<T>>
  ```
  The real bound is `List<String>`, which is only one of those difficult cases. With `Tracer`, 
  `MyTypeAlias<*>` is converted to `Pair<A<*>, B<*>>` first, and 
  `Pair<A<out Iterable<String>>, B<out List<CharSequence>>>` next. 
---  
* Super types with compound args are not limited.  

  Source Code
  ```kotlin
  interface Sub<T> : Super<T>
    where T: Serializable, T: CharSequence
  
  interface Super<T>
  
  @Tracer.Root
  class CompoundTypeSample<T> : CompoundTypeSampleTracer
    where T: CharSequence, T: Serializable
  {
    val sub: Sub<T> = TODO()
  
    override val _CompoundTypeSample: CompoundTypeSample<*> = this
  }
  ```
  Generated code
  ```
    public val CompoundTypeSampleTracer.`_Sub‹↓‹Serializable，CharSequence››` 
      inline get() = `_CompoundTypeSample`.`sub` as Sub<*>
  
    public val CompoundTypeSampleTracer.`_Super‹↓‹Serializable，CharSequence››` 
      inline get() = `_CompoundTypeSample`.`sub` as Super<*>
  ```
  
  `*` in `Sub<*>` has two bounds, which, however, can't be expressed in `Super<*>`. 
