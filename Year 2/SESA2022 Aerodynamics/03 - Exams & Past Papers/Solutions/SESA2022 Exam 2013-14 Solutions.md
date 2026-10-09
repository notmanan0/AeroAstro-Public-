---
title: "SESA2022 Exam 2013-14 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2013-14"
tags: [sesa2022, exam-solutions, past-papers]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-201314-01-SESA2022W1.pdf"]
---

# SESA2022 Exam 2013-14 Solutions

> [!info] Paper: 120 min, 4 questions (20/20/15/20). Uses the **$x$–$y$ plane**. Q4 (compressible nozzles) is from the older syllabus and is now covered in SESA2023; see [[Isentropic Nozzle Flow]] and [[Normal Shock Waves]].

## Q1

### (i) Structure of a turbulent BL in wall units
Sketch $u^+ = U/u_\tau$ against $\log y^+$ with $y^+ = u_\tau y/\nu$ (see [[Law of the Wall]]):
- **Viscous sub-layer** ($y^+<5$): $u^+ = y^+$. Viscous stress dominates and the flow is nearly laminar.
- **Buffer layer** ($5<y^+<30$–$50$): viscous and turbulent stresses are comparable. This is where turbulence production peaks and neither law fits.
- **Log layer** ($y^+>30$–$50$, $y/\delta<0.2$): $u^+ = \frac1\kappa\ln y^+ + B$ ($\kappa\approx0.4$, $B\approx5$). Turbulent (Reynolds) stress dominates.
- **Outer/wake region** ($y/\delta>0.2$): deviates from the log law and blends into the freestream. The power law is a fair fit here.

### (ii) Irrotationality: $u_r = \cos\theta/r^3$, $u_\theta = b\sin\theta/r^3$

$$
\omega_z = \frac1r\frac{\partial(ru_\theta)}{\partial r}-\frac1r\frac{\partial u_r}{\partial\theta} = \frac1r\left(-\frac{2b\sin\theta}{r^3}\right)-\frac1r\left(-\frac{\sin\theta}{r^3}\right) = \frac{\sin\theta}{r^4}(1-2b)
$$

$\omega_z = 0$ requires $\boxed{b = \tfrac12}$.

### (iii) Divergence with $b = 1/2$

$$
\nabla\cdot\mathbf V = \frac1r\frac{\partial(ru_r)}{\partial r}+\frac1r\frac{\partial u_\theta}{\partial\theta} = \frac1r\left(-\frac{2\cos\theta}{r^3}\right)+\frac1r\left(\frac{\cos\theta}{2r^3}\right) = -\frac{3\cos\theta}{2r^4}\ne0
$$

**Not divergence-free**, so this flow is not incompressible (it is irrotational but not a potential flow of an incompressible fluid).

### (iv) Rectangular wing, $AR = 6$, $\delta=\tau=0.055$, $\alpha_{L=0} = -2^\circ$, $C_{D_i} = 0.01$ at $3.4^\circ$

$$
C_L = \sqrt{\frac{C_{D_i}\pi AR}{1+\delta}} = \sqrt{\frac{0.01(6\pi)}{1.055}} = \boxed{0.4227}
$$

$$
\frac{dC_L}{d\alpha} = \frac{C_L}{\alpha-\alpha_{L=0}} = \frac{0.4227}{5.4^\circ} = 0.0783\text{ deg}^{-1} = \boxed{4.485\text{ rad}^{-1}}
$$

$$
a_0 = \frac{a}{1-\frac{a(1+\tau)}{\pi AR}} = \frac{4.485}{1-\frac{4.485(1.055)}{6\pi}} = \boxed{5.988\text{ rad}^{-1}}
$$

### (v) Same sections and $\alpha$, $AR = 10$, $\delta=\tau=0.105$

$$
a = \frac{5.988}{1+\frac{5.988(1.105)}{10\pi}} = \boxed{4.946\text{ rad}^{-1}},\qquad C_L = 4.946(5.4^\circ) = 0.4662,\qquad C_{D_i} = \frac{0.4662^2(1.105)}{10\pi} = \boxed{0.0076}
$$

The higher AR gives more lift *and* less induced drag, even though $\delta$ is larger.

## Q2: Uniform flow + vortex pair $\pm\Gamma$ at $(0,\pm c)$

### (i) Streamfunction
Vortex $\psi = \frac{\Gamma}{2\pi}\ln r = \frac{\Gamma}{4\pi}\ln r^2$:

$$
\Psi = V_\infty y+\frac{\Gamma}{4\pi}\ln[x^2+(y-c)^2]-\frac{\Gamma}{4\pi}\ln[x^2+(y+c)^2]\;✔
$$

### (ii) Stagnation points ($\Gamma = 10\pi$, $V_\infty = 1$, $c = 2$)
On $y = 0$:

$$
v = -\frac{\partial\Psi}{\partial x} = -\frac{\Gamma}{4\pi}\left[\frac{2x}{x^2+c^2}-\frac{2x}{x^2+c^2}\right] = 0\quad\text{everywhere on the axis}
$$

$$
u = \frac{\partial\Psi}{\partial y}\Big|_{y=0} = V_\infty+\frac{\Gamma}{4\pi}\left[\frac{-2c}{x^2+c^2}-\frac{2c}{x^2+c^2}\right] = V_\infty-\frac{\Gamma c}{\pi(x^2+c^2)}
$$

