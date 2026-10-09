---
title: "SESA2022 Examples Sheet 6 - Static Stability Solutions"
module: "SESA2022 Aerodynamics"
type: tutorial
stream: "Topic 6: Aircraft Aerodynamics and Static Stability"
tags:
  - sesa2022
  - tutorial-solutions
  - static-stability
sheet: "Examples Sheet 6"
theory_notes: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
key_concepts: ["[[Neutral Point and Static Margin]]", "[[Stick-Fixed vs Stick-Free Stability]]", "[[Manoeuvre Point and Manoeuvre Margin]]"]
status: complete
sources: ["02 - Sources/Stability/Examples6.pdf"]
---

# SESA2022 Examples Sheet 6 - Static Stability Solutions

> [!abstract] Sheet Info
> All given answers are reproduced ✔: Q1 ($3.11^\circ$, $9.083^\circ$, $0^\circ$); Q2 ($3.44^\circ$, $10.44^\circ$, $-5.31^\circ$); Q3 ($H_s = 0.297$, $0.273$; $H_m = 0.409$).

## Table 1

| | | |
|---|---|---|
| $A = 8$ | $e = 0.90$ | $S = 20$ m² |
| $l = 7.0$ m | $h_0 = 0.25$ | $h = 0.4$ |
| $C_{M_0} = -0.01$ | $c = 1.58$ m | |
| $\alpha_0 = -2^\circ$ | $a_0 = 2\pi$ rad⁻¹ | $\alpha_s = -6^\circ$ |
| $A_T = 7$ | $e_T = 0.85$ | $S_T = 3$ m² |
| $a_1 = 2\pi$ rad⁻¹ | $a_2 = 3.5$ rad⁻¹ | $a_3 = 1.1$ rad⁻¹ |
| $b_1 = -0.1$ rad⁻¹ | $b_2 = -0.7$ rad⁻¹ | $b_3 = -1.3$ rad⁻¹ |
| $m = 1500$ kg | $V = 50$ m/s | $\rho = 1.225$ kg/m³ |

**Derived constants** (used throughout):

$$
K = \frac{S_Tl}{Sc} = \frac{3(7)}{20(1.58)} = 0.66456,\qquad C_{L_\alpha} = a_0\frac{\pi Ae}{\pi Ae+a_0} = 2\pi\frac{22.619}{22.619+6.283} = 4.9173\text{ rad}^{-1}
$$

$$
\epsilon_\alpha = \frac{C_{L_\alpha}}{\pi Ae} = \frac{4.9173}{22.619} = 0.21739,\qquad \pi A_Te_T = \pi(7)(0.85) = 18.692,\qquad C_W = \frac{mg}{\tfrac12\rho V^2S} = \frac{14715}{30625} = 0.48049
$$

## Theory Links
- [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]] (solution algorithm §6.2)

## Q1: Stick-fixed climb at $\gamma = 20^\circ$. Find $\alpha$, $\eta$, $\beta$.

### Solution
1. **Force balance**: $C_{L^*} = C_W\cos\gamma = 0.48049\cos20^\circ = 0.45151$
2. **Moment balance**: $C_{L_T} = \dfrac{C_{M_0}+C_{L^*}(h-h_0)}{K} = \dfrac{-0.01+0.45151(0.15)}{0.66456} = 0.08687$
3. **Wing lift**: $C_L = C_{L^*}-C_{L_T}\dfrac{S_T}{S} = 0.45151-0.08687(0.15) = 0.43848$
4. **Angle of attack**: $\alpha = \alpha_0+\dfrac{C_L}{C_{L_\alpha}} = -0.034907+\dfrac{0.43848}{4.9173} = 0.05426\text{ rad} = \boxed{3.11^\circ}$
5. **Tail effective angle**:

$$
\alpha_{T_{eff}} = (1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T}
$$

$$
= 0.78261(0.05426)+0.21739(-0.034907)-0.10472-\frac{0.08687}{18.692} = -0.07449\text{ rad}\;(-4.27^\circ)
$$

6. **Stick fixed** means $\beta = 0$:

$$
\eta = \frac{C_{L_T}-a_1\alpha_{T_{eff}}}{a_2} = \frac{0.08687+2\pi(0.07449)}{3.5} = 0.15853\text{ rad} = \boxed{9.083^\circ},\qquad \boxed{\beta = 0^\circ}
$$

## Q2: Stick-free, low-altitude cruise ($\gamma = 0$). Find $\alpha$, $\eta$, $\beta$.

