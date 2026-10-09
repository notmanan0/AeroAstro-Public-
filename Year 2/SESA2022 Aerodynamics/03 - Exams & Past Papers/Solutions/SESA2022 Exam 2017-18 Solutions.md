---
title: "SESA2022 Exam 2017-18 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2017-18"
tags: [sesa2022, exam-solutions, past-papers]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-201718-01-SESA2022W1.pdf"]
---

# SESA2022 Exam 2017-18 Solutions

> [!info] Paper: 4 questions (20/30/30/20). Q4 is a repeat of 2016-17 Q3(i) and Q3(iii); see [[SESA2022 Exam 2016-17 Solutions]]. The rubric gives the TAT results $C_l = \pi(2A_0+A_1)$ and $C_{m,c/4} = \frac\pi4(A_2-A_1)$, so you don't need to derive them.

## Q1: Channel bend as a free vortex
Depth 1 m, $Q = 2$ m³/s, inner radius $r_i = 2$ m, outer radius $r_o = 4$ m. In a free vortex $V_\theta = \dfrac{K}{r}$ with $K = \dfrac{\Gamma}{2\pi}$ (see [[Elementary Potential Flows]]).

### (i) Circulation
The volume flow crosses a radial line of the bend:

$$
Q = h\int_{r_i}^{r_o}\frac Kr\,dr = hK\ln\frac{r_o}{r_i}\;\Rightarrow\;K = \frac{2}{1\cdot\ln2} = 2.885\text{ m}^2/\text{s}
$$

$$
\Gamma = 2\pi K = \boxed{18.13\text{ m}^2/\text{s}}
$$

### (ii) Velocities on the walls
In a free vortex $\boxed{V_r = 0}$ everywhere. The tangential velocities are

$$
V_{\theta,i} = \frac{2.885}{2} = \boxed{1.443\text{ m/s}},\qquad V_{\theta,o} = \frac{2.885}{4} = \boxed{0.721\text{ m/s}}
$$

### (iii) Pressure difference
The free vortex is irrotational, so Bernoulli holds across streamlines:

$$
p_o-p_i = \tfrac12\rho\left(V_i^2-V_o^2\right) = 500(2.0814-0.5203) = \boxed{781\text{ Pa}}
$$

The outer wall is at the higher pressure, which supplies the centripetal force that turns the flow.

## Q2: Microraptor tandem wings
$V = 5$ m/s, $\rho = 1.2$, $c = 0.1$ m, $Z = \frac x{10}(1-\frac xc)$. The front wing's $c/4$ is 0.1 m ahead of the CG and the rear wing's $c/4$ is 0.3 m behind it. $W' = 3\pi/4$ N/m.

### (i) Zero-lift angle
$\dfrac{dZ}{dx} = 0.1\cos\theta_0$, so $A_0 = \alpha$, $A_1 = 0.1$ and $A_{n\ge2} = 0$ (see [[SESA2022 Exam 2015-16 Solutions]]).

$$
C_l = \pi(2\alpha+0.1) = 2\pi(\alpha+0.05)\;\Rightarrow\;\boxed{\alpha_{L=0} = -0.05\text{ rad} = -2.86^\circ}
$$

### (ii) Quarter-chord moment

$$
A_2 = \frac2\pi\int_0^\pi0.1\cos\theta_0\cos2\theta_0\,d\theta_0 = 0\;\Rightarrow\;C_{m,c/4} = \frac\pi4(0-0.1) = \boxed{-0.0785}\;(=-\pi/40)
$$

This is independent of $\alpha$ because $c/4$ is the [[Aerodynamic Centre and Centre of Pressure|aerodynamic centre]].

### (iii) Trim angles
$q = \frac12(1.2)(5^2) = 15$ Pa. Per unit span, $qc = 1.5$ N/m and $M_{c/4} = qc^2C_{m,c/4} = -0.01178$ N (each wing).

**Vertical equilibrium**:

$$
L_f+L_r = W' = \frac{3\pi}4 = 2.356\text{ N/m}
$$

**Moments about the CG** (nose-up positive):

$$
0.1L_f-0.3L_r+2M_{c/4} = 0
$$

Substituting $L_r = W'-L_f$:

$$
0.4L_f = 0.3W'-2M_{c/4} = 0.7069+0.0236\;\Rightarrow\;L_f = 1.826\text{ N/m},\qquad L_r = 0.530\text{ N/m}
$$

$$
C_{l,f} = \frac{1.826}{1.5} = 1.217,\qquad C_{l,r} = \frac{0.530}{1.5} = 0.353
$$

