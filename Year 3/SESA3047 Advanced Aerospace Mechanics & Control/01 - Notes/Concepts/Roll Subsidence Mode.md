---
title: "Roll Subsidence Mode"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 6: Aircraft Flight Dynamics and Interpretation of Eigenvectors"
aliases: ["roll subsidence", "roll mode", "roll damping mode", "rolling convergence", "pure-roll approximation"]
tags: [sesa3047, concept, lateral-dynamics, flight-dynamics, roll]
status: complete
coverage: "Chapter 6 §6.7.2, Eqs. 6.41–6.43, lectured in L20 (Thu 19 Nov)"
parent_lectures: ["[[SESA3047 6.3 - Lateral Modes and their Approximations]]"]
related_concepts: ["[[Spiral Mode]]", "[[Dutch Roll Mode]]", "[[Lateral and Directional Stability]]", "[[Longitudinal and Lateral Dynamics]]"]
sources: ["02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf", "02 - Sources/Lectures/19 November 2026 at 16_00_12.txt"]
---

# Roll Subsidence Mode

The roll subsidence mode is the fast, non-oscillatory lateral mode in which the aircraft's own roll damping stops any roll rate: a large negative real eigenvalue of the lateral state matrix, with an eigenvector dominated by the roll rate $p$.

When the aircraft rolls at rate $p$, a wing section at spanwise position $y$ moves vertically at $py$, which changes its angle of attack by $py/U_\infty$. The descending wing gains lift and the rising wing loses it, producing a rolling moment $\mathring L_pp$ that opposes the roll, with $\mathring L_p<0$. Keeping only that term in the roll equation gives the first-order model

$$
J_{xx}\dot p=\mathring L_pp\quad\Rightarrow\quad p(t)=p(0)\,e^{\mathring L_pt/J_{xx}},\qquad\lambda\approx\frac{\mathring L_p}{J_{xx}},\qquad\tau=-\frac{J_{xx}}{\mathring L_p},
$$

valid when the roll is much faster than the other lateral motions and $J_{xz}$ coupling is neglected. Being first order, the mode cannot oscillate, and it is stable whenever $\mathring L_p<0$. For the Navion of Table 6.2 the estimate is $-8.41$ s⁻¹ ($\tau=0.119$ s) against $-8.44$ s⁻¹ from the full lateral model.

Stopping the roll does not level the wings: the aircraft keeps the bank angle it reached, and that bank angle then evolves on the much slower time scale of the [[Spiral Mode]]. The roll time constant sets how crisply the aircraft responds to aileron, so it is one of the handling-quality parameters.

## Related

- Derivation and Navion numbers: [[SESA3047 6.3 - Lateral Modes and their Approximations#6. Roll subsidence mode and its approximation (6.41–6.43)|6.3 §6]]
- [[Spiral Mode]] · [[Dutch Roll Mode]] · [[Lateral and Directional Stability]] · [[Eigenvectors as Mode Shapes]]
- Exam practice: [[SESA2025 Past Paper 2013-14 - Solutions#Q4. Lateral modes, a coordinated turn and the pure-roll approximation (25 marks)|SESA2025 2013-14 Q4]] · [[SESA2025 Past Paper 2024-25 - Solutions#Q4. Roll damping and the lateral modes (25 marks)|SESA2025 2024-25 Q4]]
