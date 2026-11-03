---
title: "Entropy Change Across a Shock"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 2: Oblique Shocks and Expansions"
aliases: ["shock entropy rise", "expansion shock impossible", "weak shocks are isentropic", "entropy jump"]
tags: [sesa3029, concept, entropy, normal-shock]
status: complete
parent_lectures: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]"]
related_concepts: ["[[Normal-Shock Jump Relations]]", "[[Oblique-Shock Jump Relations]]", "[[Mach Waves and Mach Angle]]"]
sources: ["02 - Sources/Lectures/Lecture2-3.pdf"]
---

# Entropy Change Across a Shock

Writing $m=M_{n1}^2-1$ for the shock strength, the entropy jump across a shock is

$$\frac{s_2-s_1}{c_v}=\ln\left(1+\frac{2\gamma}{\gamma+1}m\right)-\gamma\ln(1+m)+\gamma\ln\left(1+\frac{\gamma-1}{\gamma+1}m\right)\approx\frac{2\gamma(\gamma-1)}{3(\gamma+1)^2}m^3.$$

It depends on $M_{n1}$ alone, so the same expression covers normal and oblique shocks.

Differentiating with respect to $m$ gives

$$\frac{\mathrm d}{\mathrm dm}\left(\frac{\Delta s}{c_v}\right)=\frac{2\gamma(\gamma-1)m^2}{(1+m)(\gamma+1+2\gamma m)(\gamma+1+(\gamma-1)m)}\ge0,$$

so $\mathrm ds/\mathrm dM_{n1}=0$ at $M_{n1}=1$. This is the "show it" on Lecture 2.3, slide 9.

Two consequences follow. For $M_{n1}<1$ the jump would be negative, which the second law forbids, so expansion shocks cannot exist and a supersonic stream has to expand through an isentropic fan instead. And because the jump grows like $m^3$, weak shocks are very nearly isentropic: halving the strength cuts the loss by a factor of eight. That is why intakes compress through several weak shocks rather than one strong one.

The entropy jump sets the stagnation-pressure loss through $p_{02}/p_{01}=e^{-\Delta s/R}$. At $M=2$, $\Delta s=93.9$ J/kg K and $p_{02}/p_{01}=0.721$, matching the normal-shock table.

![[at_entropy_jump.png|760]]

## Related

- [[Normal-Shock Jump Relations]] · [[Oblique-Shock Jump Relations]] · [[Intake Pressure Recovery]]
- Full derivation: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#4. Entropy across a shock and why shocks compress|W03 §4]]
