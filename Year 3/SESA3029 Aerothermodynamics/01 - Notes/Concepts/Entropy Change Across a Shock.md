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

## Definition

> [!note] Result
> With $m=M_{n1}^2-1$:
> $$\frac{s_2-s_1}{c_v}=\ln\left(1+\frac{2\gamma}{\gamma+1}m\right)-\gamma\ln(1+m)+\gamma\ln\left(1+\frac{\gamma-1}{\gamma+1}m\right)\approx\frac{2\gamma(\gamma-1)}{3(\gamma+1)^2}m^3.$$

## Explanation

- It depends on $M_{n1}$ alone, so it is the same for normal and oblique shocks.
- Its derivative is
  $$\frac{\mathrm d}{\mathrm dm}\left(\frac{\Delta s}{c_v}\right)=\frac{2\gamma(\gamma-1)m^2}{(1+m)(\gamma+1+2\gamma m)(\gamma+1+(\gamma-1)m)}\ge0.$$
  So $\mathrm ds/\mathrm dM_{n1}=0$ at $M_{n1}=1$. This is the "show it" on Lecture 2.3, slide 9.
- $\Delta s<0$ for $M_{n1}<1$, so **expansion shocks are impossible** (second law). Expansions must happen through isentropic fans.
- The third-order contact means **weak shocks are nearly isentropic**. Halving the strength cuts the loss by 8, which is why intakes use several weak shocks.
- Link to stagnation pressure: $p_{02}/p_{01}=e^{-\Delta s/R}$. At $M=2$, $\Delta s=93.9$ J/kg K and $p_{02}/p_{01}=0.721$ ✓.

![[at_entropy_jump.png|760]]

## Related

- [[Normal-Shock Jump Relations]] · [[Oblique-Shock Jump Relations]] · [[Intake Pressure Recovery]]
- Full derivation: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#4. Entropy across a shock and why shocks compress|W03 §4]]
