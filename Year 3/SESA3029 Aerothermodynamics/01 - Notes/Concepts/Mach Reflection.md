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

A **Mach reflection** replaces a regular reflection when the wall angle lies in the range $\theta_{max}(M_2)<\theta<\theta_{max}(M_1)$. The incident shock can still attach, but the slower flow behind it cannot be turned back parallel to the wall by an attached reflected shock.

Instead, the incident shock ends at a **triple point** T. A near-normal **Mach stem** runs from T down to the wall, a curved reflected shock leaves T, and a [[Slip Line]] trails downstream from it. The stem is normal where it meets the wall, so it turns the flow by zero and keeps it parallel to the wall; the flow behind it is subsonic. Across the slip line the pressure and flow direction match, but the entropy does not, because the gas below has been through one strong shock and the gas above through two weaker ones.

The regular-reflection limit comes from solving $\theta=\theta_{max}(M_2(\theta))$:

| $M_1$ | 1.6 | 2.0 | 2.3 | 3.0 | 3.6 | 5.0 |
|---|---:|---:|---:|---:|---:|---:|
| $\theta_{RR}$ | $7.6^\circ$ | $12.9^\circ$ | $16.1^\circ$ | $21.5^\circ$ | $24.3^\circ$ | $27.8^\circ$ |

The same failure of a regular shock crossing on the axis of an over-expanded axisymmetric jet produces a **Mach disc** (Lecture 2.7, slide 7).

![[at_mach_reflection.png|760]]

## Related

- [[Regular Shock Reflection]] · [[Slip Line]] · [[Over- and Under-Expanded Jets]]
- Detail: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#2. Mach reflection|W03 §2]]
