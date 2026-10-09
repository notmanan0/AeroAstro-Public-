---
title: "Mach Waves and Mach Angle"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 2: Oblique Shocks and Expansions"
aliases: ["Mach wave", "Mach angle", "Mach cone", "zone of silence", "sonic boom"]
tags: [sesa3029, concept, mach-wave]
status: complete
parent_lectures: ["[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]"]
related_concepts: ["[[Speed of Sound and Mach Number]]", "[[Theta-Beta-Mach Relation]]"]
sources: ["02 - Sources/Lectures/Lecture2-1.pdf", "02 - Sources/Lectures/Lecture 2-1.txt"]
---

# Mach Waves and Mach Angle

## Definition

> [!note] Definition
> A **Mach wave** is an infinitely weak, isentropic pressure disturbance in a supersonic flow. It lies at the **Mach angle** to the local velocity:
> $$\boxed{\mu=\sin^{-1}\!\left(\frac1M\right)}.$$

## Derivation (moving sound source)

A source moving at $U=Ma$ emits a pulse. After time $t$, the pulse is a circle of radius $at$ centred on the point where it was emitted, which is now $Ut$ behind the source. The envelope of all such circles is tangent to each one, so

$$
\sin\mu=\frac{at}{Ut}=\frac1M.
$$

![[at_mach_waves.png|760]]

- $M<1$: the pulses stay ahead of the source. There is no envelope and sound reaches everywhere (with a Doppler shift).
- $M=1$: all pulses pass through the source together, giving a plane front (the sonic boom) and a **zone of silence** ahead.
- $M>1$: sound is heard only inside the **Mach cone** of half-angle $\mu$.

## Link to oblique shocks

Setting $\theta=0$ in the [[Theta-Beta-Mach Relation]] makes $M_1^2\sin^2\beta=1$, so $\beta=\mu$. A Mach wave is an oblique shock of vanishing strength, with $M_{n1}=M_1\sin\mu=1$ exactly. Abrupt turning produces shocks. **Gradual** turning produces a continuous family of Mach waves, the basis of expansion fans and the method of characteristics.

| $M$ | 1.1 | 1.5 | 2 | 3 | 5 |
|---|---:|---:|---:|---:|---:|
| $\mu$ | 65.4° | 41.8° | 30.0° | 19.5° | 11.5° |

## Related

- [[Speed of Sound and Mach Number]] · [[Theta-Beta-Mach Relation]] · [[Weak and Strong Oblique Shocks]]
- Detail: [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#7. Mach waves and the Mach angle|W02 §7]]
