---
title: "Darcy Friction Factor"
module: "SESA1016 Thermofluids"
type: concept
stream: "Internal Flow"
aliases: ["Darcy-Weisbach friction factor", "pipe friction factor"]
tags: [sesa1016, concept, pipe-flow]
status: complete
parent_lectures: ["[[SESA1016 T15 - Flow in Conduits]]"]
related_concepts: ["[[Major and Minor Head Losses]]", "[[Reynolds Number]]", "[[Pressure and Head]]"]
sources: ["02 - Sources/Lectures/Chapter 15.pdf"]
---

# Darcy Friction Factor

The Darcy friction factor $f$ is the dimensionless pressure drop of fully developed pipe flow per diameter of length, defined by $\Delta p=f\,\dfrac LD\,\tfrac12\rho\bar V^2$.

In fully developed flow the pressure gradient balances the wall shear, $\partial p/\partial x=-2\tau_w/R=-4\tau_w/D$, so $f$ is a dimensionless wall shear stress, $f=8\tau_w/(\rho\bar V^2)$. Dimensional analysis gives $f=f(Re_D,\epsilon/D)$, with $Re_D=\bar VD/\nu$ and $\epsilon$ the equivalent sand-grain roughness.

In laminar flow ($Re_D<2000$) the Poiseuille solution gives $f=64/Re_D$ exactly, independent of roughness. In turbulent flow $f$ comes from experiment, summarised by Colebrook's implicit equation and drawn as the Moody chart:

$$
\frac1{\sqrt f}=-2\log_{10}\left(\frac{\epsilon/D}{3.7}+\frac{2.51}{Re_D\sqrt f}\right)\qquad(Re_D>4000)
$$

At moderate $Re_D$ a rough pipe behaves as if smooth, because the roughness is buried in the viscous layer at the wall; at high $Re_D$ the curves flatten and $f$ depends on $\epsilon/D$ alone (fully rough). Solving Colebrook needs iteration, which converges in two or three steps from $f=0.02$.

Some texts use the Fanning factor $f_F=\tau_w/(\tfrac12\rho\bar V^2)=f/4$; the Darcy factor is used throughout here, and mixing the two is a factor-of-four error.

![[tf_moody_chart.png|760]]

## Related

- [[SESA1016 T15 - Flow in Conduits#6. The friction factor|T15 §6]] · [[SESA1016 T15 - Flow in Conduits#Turbulent flow and roughness|Colebrook and roughness]] · [[SESA1016 T15 - Flow in Conduits#Worked example - fuel line, a type 2 problem|type 2 iteration]]
- [[Major and Minor Head Losses]] · [[Reynolds Number]] · [[Pressure and Head]]
