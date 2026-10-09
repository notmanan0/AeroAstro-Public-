---
title: "Aerodynamic Stability Derivatives"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["aerodynamic derivatives", "stability derivatives", "M_w", "M_q", "Z_w", "control derivatives"]
tags: [sesa2027, concept, flight-dynamics]
status: complete
parent_lectures: ["[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]"]
related_concepts: ["[[Neutral Point and Static Margin]]", "[[Short Period Oscillation]]", "[[State-Space Representation]]"]
sources: ["02 - Sources/Lectures/Lecture 1.04.pdf", "02 - Sources/Lectures/Lecture 1.10.pdf", "02 - Sources/Lectures/Lecture 1.11.pdf"]
---

# Aerodynamic Stability Derivatives

## Definition

> [!note] Definition
> These are the coefficients of the first-order Taylor expansion of the aerodynamic forces and moments in the perturbation variables. For example:
> $$\Delta M_a = \mathring M_uu+\mathring M_ww+\mathring M_qq+\mathring M_{\dot w}\dot w+\mathring M_\eta\eta$$
> A ring (°) marks the **dimensional** form. Derivatives with respect to states go in $\mathbf A$; derivatives with respect to controls ($\eta$, $T$) go in $\mathbf B$.

## Explanation
**Non-dimensional estimates** from physics (L1.10):

| Derivative | Formula | Physical meaning |
|---|---|---|
| $X_u$ | $(\Lambda-2)C_D$ | Speed damping; $\Lambda = 0$ for a jet, −1 for a propeller |
| $X_w$ | $C_{L^*}-C_{D_\alpha}$ | Lift vector tilts forward with $\alpha$ |
| $Z_u$ | $-2C_{L^*}$ | Lift grows with speed |
| $Z_w$ | $-(C_{L^*_\alpha}+C_D)$ | Lift-curve slope (heave damping) |
| $M_w$ | $-H_sC_{L^*_\alpha}$ | **Pitch stiffness**; needs $H_s>0$ |
| $M_q$ | $-KC_{L_{T,\alpha}}l/\bar c$ | **Pitch damping** from the tail, $\Delta\alpha_T = ql/U$ |
| $M_{\dot w}$ | (downwash lag) | Adds damping to the SPO |
| $Z_\eta$ | $-\frac{S_T}{S}a_2$ | Elevator lift |
| $M_\eta$ | $-\bar V_Ta_2$ | Elevator control power |

**Dimensional scaling**: multiply by $\tfrac12\rho U_\infty S$ for $u$ and $w$ force derivatives, and add a factor of $\bar c$ for each moment or $q$. The $\dot w$ derivatives use $\tfrac12\rho S\bar c$ (force) or $\tfrac12\rho S\bar c^2$ (moment).

**Estimation**: back-of-envelope, ESDU/DATCOM, CFD/vortex lattice (AVL, XFLR5), wind tunnel, free flight with system identification (EKF). $C_{L_q}$ needs dynamic data, not static tests.

## Examples
- F-4C: $\mathring M_w = -1770$ N s, $\mathring M_q = -50798$ N m s, $\mathring M_{\dot w} = -132.47$ N s², $\mathring Z_w = -5215$ N s/m.
- The SPO frequency $\omega_n^2\approx(\mathring M_q\mathring Z_w-mU_\infty\mathring M_w)/(mI_{yy})$ is dominated by $-U_\infty\mathring M_w/I_{yy}$, i.e. by the **static margin**.
- PS2 Q2 derivation of $Z_\eta$: [[SESA2027 Practice Problems 2 Solutions]].

## Related
- [[Neutral Point and Static Margin]] · [[Short Period Oscillation]] · [[State-Space Representation]]

## Sources
- Lectures 1.04, 1.10, 1.11; Cook (2013), Ch. 13
