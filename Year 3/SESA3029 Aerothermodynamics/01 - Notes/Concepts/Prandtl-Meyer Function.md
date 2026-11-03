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

The Prandtl–Meyer function $\nu(M)$ is the angle through which a sonic stream has to be turned, expanding isentropically, to reach Mach number $M$:

$$\nu(M)=\sqrt{\frac{\gamma+1}{\gamma-1}}\,\tan^{-1}\sqrt{\frac{\gamma-1}{\gamma+1}(M^2-1)}-\tan^{-1}\sqrt{M^2-1}.$$

It comes from following the flow through one Mach wave at a time (full version in W03 §5). Conserving the tangential velocity across a Mach wave gives $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm dU/U$. For adiabatic flow $\mathrm dU/U=\mathrm dM/[M(1+\tfrac{\gamma-1}{2}M^2)]$, and integrating from $M=1$ with the substitution $t=\sqrt{M^2-1}$ and partial fractions gives the expression above.

For an expansion through $\theta$,

$$
\nu(M_2)=\nu(M_1)+\theta,
$$

and since $p_0$ and $T_0$ are constant through the fan, $p$, $T$ and $\rho$ follow from the isentropic ratios.

| $M$ ($\gamma=1.4$) | 1.2 | 1.8 | 2 | 2.2 | 2.5 | 3 | 3.78 |
|---|---:|---:|---:|---:|---:|---:|---:|
| $\nu$ | $3.56^\circ$ | $20.73^\circ$ | $26.38^\circ$ | $31.73^\circ$ | $39.12^\circ$ | $49.76^\circ$ | $62.76^\circ$ |

As $M\to\infty$, $\nu\to\nu_{max}=90^\circ\left(\sqrt{(\gamma+1)/(\gamma-1)}-1\right)$. That is $130.45^\circ$ for $\gamma=1.4$, but $163.3^\circ$ for the CO₂ ($\gamma=1.289$) in the MoC coursework.

In the [[Method of Characteristics]], $\nu$ is half of each [[Riemann Invariants|Riemann invariant]]: $R^+=\nu-\theta$ is constant along $C^+$ and $R^-=\nu+\theta$ along $C^-$ (Lecture 3.1; [[SESA3029 W05a - Method of Characteristics#7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)|W05a §7]]; Anderson writes $K^\pm=\theta\mp\nu$). A Prandtl–Meyer fan is a simple flow region with one invariant uniform throughout, and $\nu(M_2)=\nu(M_1)+\theta$ is just that statement. Practice: [[SESA3029 Example Sheet 2 - Solutions#Q2. Characteristics and Riemann invariants|ES2 Q2]].

![[at_prandtl_meyer_function.png|760]]

## Related

- [[Expansion Fan]] · [[Mach Waves and Mach Angle]] · [[Shock-Expansion Theory]]
- Detail: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#5. Expansion waves and the Prandtl–Meyer function|W03 §5]]
