---
title: "SESA1015 T08 - Constraint Analysis Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 8
tags: [sesa1015, tutorial, constraint-analysis]
aliases: ["SESA1015 Revision Q35 Q36 Q37"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M12 - Aircraft Constraint Analysis]]"]
sources: ["02 - Sources/Mechanics of Flight/Calculator for Revision Questions.xlsx"]
---

# SESA1015 T08 - Constraint Analysis Solutions

> [!abstract] Shared method
> Let $x=W/S$ and $y=T/W$. The simplified take-off boundary is horizontal:
>
> $$y_{TO}=\mu+\frac{V_2^2}{2gs_1}.$$
>
> The minimum required $T/W$ occurs at its lower-$x$ intersection with the turn, climb or cruise boundary specified in the question.

## Question 35 — take-off versus 2-g turn

Data: $s_1=88\ \mathrm m$, $V_2=21.6\ \mathrm{m,s^{-1}}$, $\mu=0.17$, turn speed $V=31\ \mathrm{m,s^{-1}}$, $n=2$, and

$$C_D=0.024+0.057C_L^2.$$

Take-off:

$$y_{TO}=0.17+\frac{21.6^2}{2(9.81)(88)}.$$

For the turn, $C_L=nx/q$ and

$$y_{turn}=\frac{D}{W}=\frac{qC_{D0}}x+\frac{kn^2x}{q},\qquad q=\frac12\rho_0V^2.$$

Set $y_{turn}=y_{TO}$ and multiply by $x$:

$$\frac{kn^2}{q}x^2-y_{TO}x+qC_{D0}=0.$$

Choose the lower positive root:

$$\boxed{W/S=33.05\ \mathrm{N,m^{-2}}\approx33.1\ \mathrm{N,m^{-2}}}$$

## Question 36 — take-off versus climb

Data: $s_1=56\ \mathrm m$, $V_2=18.6\ \mathrm{m,s^{-1}}$, $\mu=0.19$, climb speed $V=34\ \mathrm{m,s^{-1}}$, $ROC=6.4\ \mathrm{m,s^{-1}}$, and

$$C_D=0.022+0.056C_L^2.$$

$$y_{TO}=0.19+\frac{18.6^2}{2(9.81)(56)}.$$

For the simple climb model,

$$y_{climb}=\frac{qC_{D0}}x+\frac{kx}{q}+\frac{ROC}{V}.$$

Set $y_{climb}=y_{TO}$:

$$\frac{k}{q}x^2-\left(y_{TO}-\frac{ROC}{V}\right)x+qC_{D0}=0.$$

The lower positive root is

$$\boxed{W/S=49.81\ \mathrm{N,m^{-2}}\approx49.8\ \mathrm{N,m^{-2}}}$$

## Question 37 — take-off versus cruise

Data: $s_1=98\ \mathrm m$, $V_2=19.8\ \mathrm{m,s^{-1}}$, $\mu=0.16$, cruise speed $V=38\ \mathrm{m,s^{-1}}$, and

$$C_D=0.021+0.057C_L^2.$$

$$y_{TO}=0.16+\frac{19.8^2}{2(9.81)(98)}.$$

Cruise/level flight gives

$$y_{cruise}=\frac{qC_{D0}}x+\frac{kx}{q}.$$

Set equal and solve

$$\frac{k}{q}x^2-y_{TO}x+qC_{D0}=0.$$

The lower positive root is

$$\boxed{W/S=51.51\ \mathrm{N,m^{-2}}\approx51.5\ \mathrm{N,m^{-2}}}$$

> [!tip] Why the lower root?
> The U-shaped aerodynamic constraint can cross the horizontal take-off line twice. The prompt asks for the lowest wing loading that produces the minimum common thrust loading, so select the smaller positive root.

## Answer check

| Question | Answer |
|---:|---:|
| 35 | $33.1\ \mathrm{N,m^{-2}}$ |
| 36 | $49.8\ \mathrm{N,m^{-2}}$ |
| 37 | $51.5\ \mathrm{N,m^{-2}}$ |

