---
title: "SESA2022 Exam 2018-19 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2018-19"
tags: [sesa2022, exam-solutions, past-papers]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-201819-01-SESA2022W1.pdf"]
---

# SESA2022 Exam 2018-19 Solutions

> [!info] Paper: 4 questions (30/20/30/20). Q4(i) repeats the 2016-17 blunt-nose missile ($p_{0,2} = 9.95\times10^5$ Pa; see [[SESA2022 Exam 2016-17 Solutions]]). Q4(ii) is a good [[Virtual Origin Method]] drag calculation.

## Q1: Semicircular hangar in a wind

### (i) Model: uniform flow + doublet
Put a doublet at the centre of the hangar base, pointing into the wind (see [[Flow Past a Cylinder]] and [[Method of Images]]):

$$
\psi = V_\infty r\sin\theta-\frac{\kappa}{2\pi}\frac{\sin\theta}{r} = V_\infty\sin\theta\left(r-\frac{\kappa}{2\pi V_\infty r}\right)
$$

**Boundary conditions**
- **Hangar surface** $r = R$ must be a streamline ($V_r = 0$). Setting $\psi(R,\theta) = 0$ for all $\theta$ gives $R^2 = \dfrac{\kappa}{2\pi V_\infty}$, so $\boxed{\kappa = 2\pi R^2V_\infty}$ ✔.
- **Ground** $y = 0$ ($\theta = 0,\pi$): $\sin\theta = 0$, so $\psi = 0$. The ground is also a streamline, and the flow does not cross it.
- **Far field**: $\psi\to V_\infty y$, the uniform wind.

