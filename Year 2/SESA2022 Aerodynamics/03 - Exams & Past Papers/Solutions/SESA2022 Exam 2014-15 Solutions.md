---
title: "SESA2022 Exam 2014-15 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2014-15"
tags: [sesa2022, exam-solutions, past-papers]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-201415-01-SESA2022W1.pdf"]
---

# SESA2022 Exam 2014-15 Solutions

> [!info] Paper: 120 min, 4 questions (20/20/15/20). Q1(iv)–(v) and Q4(i)–(ii) are **identical** to [[SESA2022 Exam 2013-14 Solutions]]. Q4 (compressible nozzles) is from the older syllabus and is now in SESA2023; see [[Isentropic Nozzle Flow]] and [[Normal Shock Waves]].

## Q1

### (i) Sine profile $u/U_e = \sin(\pi\eta/2)$
**(a) Displacement thickness** (see [[Displacement and Momentum Thickness]]):

$$
\frac{\delta^*}{\delta} = \int_0^1\left(1-\sin\frac{\pi\eta}{2}\right)d\eta = 1-\frac{2}{\pi}\left[-\cos\frac{\pi\eta}{2}\right]_0^1 = 1-\frac2\pi = \boxed{0.3634}
$$

(For completeness: $\theta/\delta = \int_0^1 \sin(1-\sin)\,d\eta = \frac2\pi-\frac12 = 0.1366$, so $H = 2.66$, which is close to Blasius.)

**(b) Skin friction.** Wall shear stress:

$$
\tau_w = \mu\left.\frac{\partial u}{\partial y}\right|_{0} = \frac{\mu U_e}{\delta}\left.\frac{\pi}{2}\cos\frac{\pi\eta}{2}\right|_{\eta=0} = \frac{\pi\mu U_e}{2\delta}
$$

$$
C_f = \frac{\tau_w}{\tfrac12\rho U_e^2} = \frac{\pi\mu U_e/(2\delta)}{\tfrac12\rho U_e^2} = \boxed{\frac{\pi\mu}{\delta\rho U_e}}\;✔
$$

### (ii) Irrotationality: $u_r = -\dfrac{a\cos\theta}{2\pi r^2}$, $u_\theta = -\dfrac{a\sin\theta}{2\pi r^2}-\dfrac{b}{2\pi r}$

$$
ru_\theta = -\frac{a\sin\theta}{2\pi r}-\frac{b}{2\pi}\;\Rightarrow\;\frac{\partial(ru_\theta)}{\partial r} = \frac{a\sin\theta}{2\pi r^2},\qquad \frac{\partial u_r}{\partial\theta} = \frac{a\sin\theta}{2\pi r^2}
$$

$$
\omega_z = \frac1r\frac{a\sin\theta}{2\pi r^2}-\frac1r\frac{a\sin\theta}{2\pi r^2} = \boxed{0}\;✔
$$

This is a **doublet** (strength $a$) plus a **vortex** ($\Gamma = b$). Both are irrotational, so the sum is too (see [[Elementary Potential Flows]]).

### (iii) Streamfunction
From $u_r = \frac1r\frac{\partial\psi}{\partial\theta}$:

$$
\frac{\partial\psi}{\partial\theta} = -\frac{a\cos\theta}{2\pi r}\;\Rightarrow\;\psi = -\frac{a\sin\theta}{2\pi r}+f(r)
$$

From $u_\theta = -\frac{\partial\psi}{\partial r}$:

$$
-\frac{a\sin\theta}{2\pi r^2}-f'(r) = -\frac{a\sin\theta}{2\pi r^2}-\frac{b}{2\pi r}\;\Rightarrow\;f = \frac{b}{2\pi}\ln r
$$

$$
\boxed{\psi = -\frac{a\sin\theta}{2\pi r}+\frac{b}{2\pi}\ln r\;(+C)}
$$

### (iv) Rectangular wing, $AR = 6$, $\delta = \tau = 0.055$, $\alpha_{L=0} = -2^\circ$, $C_{D_i} = 0.01$ at $3.4^\circ$
Same as 2013-14 (see [[Downwash and Induced Drag]]):

$$
C_L = \sqrt{\frac{C_{D_i}\pi AR}{1+\delta}} = \boxed{0.4227},\qquad a = \frac{0.4227}{5.4^\circ} = \boxed{4.485\text{ rad}^{-1}}\;(0.0783/^\circ)
$$

$$
a_0 = \frac{a}{1-\frac{a(1+\tau)}{\pi AR}} = \boxed{5.988\text{ rad}^{-1}}
$$

### (v) Same sections, $AR = 10$, $\delta = \tau = 0.105$

$$
a = \frac{5.988}{1+\frac{5.988(1.105)}{10\pi}} = \boxed{4.946\text{ rad}^{-1}},\qquad C_L = 4.946\times0.09425 = 0.4662,\qquad C_{D_i} = \frac{0.4662^2(1.105)}{10\pi} = \boxed{0.00764}
$$

