---
title: "SESA1015 T05 - Climb and Glide Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 5
tags: [sesa1015, tutorial, climb, glide]
aliases: ["SESA1015 Revision Q17 Q18"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M08 - Glide and Climb Performance]]"]
sources: ["02 - Sources/Mechanics of Flight/Calculator for Revision Questions.xlsx"]
---

# SESA1015 T05 - Climb and Glide Solutions

## Question 17 — thrust for a prescribed climb rate

Given $W/S=5228\ \mathrm{N,m^{-2}}$, $b=8\ \mathrm m$, $AR=3$, $V=452\ \mathrm{kn}$, $ROC=7\ \mathrm{m,s^{-1}}$, thrust angle $\epsilon=9^\circ$, and

$$C_D=0.015+0.057C_L^2.$$

Geometry, weight and speed:

$$S=\frac{b^2}{AR}=21.333\ \mathrm{m^2},$$

$$W=(W/S)S,$$

$$V=452(0.514444)=232.51\ \mathrm{m,s^{-1}}.$$

For the shallow-climb course model, use $L\approx W$, so

$$C_L=\frac{W/S}{q},\qquad q=\frac12\rho_0V^2.$$

Then

$$D=qS(0.015+0.057C_L^2).$$

Along the flight path,

$$T\cos\epsilon-D=W\sin\gamma.$$

Since $ROC=V\sin\gamma$,

$$\boxed{T=\frac{D+W(ROC/V)}{\cos\epsilon}}.$$

$$\boxed{T=15145\ \mathrm N}$$

If the thrust angle is neglected, the course small-angle approximation gives $14959\ \mathrm N$. The exact resolution requested by the prompt is the first value.

## Question 18 — climb rate with thrust vectoring

Written data: $T=45770\ \mathrm N$, $W/S=4793\ \mathrm{N,m^{-2}}$, $S=72\ \mathrm{m^2}$, $V=412\ \mathrm{kn}$ and $D=35537\ \mathrm N$.

> [!warning] Source formatting artefact
> The text shows “79 degrees”, but the worksheet input and its warning show that the intended value is $7^\circ$. A $79^\circ$ thrust angle is inconsistent with the calculator and physical context. The solution therefore uses $7^\circ$.

$$W=(W/S)S=4793(72)=345096\ \mathrm N,$$

$$V=412(0.514444)=211.93\ \mathrm{m,s^{-1}}.$$

From

$$T\cos\epsilon-D=W\sin\gamma,$$

the vertical speed is

$$ROC=V\sin\gamma
=V\frac{T\cos\epsilon-D}{W}.$$

$$\boxed{ROC=6.075\ \mathrm{m,s^{-1}}\approx6.08\ \mathrm{m,s^{-1}}}$$

## Answer check

| Question | Answer |
|---:|---:|
| 17 | $15145\ \mathrm N$ exact; $14959\ \mathrm N$ if thrust angle is neglected |
| 18 | $6.08\ \mathrm{m,s^{-1}}$ using intended $7^\circ$ |

