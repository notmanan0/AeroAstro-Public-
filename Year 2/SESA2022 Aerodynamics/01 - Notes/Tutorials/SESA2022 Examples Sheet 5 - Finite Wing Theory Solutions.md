---
title: "SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions"
module: "SESA2022 Aerodynamics"
type: tutorial
stream: "Topic 5: Finite Wing Theory"
tags:
  - sesa2022
  - tutorial-solutions
  - finite-wing-theory
sheet: "Examples Sheet 5"
theory_notes: ["[[SESA2022 T5 - Finite Wing Theory]]"]
key_concepts: ["[[Elliptic Lift Distribution]]", "[[Downwash and Induced Drag]]", "[[Oswald Efficiency Factor]]"]
status: complete
sources: ["02 - Sources/Airfoils and Wings/Examples5.pdf"]
---

# SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions

> [!abstract] Sheet Info
> All given answers are reproduced ✔: Q1 (1498 N, 55.81 m²/s), Q2 (0.711, 0.021), Q3 (6.95°), Q4 (0.00106, 0.0243).

## Theory Links
- [[SESA2022 T5 - Finite Wing Theory]] · [[Elliptic Lift Distribution]] · [[Downwash and Induced Drag]]

## Q1: Elliptic wing, $W = 73.6$ kN, $b = 15.23$ m, $V = 90$ m/s, sea level

### (a) Induced drag
In level flight $L = W$. With $q = \frac12\rho V^2 = \frac12(1.225)(90^2) = 4961.3$ Pa:

$$
D_i = qSC_{D_i} = qS\frac{C_L^2}{\pi AR} = qS\frac{(L/qS)^2}{\pi b^2/S} = \frac{L^2}{q\pi b^2}
$$

$S$ cancels, so it isn't needed:

$$
D_i = \frac{(73600)^2}{4961.3\,\pi\,(15.23)^2} = \frac{5.417\times10^9}{3.615\times10^6} = \boxed{1498\text{ N}}
$$

### (b) Circulation at the centreline
For the ELD, $L = \rho V_\infty\int_{-b/2}^{b/2}\Gamma_0\sqrt{1-(2y/b)^2}\,dy = \rho V_\infty\Gamma_0\frac{\pi b}{4}$, so

$$
\Gamma_0 = \frac{4L}{\rho V_\infty\pi b} = \frac{4(73600)}{1.225(90)\pi(15.23)} = \boxed{55.81\text{ m}^2/\text{s}}
$$

> [!note] Halfway along a semi-span ($y = b/4$): $\Gamma = \Gamma_0\sqrt{1-1/4} = 48.33$ m²/s. The 2017-18 exam wording "halfway along the wing" means the mid-span (centreline) value.

## Q2: NACA 23012 wing, $AR = 8$, $\delta = \tau = 0.054$, $\alpha = 7^\circ$

### Solution
$a_0 = 0.1080$ deg$^{-1}$ $= 6.188$ rad$^{-1}$ and $\alpha_{L=0} = -1.3^\circ$.

$$
a = \frac{a_0}{1+\frac{a_0}{\pi AR}(1+\tau)} = \frac{6.188}{1+\frac{6.188(1.054)}{8\pi}} = \frac{6.188}{1.2595} = 4.913\text{ rad}^{-1} = 0.08575\text{ deg}^{-1}
$$

$$
C_L = a(\alpha-\alpha_{L=0}) = 0.08575(7+1.3) = \boxed{0.711}
$$

$$
C_{D_i} = \frac{C_L^2}{\pi AR}(1+\delta) = \frac{0.7117^2(1.054)}{8\pi} = \boxed{0.0212}
$$

## Q3: Rectangular wing with elliptic loading, $c = 1$ m, $b = 8$ m, $C_L = 0.5$

Symmetric section, twisted so the centre has the highest $\alpha$. Find $\alpha$ at $y = 0$.

### Solution
$S = 8$ m² and $AR = b^2/S = 8$.

1. **Induced angle** (constant for the ELD): $\alpha_i = \dfrac{C_L}{\pi AR} = \dfrac{0.5}{8\pi} = 0.01989$ rad.
2. **Centre circulation**: $C_L = \dfrac{\pi b\Gamma_0}{2V_\infty S}$, so $\dfrac{\Gamma_0}{V_\infty} = \dfrac{2SC_L}{\pi b} = \dfrac{2(8)(0.5)}{8\pi} = 0.3183$ m.
3. **Section $c_l$ at the centre**: $\rho V\Gamma_0 = \frac12\rho V^2c\,c_l(0)$, so $c_l(0) = \dfrac{2\Gamma_0}{V_\infty c} = 0.6366$. Equivalently $c_l(0) = \dfrac4\pi C_L$ for a rectangular wing.
4. **Geometric angle**, using a symmetric section ($\alpha_{L=0}=0$) and $a_0 = 2\pi$ in ideal flow:

$$
\alpha(0) = \frac{c_l(0)}{2\pi}+\alpha_i = \frac{0.6366}{2\pi}+0.01989 = 0.10132+0.01989 = 0.1212\text{ rad} = \boxed{6.95^\circ}
$$

## Q4: Spitfire Mk I

$V = 580$ km/h $= 161.1$ m/s, $\rho = 0.69$ kg/m³, $W = 26.4$ kN, $S = 22.5$ m², $b = 10.8$ m, $P = 790$ kW.

### Solution
$AR = b^2/S = 116.64/22.5 = 5.184$ and $q = \frac12(0.69)(161.1^2) = 8954$ Pa.

$$
C_L = \frac{W}{qS} = \frac{26400}{8954(22.5)} = 0.1310
$$

**Induced drag coefficient** (elliptic planform, $e = 1$):

$$
C_{D_i} = \frac{C_L^2}{\pi AR} = \frac{0.01717}{16.29} = \boxed{0.00106}
$$

**Total drag coefficient**: at maximum speed, thrust power equals drag power, so $D = P/V = 790000/161.1 = 4903$ N and

$$
C_D = \frac{D}{qS} = \frac{4903}{8954(22.5)} = \boxed{0.0243}
$$

Induced drag is only about 4% of the total at top speed, where profile drag dominates.

## Sources
- `02 - Sources/Airfoils and Wings/Examples5.pdf`
