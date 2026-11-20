---
title: "Lanchester's Phugoid Approximation"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 6: Aircraft Flight Dynamics and Interpretation of Eigenvectors"
aliases: ["Lanchester approximation", "Lanchester's approximation", "constant-energy phugoid approximation", "phugoid energy approximation"]
tags: [sesa3047, concept, phugoid, flight-dynamics, energy]
status: complete
coverage: "Chapter 6 §6.6, Eqs. 6.28–6.33, lectured in L18 (Mon 16 Nov)"
parent_lectures: ["[[SESA3047 6.2 - Phugoid Approximation]]"]
related_concepts: ["[[Phugoid Mode]]", "[[Separation of Time Scales]]", "[[Damping Ratio and Natural Frequency]]"]
sources: ["02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf", "02 - Sources/Lectures/16 November 2026 at 11_51_48.txt"]
---

# Lanchester's Phugoid Approximation

Lanchester's phugoid approximation models the phugoid as a loss-free exchange of kinetic and potential energy at constant lift coefficient, which gives $\ddot h+(2g^2/U_\infty^2)h=0$: an undamped oscillation with $\omega_n=\sqrt2\,g/U_\infty$.

It rests on four assumptions: total energy constant (thrust balances drag, nothing dissipated), $\alpha$ and $C_L$ fixed at their trim values, the lift acting vertically (a shallow flight path), and $h$ measured from the trim height where the speed is $U_\infty$. Energy conservation gives $U^2=U_\infty^2-2gh$, so at fixed $C_L$ the lift is $L=mg-\rho SC_Lgh$, exactly linear in height. Newton's law $m\ddot h=L-mg$ with the trim $C_L=mg/(\tfrac12\rho U_\infty^2S)$ then gives the oscillator. The period, $T=\sqrt2\,\pi U_\infty/g$, depends only on the trim speed.

The same energy balance fixes the mode shape. To first order $u=-gh/U_\infty$, so speed is in antiphase with height, and the flight-path angle $\gamma\approx\dot h/U_\infty$ has amplitude $\sqrt2\,|u|/U_\infty$ and leads $h$ by a quarter cycle. At constant $\alpha$ the pitch attitude moves with $\gamma$.

The frequency is usually close: 0.0779 rad/s for the F-4C at 178 m/s against 0.0781 rad/s from the full model. The damping is lost by construction, because the change of drag with speed is what damps a real phugoid, so the approximation cannot say whether the mode is stable. It is the special case $\mathring M_u=0$, $\mathring Z_u=-2mg/U_\infty$ of the improved approximation, Eq. 6.38. It can still be well off: about 11 % high for the SESA2025 2013-14 aircraft (0.231 against 0.208 rad/s). The cause there is the pitch-damping term $\mathring M_qq$, which both approximations drop. Eq. 6.38 is no better for that aircraft, at 0.277 rad/s, and keeping $\mathring M_q$ in the moment balance recovers 0.208 rad/s.

## Related

- Derivation, mode shape and F-4C numbers: [[SESA3047 6.2 - Phugoid Approximation#2. Lanchester's approximation (6.28–6.33)|6.2 §2]]
- [[Phugoid Mode]] · [[Separation of Time Scales]] · [[Damping Ratio and Natural Frequency]] · [[Aerodynamic Stability Derivatives]]
- Exam practice: [[SESA2025 Past Paper 2013-14 - Solutions#Q3. Longitudinal modes, SPO approximation and Lanchester's phugoid (25 marks)|SESA2025 2013-14 Q3]]
