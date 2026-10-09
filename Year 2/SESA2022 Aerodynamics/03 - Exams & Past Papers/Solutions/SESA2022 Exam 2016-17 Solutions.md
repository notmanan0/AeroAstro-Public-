---
title: "SESA2022 Exam 2016-17 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2016-17"
tags: [sesa2022, exam-solutions, past-papers]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-201617-01-SESA2022W1.pdf"]
---

# SESA2022 Exam 2016-17 Solutions

> [!info] Paper: 3 questions (30/30/30). Q2 is **word-for-word identical** to 2015-16 Q2, so see [[SESA2022 Exam 2015-16 Solutions]]. Q3(i)–(ii) are gas dynamics (now SESA2023).

## Q1: Lifting cylinder, $\psi = V_\infty r\sin\theta\left(1-\frac{R^2}{r^2}\right)+\frac{\Gamma}{2\pi}\ln\frac rR$

### (i) Surface velocities and pressure
See [[Flow Past a Cylinder]].

$$
V_r = \frac1r\frac{\partial\psi}{\partial\theta} = V_\infty\cos\theta\left(1-\frac{R^2}{r^2}\right)\;\xrightarrow{r=R}\;\boxed{V_r = 0}
$$

$$
V_\theta = -\frac{\partial\psi}{\partial r} = -V_\infty\sin\theta\left(1+\frac{R^2}{r^2}\right)-\frac{\Gamma}{2\pi r}\;\xrightarrow{r=R}\;\boxed{V_\theta = -2V_\infty\sin\theta-\frac{\Gamma}{2\pi R}}
$$

Bernoulli between the freestream and the surface:

$$
\boxed{p(\theta) = p_\infty+\tfrac12\rho V_\infty^2\left[1-\left(2\sin\theta+\frac{\Gamma}{2\pi RV_\infty}\right)^2\right]}
$$

With this sign convention $\Gamma>0$ is **clockwise** and gives upward lift.

### (ii) Kutta–Joukowski by pressure integration
Let $k = \Gamma/(2\pi RV_\infty)$. The surface element $R\,d\theta$ has outward normal $(\cos\theta,\sin\theta)$, so the lift per unit span is

$$
L' = -\int_0^{2\pi}p\sin\theta\,R\,d\theta
$$

$p_\infty$ and the $\frac12\rho V_\infty^2$ constant integrate to zero against $\sin\theta$. Expanding $(2\sin\theta+k)^2 = 4\sin^2\theta+4k\sin\theta+k^2$, only the $4k\sin\theta$ term survives against $\sin\theta$ ($\int\sin^3 = \int\sin = 0$):

$$
L' = -R\cdot\tfrac12\rho V_\infty^2\int_0^{2\pi}(-4k\sin^2\theta)\,d\theta = 2\rho V_\infty^2Rk\,\pi = 2\pi R\rho V_\infty^2\frac{\Gamma}{2\pi RV_\infty} = \boxed{\rho V_\infty\Gamma}\;✔
$$

By the same symmetry the drag ($\int p\cos\theta$) is zero ([[D'Alembert's Paradox]]).

### (iii) $c_l = -2.8242$: $C_p$ at maximum speed
The reference area per unit span is the diameter, $S = 2R$:

$$
c_l = \frac{\rho V_\infty\Gamma}{\tfrac12\rho V_\infty^2(2R)} = \frac{\Gamma}{RV_\infty} = 2\pi k\;\Rightarrow\;k = \frac{-2.8242}{2\pi} = -0.4495
$$

The surface speed is $|2\sin\theta+k|$, maximised at $\sin\theta = -1$ ($\theta = 270^\circ$, the underside, as expected for downforce):

$$
\frac{V_{max}}{V_\infty} = 2+0.4495 = 2.4495 = \sqrt6\quad\Rightarrow\quad C_{p,min} = 1-6 = \boxed{-5.00}
$$

### (iv) Stagnation point and $|V| = V_\infty$
- **Stagnation**: $\boxed{C_p = 1}$, at $\sin\theta = -k/2 = 0.2247$, i.e. $\theta = 13.0^\circ$ and $167.0^\circ$ (both on the **upper** surface, since circulation is anticlockwise).
- **$|V| = V_\infty$**: $\boxed{C_p = 0}$, at $2\sin\theta+k = \pm1$, i.e. $\sin\theta = 0.725$ ($46.4^\circ$, $133.6^\circ$) or $\sin\theta = -0.275$ ($196.0^\circ$, $344.0^\circ$).

![[e1617_q1_cylinder_cp.png|650]]

