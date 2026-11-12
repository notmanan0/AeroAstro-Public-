---
title: "Skin-friction and Pressure Drag"
module: "SESA1016 Thermofluids"
type: concept
stream: "Viscous Flow"
aliases: ["friction drag", "form drag", "pressure drag"]
tags: [sesa1016, concept, drag]
status: complete
parent_lectures: ["[[SESA1016 T14 - Boundary Layers and the Origin of Drag]]"]
related_concepts: ["[[Boundary-layer Thickness Measures]]", "[[Pressure Coefficient]]", "[[Newtonian Fluid and Viscosity]]"]
sources: ["02 - Sources/Lectures/Chapter 14.pdf"]
---

# Skin-friction and Pressure Drag

The drag on a body has two parts: skin-friction drag, the streamwise resultant of the wall shear stress $\tau_w$ over the surface, and pressure (form) drag, the streamwise resultant of the pressure acting normal to the surface.

Both come from integrating the surface stresses. On each element of surface $dA$ the pressure force acts along the normal and the shear force along the surface, and the drag is the sum of their streamwise components over the whole body, $D=\int_A(-p\sin\theta+\tau\cos\theta)\,dA=D_p+D_v$ with $\theta$ the local surface angle as defined in T14. A thin flat plate aligned with the flow has only skin friction, since the pressure acts normal to the flow direction; a flat plate normal to the flow has only pressure drag.

Skin friction is governed by the boundary layer. A turbulent layer has a fuller profile and a steeper velocity gradient at the wall, so its $\tau_w$ and skin friction are several times the laminar value. The skin-friction coefficient is $c_f=\tau_w/(\tfrac12\rho V_\infty^2)$.

Pressure drag is caused by separation. On a bluff body such as a cylinder the boundary layer cannot climb the adverse pressure gradient on the rear, it separates, and the wake behind stays at low pressure instead of recovering the high pressure of the front. The front-to-back difference is the pressure drag, which dominates for bluff bodies. A turbulent boundary layer carries more momentum near the wall and separates later, giving a narrower wake; this is why the sphere's drag coefficient falls by a factor of about 5 at the drag crisis, and why golf balls are dimpled. Streamlining delays separation and trades a large pressure drag for a little extra skin friction.

![[tf_drag_separation.png|760]]

## Related

- [[SESA1016 T14 - Boundary Layers and the Origin of Drag#3. Wall shear stress and skin friction|skin friction]] · [[SESA1016 T14 - Boundary Layers and the Origin of Drag#7. Pressure drag|pressure drag]] · [[SESA1016 T14 - Boundary Layers and the Origin of Drag#Laminar and turbulent separation, and the drag crisis|drag crisis]] · [[SESA1016 T14 - Boundary Layers and the Origin of Drag#8. Calculating drag from surface data|drag from surface data]]
- [[Boundary-layer Thickness Measures]] · [[Pressure Coefficient]] · [[Newtonian Fluid and Viscosity]]
