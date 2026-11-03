---
title: "Drag Divergence"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 4: High-speed aerodynamics"
aliases: ["drag divergence", "drag rise", "transonic drag rise", "drag-divergence Mach number", "M_dd", "supercritical aerofoil", "supercritical section", "area rule", "Whitcomb area rule", "shock buffeting", "transonic buffet", "shock buffet"]
tags: [sesa3029, concept, transonic, wave-drag, aerofoil]
status: complete
parent_lectures: ["[[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]"]
related_concepts: ["[[Critical Mach Number]]", "[[Supersonic Wave Drag]]", "[[Shock-Expansion Theory]]"]
sources: ["02 - Sources/Lectures/Lecture4-2.pdf", "02 - Sources/Lectures/Lecture4-1.txt"]
---

# Drag Divergence

Drag divergence is the steep rise in an aerofoil's drag at transonic speed, a little above the [[Critical Mach Number|critical Mach number]], once a supersonic region and its terminating shock have formed on the surface (4.2 slides 13–15). In the 4.2 Euler CFD of a 12 % aerofoil at $\alpha=0.1$ rad the drag starts to rise near $M_\infty\approx0.6$, peaks in the transonic range and levels off for $M_\infty>1$.

The course explains it with the duct picture. The region between the upper surface and a nearby streamline acts as a converging–diverging duct. In subsonic flow the speed peaks at the crest and the pressure recovers behind it. Once the flow is sonic at the crest, the diverging part behind it **accelerates** the supersonic flow ($\mathrm dA/A=(M^2-1)\,\mathrm dU/U$), so the pressure keeps falling until a shock jumps it back up. That extra suction acts on the backward-facing part of the surface and pulls the aerofoil rearwards: *"suction force in the drag direction"*. It also adds lift, which gives the transonic lift peak.

There are three ways to delay or reduce it (4.2 slides 16–17). A supercritical (flat-rooftop) section weakens the shock. Wing sweep lowers the Mach number the section sees to $M_\infty\cos\Lambda$ (the slide writes the sweep angle as $\beta$). And the area rule keeps the aircraft's total cross-sectional area smooth along its length.

Shocks on a transonic wing need not be steady. In shock buffeting they move back and forth, lift and drag fluctuate, and the wing vibrates (L4-1, ll. 224–232).

![[at_drag_divergence_cp.png|760]]

## Related

- [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#8. Lift, drag and the mechanism of drag divergence (4.2 slides 13–15)|W07a §§8–9]]
- [[Critical Mach Number]] · [[Supersonic Wave Drag]] · [[Shock-Expansion Theory]]
