---
title: "SESA1015 T04 - Range and Endurance Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 4
tags: [sesa1015, tutorial, range, endurance]
aliases: ["SESA1015 Revision Q5 Q16 Q20 Q27 Q29"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M06 - Jet Aircraft Range and Endurance]]", "[[SESA1015 M07 - Propeller Aircraft Range and Endurance]]"]
sources: ["02 - Sources/Mechanics of Flight/Calculator for Revision Questions.xlsx"]
---

# SESA1015 T04 - Range and Endurance Solutions

## Question 5 — jet Breguet range

Given $b=86.3\ \mathrm m$, $AR=8.5$, $M=0.82$, $T=223\ \mathrm K$, $\sigma=0.31$, initial $W/S=5414\ \mathrm{N,m^{-2}}$, fuel used $=683182\ \mathrm N$, and $c_T=1.5\ \mathrm{h^{-1}}$.

First,

$$S=\frac{b^2}{AR},\qquad W_1=(W/S)S,\qquad W_2=W_1-683182.$$

The cruise speed and density are

$$V=M\sqrt{\gamma RT},\qquad \rho=\sigma\rho_0.$$

At the start,

$$C_L=\frac{2(W/S)}{\rho V^2},$$

$$C_D=0.016+0.043C_L^2.$$

The question asks us to assume constant $L/D$, so use

$$R=\frac{V}{c_T}\frac{C_L}{C_D}\ln\frac{W_1}{W_2},$$

with $c_T=1.5/3600\ \mathrm{s^{-1}}$.

$$\boxed{R=1691.48\ \mathrm{km}\approx1691\ \mathrm{km}}$$

## Question 16 — required jet SFC

Given $b=30.5\ \mathrm m$, $AR=9.1$, $W/S=5808\ \mathrm{N,m^{-2}}$, $M=0.81$, $T=216.74\ \mathrm K$, $\rho=0.3724\ \mathrm{kg,m^{-3}}$, fuel mass $21505\ \mathrm{kg}$, and $R=3899\ \mathrm{nm}$.

$$S=\frac{b^2}{AR},\qquad W_1=(W/S)S,$$

$$W_2=W_1-(21505)g.$$

$$V=M\sqrt{\gamma RT},\qquad C_L=\frac{2(W/S)}{\rho V^2},$$

$$C_D=0.016+0.044C_L^2.$$

Rearrange Breguet:

$$\boxed{c_T=\frac{V(L/D)\ln(W_1/W_2)}R}.$$

Use $R=3899(1852)\ \mathrm m$:

$$\boxed{c_T=2.725\times10^{-4}\ \mathrm{N,s^{-1},N^{-1}}}$$

The same unit can be read as s$^{-1}$ under the weight-flow definition.

## Question 20 — seasonal flight-time difference

Distance $d=4894\ \mathrm{nm}$ and Mach number $M=0.84$ are fixed. TAS changes because

$$V=M\sqrt{\gamma RT}.$$

Use

$$T_{summer}=236.15\ \mathrm K,\qquad T_{winter}=201.15\ \mathrm K.$$

Then

$$t_s=\frac d{V_s},\qquad t_w=\frac d{V_w}.$$

The colder winter atmosphere has the lower speed of sound and therefore the lower TAS at the same Mach.

$$\boxed{|t_w-t_s|=48.76\ \mathrm{min}\approx48.8\ \mathrm{min}}$$

Wind is not included.

## Question 27 — propeller fuel weight

Dry/final weight $W_2=8697\ \mathrm N$, range $R=969\ \mathrm{nm}$, propulsive efficiency $\eta_p=0.8374$, and SFC $c_P=2.77\ \mathrm{N/(kW,h)}$. The polar is

$$C_D=0.028+0.070C_L^2.$$

Maximum propeller range occurs at maximum $L/D$:

$$C_L=\sqrt{\frac{0.028}{0.070}},\qquad \frac LD=\frac{C_L}{0.028+0.070C_L^2}.$$

Convert the SFC:

$$c_P=\frac{2.77}{1000(3600)}\ \mathrm{N/(W,s)}.$$

The propeller Breguet relation in this convention is

$$R=\frac{\eta_p}{c_P}\frac LD\ln\frac{W_1}{W_2}.$$

Thus

$$W_1=W_2\exp\left(\frac{Rc_P}{\eta_p(L/D)}\right).$$

Fuel weight is $W_f=W_1-W_2$:

$$\boxed{W_f=1367.18\ \mathrm N\approx1367\ \mathrm N}$$

## Question 29 — course constant-$L/D$ cruise model

Given $m_1=251\times10^3\ \mathrm{kg}$, $m_2=146\times10^3\ \mathrm{kg}$, $M=0.48$, $c_T=1.0\times10^{-4}\ \mathrm{s^{-1}}$, $b=50.9\ \mathrm m$, $AR=9.0$, $\sigma=0.309$, $\theta=0.759$, and

$$C_D=0.017+0.032C_L^2.$$

Compute the start-of-cruise state:

$$S=\frac{b^2}{AR},\quad T=288.15\theta,\quad \rho=1.225\sigma,$$

$$V=M\sqrt{\gamma RT},\quad C_L=\frac{m_1g}{\tfrac12\rho V^2S},$$

$$C_D=0.017+0.032C_L^2.$$

The workbook's intended approximation holds this start-of-cruise $L/D$ and speed in the logarithmic Breguet form:

$$R=\frac{V}{c_T}\frac{C_L}{C_D}\ln\frac{m_1}{m_2}.$$

$$\boxed{R=9753.76\ \mathrm{km}\approx9754\ \mathrm{km}}$$

> [!warning] Model statement
> Strict constant-altitude flight with changing weight does not simultaneously hold $V$, $C_L$ and $L/D$ fixed. The result above follows the course calculator's stated constant-$L/D$ approximation.

## Answer check

| Question | Answer |
|---:|---:|
| 5 | $1691\ \mathrm{km}$ |
| 16 | $2.725\times10^{-4}\ \mathrm{s^{-1}}$ |
| 20 | $48.8\ \mathrm{min}$ |
| 27 | $1367\ \mathrm N$ fuel weight |
| 29 | $9754\ \mathrm{km}$ |