## Q2: TAT and lifting-line bookwork
Identical to 2015-16:
- $c_\ell = \pi(2A_0+A_1)$
- $c_\ell = 0.2\pi = \boxed{0.628}$ at $\alpha = 0.05$
- $C_L = \pi AR\,B_1$
- $C_{D_i} = \dfrac{C_L^2}{\pi AR}(1+\delta)$ with $\delta = \sum_{n\ge2}n(B_n/B_1)^2$

## Q3

### (i) Blunt missile, $M_1 = 4$, $p_1 = 4.722\times10^4$ Pa, $T_1 = 249.2$ K
The stagnation point sits behind a normal shock, so find the post-shock state and then decelerate isentropically to rest (see [[Normal Shock Waves]]).

$$
M_2^2 = \frac{1+0.2(16)}{1.4(16)-0.2} = \frac{4.2}{22.2} = 0.1892\;\Rightarrow\;M_2 = 0.435
$$

$$
\frac{\rho_2}{\rho_1} = \frac{2.4(16)}{2+0.4(16)} = 4.571,\qquad \frac{T_2}{T_1} = \frac{T_0/T_1}{T_0/T_2} = \frac{1+0.2(16)}{1+0.2(0.1892)} = \frac{4.2}{1.0378} = 4.047
$$

$$
\frac{p_2}{p_1} = \frac{\rho_2}{\rho_1}\frac{T_2}{T_1} = 18.50\;\Rightarrow\;p_2 = 8.736\times10^5\text{ Pa}
$$

$$
p_{0,2} = p_2\left(1+0.2M_2^2\right)^{3.5} = 8.736\times10^5\times1.1387 = \boxed{9.95\times10^5\text{ Pa}\;(\approx9.9\text{ bar})}
$$

(This is 21.1 × ambient. The shock loses about 86 % of the freestream stagnation pressure, which is $p_1(4.2)^{3.5} = 7.19\times10^6$ Pa.)

### (ii) Area–velocity relation
**Assumptions**: steady, quasi-1D, inviscid, isentropic.
- Continuity: $\dfrac{d\rho}\rho+\dfrac{dV}V+\dfrac{dA}A = 0$.
- Euler: $dp = -\rho V\,dV$.
- Isentropic: $dp = a^2d\rho$, so $\dfrac{d\rho}{\rho} = -M^2\dfrac{dV}{V}$.

Combining:

$$
\boxed{\frac{dA}{A} = (M^2-1)\frac{dV}{V}}
$$

Subsonic flow accelerates in a converging duct, supersonic flow in a diverging duct, and $M = 1$ only at a throat (see [[Isentropic Nozzle Flow]]).

### (iii) Flat-plate drag ∝ $\theta$, and the momentum integral equation
Take a control volume from the leading edge ($x=0$, uniform inflow $U_\infty$ over height $h$) to station $x$, with its upper boundary at $y = h>\delta$ (see [[Momentum Integral Equation]]).

**Mass.** Inflow $\rho U_\infty h$ exceeds the outflow at $x$, $\int_0^h\rho u\,dy$. The difference leaves through the top at velocity $\approx U_\infty$ in the $x$-direction:

$$
\dot m_{top} = \int_0^h\rho(U_\infty-u)\,dy
$$

**$x$-momentum.** With zero pressure gradient, the only force is wall friction $-D'$ (the drag on the plate, reversed):

$$
-D' = \underbrace{\int_0^h\rho u^2\,dy}_{\text{out at }x}+\underbrace{U_\infty\int_0^h\rho(U_\infty-u)\,dy}_{\text{out top}}-\underbrace{\rho U_\infty^2h}_{\text{in}}
$$

$$
D' = \rho\int_0^h u(U_\infty-u)\,dy = \rho U_\infty^2\int_0^\infty\frac{u}{U_\infty}\left(1-\frac{u}{U_\infty}\right)dy = \boxed{\rho U_\infty^2\,\theta(x)}
$$

So the drag up to $x$ equals the momentum deficit in the wake.

**MIE.** $D'(x) = \int_0^x\tau_w\,dx$, so $dD'/dx = \tau_w$:

$$
\boxed{\frac{d\theta}{dx} = \frac{\tau_w}{\rho U_\infty^2} = \frac{C_f}{2} = \frac{\nu}{U_\infty^2}\left.\frac{\partial u}{\partial y}\right|_{y=0}}
$$

This is von Kármán's momentum integral equation for $dp/dx = 0$. With a pressure gradient it gains a term: $\frac{d\theta}{dx}+(2+H)\frac{\theta}{U_e}\frac{dU_e}{dx} = \frac{C_f}{2}$.

## Sources
- `03 - Exams & Past Papers/SESA2022-201617-01-SESA2022W1.pdf`. Numbers verified in Python.
