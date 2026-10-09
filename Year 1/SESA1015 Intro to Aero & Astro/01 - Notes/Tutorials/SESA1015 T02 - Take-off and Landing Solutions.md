---
title: "SESA1015 T02 - Take-off and Landing Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 2
tags: [sesa1015, tutorial, takeoff, landing]
aliases: ["SESA1015 Revision Q3 Q7 Q19 Q21 Q22 Q23 Q24 Q28 Q38 Q39 Q40"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M09 - Take-off and Landing Performance]]"]
sources: ["02 - Sources/Mechanics of Flight/Calculator for Revision Questions.xlsx"]
---

# SESA1015 T02 - Take-off and Landing Solutions

> [!abstract] Shared approximation
> These workbook questions neglect lift and aerodynamic drag during the ground roll, giving constant acceleration $a=g(T/W-\mu)$. Hence
>
> $$\boxed{s_1=\frac{V_2^2}{2g(T/W-\mu)}}.$$
>
> Use the written prompt values. This is a deliberately simpler model than [[Take-off Ground Run]].

## Question 3 — total thrust for a 1500 m runway

Given $b=41.2\ \mathrm m$, $AR=11.7$, $C_{L,max}=2.26$, $m=70856\ \mathrm{kg}$, $\mu=0.02$ and $V_2=1.2V_s$.

$$S=\frac{b^2}{AR}=145.08\ \mathrm{m^2},\qquad W=mg.$$

$$V_s=\sqrt{\frac{2W}{\rho_0SC_{L,max}}},\qquad V_2=1.2V_s.$$

Rearrange the ground-run formula:

$$\frac TW=\mu+\frac{V_2^2}{2gs_1}.$$

Then $T=W(T/W)$, giving

$$\boxed{T=131619\ \mathrm N}$$

for total aircraft thrust. If equal engines are assumed, each of the two engines supplies half.

## Question 7 — all-engines take-off run

Given $b=51\ \mathrm m$, $AR=8$, $C_{L,TO}=1.7$, $W=2763\ \mathrm{kN}$, $T/W=0.22$, $\mu=0.01$ and $V_2=1.19V_s$:

$$S=\frac{51^2}{8}=325.125\ \mathrm{m^2},$$

$$V_s=\sqrt{\frac{2W}{\rho_0SC_{L,TO}}},\qquad V_2=1.19V_s.$$

$$s_1=\frac{V_2^2}{2g(0.22-0.01)}.$$

$$\boxed{s_1=2805\ \mathrm m}$$

## Question 19 — ground run from stated stall speed

$$V_2=1.2(123)=147.6\ \mathrm{m,s^{-1}}.$$

$$s_1=\frac{147.6^2}{2(9.81)(0.35-0.06)}.$$

$$\boxed{s_1=3828.9\ \mathrm m}$$

## Inverse problems: Questions 21–24

For these questions first obtain

$$V_2=\sqrt{2gs_1(T/W-\mu)},\qquad V_s=\frac{V_2}{K},$$

then

$$\boxed{C_L=\frac{2(W/S)}{\rho_0V_s^2}}.$$

### Question 21

$$S=\frac{64.5^2}{8.14},\qquad W=396890g,$$

$$V_2^2=2g(2834)(0.27-0.02),\qquad K=1.2.$$

$$\boxed{C_{L,TO}=1.288}$$

### Question 22

Using $S=367\ \mathrm{m^2}$, $m=224152\ \mathrm{kg}$, $s_1=2614\ \mathrm m$, $T/W=0.30$, $\mu=0.02$ and $K=1.2$:

$$\boxed{C_{L,TO}=0.981}$$

### Question 23

$$S=\frac{70.9^2}{9},\quad W=5.472\times10^6\ \mathrm N,\quad K=1.28,$$

with $s_1=1774\ \mathrm m$, $T/W=0.25$, $\mu=0.02$:

$$\boxed{C_{L,TO}=3.274}$$

This unusually high result is a useful plausibility warning: the simplified inputs imply a demanding high-lift requirement.

### Question 24

$$S=\frac{82.7^2}{9.7},\quad W=4.701690\times10^6\ \mathrm N,\quad K=1.2,$$

with $s_1=1800\ \mathrm m$, $T/W=0.33$, $\mu=0.02$:

$$\boxed{C_{L,TO}=1.432}$$

## Question 28 — summer versus winter runway roll

At the same sea-level pressure, the perfect-gas law gives $\rho=p/(RT)$. For the same aircraft/configuration, required true lift-off speed squared scales as $1/\rho$, and the simplified acceleration factor is unchanged. Hence $s\propto1/\rho\propto T$.

$$T_w=278.15\ \mathrm K,\qquad T_s=319.15\ \mathrm K.$$

$$\frac{s_s-s_w}{s_w}=\frac{T_s}{T_w}-1=0.147402.$$

$$\boxed{\text{Summer ground roll is }14.74\%\text{ longer.}}$$

## Question 38 — take-off thrust loading only

Given $s_1=85\ \mathrm m$, $V_2=21.8\ \mathrm{m,s^{-1}}$ and $\mu=0.18$:

$$\frac TW=\mu+\frac{V_2^2}{2gs_1}
=0.18+\frac{21.8^2}{2(9.81)(85)}.$$

$$\boxed{T/W=0.465\approx0.46}$$

The turn data are distractors because the prompt explicitly asks for the take-off constraint only.

## Question 39 — landing wing-loading limit

Taking the supplied approach speed as the limiting speed for this simplified constraint,

$$\frac WS=\frac12\rho_0V_A^2C_{L,max}.$$

$$\frac WS=\frac12(1.225)(16.7)^2(1.10).$$

$$\boxed{W/S=187.90\ \mathrm{N,m^{-2}}}$$

## Question 40 — required $C_{L,max}$ comparison

The prompt is an embedded image. Both airliners have the same minimum landing speed, while

$$\left(\frac WS\right)_A=3077\ \mathrm{N,m^{-2}},\qquad
\left(\frac WS\right)_B=4306\ \mathrm{N,m^{-2}}.$$

At equal $V$ and $\rho$, $C_{L,max}\propto W/S$:

$$\frac{C_{L,max,B}}{C_{L,max,A}}=\frac{4306}{3077}=1.399415.$$

$$\boxed{C_{L,max,B}\text{ is }39.94\%\approx40\%\text{ greater.}}$$

## Answer check

| Question | Answer |
|---:|---:|
| 3 | $131619\ \mathrm N$ total thrust |
| 7 | $2805\ \mathrm m$ |
| 19 | $3828.9\ \mathrm m$ |
| 21 | $C_L=1.288$ |
| 22 | $C_L=0.981$ |
| 23 | $C_L=3.274$ |
| 24 | $C_L=1.432$ |
| 28 | $14.74\%$ longer in summer |
| 38 | $T/W=0.465$ |
| 39 | $187.90\ \mathrm{N,m^{-2}}$ |
| 40 | $39.94\%$ |

