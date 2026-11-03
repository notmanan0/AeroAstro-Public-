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
sources: ["02 - Sources/Lectures/Lecture 1.05.pdf", "02 - Sources/Lectures/Lecture 1.06.pdf", "Cook (2013), Ch. 6–7"]
---

# Short Period Oscillation

The **short-period oscillation (SPO)** is the fast, usually well-damped longitudinal mode: a pitching oscillation in $\alpha$ (or $w$) and $q$ at almost constant airspeed, with a period of a few seconds. With $u = 0$, $\gamma_0 = 0$, $\mathring Z_{\dot w}\ll m$ and $\mathring Z_q\ll mU_\infty$, the SPO approximation gives it in closed form:

$$
\omega_n^2 = \frac{\mathring M_q\mathring Z_w-mU_\infty\mathring M_w}{mI_{yy}},\qquad 2\zeta\omega_n = -\left(\frac{\mathring Z_w}{m}+\frac{\mathring M_q}{I_{yy}}+\frac{U_\infty\mathring M_{\dot w}}{I_{yy}}\right).
$$

Physically, a disturbance in $\alpha$ is opposed by the pitch stiffness $M_w<0$, which comes from the static margin, but the aircraft overshoots. The overshoot is damped by $M_q$, from the tail incidence $ql/U$, and by the downwash lag in $M_{\dot w}$. The whole thing is over before the speed has time to change. The frequency is dominated by $-U_\infty\mathring M_w/I_{yy}$, so a larger static margin or a higher speed gives a faster SPO, and the damping comes mainly from $\mathring M_q$ and $\mathring Z_w$. For the F-4C the approximation is within 0.5 % of the full 4×4 model, which is why it is the design model for pitch control. With elevator input it gives the Part B plant,

$$
\frac{q}{\eta} = \frac{m_\eta s+(m_wz_\eta-m_\eta z_w)}{s^2-(m_q+z_w)s+(z_wm_q-z_qm_w)} .
$$

Pilots feel the SPO directly, so the handling-quality rules are strict. CS/FAR 25.181 requires it to be heavily damped, and MIL-F-8785C Level 1, Category A needs $0.35\le\zeta_{sp}\le1.30$. The F-4C at 178 m/s has $\omega_n = 1.41$ rad/s and $\zeta = 0.26$. PS1 Q2, at 356 m/s, has $\omega_n = 5.43$ rad/s and $\zeta = 0.16$, too lightly damped without a stability augmentation system ([[SESA2027 Practice Problems 1 Solutions]]). In PS1 Q1, $\lambda = -0.7\pm3i$ gives $T = 2.09$ s and $t_{1/2} = 0.99$ s.

![[amc_ps1_q1_spo_pitch.png|560]]

## Related

- The SPO characteristic equation line by line: [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid#5. The SPO approximation (L1.06)|A3 §5]]
- [[Phugoid Mode]] · [[Damping Ratio and Natural Frequency]] · [[Aerodynamic Stability Derivatives]] · [[Neutral Point and Static Margin]] · [[Stability vs Manoeuvrability]]
