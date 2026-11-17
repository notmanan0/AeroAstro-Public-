---
title: "Windmill Brake State"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["windmill state", "windmill-brake state", "windmilling rotor"]
tags: [sesa3043, concept, rotor, descent]
status: complete
parent_lectures: ["[[SESA3043 4.2 - Rotor in Axial Flight]]"]
related_concepts: ["[[Rotor Working States in Axial Flight]]", "[[Induced Velocity in Axial Flight]]", "[[Vortex Ring State]]", "[[Autorotation]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Windmill Brake State

The windmill brake state is the flow of a rotor in fast axial descent, $V_D\geq2v_0$, in which the air flows up through the disc everywhere and the rotor slows it down, extracting power like a windmill.

The relative flow comes up from below at $V_D$, is slowed to $V_D-v_i$ at the disc and to $V_D-2v_i$ in the wake above. Bernoulli and the momentum balance give $T=\rho A(V_D-v_i)\,2v_i$, i.e. $\bar v_i^2-\bar V_D\bar v_i+1=0$. Its roots are real only for $\bar V_D\geq2$; both are positive, and the physical one is

$$
\bar v_i=\frac{\bar V_D}{2}-\sqrt{\frac{\bar V_D^2}{4}-1},
$$

because the larger root would make the wake velocity $V_D-2v_i$ negative, reversing the flow at one end of the streamtube. At $\bar V_D=2$ the wake is brought to rest and $\bar v_i=1$; at large $\bar V_D$, $\bar v_i\approx1/\bar V_D$.

The power, $P=T(-V_D+v_i)$, is always negative here, at most $-Tv_0$: the air drives the rotor. For the Lynx at 5330 kg descending vertically at 30 m/s ($\bar V_D=2.33$), $v_i=7.30$ m/s and the rotor extracts about 1.19 MW ([[SESA3043 4.2 - Rotor in Axial Flight#Example 2: Lynx descending vertically at 30 m/s|4.2, Example 2]]).

## Related

- Parent lecture: [[SESA3043 4.2 - Rotor in Axial Flight]]
- Related concepts: [[Rotor Working States in Axial Flight]] · [[Induced Velocity in Axial Flight]] · [[Vortex Ring State]] · [[Autorotation]]

## Sources

- Sources: CH4 Rotor Aerodynamics, slides 48–53, 58, 63–65.
- Notes: written ahead from the slides, 17 Nov 2026.
