---
title: "Dutch Roll Mode"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 6: Aircraft Flight Dynamics and Interpretation of Eigenvectors"
aliases: ["Dutch roll", "Dutch mode", "Dutch-roll oscillation", "lateral-directional oscillation"]
tags: [sesa3047, concept, lateral-dynamics, flight-dynamics, dutch-roll, yaw-damper]
status: complete
coverage: "Chapter 6 §§6.7.4 and 6.9, Eqs. 6.48–6.49 and 6.55–6.58; the mechanism lectured in L20 (Thu 19 Nov), the approximation handout only"
parent_lectures: ["[[SESA3047 6.3 - Lateral Modes and their Approximations]]"]
related_concepts: ["[[Roll Subsidence Mode]]", "[[Spiral Mode]]", "[[Lateral and Directional Stability]]", "[[Damping Ratio and Natural Frequency]]"]
sources: ["02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf", "02 - Sources/Lectures/19 November 2026 at 15_02_48.txt", "02 - Sources/Lectures/19 November 2026 at 16_00_12.txt"]
---

# Dutch Roll Mode

The Dutch roll is the oscillatory lateral mode: a lightly damped complex pair of eigenvalues in which sideslip, yaw and roll oscillate together, the nose swinging from side to side about the flight path while the wings rock.

A sideslip makes the fin produce a restoring yawing moment, $\mathring N_vv$ with $\mathring N_v>0$, that turns the nose back towards the relative wind. Yaw inertia carries the nose past alignment, the sideslip reverses, the moment reverses, and the overshoot repeats; yaw damping $\mathring N_rr$, with $\mathring N_r<0$, makes each swing smaller. Each change of sideslip also rolls the aircraft through the dihedral effect, which is why the wings rock in step.

Keeping only sideslip and yaw rate, with $p=\phi=0$ and $\mathring Y_r\ll mU_\infty$, gives a two-state oscillator:

$$
\omega_n^2=\frac{\mathring Y_v\mathring N_r+mU_\infty\mathring N_v}{mJ_{zz}},\qquad\zeta=-\frac{1}{2\omega_n}\left(\frac{\mathring N_r}{J_{zz}}+\frac{\mathring Y_v}{m}\right).
$$

The stiffness is mostly the directional-stability term $U_\infty\mathring N_v/J_{zz}$ (the weathercock effect) and the damping comes from $\mathring N_r$ and the side force $\mathring Y_v$. For the Navion it gives $-0.508\pm2.11j$ against $-0.487\pm2.34j$ from the full model; the error is the roll it leaves out, since the bank angle in the full eigenvector is as large as the sideslip.

The Dutch roll is the only second-order lateral mode, so it is the only one that can overshoot. Oscillation in recorded $v$, $p$, $r$ or $\phi$ therefore identifies it. Its light damping makes it uncomfortable, especially for passengers far from the centre of gravity, and a yaw damper (yaw-rate feedback to the rudder) is commonly fitted to add damping. Stronger directional stability raises its frequency but lowers its damping ratio, and it destabilises the [[Spiral Mode]].

## Related

- Mechanism, approximation and Navion numbers: [[SESA3047 6.3 - Lateral Modes and their Approximations#9. The Dutch roll (6.48–6.49)|6.3 §9]] and [[SESA3047 6.3 - Lateral Modes and their Approximations#10. Dutch-roll approximation (6.55–6.58)|§10]]
- [[Roll Subsidence Mode]] · [[Spiral Mode]] · [[Lateral and Directional Stability]] · [[Damping Ratio and Natural Frequency]]
- Exam practice: [[SESA2025 Past Paper 2015-16 - Solutions#Q4. Lateral response from plots and the Dutch roll approximation (25 marks)|SESA2025 2015-16 Q4]] · [[SESA2025 Past Paper 2016-17 - Solutions#Q3. Coordinated turn, Dutch roll and yaw damping (30 marks)|SESA2025 2016-17 Q3]]