### Solution
1. $C_{L^*} = C_W = 0.48049$
2. $C_{L_T} = \dfrac{-0.01+0.48049(0.15)}{0.66456} = 0.09341$
3. $C_L = 0.48049-0.09341(0.15) = 0.46648$
4. $\alpha = -0.034907+\dfrac{0.46648}{4.9173} = 0.05996\text{ rad} = \boxed{3.44^\circ}$
5. $\alpha_{T_{eff}} = 0.78261(0.05996)-0.007588-0.10472-\dfrac{0.09341}{18.692} = -0.07039$ rad
6. **Stick free**: solve the tail-lift and zero-hinge-moment equations together:

$$
\begin{aligned}
a_2\eta+a_3\beta &= C_{L_T}-a_1\alpha_{T_{eff}} = 0.53568\\
b_2\eta+b_3\beta &= -b_1\alpha_{T_{eff}} = -0.007039
\end{aligned}
\quad\Rightarrow\quad
\begin{pmatrix}3.5&1.1\\-0.7&-1.3\end{pmatrix}\begin{pmatrix}\eta\\\beta\end{pmatrix} = \begin{pmatrix}0.53568\\-0.007039\end{pmatrix}
$$

$$
\eta = 0.18216\text{ rad} = \boxed{10.44^\circ},\qquad \beta = -0.09268\text{ rad} = \boxed{-5.31^\circ}
$$

The tab is deflected up (negative) to hold the elevator down with zero stick force.

## Q3: Altitude with $\rho = 0.855$ kg/m³ ($C_D = 0.004$ is not needed)

### (a) Stick-fixed static margin

$$
k = a_1\frac{\pi A_Te_T}{\pi A_Te_T+a_1} = 6.2832\frac{18.692}{24.975} = 4.7025,\qquad C_{L_{T,\alpha}} = k(1-\epsilon_\alpha) = 3.6802
$$

$$
C_{L^*_\alpha} = C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S} = 4.9173+0.5520 = 5.4693
$$

$$
H_s = h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}} = 0.25-0.4+0.66456\frac{3.6802}{5.4693} = \boxed{0.297}
$$

Positive, so the aircraft is statically stable. The neutral point is at $h_n = 0.697$.

### (b) Stick-free static margin

$$
\bar a_1 = a_1-a_2\frac{b_1}{b_2} = 6.2832-3.5\frac{-0.1}{-0.7} = 5.7832,\qquad \bar k = 5.7832\frac{18.692}{18.692+5.7832} = 4.4167
$$

$$
C_{L_{T,\alpha}} = 4.4167(0.78261) = 3.4566,\qquad C_{L^*_\alpha} = 4.9173+0.5185 = 5.4358
$$

$$
H_s = -0.15+0.66456\frac{3.4566}{5.4358} = \boxed{0.273}
$$

This is lower than stick-fixed, as expected (floating elevator).

### (c) Stick-fixed manoeuvre margin

$$
\Phi = \frac{\rho Sl}{2m} = \frac{0.855(20)(7)}{3000} = 0.0399
$$

$$
C_{L_{T,\alpha}} = k\frac{1-\epsilon_\alpha+\Phi C_{L_\alpha}}{1-k\Phi\frac{S_T}{S}} = 4.7025\frac{0.78261+0.0399(4.9173)}{1-4.7025(0.0399)(0.15)} = 4.7362
$$

$$
H_m = h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}} = -0.15+0.66456\frac{4.7362}{5.6277} = \boxed{0.409}
$$

$H_m > H_s$: the aircraft is more stable in manoeuvres because of pitch damping.

```python
import numpy as np; pi=np.pi
A,e,S,l,h0,h,c,AT,eT,ST=8,.9,20,7,.25,.4,1.58,7,.85,3; a1,a2,b1,b2=2*pi,3.5,-.1,-.7
K=ST*l/(S*c); CLa=2*pi*pi*A*e/(pi*A*e+2*pi); ea=CLa/(pi*A*e)
k=lambda a: a*pi*AT*eT/(pi*AT*eT+a)
Hs=lambda kk: h0-h+K*kk*(1-ea)/(CLa+kk*(1-ea)*ST/S)
print(Hs(k(a1)), Hs(k(a1-a2*b1/b2)))          # 0.2972 0.2726
```

## Sources
- `02 - Sources/Stability/Examples6.pdf`; worked through with the lecture algorithm (Topic 6 slides 77–81)
