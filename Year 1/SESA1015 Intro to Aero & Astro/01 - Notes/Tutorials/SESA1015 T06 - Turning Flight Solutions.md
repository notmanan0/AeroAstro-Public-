---
title: "SESA1015 T06 - Turning Flight Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 6
tags: [sesa1015, tutorial, turning-flight]
aliases: ["SESA1015 Revision Q6 Q25 Q26 Q31"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]"]
sources: ["02 - Sources/Mechanics of Flight/Calculator for Revision Questions.xlsx"]
---

# SESA1015 T06 - Turning Flight Solutions

## Question 6 — thrust in a 6-g turn

Given $n=6$, $V=381\ \mathrm{kn}$, $W/S=3709\ \mathrm{N,m^{-2}}$, $S=30\ \mathrm{m^2}$ and

$$C_D=0.010+0.070C_L^2.$$

Convert speed:

$$V=381(0.514444)=196.00\ \mathrm{m,s^{-1}}.$$

In a level $n$-g turn, $L=nW$, so

$$C_L=\frac{n(W/S)}q,qquad q=\frac12\rho_0V^2.$$

Then

$$C_D=0.010+0.070C_L^2,qquad T=D=qSC_D.$$

$$\boxed{T=51257\ \mathrm N}$$

This is the thrust to sustain the turn in the simplified model, not merely initiate it.

## Stall-limited radius derivation

At a fixed speed, the maximum lift-limited load factor follows from

$$n_{max}=\frac{L_{max}}W=\left(\frac V{V_s}\right)^2.$$

The coordinated-turn relation is

$$R=\frac{V^2}{g\sqrt{n^2-1}}.$$

Therefore

$$\boxed{R_{min}=\frac{V^2}{g\sqrt{(V/V_s)^4-1}}}.$$

## Question 25

For $V=82\ \mathrm{m,s^{-1}}$ and $V_s=44\ \mathrm{m,s^{-1}}$,

$$\boxed{R_{min}=206.08\ \mathrm m\approx206\ \mathrm m}$$

## Question 26

For $V=106\ \mathrm{m,s^{-1}}$ and $V_s=60\ \mathrm{m,s^{-1}}$,

$$\boxed{R_{min}=387.39\ \mathrm m}$$

## Question 31 — thrust-limited turn radius

Given excess thrust above level-flight requirement $\Delta T=534\ \mathrm N$, $V=109\ \mathrm{m,s^{-1}}$, $W=5322\ \mathrm N$, $S=14\ \mathrm{m^2}$ and $k=0.057$.

At the same speed, parasite drag is unchanged. The extra thrust supports the turn's extra induced drag:

$$\Delta T=\Delta D_i
=\frac{kW^2}{qS}(n^2-1)
=\frac{2kW^2}{\rho V^2S}(n^2-1).$$

Thus

$$\sqrt{n^2-1}=\sqrt{\frac{\Delta T\,\rho V^2S}{2kW^2}}.$$

Substitute into $R=V^2/[g\sqrt{n^2-1}]$:

$$R=\frac Vg\sqrt{\frac{2kW^2}{\rho S\Delta T}}.$$

$$\boxed{R=208.63\ \mathrm m\approx209\ \mathrm m}$$

The $C_{D0}$ value cancels because the question gives **excess** thrust above the 1-g level-flight requirement.

## Answer check

| Question | Answer |
|---:|---:|
| 6 | $51257\ \mathrm N$ |
| 25 | $206\ \mathrm m$ |
| 26 | $387.4\ \mathrm m$ |
| 31 | $209\ \mathrm m$ |

