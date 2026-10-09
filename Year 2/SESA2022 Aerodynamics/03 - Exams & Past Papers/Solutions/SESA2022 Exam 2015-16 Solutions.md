---
title: "SESA2022 Exam 2015-16 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2015-16"
tags: [sesa2022, exam-solutions, past-papers]
topics: ["[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-201516-01-SESA2022W1.pdf"]
---

# SESA2022 Exam 2015-16 Solutions

> [!info] Paper: 3 questions (25/30/20). This is almost pure bookwork: a Rankine oval, the TAT and lifting-line derivations, and gas dynamics (Q3, now in SESA2023; see [[Normal Shock Waves]] and [[Isentropic Nozzle Flow]]).

## Q1: Rankine oval

### (i) Derivative of $\tan^{-1}$
Let $f = \tan^{-1}g$, so $\tan f = g$. Differentiating:

$$
\sec^2 f\,\frac{df}{dx} = \frac{dg}{dx}\;\Rightarrow\;\boxed{\frac{df}{dx} = \cos^2 f\,\frac{dg}{dx}}
$$

Equivalently $\cos^2 f = \frac{1}{1+g^2}$, which is the usual $\frac{d}{dx}\tan^{-1}g = \frac{g'}{1+g^2}$.

### (ii) Stagnation points of $\psi = y+\sigma\left[\tan^{-1}\frac{y}{x+1}-\tan^{-1}\frac{y}{x-1}\right]$
This is a dimensionless source at $(-1,0)$ and sink at $(1,0)$, each of strength $2\pi\sigma$, in a unit freestream (see [[Rankine Oval]]). Using (i):

$$
\frac{\partial}{\partial y}\tan^{-1}\frac{y}{x\pm1} = \frac{x\pm1}{(x\pm1)^2+y^2},\qquad \frac{\partial}{\partial x}\tan^{-1}\frac{y}{x\pm1} = \frac{-y}{(x\pm1)^2+y^2}
$$

$$
u = \frac{\partial\psi}{\partial y} = 1+\sigma\left[\frac{x+1}{(x+1)^2+y^2}-\frac{x-1}{(x-1)^2+y^2}\right],\qquad v = -\frac{\partial\psi}{\partial x} = \sigma\left[\frac{y}{(x+1)^2+y^2}-\frac{y}{(x-1)^2+y^2}\right]
$$

$v=0$ requires $y=0$ (or $x=0$, but there $u>0$). On $y=0$:

$$
u = 1+\sigma\left[\frac1{x+1}-\frac1{x-1}\right] = 1-\frac{2\sigma}{x^2-1} = 0\;\Rightarrow\;\boxed{x_s = \pm\sqrt{1+2\sigma},\quad y_s = 0}
$$

On the axis outside the singularities, $\theta_1 = \theta_2$ (both $0$ downstream, both $\pi$ upstream), so $\boxed{\psi_s = 0}$. The oval is the $\psi = 0$ streamline. For $\sigma = 0.2335$, $x_s = \pm1.211$.

### (iii) Half-thickness and $C_p$ at the top ($\sigma = 0.2335$)
At the top, $x = 0$. There $\theta_1 = \tan^{-1}y$ and $\theta_2 = \pi-\tan^{-1}y$, so $\psi = 0$ gives

$$
y_{top}+\sigma\left(2\tan^{-1}y_{top}-\pi\right) = 0
$$

**Slender-body approximation** ($\theta_1\ll1$, so $\tan^{-1}y\approx y$):

$$
y_{top}(1+2\sigma) = \pi\sigma\;\Rightarrow\;y_{top} = \frac{\pi\sigma}{1+2\sigma} = \frac{0.7336}{1.467} = \boxed{0.500}
$$

(The exact root is $0.512$, so the approximation is about 2 % low.)

**Velocity at the top.** At $x=0$, $v=0$ by symmetry and

$$
u = 1+\sigma\left[\frac{1}{1+y^2}+\frac{1}{1+y^2}\right] = 1+\frac{2\sigma}{1+y_{top}^2} = 1+\frac{0.467}{1.25} = 1.374
$$

$$
C_p = 1-\frac{u^2}{V_\infty^2} = 1-1.374^2 = \boxed{-0.887}
$$

(With the exact $y_{top}$: $C_p = -0.877$.) The top is the point of maximum velocity and minimum pressure.

## Q2: TAT and lifting-line bookwork

### (i) $c_\ell$ from the Fourier coefficients
$d\xi = \frac c2\sin\theta\,d\theta$:

$$
\Gamma = \int_0^c\gamma\,d\xi = cV_\infty\int_0^\pi\left[A_0(1+\cos\theta)+\sum A_n\sin n\theta\sin\theta\right]d\theta = cV_\infty\left(\pi A_0+\frac\pi2A_1\right)
$$

using $\int_0^\pi\sin n\theta\sin\theta\,d\theta = \frac\pi2\delta_{n1}$. Kutta–Joukowski ($L' = \rho V_\infty\Gamma$) gives

$$
c_\ell = \frac{2\Gamma}{V_\infty c} = \boxed{\pi(2A_0+A_1)}
$$

### (ii) $Z = \frac x{10}\left(1-\frac xc\right)$, $\alpha = 0.05$ rad
$\dfrac{dZ}{dx} = 0.1(1-2x/c) = 0.1\cos\theta_0$:

$$
A_0 = \alpha-\frac{0.1}\pi\int_0^\pi\cos\theta_0\,d\theta_0 = \alpha = 0.05,\qquad A_1 = \frac2\pi\int_0^\pi0.1\cos^2\theta_0\,d\theta_0 = 0.1
$$

$$
c_\ell = \pi(2\times0.05+0.1) = 0.2\pi = \boxed{0.628}
$$

Equivalently $\alpha_{L=0} = -0.05$ rad and $c_\ell = 2\pi(0.05+0.05)$. The same camber line appears in [[SESA2022 Exam 2014-15 Solutions]].

### (iii) $C_L$ from $\Gamma(\theta) = 2bV_\infty\sum B_n\sin n\theta$
$y = -\frac b2\cos\theta$, so $dy = \frac b2\sin\theta\,d\theta$:

$$
L = \rho V_\infty\int_{-b/2}^{b/2}\Gamma\,dy = \rho V_\infty^2b^2\sum B_n\int_0^\pi\sin n\theta\sin\theta\,d\theta = \frac\pi2\rho V_\infty^2b^2B_1
$$

$$
C_L = \frac{2L}{\rho V_\infty^2S} = \pi B_1\frac{b^2}{S} = \boxed{\pi AR\,B_1}
$$

Only $B_1$ produces lift.

### (iv) $C_{D_i}$
The induced drag is the lift tilted back by $\alpha_i$: $D_i = \rho V_\infty\int\Gamma\alpha_i\,dy$ (see [[Downwash and Induced Drag]]).

$$
D_i = \rho V_\infty\int_0^\pi\left(2bV_\infty\sum_nB_n\sin n\theta\right)\left(\sum_m mB_m\frac{\sin m\theta}{\sin\theta}\right)\frac b2\sin\theta\,d\theta = \rho V_\infty^2b^2\sum_n\sum_m mB_nB_m\int_0^\pi\sin n\theta\sin m\theta\,d\theta
$$

Orthogonality ($\int_0^\pi\sin n\theta\sin m\theta\,d\theta = \frac\pi2\delta_{nm}$) leaves

$$
D_i = \frac\pi2\rho V_\infty^2b^2\sum_n nB_n^2\;\Rightarrow\;C_{D_i} = \pi AR\sum_{n}nB_n^2
$$

Substituting $B_1 = C_L/(\pi AR)$:

$$
\boxed{C_{D_i} = \pi AR\,B_1^2\left[1+\sum_{n\ge2}n\left(\frac{B_n}{B_1}\right)^2\right] = \frac{C_L^2}{\pi AR}(1+\delta)},\qquad \delta = \sum_{n\ge2}n\left(\frac{B_n}{B_1}\right)^2\ge0
$$

Since $\delta\ge0$, the **elliptic** distribution ($B_n = 0$ for $n\ge2$) gives the minimum induced drag (see [[Elliptic Lift Distribution]]).

## Q3: Gas dynamics

### (i) Prandtl relation $a^{*2} = u_1u_2$
1. Divide momentum by continuity: $\dfrac{p_1}{\rho_1u_1}-\dfrac{p_2}{\rho_2u_2} = u_2-u_1$. With $p/\rho = a^2/\gamma$, this becomes $\dfrac{a_1^2}{\gamma u_1}-\dfrac{a_2^2}{\gamma u_2} = u_2-u_1$.
2. Energy: $c_pT = \frac{a^2}{\gamma-1}$, so $\frac{a^2}{\gamma-1}+\frac{u^2}{2} = $ const $= \frac{a^{*2}}{\gamma-1}+\frac{a^{*2}}2 = \frac{\gamma+1}{2(\gamma-1)}a^{*2}$ (evaluated at the sonic state). Hence $a_{i}^2 = \frac{\gamma+1}{2}a^{*2}-\frac{\gamma-1}{2}u_i^2$.
3. Substitute into step 1:

$$
\frac{\gamma+1}{2\gamma}a^{*2}\left(\frac1{u_1}-\frac1{u_2}\right)-\frac{\gamma-1}{2\gamma}(u_1-u_2) = u_2-u_1
$$

$$
\frac{\gamma+1}{2\gamma}a^{*2}\frac{u_2-u_1}{u_1u_2} = \left(1-\frac{\gamma-1}{2\gamma}\right)(u_2-u_1) = \frac{\gamma+1}{2\gamma}(u_2-u_1)
$$

4. Across a shock $u_1\ne u_2$, so $\boxed{a^{*2} = u_1u_2}$.

### (ii) Choked mass flow
At the throat $M=1$, so $u^* = a^* = \sqrt{\gamma RT^*}$ and $\rho^* = p^*/(RT^*)$:

$$
\dot m = \rho^*u^*A^* = \frac{p^*}{RT^*}\sqrt{\gamma RT^*}A^* = p^*A^*\sqrt{\frac{\gamma}{RT^*}}
$$

From $T_0/T = 1+\frac{\gamma-1}2M^2$ at $M=1$: $\dfrac{T^*}{T_0} = \dfrac2{\gamma+1}$ and $\dfrac{p^*}{p_0} = \left(\dfrac2{\gamma+1}\right)^{\gamma/(\gamma-1)}$. Then

$$
\dot m = p_0A^*\sqrt{\frac{\gamma}{RT_0}}\left(\frac2{\gamma+1}\right)^{\frac{\gamma}{\gamma-1}-\frac12} = p_0A^*\sqrt{\frac{\gamma}{RT_0}}\left(\frac2{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}
$$

$$
\boxed{\dot m = \frac{p_0A^*}{\sqrt{T_0}}\sqrt{\frac\gamma R\left(\frac2{\gamma+1}\right)^{\frac{\gamma+1}{\gamma-1}}}}
$$

For air, $\sqrt{\cdot} = 0.0404\text{ s K}^{1/2}\text{ m}^{-1}$. The mass flow depends only on $p_0$, $T_0$ and $A^*$, so a choked nozzle can't pass more flow by lowering the back pressure.

## Sources
- `03 - Exams & Past Papers/SESA2022-201516-01-SESA2022W1.pdf`. Numbers verified in Python.