The upper half of the full-cylinder flow is exactly the flow over a semicircle on the ground (the ground is the cylinder's symmetry plane).

### (ii) Pressure coefficients
$$
V_r = V_\infty\cos\theta\left(1-\frac{R^2}{r^2}\right),\qquad V_\theta = -V_\infty\sin\theta\left(1+\frac{R^2}{r^2}\right)
$$

**Ground** ($\theta = 0$ or $\pi$, $|x| = r\ge R$): $V_\theta = 0$ and $|V| = V_\infty(1-R^2/x^2)$, so

$$
\boxed{C_p = 1-\left(1-\frac{R^2}{x^2}\right)^2}
$$

This is identical upstream and downstream, rising from 0 far away to 1 at the hangar feet.

**Hangar** ($r = R$): $V_r = 0$ and $V_\theta = -2V_\infty\sin\theta$, so

$$
\boxed{C_p = 1-4\sin^2\theta}
$$

![[e1819_q1_hangar_cp.png|760]]

### (iii) Worst-case load ($\rho = 1.2$, $V_\infty = 30$ m/s, $p_{in} = p_\infty$)
$q = \frac12(1.2)(30^2) = 540$ Pa. The net load on the skin is $p_{in}-p_{out} = -C_pq$ (positive means outward/upward):
- **Roof apex** ($\theta = 90^\circ$): $C_p = -3$, so the net load is $\boxed{1620\text{ N/m}^2\text{ outward (suction), at the top}}$. This is the worst case, trying to lift the roof off.
- At the windward/leeward feet ($C_p = 1$): 540 N/m² inward.

### (iv) Real flow
- Upstream the ground boundary layer meets an adverse pressure gradient near the windward foot, which gives a small separation/horseshoe region.
- The flow accelerates over the roof, then **separates on the leeward side**, somewhere just past the apex. Turbulent separation happens later than laminar.
- Behind the hangar there is a large recirculating **wake** with nearly constant base pressure ($C_p\approx-0.5$ to $-1$). The flow reattaches on the ground several $R$ downstream.
- Consequences: the pressure recovery on the leeward half is lost (giving drag, unlike the potential solution), the peak suction is weaker than $-3$ (typically $-1$ to $-1.5$), and the loading is asymmetric and unsteady because of vortex shedding. See [[Boundary Layer Separation]] and [[D'Alembert's Paradox]].

## Q2: Symmetric aerofoil with a 25 % flap, $\delta = 10^\circ$, $c_l = 1.5$

### (i) Zero-lift angle
Hinge at $x = 0.75c$: $\cos\theta_h = 1-2(0.75) = -0.5$, so $\theta_h = 2\pi/3$. The camber slope is $dZ/dx = 0$ ahead of the hinge and $-\delta$ on the flap (see [[Trailing-Edge Flap in Thin Aerofoil Theory]]).

$$
A_0 = \alpha+\frac\delta\pi(\pi-\theta_h) = \alpha+\frac\delta3,\qquad A_n = -\frac{2\delta}{\pi}\int_{\theta_h}^{\pi}\cos n\theta_0\,d\theta_0 = \frac{2\delta}{n\pi}\sin n\theta_h
$$

$$
A_1 = \frac{\sqrt3}{\pi}\delta,\qquad A_2 = -\frac{\sqrt3}{2\pi}\delta
$$

$$
c_l = \pi(2A_0+A_1) = 2\pi\alpha+\left(\frac{2\pi}3+\sqrt3\right)\delta = 2\pi\alpha+3.826\,\delta
$$

$$
\alpha_{L=0} = -\frac{3.826}{2\pi}\delta = -0.609\,\delta = -0.609(10^\circ) = \boxed{-6.09^\circ}
$$

### (ii) Geometric angle of attack

$$
\alpha = \frac{c_l}{2\pi}+\alpha_{L=0} = 0.2387-0.1063 = 0.1324\text{ rad} = \boxed{7.59^\circ}
$$

### (iii) Quarter-chord moment

$$
c_{m,c/4} = \frac\pi4(A_2-A_1) = -\frac{3\sqrt3}{8}\delta = -0.6495(0.1745) = \boxed{-0.113}\;\text{(nose-down)}
$$

### (iv) Sketch
$c_{m,c/4}$ is a **horizontal line** against $\alpha$ because the quarter-chord is the [[Aerodynamic Centre and Centre of Pressure|aerodynamic centre]] in TAT. It sits at 0 for the clean symmetric section and shifts down by $0.6495\delta$ when the flap is deflected.

![[e1819_q2_cm_flap.png|650]]

## Q3: Elliptic lift distribution

### (i) Constant downwash
With $y = -\frac b2\cos\theta$: $\Gamma = \Gamma_0\sin\theta$ and $\dfrac{d\Gamma}{dy} = \dfrac{d\Gamma/d\theta}{dy/d\theta} = \dfrac{\Gamma_0\cos\theta}{\frac b2\sin\theta}$. Also $y_0-y = \frac b2(\cos\theta-\cos\theta_0)$ and $dy = \frac b2\sin\theta\,d\theta$:

$$
w(\theta_0) = -\frac1{4\pi}\int_0^\pi\frac{\Gamma_0\cos\theta}{\frac b2\sin\theta}\cdot\frac{\frac b2\sin\theta\,d\theta}{\frac b2(\cos\theta-\cos\theta_0)} = -\frac{\Gamma_0}{2\pi b}\underbrace{\int_0^\pi\frac{\cos\theta\,d\theta}{\cos\theta-\cos\theta_0}}_{=\pi}
$$

$$
\boxed{w = -\frac{\Gamma_0}{2b}}\quad\text{(constant along the span)}
$$

This uses the Glauert integral with $n = 1$ (see [[Glauert Integrals]] and [[Elliptic Lift Distribution]]).

### (ii) $C_L$ and $C_L/c_l(0)$

$$
L = \rho V_\infty\int_{-b/2}^{b/2}\Gamma_0\sqrt{1-(2y/b)^2}\,dy = \rho V_\infty\Gamma_0\frac{b}{2}\int_0^\pi\sin^2\theta\,d\theta = \rho V_\infty\Gamma_0\frac{\pi b}{4}
$$

$$
\boxed{C_L = \frac{L}{\frac12\rho V_\infty^2S} = \frac{\pi b\,\Gamma_0}{2V_\infty S}}
$$

Rectangular planform: $S = bc$, and at the centre $c_l(0) = \dfrac{\rho V_\infty\Gamma_0}{\frac12\rho V_\infty^2c} = \dfrac{2\Gamma_0}{V_\infty c}$. Then

$$
\frac{C_L}{c_l(0)} = \frac{\pi b\Gamma_0/(2V_\infty bc)}{2\Gamma_0/(V_\infty c)} = \boxed{\frac\pi4 = 0.785}
$$

The average of an ellipse is $\pi/4$ of its peak.

### (iii) Centre-section geometric AoA: $c = 1$ m, $b = 8$ m ($AR = 8$), $C_L = 0.5$, symmetric section
- Centre section lift: $c_l(0) = \frac4\pi C_L = 0.6366$.
- Effective angle (2D, $\alpha_{L=0} = 0$): $\alpha_{eff} = c_l/(2\pi) = 0.1013$ rad.
- Induced angle (the same everywhere for an ELD): $\alpha_i = \dfrac{C_L}{\pi AR} = \dfrac{0.5}{8\pi} = 0.0199$ rad. Check: $-w/V = \Gamma_0/(2bV) = (c_l(0)c/2)/(2b) = 0.3183/16 = 0.0199$ ✔.

$$
\alpha_{geo}(0) = \alpha_{eff}+\alpha_i = 0.1013+0.0199 = 0.1212\text{ rad} = \boxed{6.95^\circ}
$$

The twist then reduces the geometric angle towards the tips so that $c_l\propto\sqrt{1-(2y/b)^2}$.

## Q4

### (i) Blunt missile at $M = 4$
As in 2016-17: $M_2 = 0.435$, $p_2/p_1 = 18.5$ and $p_{0,2} = \boxed{9.95\times10^5\text{ Pa}}$.

### (ii) Symmetric aerofoil at $\alpha = 0$, $Re_c = 6\times10^5$, transition at $x_T = c/2$
See [[Virtual Origin Method]].

**Laminar** up to $x_T$ ($Re_{x_T} = 3\times10^5$):

$$
\frac{\theta_T}{c} = 0.5\times\frac{0.664}{\sqrt{3\times10^5}} = 6.061\times10^{-4}
$$

**Virtual origin**:

$$
\frac{x_0}{c} = 0.5\left(1-38.22(3\times10^5)^{-3/8}\right) = 0.5(1-0.3376) = 0.3312
$$

This choice makes the turbulent $\theta$ equal the laminar value at $x_T$ (check: $0.036(0.1688)(1.013\times10^5)^{-1/5} = 6.061\times10^{-4}$ ✔).

**Turbulent** at the trailing edge: $x-x_0 = 0.6688c$ and $Re_{x-x_0} = 4.013\times10^5$:

$$
\frac{\theta_{TE}}{c} = 0.036(0.6688)(4.013\times10^5)^{-1/5} = 1.823\times10^{-3}
$$

**Drag.** Per surface $D' = \rho V_\infty^2\theta_{TE}$. There are two surfaces:

$$
C_d = \frac{2\rho V_\infty^2\theta_{TE}}{\frac12\rho V_\infty^2c} = \frac{4\theta_{TE}}{c} = \boxed{7.29\times10^{-3}}
$$

(For comparison, fully laminar flow would give $C_d = 4(0.664)/\sqrt{6\times10^5} = 3.43\times10^{-3}$, so mid-chord transition roughly doubles the drag.)

## Sources
- `03 - Exams & Past Papers/SESA2022-201819-01-SESA2022W1.pdf`. Numbers verified in Python.
