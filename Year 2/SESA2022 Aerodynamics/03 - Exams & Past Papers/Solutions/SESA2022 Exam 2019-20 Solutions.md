---
title: "SESA2022 Exam 2019-20 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2019-20"
tags: [sesa2022, exam-solutions, past-papers]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-201920-01-SESA2022.pdf"]
---

# SESA2022 Exam 2019-20 Solutions

> [!info] Paper: 4 questions (20/30/30/20), with isentropic and normal-shock tables in the appendix. Q4(ii) is **identical** to 2018-19 Q4(ii) ($C_d = 7.29\times10^{-3}$; see [[SESA2022 Exam 2018-19 Solutions]]).

## Q1: 90° corner flow, $\psi = 2r^2\sin2\theta$

### (i) Velocity components

$$
\boxed{V_r = \frac1r\frac{\partial\psi}{\partial\theta} = 4r\cos2\theta,\qquad V_\theta = -\frac{\partial\psi}{\partial r} = -4r\sin2\theta}
$$

In Cartesian form $\psi = 4xy$, so $u = 4x$ and $v = -4y$. The speed is $|V| = 4r$.

### (ii) Irrotational?

$$
\omega_z = \frac1r\frac{\partial(-4r^2\sin2\theta)}{\partial r}-\frac1r\frac{\partial(4r\cos2\theta)}{\partial\theta} = \frac1r(-8r\sin2\theta)-\frac1r(-8r\sin2\theta) = \boxed{0}\;\text{irrotational}
$$

### (iii) Velocity potential
$\dfrac{\partial\phi}{\partial r} = 4r\cos2\theta$ gives $\phi = 2r^2\cos2\theta+f(\theta)$. Checking with $\frac1r\frac{\partial\phi}{\partial\theta} = -4r\sin2\theta = V_\theta$ gives $f' = 0$:

$$
\boxed{\phi = 2r^2\cos2\theta = 2(x^2-y^2)}
$$

### (iv) Sketch
Streamlines are rectangular hyperbolae $xy = $ const, asymptotic to the walls. Equipotentials are hyperbolae $x^2-y^2 = $ const, crossing the streamlines at right angles. The corner (origin) is a stagnation point. See [[Streamfunction and Velocity Potential]].

![[e1920_q1_corner.png|520]]

### (v) $p_B$ given $p_A = 30$ kPa, $\rho = 1000$
- $A = (1,0)$: $V_A = 4$ m/s.
- $B = (0,0.5)$: $V_B = 2$ m/s.

The flow is irrotational and horizontal, so Bernoulli applies between any two points:

$$
p_B = p_A+\tfrac12\rho(V_A^2-V_B^2) = 30000+500(16-4) = \boxed{36\text{ kPa}}
$$

B is closer to the stagnation corner, so it has lower speed and higher pressure.

## Q2: UAV aerofoil, $z/c = \epsilon\frac xc\left(1-\frac xc\right)$

### (i) $\epsilon$ for $C_l = 0.314$ at $\alpha = 0$
$\dfrac{dz}{dx} = \epsilon(1-2x/c) = \epsilon\cos\theta_0$, so

$$
A_0 = \alpha-\frac\epsilon\pi\int_0^\pi\cos\theta_0\,d\theta_0 = \alpha,\qquad A_1 = \frac{2\epsilon}\pi\int_0^\pi\cos^2\theta_0\,d\theta_0 = \epsilon,\qquad A_2 = 0
$$

$$
C_l = \pi(2\alpha+\epsilon)\;\xrightarrow{\alpha=0}\;\pi\epsilon = 0.314\;\Rightarrow\;\boxed{\epsilon = 0.1}
$$

The zero-lift angle is $\alpha_{L=0} = -\epsilon/2 = -2.86^\circ$.

### (ii) Maximum camber
$dz/dx = 0$ at $x = c/2$, so $z_{max} = \epsilon c/4 = 0.025c$. Maximum camber is $\boxed{2.5\,\%\text{ at mid-chord}}$.

### (iii) Quarter-chord moment

$$
C_{m,c/4} = \frac\pi4(A_2-A_1) = -\frac{\pi\epsilon}{4} = \boxed{-0.0785}
$$

### (iv) Voltage to hold lift when $V$ drops from 10 to 8 m/s at $\alpha = 5^\circ$
Constant lift means $V^2C_l = $ const.

**Initial** ($\epsilon = 0.1$, $E = 650$ V): $C_{l,1} = \pi(2\times0.08727+0.1) = 0.8625$.

**Required**:

$$
C_{l,2} = C_{l,1}\left(\frac{10}{8}\right)^2 = 1.3476
$$

$$
\epsilon_2 = \frac{C_{l,2}}{\pi}-2\alpha = 0.4290-0.1745 = 0.2544
$$

