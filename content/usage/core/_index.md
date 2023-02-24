---
title: Core
weight: 1
---

## Root
{{< video src="core usage" >}}

{{< hint type=tip title="Traceable elements are module-visible and have no receivers" >}}
{{< /hint >}}

## Nodes
Now we add one bedroom and some inner objects as below. Bedroom is rebuilt under `HouseTracer`, in 
the same module with `House`, and has traceable elements, so it needs annotated with 
`Tracer.Nodes(House::class)`.



