---
title: "Aerodynamic Stability Derivatives"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["aerodynamic derivatives", "stability derivatives", "M_w", "M_q", "Z_w", "control derivatives", "concise derivatives"]
tags: [sesa2027, concept, flight-dynamics]
status: complete
parent_lectures: ["[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]"]
related_concepts: ["[[Neutral Point and Static Margin]]", "[[Short Period Oscillation]]", "[[State-Space Representation]]"]
sources: ["02 - Sources/Lectures/Lecture 1.04.pdf", "02 - Sources/Lectures/Lecture 1.10.pdf", "02 - Sources/Lectures/Lecture 1.11.pdf", "Cook (2013), Ch. 13"]
---

# Aerodynamic Stability Derivatives

Stability derivatives are the coefficients of the first-order Taylor expansion of the aerodynamic forces and moments in the perturbation variables. The pitching moment, for example, is written

$$
\Delta M_a = \mathring M_uu+\mathring M_ww+\mathring M_qq+\mathring M_{\dot w}\dot w+\mathring M_\eta\eta ,
$$

where the ring (°) marks the dimensional form. Derivatives with respect to states end up in the state matrix $\mathbf A$; those with respect to controls ($\eta$, thrust) are control derivatives and go in $\mathbf B$.

L1.10 estimates each non-dimensional derivative from simple physics:

| Derivative | Formula | Physical meaning |
|---|---|---|
| $X_u$ | $(\Lambda-2)C_D$ | Speed damping; $\Lambda = 0$ for a jet, −1 for a propeller |
| $X_w$ | $C_{L^*}-C_{D_\alpha}$ | Lift vector tilts forward with $\alpha$ |
| $Z_u$ | $-2C_{L^*}$ | Lift grows with speed |
| $Z_w$ | $-(C_{L^*_\alpha}+C_D)$ | Lift-curve slope (heave damping) |
| $M_w$ | $-H_sC_{L^*_\alpha}$ | Pitch stiffness; needs $H_s>0$ |
| $M_q$ | $-KC_{L_{T,\alpha}}l/\bar c$ | Pitch damping from the tail, $\Delta\alpha_T = ql/U$ |
| $M_{\dot w}$ | (downwash lag) | Adds damping to the SPO |
| $Z_\eta$ | $-\frac{S_T}{S}a_2$ | Elevator lift |
| $M_\eta$ | $-\bar V_Ta_2$ | Elevator control power |

To turn these into dimensional derivatives, multiply the $u$ and $w$ force derivatives by $\tfrac12\rho U_\infty S$ and add a factor $\bar c$ for each moment or $q$. The $\dot w$ derivatives scale with $\tfrac12\rho S\bar c$ (force) or $\tfrac12\rho S\bar c^2$ (moment). For the F-4C this gives $\mathring M_w = -1770$ N s, $\mathring M_q = -50798$ N m s, $\mathring M_{\dot w} = -132.47$ N s² and $\mathring Z_w = -5215$ N s/m.

The derivatives that matter most are $M_w$ and $M_q$. The short-period frequency, $\omega_n^2\approx(\mathring M_q\mathring Z_w-mU_\infty\mathring M_w)/(mI_{yy})$, is dominated by the $-U_\infty\mathring M_w/I_{yy}$ term, so in practice by the static margin. In real projects the numbers come from a ladder of methods: back-of-envelope estimates, ESDU or DATCOM, vortex-lattice or CFD codes (AVL, XFLR5), wind-tunnel tests, and free-flight system identification (for example with an EKF). $C_{L_q}$ needs dynamic data; a static test can't give it.

## Related

- Derivations of the force, moment and elevator derivatives: [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives#4. Estimating the derivatives from physics (L1.10)|A2 §4]]; the $Z_\eta$ derivation in PS2 Q2: [[SESA2027 Practice Problems 2 Solutions]]
- [[Neutral Point and Static Margin]] · [[Short Period Oscillation]] · [[State-Space Representation]]
