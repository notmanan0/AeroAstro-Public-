---
title: "Supersonic Wave Drag"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 4: High-speed aerodynamics"
aliases: ["wave drag", "supersonic wave drag", "wave drag due to lift", "wave drag due to thickness", "diamond aerofoil", "diamond shaped aerofoil", "double-wedge aerofoil", "faceted aerofoil", "optimum supersonic aerofoil"]
tags: [sesa3029, concept, supersonic, wave-drag, aerofoil-design]
status: complete
parent_lectures: ["[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]"]
related_concepts: ["[[Ackeret Theory]]", "[[Shock-Expansion Theory]]", "[[Drag Divergence]]"]
sources: ["02 - Sources/Lectures/Lecture4-6.pdf", "02 - Sources/Lectures/Lecture2-5.pdf"]
---

# Supersonic Wave Drag

Wave drag is the drag an inviscid supersonic flow exerts on a body through the pressure changes in its shock and expansion waves. It exists with no boundary layer at all. At supersonic speed there is no leading-edge suction to cancel the rearward component of the pressure forces, as there is in subsonic flow (W03 §6).

Ackeret theory splits the wave drag of a thin aerofoil into three positive parts (4.6 slide 6):

$$
C_d=\frac{4}{\sqrt{M_\infty^2-1}}\left[\alpha^2+\frac1c\int_0^c\left(\frac{\mathrm dh}{\mathrm dx}\right)^2\mathrm dx+\frac1c\int_0^c\left(\frac{\mathrm dy_c}{\mathrm dx}\right)^2\mathrm dx\right],
$$

drag due to lift (incidence), drag due to thickness and drag due to camber. Camber adds drag but no lift, so supersonic sections are symmetric. Among symmetric sections of thickness $t$, the thickness integral is smallest for straight (faceted) faces meeting at mid-chord: the diamond, with $\int_0^c h'^2\,\mathrm dx=t^2/c$ (4.6 slides 7–9). A biconvex section has $4/3$ of this. For the diamond,

$$
C_d=\frac{4}{\sqrt{M_\infty^2-1}}\left[\alpha^2+\left(\frac tc\right)^2\right],\qquad
\left(\frac LD\right)_{max}=\frac{1}{2\,t/c}\ \text{ at }\ \alpha=\frac tc ,
$$

where the drag due to lift equals the drag due to thickness. At that angle the upper front face is aligned with the free stream.

At transonic speed the wave drag appears first as [[Drag Divergence|drag divergence]]. For a whole aircraft, the area rule reduces it by keeping the cross-sectional area distribution smooth.

![[at_thickness_drag.png|760]]

## Related

- [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#8. Drag coefficient (4.6 slide 6)|W07c §§8–10]] · [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#Diamond aerofoil|W03, diamond aerofoil]]
- [[Ackeret Theory]] · [[Shock-Expansion Theory]] · [[Drag Divergence]]
