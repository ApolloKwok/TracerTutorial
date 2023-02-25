---
title: Core
weight: 1
---

## Root
<img src=../../simpleHouse.png width=300/>

Each class annotated with `Tracer.Root` and considered as the tracing start point. Its module-visible 
elements would be traced as below. 
{{< video src="root" >}}

<br><br>
## Nodes
<img src=comprehensiveHouse.png />  

Now we add one bedroom and some inner objects as below. Bedroom is rebuilt under `HouseTracer`, in 
the same module with `House`, and has traceable elements, so it needs annotated with `Tracer.Nodes(House::class)`.
{{< video src="nodes" >}}