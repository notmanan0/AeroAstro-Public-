---
title: "Reynolds Analogy"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["Reynolds analogy", "Reynolds' analogy", "Chilton-Colburn analogy", "Chilton–Colburn analogy", "Colburn analogy", "St = cf/2"]
tags: [sesa3029, concept, heat-transfer, convection, boundary-layer, skin-friction]
status: complete
parent_lectures: ["[[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]"]
related_concepts: ["[[Stanton Number]]", "[[Nusselt Number]]", "[[Prandtl Number]]", "[[Thermal Boundary Layer]]", "[[Blasius and Falkner-Skan Similarity Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture5.3.pdf"]
---

# Reynolds Analogy

The Reynolds analogy links heat transfer to skin friction: on a flat plate with zero pressure gradient and $\mathrm{Pr}=1$, $\mathrm{St}=c_f/2$. In this module the name also covers the general correlation form $\mathrm{Nu}_x=C\,\mathrm{Re}_x^n\mathrm{Pr}^m$ that follows from it.

The basis is that the boundary-layer momentum equation, $uu_x+vu_y=\nu u_{yy}$, and the low-speed boundary-layer energy equation, $uT_x+vT_y=\alpha T_{yy}$, have the same form. In terms of $u^*=u/V$ and $T^*=(T-T_s)/(T_\infty-T_s)$ they also have the same boundary conditions (0 at the wall, 1 at the edge). When $\nu=\alpha$, that is $\mathrm{Pr}=1$, the solutions coincide, so the wall gradients are equal, and writing $c_f/2=(\mu/\rho V)\,\partial u^*/\partial y|_0$ and $\mathrm{St}=(k/\rho Vc_p)\,\partial T^*/\partial y|_0$ gives $\mathrm{St}/(c_f/2)=1/\mathrm{Pr}=1$.

For other Prandtl numbers the Chilton–Colburn form $\mathrm{St}\,\mathrm{Pr}^{2/3}=c_f/2$ ($0.6<\mathrm{Pr}<60$) corrects for the different layer thicknesses. With the Blasius $c_{f,x}=0.664\,\mathrm{Re}_x^{-1/2}$ it gives exactly the laminar correlation $\mathrm{Nu}_x=0.332\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}$; with the turbulent $c_{f,x}=0.0592\,\mathrm{Re}_x^{-1/5}$ it gives $\mathrm{Nu}_x=0.0296\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^{1/3}$. The exponent of Re in the correlation is set by the friction law and the $\mathrm{Pr}^{1/3}$ by the thickness ratio.

The analogy fails with a pressure gradient (the momentum equation gains a term the energy equation lacks; near separation $c_f\to0$ while heat transfer continues), for form drag, and at high speed, where frictional heating requires the recovery temperature.

![[at_w09b_reynolds_analogy.png|760]]

## Related

- Parent lectures: [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#7. The Reynolds analogy|W09b §7]]
- Related concepts: [[Stanton Number]] · [[Nusselt Number]] · [[Prandtl Number]] · [[Thermal Boundary Layer]] · [[Blasius and Falkner-Skan Similarity Solutions]] · [[Prandtl Boundary-Layer Equations]]

## Sources

- L5.3 slides 7–8 (the general form). The $\mathrm{St}=c_f/2$ derivation and the Chilton–Colburn form are standard (Çengel, *Heat Transfer*, external forced convection).
