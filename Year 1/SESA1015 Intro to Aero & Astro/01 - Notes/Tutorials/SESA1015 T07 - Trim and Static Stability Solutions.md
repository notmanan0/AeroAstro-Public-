---
title: "SESA1015 T07 - Trim and Static Stability Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 7
tags: [sesa1015, tutorial, trim, static-stability]
aliases: ["SESA1015 Revision Q8 Q13"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M11 - Longitudinal Trim and Static Stability]]"]
sources: ["02 - Sources/Mechanics of Flight/Calculator for Revision Questions.xlsx"]
---

# SESA1015 T07 - Trim and Static Stability Solutions

## Question 8 — tail area from static margin

Given wing lift slope $a_w=4.92\ \mathrm{rad^{-1}}$, tail lift slope $a_t=5.02\ \mathrm{rad^{-1}}$, CG $h=0.51$, wing aerodynamic centre $h_0=0.25$, desired static margin $SM=0.18$, wing $S=1.39\ \mathrm{m^2}$, $AR=7$, tail arm $l_t=0.93\ \mathrm m$, and $d\epsilon/d\alpha=0.21$.

The desired neutral point is

$$h_n=h+SM=0.69.$$

For the first-order conventional-tail model,

$$h_n=h_0+V_H\frac{a_t}{a_w}\left(1-\frac{d\epsilon}{d\alpha}\right).$$

Hence

$$V_H=(h_n-h_0)\frac{a_w}{a_t}\frac{1}{1-d\epsilon/d\alpha}.$$

The representative wing chord from the given geometry is

$$\bar c=\sqrt{\frac SAR}.$$

Finally,

$$V_H=\frac{S_Tl_t}{S\bar c}\quad\Rightarrow\quad
S_T=V_H\frac{S\bar c}{l_t}.$$

$$\boxed{S_T=0.36356\ \mathrm{m^2}\approx0.364\ \mathrm{m^2}}$$

The wing zero-lift offset in the given $C_L$ equation does not enter the neutral-point slope calculation.

## Question 13 — stabiliser trim angle

The CG lies at the wing/fuselage aerodynamic centre, so main lift creates no additional moment about the CG. Given

$$C_{m,ac}=-0.094,$$

$$S_T/S=0.22,\qquad l_t/\bar c=4.7,$$

and symmetric-tail lift slope $a_t=0.088\ \mathrm{deg^{-1}}$.

With upward tail lift aft producing a nose-down moment under the adopted convention,

$$0=C_{m,ac}-\left(\frac{S_T}{S}\right)\left(\frac{l_t}{\bar c}\right)C_{L_T}.$$

Therefore

$$C_{L_T}=\frac{-0.094}{(0.22)(4.7)}=-0.09091.$$

For the symmetric tail, $C_{L_T}=a_t\alpha_T$:

$$\alpha_T=\frac{-0.09091}{0.088}.$$

$$\boxed{\alpha_T=-1.03^\circ}$$

The negative angle produces the required negative tail lift to balance the negative wing/fuselage pitching-moment coefficient under this sign convention.

## Answer check

| Question | Answer |
|---:|---:|
| 8 | $S_T=0.364\ \mathrm{m^2}$ |
| 13 | $\alpha_T=-1.03^\circ$ |

