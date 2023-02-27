---
title: Core
weight: 1
---

## Root
<img src=../../simpleHouse.png width=300/>

Each class annotated with `Tracer.Root` is considered as the trace start point. Its module-visible 
elements would be traced as below. 
{{< video src="root" >}}

<br><br>
## Nodes
Now we add one bedroom and some inner objects as below. If each bedroom is explored from `House`, 
there would be two windows, two beds and ... everywhere. This could be solved by annotating 
`Bedroom` with `Tracer.Nodes(House::class)`, which makes its inner elements shared and connect 
with those inside `House` but outside `Bedroom`. If you are in `Living room` and need 
`master bedroom`'s `Quilt`, reference it like `_Bedroom_House_masterBedroom._Quilt`.

<img src=../comprehensiveHouse.png />
<br><br>
{{< video src="nodes" >}}