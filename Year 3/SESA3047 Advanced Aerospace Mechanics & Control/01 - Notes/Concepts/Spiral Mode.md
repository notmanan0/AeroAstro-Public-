---
title: "Spiral Mode"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 6: Aircraft Flight Dynamics and Interpretation of Eigenvectors"
aliases: ["spiral", "slow spiral mode", "spiral divergence", "spiral convergence", "spiral stability"]
tags: [sesa3047, concept, lateral-dynamics, flight-dynamics, spiral]
status: complete
coverage: "Chapter 6 §§6.7.3 and 6.8, Eqs. 6.44–6.47 and 6.50–6.54, lectured in L20 (Thu 19 Nov)"
parent_lectures: ["[[SESA3047 6.3 - Lateral Modes and their Approximations]]"]
related_concepts: ["[[Roll Subsidence Mode]]", "[[Dutch Roll Mode]]", "[[Lateral and Directional Stability]]", "[[Separation of Time Scales]]"]
sources: ["02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf", "02 - Sources/Lectures/19 November 2026 at 16_00_12.txt"]
---

# Spiral Mode

The spiral mode is the slow, non-oscillatory lateral mode in which the bank angle $\phi$ creeps back to zero or slowly grows into a tightening, descending turn: a real eigenvalue very close to zero, with an eigenvector dominated by $\phi$.

After a disturbance has banked the aircraft and roll damping has stopped the roll rate, the tilted lift has a horizontal component that turns the aircraft towards the lower wing. A small sideslip develops; directional stability yaws the nose into the turn, while the dihedral effect, $\mathring L_vv$, tends to raise the lower wing. In the turn the outer wing moves faster, at $U_\infty-ry$, and makes more lift, rolling the aircraft further, which is $\mathring L_rr$ with $\mathring L_r>0$. If the dihedral wins, the wings level slowly; if the yaw-induced roll wins, greater bank gives a tighter turn, a larger yaw rate and more inward roll, a slow spiral divergence.

Because the mode is so slow, every other state is in balance at each instant and the aircraft flies a sequence of nearly steady turns with $r\approx g\phi/U_\infty$. Setting $\dot v=\dot p=\dot r=0$ and neglecting side forces gives

$$
\lambda_\text{sp}=-\frac{g}{U_\infty}\,\frac{L_vN_r-L_rN_v}{L_vN_p-L_pN_v},
$$

which holds at level trim with dimensional or non-dimensional derivatives alike. With the usual positive denominator, the spiral is stable when $L_vN_r>L_rN_v$: dihedral and yaw damping stabilise it, yaw-induced roll and directional stability destabilise it. The condition is exact in the full lateral model, because $\det\mathbf A'=mg(\mathring L_v\mathring N_r-\mathring L_r\mathring N_v)$ fixes the sign of the product of the eigenvalues. For the Navion the estimate is $-0.0097$ s⁻¹ against $-0.0087$ s⁻¹; raising its $N_v$ by 23 % would make the spiral unstable.

Many aircraft have a slightly unstable spiral. That is acceptable because the doubling time is typically a minute or more, leaving the pilot ample time to correct it.

## Related

- Mechanism, derivation and the $N_v$ trade: [[SESA3047 6.3 - Lateral Modes and their Approximations#7. The spiral mode (6.44–6.47)|6.3 §7]], [[SESA3047 6.3 - Lateral Modes and their Approximations#8. Spiral mode approximation (6.50–6.54)|§8]] and [[SESA3047 6.3 - Lateral Modes and their Approximations#Practice problem 4: stronger directional stability|§12]]
- [[Roll Subsidence Mode]] · [[Dutch Roll Mode]] · [[Lateral and Directional Stability]] · [[Separation of Time Scales]]
- Exam practice: [[SESA2025 Past Paper 2018-19 - Solutions#Q4. Lateral derivatives and the spiral mode (25 marks)|SESA2025 2018-19 Q4]]
