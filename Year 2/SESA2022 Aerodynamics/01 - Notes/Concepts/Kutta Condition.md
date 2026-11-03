---
title: "Kutta Condition"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["Kutta condition", "smooth trailing-edge flow"]
tags: [sesa2022, concept, thin-aerofoil-theory]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Vortex Sheet]]", "[[Kelvin's Circulation Theorem]]", "[[Kutta-Joukowski Theorem]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-10-28.txt … 2025-11-05.txt (2025-26 transcripts)"]
---

# Kutta Condition

Potential flow round a sharp-trailing-edge aerofoil has a solution for every value of the circulation, and the Kutta condition picks the one in which the flow leaves the trailing edge smoothly. For a vortex sheet that means $\gamma(TE) = V_1-V_2 = 0$.

Inviscid theory on its own allows any circulation, but with the wrong $\Gamma$ the flow would have to wrap round the sharp trailing edge at infinite velocity, which viscosity doesn't allow. At a finite-angle trailing edge the condition makes the edge a stagnation point ($V_1 = V_2 = 0$); at a cusped one the two velocities are finite and equal. Either way $\gamma(TE) = 0$, and in the Fourier solution of thin aerofoil theory the $(1+\cos\theta)/\sin\theta$ form of the $A_0$ term is chosen precisely so that $\gamma\to0$ at $\theta = \pi$. Every thin-aerofoil question uses it implicitly ([[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]]).

The physical mechanism is the starting vortex. During start-up, viscous shear at the trailing edge sheds vorticity into the wake, and by [[Kelvin's Circulation Theorem]] an equal and opposite bound circulation appears on the aerofoil. The shedding stops once the flow leaves the trailing edge smoothly, which is exactly the Kutta condition.

## Related

- Full derivation and worked examples: [[SESA2022 T4 - Thin Aerofoil Theory#Kutta condition|T4 §2]]
- [[Vortex Sheet]] · [[Kelvin's Circulation Theorem]] · [[Kutta-Joukowski Theorem]]
