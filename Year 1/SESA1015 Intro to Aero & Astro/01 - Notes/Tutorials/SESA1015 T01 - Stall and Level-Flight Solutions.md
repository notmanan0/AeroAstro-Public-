---
title: "SESA1015 T01 - Stall and Level-Flight Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 1
tags: [sesa1015, tutorial, stall, level-flight]
aliases: ["SESA1015 Revision Q1 Q2 Q4 Q14 Q15 Q30 Q42"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]", "[[SESA1015 M04 - Steady Level Flight and Stall]]", "[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
sources: ["02 - Sources/Mechanics of Flight/Calculator for Revision Questions.xlsx"]
---

# SESA1015 T01 - Stall and Level-Flight Solutions

> [!abstract] Workbook rule
> These solutions use the values written in each question, not the editable calculator cells beneath it. Several calculator cells contain values from a different randomised version.

## Question 1 — wing loading change and altitude stall speed

Given $C_{L,max}=1.75$, original $W/S=4981\ \mathrm{N,m^{-2}}$, desired stall-speed reduction 14%, and $\sigma=0.75$.

### (a) New wing loading

At fixed density and $C_{L,max}$, $V_s\propto\sqrt{W/S}$. Hence

$$\frac{(W/S)_{new}}{(W/S)_{old}}=\left(\frac{V_{s,new}}{V_{s,old}}\right)^2=(1-0.14)^2.$$

$$\boxed{(W/S)_{new}=4981(0.86)^2=3683.95\ \mathrm{N,m^{-2}}}$$

### (b) True stall speed at altitude

The question returns to the stated aircraft wing loading $4981\ \mathrm{N,m^{-2}}$:

$$\rho=\sigma\rho_0=0.75(1.225)=0.91875\ \mathrm{kg,m^{-3}},$$

$$V_s=\sqrt{\frac{2(W/S)}{\rho C_{L,max}}}
=\sqrt{\frac{2(4981)}{(0.91875)(1.75)}}.$$

$$\boxed{V_s=78.71\ \mathrm{m,s^{-1}}}$$

## Question 2 — duplicate prompt

Question 2 repeats the written prompt of Question 1. Therefore

$$\boxed{(W/S)_{new}=3683.95\ \mathrm{N,m^{-2}},\qquad V_s=78.71\ \mathrm{m,s^{-1}}.}$$

## Question 4 — induced-drag fraction after a speed increase

In steady level flight $L=W$ is unchanged. From

$$D_i=\frac{kL^2}{qS}=\frac{2kW^2}{\rho V^2S},$$

$D_i\propto V^{-2}$. Therefore

$$\frac{D_{i,2}}{D_{i,1}}=\left(\frac{57}{103}\right)^2=0.306249.$$

$$\boxed{D_{i,2}/D_{i,1}=0.306}$$

The induced drag is 30.6% of its original value, i.e. reduced by about 69.4%.

## Question 14 — minimum-power speed

Given $m=8207\ \mathrm{kg}$, $S=30\ \mathrm{m^2}$, $\sigma=0.43$ and

$$C_D=0.020+0.044C_L^2.$$

At minimum power,

$$C_{L,MP}=\sqrt{\frac{3C_{D0}}k}=\sqrt{\frac{3(0.020)}{0.044}}=1.16775.$$

With $\rho=1.225(0.43)=0.52675\ \mathrm{kg,m^{-3}}$ and $W=8207(9.81)$,

$$V_{MP}=\sqrt{\frac{2W}{\rho SC_{L,MP}}}.$$

$$\boxed{V_{MP}=93.41\ \mathrm{m,s^{-1}}}$$

## Question 15 — minimum-drag speed

Given $W/S=4586\ \mathrm{N,m^{-2}}$, $\rho=0.68\ \mathrm{kg,m^{-3}}$ and

$$C_D=0.022+0.045C_L^2,$$

the minimum-drag coefficient is

$$C_{L,MD}=\sqrt{\frac{0.022}{0.045}}=0.69921.$$

Then

$$V_{MD}=\sqrt{\frac{2(W/S)}{\rho C_{L,MD}}}
=\sqrt{\frac{2(4586)}{(0.68)(0.69921)}}.$$

$$\boxed{V_{MD}=138.9\ \mathrm{m,s^{-1}}}$$

The stated total weight is not required because wing loading is already supplied.

## Question 30 — cruise wing loading

Given $M=0.61$, $\sigma=0.297$, $\theta=0.75$ and $C_L=0.23$:

$$T=288.15(0.75)=216.11\ \mathrm K,$$

$$\rho=1.225(0.297)=0.36383\ \mathrm{kg,m^{-3}},$$

$$a=\sqrt{1.4(287)(216.11)},\qquad V=0.61a.$$

Level flight gives

$$\frac WS=qC_L=\frac12\rho V^2C_L.$$

$$\boxed{W/S=1351.89\ \mathrm{N,m^{-2}}}$$

## Question 42 — lift-to-drag ratio

Given $V=25\ \mathrm{m,s^{-1}}$, $\sigma=0.81$, $b=2.2\ \mathrm m$, $AR=7.1$, $m=27\ \mathrm{kg}$ and $C_D=0.084$.

$$S=\frac{b^2}{AR}=\frac{2.2^2}{7.1}=0.68169\ \mathrm{m^2},$$

$$\rho=1.225(0.81)=0.99225\ \mathrm{kg,m^{-3}}.$$

From $L=W$,

$$C_L=\frac{mg}{\tfrac12\rho V^2S}.$$

Therefore

$$\frac LD=\frac{C_L}{C_D}=14.9175.$$

$$\boxed{L/D=14.92}$$

## Answer check

| Question | Answer |
|---:|---:|
| 1 | $3683.95\ \mathrm{N,m^{-2}}$; $78.71\ \mathrm{m,s^{-1}}$ |
| 2 | same as Q1 |
| 4 | $0.306$ |
| 14 | $93.41\ \mathrm{m,s^{-1}}$ |
| 15 | $138.9\ \mathrm{m,s^{-1}}$ |
| 30 | $1351.89\ \mathrm{N,m^{-2}}$ |
| 42 | $14.92$ |

