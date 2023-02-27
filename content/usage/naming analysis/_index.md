---
title: Property naming analysis
weight: 2
---

* `__`: beginning with double `_` tells it's from outside like getting `WifiRouter` as below.  
  <img src=outside.png width=500/>
---

* `˚`: as shown in the image above, `˚House` means that `House` is the nearest owner annotated
  with `Tracer.Root` or `Tracer.Nodes` of that `WifiRouter`.
---

* `suspend () -> Pair<Pillow, Pillow>?` would be converted to `⍒❨❩-›Pair‹Pillow，Pillow›？`.
  (suspend) lambda, generic type and nullability are all supported. Unfortunately, android forbids
  most original common symbols in property names, making me choose these substitutes 
 `⍒` `❨` `❩` `-›` `‹` `›` `？`.
---

* `↑` `↓`. `↑` represent `in`, `↓` represent `out`. `Array<in House>` is converted to
  `Array‹↑House›`
---

* As shown below, there are 3 houses inside `X`, making their corresponding generated property
  names different. `nullability` `suspend` and `variance` are omitted in type equality comparison.

  {{< columns size=small >}}
  ![](x.png)<--->![](y.png)
  {{< /columns >}}
  <img src=xyElements.png />
---

* Generic type with a single bound
  {{< columns size=small >}}
  ![](generic.png)<--->![](_generic.png)
  {{< /columns >}}
---

* Generic type with multiple bounds
  {{< columns size=small >}}
  ![](compound.png) <---> ![](_compound.png)
  {{< /columns >}} 