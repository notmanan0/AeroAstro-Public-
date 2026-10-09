---
title: "SESA1015 T03 - Wind-Tunnel Data Reduction Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 3
tags: [sesa1015, tutorial, wind-tunnel, data-reduction]
aliases: ["SESA1015 Revision Q9 Q10 Q11 Q12 Q41"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]", "[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]"]
sources: ["02 - Sources/Mechanics of Flight/Calculator for Revision Questions.xlsx"]
---

# SESA1015 T03 - Wind-Tunnel Data Reduction Solutions

> [!abstract] Method
> Convert measured forces to coefficients using the stated tunnel speed, density and reference area. Then reduce $C_L(\alpha)$ or $C_D(C_L^2)$. Do not use the unrelated editable values elsewhere on the worksheet.

## Question 9 — lift-curve slope

Given $S=1.1\ \mathrm{m^2}$, $V=22\ \mathrm{m,s^{-1}}$, $\rho=1.225\ \mathrm{kg,m^{-3}}$, and vertical forces $29.7$ and $190.4\ \mathrm N$ at $0.5^\circ$ and $6.0^\circ$.

$$qS=\frac12\rho V^2S.$$

$$C_{L1}=\frac{29.7}{qS},\qquad C_{L2}=\frac{190.4}{qS}.$$

The slope in per degree is

$$C_{L_\alpha}=\frac{C_{L2}-C_{L1}}{6.0-0.5}.$$

$$\boxed{C_{L_\alpha}=0.0896\ \mathrm{deg^{-1}}\approx0.090\ \mathrm{deg^{-1}}}$$

In per radian, multiply by $180/\pi$: about $5.13\ \mathrm{rad^{-1}}$.

## Question 10 — zero-lift angle

Given $S=1.0\ \mathrm{m^2}$, $V=21\ \mathrm{m,s^{-1}}$, vertical forces $28.2$ and $188.7\ \mathrm N$ at $0.1^\circ$ and $6.3^\circ$.

Convert each force to $C_L$ and form the straight line

$$C_L=m\alpha+c,$$

where

$$m=\frac{C_{L2}-C_{L1}}{6.3-0.1}.$$

The zero-lift angle is the $x$ intercept:

$$\alpha_{L=0}=\alpha_1-\frac{C_{L1}}m.$$

$$\boxed{\alpha_{L=0}=-0.989^\circ}$$

The negative value is consistent with a cambered lifting configuration.

## Question 11 — profile drag coefficient

Given $S=1.3\ \mathrm{m^2}$, $V=22\ \mathrm{m,s^{-1}}$ and the two force pairs

$$ (L_1,D_1)=(29.7,9.60)\ \mathrm N,$$

$$ (L_2,D_2)=(193.1,17.73)\ \mathrm N.$$

First compute

$$C_{Li}=\frac{L_i}{qS},\qquad C_{Di}=\frac{D_i}{qS}.$$

Use both points in

$$C_D=C_{D0}+kC_L^2.$$

Subtract the two equations:

$$k=\frac{C_{D2}-C_{D1}}{C_{L2}^2-C_{L1}^2}.$$

Then

$$C_{D0}=C_{D1}-kC_{L1}^2.$$

$$\boxed{C_{D0}=0.024399\approx0.024}$$

Using the first measured $C_D$ directly would be only an approximation because its lift is small but not zero.

## Question 12 — induced term and profile drag

Given $S=1.2\ \mathrm{m^2}$, $V=20\ \mathrm{m,s^{-1}}$,

$$ (L_1,D_1)=(30.8,9.52)\ \mathrm N,$$

$$ (L_2,D_2)=(182.6,15.86)\ \mathrm N.$$

Here

$$qS=\frac12(1.225)(20^2)(1.2)=294\ \mathrm N.$$

So

$$C_{L1}=30.8/294,\ C_{D1}=9.52/294,$$

$$C_{L2}=182.6/294,\ C_{D2}=15.86/294.$$

Apply the same two-equation polar reduction:

$$\boxed{k=0.057540\approx0.058}$$

$$\boxed{C_{D0}=0.031749\approx0.032}$$

## Question 41 — wind-tunnel lift-cell capacity

Full aircraft: $S_f=8.9\ \mathrm{m^2}$, $AR=7.0$, $m=312\ \mathrm{kg}$, landing speed $15.8\ \mathrm{m,s^{-1}}$. Model span $b_m=2.15\ \mathrm m$.

Full span is

$$b_f=\sqrt{AR\,S_f}.$$

For a geometrically similar model, define length scale $\lambda=b_f/b_m$. Boundary-layer similarity at the same fluid properties requires equal Reynolds number:

$$V_mc_m=V_fc_f\quad\Rightarrow\quad V_m=\lambda V_f.$$

Model area is $S_m=S_f/\lambda^2$. Therefore

$$q_mS_m=\frac12\rho(\lambda V_f)^2\frac{S_f}{\lambda^2}=q_fS_f.$$

At the same $C_L$, the model lift equals the full-scale lift. At the design landing condition that is the aircraft weight:

$$L_m=mg=312(9.81).$$

$$\boxed{L_{cell}=3060.7\ \mathrm N}$$

This result is a consequence of the exact speed scaling stated in the question; real tunnels face Mach, blockage and model-strength constraints.

## Answer check

| Question | Answer |
|---:|---:|
| 9 | $0.090\ \mathrm{deg^{-1}}$ |
| 10 | $-0.989^\circ$ |
| 11 | $C_{D0}=0.024$ |
| 12 | $k=0.058$, $C_{D0}=0.032$ |
| 41 | $3060.7\ \mathrm N$ |