## Q2: Uniform flow + source $\Lambda_1$ at $(-b,0)$ + sink $\Lambda_2$ at $(b,0)$

### (i) Velocity potential
Source/sink: $\phi = \frac{\Lambda}{2\pi}\ln r = \frac{\Lambda}{4\pi}\ln r^2$ with $r^2$ measured from the singularity. Superposition (see [[Elementary Potential Flows]]):

$$
\phi_{tot} = V_\infty x+\frac{1}{4\pi}\Big\{\Lambda_1\ln[(x+b)^2+y^2]+\Lambda_2\ln[(x-b)^2+y^2]\Big\}\;✔
$$

A sink has $\Lambda_2<0$ in this convention.

### (ii) Sink strength for stagnation at $(4,0)$; $\Lambda_1 = 2\pi$, $V_\infty = 1$, $b = 2$
Differentiate:

$$
u = \frac{\partial\phi}{\partial x} = V_\infty+\frac{\Lambda_1}{2\pi}\frac{x+b}{(x+b)^2+y^2}+\frac{\Lambda_2}{2\pi}\frac{x-b}{(x-b)^2+y^2},\qquad v = \frac{\Lambda_1}{2\pi}\frac{y}{(x+b)^2+y^2}+\frac{\Lambda_2}{2\pi}\frac{y}{(x-b)^2+y^2}
$$

On $y=0$, $v=0$ automatically. Setting $u(4,0) = 0$:

$$
1+\frac{2\pi}{2\pi}\cdot\frac16+\frac{\Lambda_2}{2\pi}\cdot\frac12 = 0\;\Rightarrow\;\Lambda_2 = -\frac76(4\pi) = \boxed{-\frac{14\pi}{3} = -14.66\text{ m}^2/\text{s}}
$$

The sink is stronger than the source. The other axis stagnation point is at $x = -8/3$ m, upstream of the source. Check: $1+\frac{1}{-2/3}-\frac{7/3}{-14/3} = 1-1.5+0.5 = 0$ ✔.

### (iii) Streamline slope at $(4,3)$
$r_1^2 = 6^2+3^2 = 45$ and $r_2^2 = 2^2+3^2 = 13$:

$$
u = 1+\frac{6}{45}-\frac73\cdot\frac{2}{13} = 0.7744,\qquad v = \frac{3}{45}-\frac73\cdot\frac{3}{13} = -0.4718
$$

$$
\frac{dy}{dx}\Big|_{\psi} = \frac vu = \boxed{-0.609}
$$

The streamline is turning down towards the sink.

### (iv) Pressure coefficients

$$
c_p(4,3) = 1-\frac{u^2+v^2}{V_\infty^2} = 1-(0.5996+0.2226) = \boxed{0.178},\qquad c_p(4,0) = \boxed{1}\;\text{(stagnation)}
$$

![[e1415_q2_source_sink.png|650]]

The red $\psi=0$ line is the dividing streamline. Because the sink is stronger than the source, the net sink swallows a stream of half-width $|\Lambda_1+\Lambda_2|/(2V_\infty) = (8\pi/3)/2 \approx 4.2$ m. This is **not** a closed Rankine oval.

## Q3: Thin aerofoil theory

### (i) Lift coefficient and zero-lift angle
Circulation (see [[Vortex Sheet]] and [[Glauert Integrals]]):

$$
\Gamma = \int_0^c\gamma\,dx = \frac c2\int_0^\pi\gamma(\theta)\sin\theta\,d\theta = cV_\infty\left[A_0\int_0^\pi(1+\cos\theta)d\theta+\sum A_n\int_0^\pi\sin n\theta\sin\theta\,d\theta\right] = cV_\infty\pi\left(A_0+\frac{A_1}{2}\right)
$$

Kutta–Joukowski $L' = \rho V_\infty\Gamma$ gives

$$
c_l = \frac{2\Gamma}{V_\infty c} = \boxed{\pi(2A_0+A_1)}
$$

Substituting $A_0$ and $A_1$:

$$
c_l = 2\pi\alpha-2\int_0^\pi\frac{dZ}{dx}d\theta_0+2\int_0^\pi\frac{dZ}{dx}\cos\theta_0\,d\theta_0 = 2\pi\left[\alpha+\frac1\pi\int_0^\pi\frac{dZ}{dx}(\cos\theta_0-1)\,d\theta_0\right]
$$

$$
\boxed{c_l = 2\pi(\alpha-\alpha_{L=0}),\qquad \alpha_{L=0} = -\frac1\pi\int_0^\pi\frac{dZ}{dx}(\cos\theta_0-1)\,d\theta_0}
$$

