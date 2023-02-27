---
title: Annotations
weight: 1
---

Click them to expand
{{< expand "Root">}}
<img src=../../simpleHouse.png width=300/>

Each class annotated with `Tracer.Root` is considered as the trace start point. Its module-visible 
elements would be traced as below. 
{{< video src="root" >}}
{{< /expand >}}

{{< expand "Nodes">}}
Now we add one bedroom and some inner objects as below. Annotate`Bedroom` with 
`Tracer.Nodes(House::class)`, which makes `Bedroom`'s inner elements shared and connect with those 
inside `House` but outside `Bedroom`. 

<img src=../comprehensiveHouse.png />
<br><br>
{{< video src="nodes" >}}
<br><br>
{{< /expand >}}

{{< expand "Tips">}}
* Classes from other modules or Java are considered as foreigners. They wouldn't be 
explored inside, and you needn't to consider `Tracer.Nodes` for them.  
... other conditions
* Rebuilt classes without inner elements are cpm
{{< /expand >}}

{{< expand "Omit" >}}

{{< /expand >}}