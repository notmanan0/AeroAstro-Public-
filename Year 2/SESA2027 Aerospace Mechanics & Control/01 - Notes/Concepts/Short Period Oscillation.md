---
title: "Short Period Oscillation"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["SPO", "short period", "short-period mode", "SPO approximation"]
tags: [sesa2027, concept, flight-dynamics, modes]
status: complete
parent_lectures: ["[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
related_concepts: ["[[Phugoid Mode]]", "[[Damping Ratio and Natural Frequency]]", "[[Aerodynamic Stability Derivatives]]", "[[Neutral Point and Static Margin]]"]
sources: ["02 - Sources/Lectures/Lecture 1.05.pdf", "02 - Sources/Lectures/Lecture 1.06.pdf"]
---

# Short Period Oscillation

## Definition

> [!note] Definition
> The **fast, usually heavily damped** longitudinal mode. It is a pitching oscillation in $\alpha$ ($w$) and $q$ at almost **constant airspeed**, with a period of a few seconds. The **SPO approximation** (with $u = 0$, $\gamma_0 = 0$, $\mathring Z_{\dot w}\ll m$, $\mathring Z_q\ll mU_\infty$) gives
>
> $$\omega_n^2 = \frac{\mathring M_q\mathring Z_w-mU_\infty\mathring M_w}{mI_{yy}},\qquad 2\zeta\omega_n = -\left(\frac{\mathring Z_w}{m}+\frac{\mathring M_q}{I_{yy}}+\frac{U_\infty\mathring M_{\dot w}}{I_{yy}}\right)$$

## Explanation
- **Physics**:
  - A disturbance in $\alpha$ is opposed by the pitch stiffness $M_w<0$ (static margin), but the aircraft overshoots.
  - The motion is damped by $M_q$: tail incidence $ql/U$ plus downwash lag ($M_{\dot w}$).
  - It is too fast for the speed to change.
- **Frequency** is dominated by $-U_\infty\mathring M_w/I_{yy}$. A larger static margin or higher speed gives a faster SPO.
- **Damping** comes mainly from $\mathring M_q$ and $\mathring Z_w$.
- **Accuracy**: the approximation is excellent (F-4C: under 0.5 % error vs 4×4), so it is the design model for pitch control (DAP2).
- **Handling qualities**: pilots feel the SPO directly.
  - CS/FAR 25.181 requires it to be heavily damped.
  - MIL-F-8785C Level 1 Category A needs $0.35\le\zeta_{sp}\le1.30$.
- **SPO with elevator input**: $q/\eta = \dfrac{m_\eta s+(m_wz_\eta-m_\eta z_w)}{s^2-(m_q+z_w)s+(z_wm_q-z_qm_w)}$, the Part B plant.

## Examples
- F-4C at 178 m/s: $\omega_n = 1.41$ rad/s, $\zeta = 0.26$.
- PS1 Q2 at 356 m/s: $\omega_n = 5.43$ rad/s, $\zeta = 0.16$. That is too lightly damped and needs a SAS ([[SESA2027 Practice Problems 1 Solutions]]).
- PS1 Q1: $\lambda = -0.7\pm3i$, $T = 2.09$ s, $t_{1/2} = 0.99$ s.

![[amc_ps1_q1_spo_pitch.png|560]]

## Related
- [[Phugoid Mode]] · [[Damping Ratio and Natural Frequency]] · [[Aerodynamic Stability Derivatives]] · [[Neutral Point and Static Margin]] · [[Stability vs Manoeuvrability]]

## Sources
- Lectures 1.05–1.06; Cook (2013), Ch. 6–7
