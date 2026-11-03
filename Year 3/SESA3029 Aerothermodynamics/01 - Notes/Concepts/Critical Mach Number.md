---
title: "Critical Mach Number"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 4: High-speed aerodynamics"
aliases: ["critical Mach number", "M_crit", "Mcrit", "M_cr", "first critical Mach number", "critical pressure coefficient", "Cp,cr", "sonic pressure coefficient"]
tags: [sesa3029, concept, transonic, compressible-flow, aerofoil]
status: complete
parent_lectures: ["[[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]", "[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]"]
related_concepts: ["[[Prandtl-Glauert Transformation]]", "[[Drag Divergence]]", "[[Stagnation Properties]]"]
sources: ["02 - Sources/Lectures/Lecture4-2.pdf", "02 - Sources/Lectures/Lecture4-4.pdf"]
---

# Critical Mach Number

The critical Mach number $M_{crit}$ is the **free-stream** Mach number at which the local Mach number first reaches 1.0 at some point on the aerofoil surface (4.2 slide 7). Below it the flow is subsonic everywhere; above it a supersonic region forms on the surface and, before long, ends in a shock.

To estimate it, combine two relations at the point of minimum pressure, where the flow is fastest. The first is the isentropic pressure coefficient at which the local flow is sonic. It depends only on the free stream:

$$
C_{p,cr}=\frac{2}{\gamma M_\infty^2}\left[\left(\frac{1+\frac{\gamma-1}{2}M_\infty^2}{1+\frac{\gamma-1}{2}}\right)^{\gamma/(\gamma-1)}-1\right].
$$

The second is the aerofoil's own suction peak at that Mach number, here the Prandtl–Glauert-corrected incompressible value $C_{p0,min}/\sqrt{1-M_\infty^2}$. $M_{crit}$ is where the two are equal. The equation has no closed form; plot or tabulate both sides and find the crossing (4.4 slides 8–9).

For $C_{p0,min}=-0.4$ in air ($\gamma=1.4$), Prandtl–Glauert gives $M_{crit}=0.747$ and Kármán–Tsien gives $0.733$ (4.4 slides 9 and 11). A larger suction peak lowers it: $C_{p0,min}=-1.0$ gives 0.606, and Example Sheet 2 Q6's $-2.5$ gives 0.448. That is why high-subsonic aircraft use thin sections, flat-rooftop supercritical sections and wing sweep.

$M_{crit}$ is not the same as the drag-divergence Mach number. Drag starts to rise steeply somewhat above $M_{crit}$, once the shock terminating the supersonic region is strong enough ([[Drag Divergence]]).

![[at_critical_mach_number.png|760]]

## Related

- [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#8. Estimating the critical Mach number (4.4 slides 7–9)|W07b §8]] (derivation and worked example) · [[SESA3029 Example Sheet 2 - Solutions#Q6. Critical Mach number via Prandtl–Glauert|ES2 Q6]]
- [[Prandtl-Glauert Transformation]] · [[Drag Divergence]] · [[Stagnation Properties]]