$$
\alpha = \frac{C_l}{2\pi}+\alpha_{L=0}:\qquad \boxed{\alpha_f = 0.1438\text{ rad} = 8.24^\circ},\qquad \boxed{\alpha_r = 0.0063\text{ rad} = 0.36^\circ}
$$

### (iv) Comment
- The front wing carries **77.5 %** of the weight at a high $C_l\approx1.2$, close to a typical thin-section stall.
- The rear wing carries only **22.5 %** at almost zero geometric incidence. It mainly balances the moment, because the CG is much closer to the front wing (a lever arm of 0.1 m against 0.3 m).
- Both wings lift upwards. Unlike a conventional tailplane, the rear surface is not a download.
- Assuming undisturbed flow on the rear wing ignores the front wing's downwash, which would in reality reduce the rear wing's effective incidence (see [[Downwash and Induced Drag]]).

## Q3: Lifting line

### (i) $C_L = \pi AR\,B_1$
$L = \rho V_\infty\int\Gamma\,dy$ with $dy = \frac b2\sin\theta\,d\theta$:

$$
L = \rho V_\infty^2b^2\sum B_n\int_0^\pi\sin n\theta\sin\theta\,d\theta = \frac\pi2\rho V_\infty^2b^2B_1\;\Rightarrow\;\boxed{C_L = \frac{2L}{\rho V_\infty^2S} = \pi AR\,B_1}
$$

### (ii) Elliptic wing, $W = 73.6$ kN, $b = 15.23$ m, $V = 90$ m/s, sea level
See [[Elliptic Lift Distribution]]. $q = \frac12(1.225)(90^2) = 4961$ Pa.

**(a) Induced drag.** For elliptic loading, $D_i = \dfrac{L^2}{\pi qb^2}$ (independent of $S$), because $C_{D_i}qS = \frac{C_L^2qS}{\pi AR} = \frac{L^2}{\pi qb^2}$:

$$
D_i = \frac{73600^2}{\pi(4961)(15.23^2)} = \boxed{1498\text{ N}}
$$

**(b) Circulation.** $L = \rho V\Gamma_0\frac{\pi b}{4}$, so

$$
\Gamma_0 = \frac{4L}{\pi\rho Vb} = \frac{4(73600)}{\pi(1.225)(90)(15.23)} = 55.8\text{ m}^2/\text{s}\quad\text{(at the root)}
$$

Halfway along the semi-span ($y = b/4$):

$$
\Gamma = \Gamma_0\sqrt{1-\left(\frac{2y}{b}\right)^2} = 55.8\sqrt{0.75} = \boxed{48.3\text{ m}^2/\text{s}}
$$

### (iii) Elliptic wing, $AR = 6$, $b = 12$ m, $W/S = 900$ N/m², $V = 41.67$ m/s
$S = b^2/AR = 24$ m², $L = 21.6$ kN and $q = \frac12(1.225)(41.67^2) = 1063.5$ Pa.

$$
C_L = \frac{900}{1063.5} = 0.846,\qquad C_{D_i} = \frac{C_L^2}{\pi AR} = \frac{0.716}{6\pi} = 0.0380
$$

$$
D_i = qSC_{D_i} = 970\text{ N}\;\Rightarrow\;P_i = D_iV = \boxed{40.4\text{ kW}}
$$

**Lift-curve slope**, taking $a_0 = 2\pi$ (thin aerofoil) and $\tau = 0$ (elliptic):

$$
a = \frac{a_0}{1+\frac{a_0}{\pi AR}} = \frac{2\pi}{1+\frac26} = 4.71\text{ rad}^{-1}\;\Rightarrow\;\frac{a}{a_0} = 0.75
$$

That is a $\boxed{25\,\%}$ reduction, because induced downwash reduces the effective incidence.

## Q4
Repeat of 2016-17:
- **(i)** Blunt nose at $M = 4$: $M_2 = 0.435$, $p_2/p_1 = 18.5$, $p_{0,2} = \boxed{9.95\times10^5\text{ Pa}}$.
- **(ii)** Flat-plate CV: $D' = \rho U_\infty^2\theta$ and $\dfrac{d\theta}{dx} = \dfrac{\tau_w}{\rho U_\infty^2} = \dfrac{\nu}{U_\infty^2}\left.\dfrac{\partial u}{\partial y}\right|_0$ (see [[Momentum Integral Equation]]).

## Sources
- `03 - Exams & Past Papers/SESA2022-201718-01-SESA2022W1.pdf`. Numbers verified in Python.