$$
E = 1000(0.2544)+550 = \boxed{804\text{ V}}\quad(\text{an increase of }154\text{ V})
$$

The new maximum camber is $0.2544/4 = 6.4\,\%$. This is large, and in reality it would push the section towards trailing-edge separation.

## Q3: Elliptic loading on a twisted rectangular wing

### (i) $C_L$ for an ELD
With $y = -\frac b2\cos\theta$:

$$
L = \rho V_\infty\Gamma_0\frac b2\int_0^\pi\sin^2\theta\,d\theta = \frac{\pi}{4}\rho V_\infty\Gamma_0b\;\Rightarrow\;\boxed{C_L = \frac{\pi b\Gamma_0}{2V_\infty S}}
$$

See [[Elliptic Lift Distribution]].

### (ii) $AR = 6$, $C_L = 0.75$: centre-section $C_l$ and $\alpha$
For a rectangular wing, $C_L/C_l(0) = \pi/4$ (see [[SESA2022 Exam 2018-19 Solutions]] Q3(ii)):

$$
C_l(0) = \frac4\pi(0.75) = \boxed{0.955}
$$

The symmetric section gives $\alpha_{eff}(0) = C_l/(2\pi) = 0.1520$ rad. The induced angle for an ELD is uniform: $\alpha_i = \dfrac{C_L}{\pi AR} = \dfrac{0.75}{6\pi} = 0.0398$ rad.

$$
\alpha|_{y=0} = 0.1520+0.0398 = 0.1918\text{ rad} = \boxed{10.99^\circ}
$$

### (iii) Tip angle and twist
At the tip $\Gamma = 0$, so $C_l = 0$ and $\alpha_{eff} = 0$. Only the induced angle remains:

$$
\alpha|_{y=b/2} = \alpha_i = \boxed{2.28^\circ},\qquad \Delta\alpha_{twist} = \alpha_{eff}(0) = \boxed{8.71^\circ}\;(0.152\text{ rad})
$$

### (iv) Why changing $AR$ can't halve the twist, and what can
The induced angle is the same everywhere for an ELD, so it cancels in the twist:

$$
\Delta\alpha_{twist} = \frac{C_l(0)}{2\pi} = \frac{4C_L/\pi}{2\pi} = \boxed{\frac{2C_L}{\pi^2}}\quad\text{(no }AR\text{ dependence)}
$$

Aspect ratio only shifts both angles by the same $\alpha_i$.

**Alternatives**
1. **Halve $C_L$** (twist ∝ $C_L$). Either double the wing area, which adds structural weight, wetted area and skin-friction drag, or fly $\sqrt2$ faster, which multiplies profile-drag power by about $2\sqrt2$. Both move the aircraft away from the $(L/D)_{max}$ condition (see [[Maximum Lift-to-Drag Ratio]]).
2. **Taper the planform** towards an elliptic chord $c(y)$. Since $C_l(y) = 2\Gamma(y)/(V_\infty c(y))$, an elliptic chord gives constant $C_l$, so the ELD needs **zero** twist. Any taper between rectangular and elliptic reduces the twist; 50 % is easily reached. The costs are manufacturing complexity and higher tip $C_l$ (a tip-stall risk).

## Q4

### (i) Nozzle $A = 1+0.16x^2$, shock at $x = 1.5$ m, $p_{0} = 1$ bar
Throat at $x = 0$: $A^* = 1$ m². Shock station $A_s = 1+0.16(2.25) = 1.36$. Exit $A_e = 1+0.16(4) = 1.64$. See [[Isentropic Nozzle Flow]] and [[Normal Shock Waves]].

1. Before the shock, $A/A^* = 1.36$ (supersonic): $M_1 = 1.72$.
2. Normal-shock table: $M_2 = 0.635$ and $p_{02}/p_{01} = 0.846$.
3. New sonic area $A_2^* = A^*/0.846 = 1.182$, so $A_e/A_2^* = 1.64\times0.846 = 1.387$. Subsonic branch: $\boxed{M_e = 0.48}$.
4. $p_{0e} = 0.846\times10^5$ Pa, and $p/p_0 = (1+0.2M_e^2)^{-3.5} = 0.856$, so $\boxed{p_e\approx72.4\text{ kPa}}$.

(For comparison, the fully supersonic design exit would have $M_e = 1.97$.)

### (ii) Aerofoil drag with transition at mid-chord
Identical to 2018-19: $\theta_{TE}/c = 1.823\times10^{-3}$ and $C_d = 4\theta_{TE}/c = \boxed{7.29\times10^{-3}}$.

## Sources
- `03 - Exams & Past Papers/SESA2022-201920-01-SESA2022.pdf`. Numbers verified in Python and against the appendix tables.
