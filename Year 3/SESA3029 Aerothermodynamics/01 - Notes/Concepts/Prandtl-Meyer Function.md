---
title: "Prandtl-Meyer Function"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 2: Oblique Shocks and Expansions"
aliases: ["Prandtl–Meyer function", "Prandtl-Meyer angle", "nu(M)", "Prandtl-Meyer expansion"]
tags: [sesa3029, concept, prandtl-meyer, expansion]
status: complete
parent_lectures: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]"]
related_concepts: ["[[Expansion Fan]]", "[[Mach Waves and Mach Angle]]", "[[Shock-Expansion Theory]]"]
sources: ["02 - Sources/Lectures/Lecture2-4.pdf"]
---

# Prandtl-Meyer Function

## Definition

> [!note] Definition
> $$\nu(M)=\sqrt{\frac{\gamma+1}{\gamma-1}}\,\tan^{-1}\sqrt{\frac{\gamma-1}{\gamma+1}(M^2-1)}-\tan^{-1}\sqrt{M^2-1},$$
> the angle through which a sonic stream must be turned (expanded) isentropically to reach $M$.

## Explanation

**Derivation, in outline** (full version in W03 §5):

1. Tangential velocity is conserved across a Mach wave, which gives $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm dU/U$.
2. Adiabatic flow gives $\mathrm dU/U=\mathrm dM/[M(1+\tfrac{\gamma-1}{2}M^2)]$.
3. Integrate from $M=1$ with $t=\sqrt{M^2-1}$ and partial fractions.

**Use:**

$$
\nu(M_2)=\nu(M_1)+\theta
$$

for an expansion through $\theta$. Then get $p$, $T$ and $\rho$ from the isentropic ratios, since $p_0$ and $T_0$ are constant.

**Values** ($\gamma=1.4$):

| $M$ | 1.2 | 1.8 | 2 | 2.2 | 2.5 | 3 | 3.78 |
|---|---:|---:|---:|---:|---:|---:|---:|
| $\nu$ | $3.56^\circ$ | $20.73^\circ$ | $26.38^\circ$ | $31.73^\circ$ | $39.12^\circ$ | $49.76^\circ$ | $62.76^\circ$ |

$\nu_{max}=130.45^\circ$ as $M\to\infty$.

In the method of characteristics, $\theta\pm\nu$ are the **Riemann invariants** ([[SESA3029 Example Sheet 2 - Solutions#Q2. Characteristics and Riemann invariants|ES2 Q2]]).

![[at_prandtl_meyer_derivation.png|760]]

## Related

- [[Expansion Fan]] · [[Mach Waves and Mach Angle]] · [[Shock-Expansion Theory]]
- Detail: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#5. Expansion waves and the Prandtl–Meyer function|W03 §5]]
