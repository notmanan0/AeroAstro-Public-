---
title: "Mach Reflection"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 2: Oblique Shocks and Expansions"
aliases: ["Mach stem", "triple point", "Mach disc", "Mach disk"]
tags: [sesa3029, concept, shock-reflection]
status: complete
parent_lectures: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]"]
related_concepts: ["[[Regular Shock Reflection]]", "[[Slip Line]]", "[[Over- and Under-Expanded Jets]]"]
sources: ["02 - Sources/Lectures/Lecture2-3.pdf", "02 - Sources/Lectures/Lecture2-7.pdf"]
---

# Mach Reflection

## Definition

> [!note] Definition
> A **Mach reflection** forms when the wall angle satisfies $\theta_{max}(M_2)<\theta<\theta_{max}(M_1)$. The incident shock is attached, but no attached reflected shock could turn the flow back. Its structure:
> - the incident shock ends at a **triple point** T;
> - a near-normal **Mach stem** runs from T to the wall;
> - a curved reflected shock leaves T;
> - a [[Slip Line]] trails from T.

## Explanation

- The Mach stem is normal at the wall, so it turns the flow by zero and keeps it parallel to the wall. Behind it the flow is subsonic.
- Above and below the slip line the pressure and direction match, but the entropy differs: the stem is strong, while the incident-plus-reflected pair is two weaker shocks.
- Regular-reflection limit, from solving $\theta=\theta_{max}(M_2(\theta))$:

| $M_1$ | 1.6 | 2.0 | 2.3 | 3.0 | 3.6 | 5.0 |
|---|---:|---:|---:|---:|---:|---:|
| $\theta_{RR}$ | $7.6^\circ$ | $12.9^\circ$ | $16.1^\circ$ | $21.5^\circ$ | $24.3^\circ$ | $27.8^\circ$ |

- In axisymmetric over-expanded jets, the same failure of a regular shock crossing produces a **Mach disc** (Lecture 2.7, slide 7).

![[at_mach_reflection.png|760]]

## Related

- [[Regular Shock Reflection]] · [[Slip Line]] · [[Over- and Under-Expanded Jets]]
- Detail: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#2. Mach reflection|W03 §2]]
