---
title: "Over- and Under-Expanded Jets"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 3: Nozzles and the Method of Characteristics"
aliases: ["over-expanded jet", "under-expanded jet", "shock diamonds", "Mach diamonds", "lip shock", "jet barrel"]
tags: [sesa3029, concept, nozzle, jet]
status: complete
parent_lectures: ["[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]"]
related_concepts: ["[[Converging-Diverging Nozzle Operating Regimes]]", "[[Slip Line]]", "[[Expansion Fan]]", "[[Mach Reflection]]"]
sources: ["02 - Sources/Lectures/Lecture2-7.pdf"]
---

# Over- and Under-Expanded Jets

## Definition

> [!note] Definition
> A supersonic nozzle is
> - **over-expanded** if its exit pressure is below ambient ($p_{b6}<p_b<p_{b5}$, so $p_e<p_\infty$);
> - **under-expanded** if it is above ambient ($p_b<p_{b6}$, so $p_e>p_\infty$).
>
> The jet adjusts to $p_\infty$ through waves at the nozzle lip, which then reflect from the constant-pressure jet boundary, giving **shock diamonds**.

## Explanation

**Over-expanded** cycle (Lecture 2.7, slides 3–4):

1. Lip **oblique shocks** recompress the jet to $p_\infty$, and the boundary turns inward.
2. The shocks cross, and the pressure rises above $p_\infty$.
3. They reflect from the boundary as **fans**.
4. The fans cross, and the pressure falls below $p_\infty$.
5. The fans reflect as compressions, and the cycle repeats.

**Under-expanded** (slides 5–6): the same cycle, starting with lip **fans**.

**Sizing the lip shock:**

$$
M_{n1}=\sqrt{1+\frac{\gamma+1}{2\gamma}\left(\frac{p_\infty}{p_e}-1\right)}.
$$

For $M_e=2.2$ and $p_b/p_0=0.2$: $\beta=39.7^\circ$, $\theta=13.7^\circ$, a regular crossing.

**Sizing the lip fan:** $\nu(M_j)-\nu(M_e)$, with $M_j$ set by $p_\infty/p_0$. For $p_b/p_0=0.05$ the turn is $9.7^\circ$.

**Mach disc:** if the lip-shock turn exceeds $\theta_{max}$ behind it, a Mach disc appears (planar estimate: $p_b/p_0>0.216$ for $M_e=2.2$). See [[Mach Reflection]].

![[at_nozzle_jets.png|760]]

## Related

- [[Converging-Diverging Nozzle Operating Regimes]] (SESA2023) · [[Slip Line]] · [[Expansion Fan]] · [[Mach Reflection]] · [[Afterburning (Reheat)]]
- Detail: [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#5. Over-expanded jets: lip shocks and shock diamonds (Lecture 2.7, slides 3–4)|W04 §5–6]]
