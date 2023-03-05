---
title: Property naming rules
weight: 2
---

## Type symbols   
  `suspend (MutableMap<in String, out CharSequence>) -> Comparable<*>?` would be converted to
  `⍒❨MutableMap‹↑String，↓CharSequence›❩-›Comparable‹✶›？`.
  Unfortunately, android forbids most original common symbols in property names, making me choose
  these substitutes `⍒` `❨` `❩` `-›` `‹` `›` `？` `，` `✶` `↑` `↓`.

  Wildcard `*` would be tried converting to its bound with the covariance if needed, like from
  from `Array<*>` to `Array‹↓Any？›` and `List<*>` to `List‹Any？›`. `Comparable<*>` is not
  convertible because its source code is `Comparable<in T>`.  
<br>
## Generic type
  ### Single bound
   {{< columns size=small >}}
   ![](generic(1).png)<--->![](_generic(1).png)
   {{< /columns >}}
  
  ### Multiple bounds
   {{< columns size=small >}}
   ![](generic(2).png) <---> ![](_generic(2).png)
   {{< /columns >}}
  
  ### Covariance(↓) may be needed.
   {{< columns size=small >}}
   ![](generic(3).png) <---> ![](_generic(3).png)
   {{< /columns >}}

## Type symbols   
  `suspend (MutableMap<in String, out CharSequence>) -> Comparable<*>?` would be converted to 
  `⍒❨MutableMap‹↑String，↓CharSequence›❩-›Comparable‹✶›？`.
  Unfortunately, android forbids most original common symbols in property names, making me choose 
  these substitutes `⍒` `❨` `❩` `-›` `‹` `›` `？` `，` `✶` `↑` `↓`.
  
  Wildcard `*` would be tried converting to its bound with the covariance if needed, like from
  from `Array<*>` to `Array‹↓Any？›` and `List<*>` to `List‹Any？›`. `Comparable<*>` is not 
  convertible because its source code is `Comparable<in T>`.
---

* **Generic type**  
  
  1. single bound
  {{< columns size=small >}}
  ![](generic(1).png)<--->![](_generic(1).png)
  {{< /columns >}}  
  ---
  2. multiple bounds
  {{< columns size=small >}}
  ![](generic(2).png) <---> ![](_generic(2).png)
  {{< /columns >}}
  ---
  3. `↓` (covariance) may be needed.
  {{< columns size=small >}}
  ![](generic(3).png) <---> ![](_generic(3).png)
  {{< /columns >}} 
---
* **Position qualifier**
  1. `__` : beginning with double `_` tells it's from outside. See
     [Annotations.Nodes](https://apollokwok.github.io/TracerTutorial/usage/annotations/nodes.mp4) if
     you forget other code.
     <img src="../comprehensiveHouse.png" height=220/>  
     <img src=underline.png width=300/>
  ---
  2. `˚`: as shown in the image above, `˚House` means that `House` is the nearest owner with
     `@Tracer.Root` or `Tracer.Nodes` of that `WifiRouter`. I consider this as level tag.
  ---
  3. Same types would be traced with `owner name` or `property name` further to be 
    distinguished. There would be `by` inside if one same type is super and from the trace start point. 
  {{< columns size=small >}}
  ![](foo.png)<--->![](_foo.png)
  {{< /columns >}} 
  ---
  4. `nullability` `suspend` `generic name` and `variance` are omitted in type equality 
  comparison to hint better. 
  {{< columns size=small >}}
  ![](lambda.png)<--->![](lambda(1).png) 
  {{< /columns >}}
  <img src=_lambda.png /> 
  ---
  5. Elements of common types or common types embedded in common containers are always traced with 
     `owner name` and `property name` to be clear like `_String_X_name`.

     **Common types**      
       `String` `Any` `Short` `ShortArray` `UShort` `UShortArray` `Int` `IntArray` `UInt` `UIntArray`    
       `Long` `LongArray` `ULong` `ULongArray` `Byte` `ByteArray` `UByte` `UByteArray`     
       `Float` `FloatArray` `Double` `DoubleArray` `Boolean` `BooleanArray` `Char` `CharArray`      
   
     **Common containers**  
       `Pair` `Triple` `Array` `Sequence`    
       `Iterable` `Collection` `List` `Set` `Map`    
       `MutableIterable` `MutableCollection` `MutableList` `MutableSet` `MutableMap`    
     
     **Example**    
     ![](common.png)![](_common.png)