Setting $u=0$ gives $x^2 = \dfrac{\Gamma c}{\pi V_\infty}-c^2 = 20-4 = 16$, so $\boxed{(\pm4, 0)}$.

On the $y$-axis, $u = V_\infty+\frac{\Gamma c}{\pi(y^2-c^2)}$ with $v = 0$. That would need $y^2 = -16$, so there are no other stagnation points.

At the stagnation points both logs are equal, so $\boxed{\Psi = 0}$.

### (iii) $c_p$ along the $x$-axis

$$
c_p(x,0) = 1-\frac{u^2}{V_\infty^2} = 1-\left(1-\frac{\Gamma c}{\pi V_\infty(x^2+c^2)}\right)^2 = 1-\left(1-\frac{20}{x^2+4}\right)^2
$$

- At $x = 0$: $u = 1-5 = -4$ (reversed flow between the vortices), so $\boxed{c_p = -15}$.
- At the stagnation points: $\boxed{c_p = 1}$.

### (iv) Sketch
$\Psi = 0$ consists of the $x$-axis *and* a closed oval through $(\pm4,0)$. The fluid inside circulates around each vortex (clockwise above, anticlockwise below) and forms a closed "body" that the external flow passes round, like a Rankine oval.

![[e1314_q2_vortex_pair.png|620]]

## Q3: Symmetric aerofoil, TE flap at $x/c = 0.75$, deflection $\phi$

### (i) Camber slope
$\dfrac{dZ}{dx} = 0$ for $x<0.75c$ ($\theta_0<2\pi/3$) and $-\phi$ for $x>0.75c$ ($\theta_0>2\pi/3$). This is a step function; see [[Trailing-Edge Flap in Thin Aerofoil Theory]].

### (ii) $\phi$ for $C_l = 0.863$ at $\alpha = 6^\circ$
From TAT: $A_0 = \alpha+\phi/3$, $A_1 = \sqrt3\phi/\pi$, $A_2 = -\sqrt3\phi/(2\pi)$, so

$$
C_l = 2\pi\alpha+\left(\frac{2\pi}{3}+\sqrt3\right)\phi
$$

$$
0.863 = 2\pi(0.10472)+3.8264\phi\;\Rightarrow\;\phi = 0.05358\text{ rad} = \boxed{3.07^\circ}
$$

### (iii) Moment and flap derivatives

$$
C_{m,c/4} = \frac\pi4(A_2-A_1) = -\frac{3\sqrt3}{8}\phi = -0.6495(0.05358) = \boxed{-0.0348}
$$

$$
\frac{\partial C_l}{\partial\phi} = \frac{2\pi}{3}+\sqrt3 = \boxed{3.826\text{ rad}^{-1}},\qquad \frac{\partial C_{m,c/4}}{\partial\phi} = -\frac{3\sqrt3}{8} = \boxed{-0.650\text{ rad}^{-1}}
$$

## Q4: Compressible flow in ducts

### (i) Area–velocity relation
**Assumptions**: steady, quasi-1D, inviscid, adiabatic, isentropic, no body forces.
- Continuity: $\rho VA = $ const, so $\dfrac{d\rho}{\rho}+\dfrac{dV}{V}+\dfrac{dA}{A} = 0$.
- Euler (momentum): $dp = -\rho V\,dV$.
- Isentropic: $dp = a^2d\rho$, so $\dfrac{d\rho}{\rho} = -\dfrac{V\,dV}{a^2} = -M^2\dfrac{dV}{V}$.

Substituting:

$$
-M^2\frac{dV}{V}+\frac{dV}{V}+\frac{dA}{A} = 0\quad\Rightarrow\quad\boxed{\frac{dA}{A} = (M^2-1)\frac{dV}{V}}
$$

### (ii) Why a convergent–divergent nozzle?
- For $M<1$: $dA<0$ gives $dV>0$, so a **converging** duct accelerates subsonic flow.
- For $M>1$: $dA>0$ gives $dV>0$, so a **diverging** duct accelerates supersonic flow.
- At $M = 1$: $dA = 0$, so sonic conditions can only occur at a **throat** (minimum area).

To go from subsonic to supersonic you must converge to $M=1$ at the throat and then diverge.

### (iii) $A = 1+x^2$, $-1\le x\le1.414$
The throat is at $x=0$ with $A^* = 1$. The exit has $A_e = 1+2 = 3$, so $A_e/A^* = 3$. From the isentropic tables (supersonic branch):

$$
\frac{A}{A^*} = \frac1M\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{\frac{\gamma+1}{2(\gamma-1)}}\quad\Rightarrow\quad\boxed{M_e = 2.64}
$$

### (iv) Shock at $x = 1$
- Before the shock: $A = 2$, $A/A^* = 2$, so $M_1 = 2.20$ (supersonic).
- Normal-shock tables: $M_2 = \boxed{0.547}$ and $p_{02}/p_{01} = 0.629$.
- New sonic reference: $A_2^* = A^*/(p_{02}/p_{01}) = 1.589$, so $A_e/A_2^* = 3/1.589 = 1.888$.
- Subsonic branch: $\boxed{M_e = 0.327}$.

## Sources
- `03 - Exams & Past Papers/SESA2022-201314-01-SESA2022W1.pdf`. Numbers verified in Python.