### (ii) $Z = \dfrac{x}{10}\left(1-\dfrac xc\right)$ at $\alpha = 0$
$\dfrac{dZ}{dx} = 0.1\left(1-\dfrac{2x}{c}\right)$. With $x = \frac c2(1-\cos\theta_0)$ we have $1-\frac{2x}{c} = \cos\theta_0$, so $\dfrac{dZ}{dx} = 0.1\cos\theta_0$.

$$
\alpha_{L=0} = -\frac{0.1}{\pi}\int_0^\pi(\cos^2\theta_0-\cos\theta_0)\,d\theta_0 = -\frac{0.1}{\pi}\cdot\frac\pi2 = -0.05\text{ rad}\;(-2.86^\circ)
$$

$$
c_l(\alpha=0) = 2\pi(0.05) = \boxed{0.314}
$$

Check via coefficients: $A_0 = \alpha$ and $A_1 = \frac2\pi\int0.1\cos^2 = 0.1$, so $c_l = \pi(0+0.1) = 0.314$ ✔. The maximum camber is $c/40$ (2.5 %) at mid-chord.

## Q4: Compressible duct flow

### (i) $A = 1+x^2$, supersonic design exit
Throat at $x=0$ ($A^*=1$). Exit $A_e = 1+1.414^2 = 3$, so $A_e/A^* = 3$ gives $\boxed{M_e = 2.64}$ (supersonic branch, isentropic tables).

### (ii) Shock at $x = 1$
- $A/A^* = 2$ gives $M_1 = 2.20$.
- Normal-shock tables: $\boxed{M_2 = 0.547}$ and $p_{02}/p_{01} = 0.629$.
- $A_2^* = A^*/(p_{02}/p_{01}) = 1.589$, so $A_e/A_2^* = 1.888$. The subsonic branch gives $\boxed{M_e = 0.327}$.

### (iii) $a_0^2/a^2 = 1+\frac{\gamma-1}{2}M^2$
With $h = c_pT$:

$$
c_pT_0 = c_pT+\frac{V^2}{2}\;\Rightarrow\;\frac{T_0}{T} = 1+\frac{V^2}{2c_pT}
$$

Using $c_p = \frac{\gamma R}{\gamma-1}$ and $a^2 = \gamma RT$ gives $2c_pT = \frac{2a^2}{\gamma-1}$. Hence

$$
\frac{a_0^2}{a^2} = \frac{T_0}{T} = 1+\frac{\gamma-1}{2}\frac{V^2}{a^2} = \boxed{1+\frac{\gamma-1}{2}M^2}
$$

### (iv) Prandtl relation $V_1V_2 = a^{*2} = \dfrac{2a_0^2}{\gamma+1}$
**Assumptions**: steady, 1D, adiabatic, no body forces and no friction across a thin normal shock; calorically perfect gas.

1. Continuity: $\rho_1V_1 = \rho_2V_2$.
2. Momentum: $p_1+\rho_1V_1^2 = p_2+\rho_2V_2^2$.
3. Dividing (2) by (1): $\dfrac{p_1}{\rho_1V_1}-\dfrac{p_2}{\rho_2V_2} = V_2-V_1$. Since $p/\rho = a^2/\gamma$, this gives $\dfrac{a_1^2}{\gamma V_1}-\dfrac{a_2^2}{\gamma V_2} = V_2-V_1$.
4. Energy (adiabatic, so $h_0$ and $a_0$ are constant across the shock):

$$
\frac{a^2}{\gamma-1}+\frac{V^2}{2} = \frac{a_0^2}{\gamma-1} = \frac{\gamma+1}{2(\gamma-1)}a^{*2}\;\Rightarrow\;a_{1,2}^2 = \frac{\gamma+1}{2}a^{*2}-\frac{\gamma-1}{2}V_{1,2}^2
$$

   Here $a^*$ is the speed of sound where $M=1$, and $a^{*2} = \frac{2a_0^2}{\gamma+1}$ from (iii) with $M=1$.
5. Substituting into (3):

$$
\frac{\gamma+1}{2\gamma}a^{*2}\left(\frac1{V_1}-\frac1{V_2}\right)+\frac{\gamma-1}{2\gamma}(V_2-V_1) = V_2-V_1
$$

$$
\frac{\gamma+1}{2\gamma}a^{*2}\frac{V_2-V_1}{V_1V_2} = \frac{\gamma+1}{2\gamma}(V_2-V_1)
$$

6. For a shock $V_1\ne V_2$, so

$$
\boxed{V_1V_2 = a^{*2} = \frac{2a_0^2}{\gamma+1}}
$$

Consequence: $M_1^*M_2^* = 1$, so if the upstream flow is supersonic the downstream flow must be subsonic.

## Sources
- `03 - Exams & Past Papers/SESA2022-201415-01-SESA2022W1.pdf`. Numbers verified in Python.
