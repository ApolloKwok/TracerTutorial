---
title: Annotations
weight: 1
---

Click them to expand.
{{< expand "Root">}}
<img src=../../simpleHouse.png width=300/>

Each class with `@Tracer.Root` is considered as the trace start point, followed by interior 
module-visible elements.  
<br>
{{< video src="root" >}}

{{< hint type=note >}}
An interior element wouldn't be traced insides if it's nullable or its type class is with `@Tracer.
Root`. As a qualified design, `Tracer.Root` classes are independent and avoid being explored too 
insides. 
{{< /hint >}}

{{< /expand >}}

{{< expand "Nodes">}}
Now we add one bedroom and some inner objects as below. Annotate `Bedroom` with 
`Tracer.Nodes(House::class)`, which makes `Bedroom`'s interior elements shared and connect with those 
inside `House` but outside `Bedroom`. 

<img src=../comprehensiveHouse.png />
<br><br>
{{< video src="nodes" >}}
{{< hint type=note >}}
An interior element wouldn't be traced insides if its type class is with `@Tracer.Nodes`.
If `Living room` needs the quilt from `master bedroom`'s`Bed`, use 
`_Bedroom_House_masterBedroom._Quilt`.
{{< /hint >}}

{{< /expand >}}

{{< expand "Tip">}}
`Tracer.Tip` represents the trace end, meaning elements of annotated classes wouldn't be traced 
insides. Furthermore, classes are considered as `Tracer.Tip` by default if they are from other 
modules or Java files, or with rebuilt symbols (type parameters, value parameters in the 
constructor, abstract or open). Like `Tracer.Root` classes, they should avoid being exploring too 
insides if qualified.

{{< columns size=small >}}
<img src=tip.png><---><img src=_tip.png>
{{< /columns >}}
{{< /expand >}}

{{< expand "Omit" >}}
Properties and super types with `@Tracer.Omit` would be omitted, which is generally used 
with some unsupported new syntaxes, e.g. `T & Any` before `ksp 1.8.0-1.0.9`(exclusive), 
and `context receiver`. Super type trace rules are later explained on page 
[Details](https://apollokwok.github.io//TracerTutorial/usage/details/#partial-super-types-are-traceable).   
<br> 
{{<video src="omit" >}}
{{< /expand >}}