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
Now we add one bedroom and some inner objects as below. Annotate`Bedroom` with 
`Tracer.Nodes(House::class)`, which makes `Bedroom`'s inner elements shared and connect with those 
inside `House` but outside `Bedroom`. 

<img src=../comprehensiveHouse.png />
<br><br>
{{< video src="nodes" >}}