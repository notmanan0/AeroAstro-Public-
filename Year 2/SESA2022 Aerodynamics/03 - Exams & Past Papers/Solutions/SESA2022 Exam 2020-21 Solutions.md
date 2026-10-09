---
title: "SESA2022 Exam 2020-21 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2020-21"
tags: [sesa2022, exam-solutions, past-papers, open-book]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-202021-01-SESA2022.pdf"]
---

# SESA2022 Exam 2020-21 Solutions

> [!info] Paper: 24-hour online assessment (COVID year).
> - **Part A** (25 %) was a Blackboard multiple-choice quiz and isn't in the paper, so it isn't covered here.
> - **Part B** (50 %) is a UAV wing design with **per-student parameters** from `SESA2022 2021 parameters.pdf`, which isn't in the vault.
> - **Part C** (25 %) is a vortex in a corner via the method of images.

> [!warning] Example parameters
> Part B is worked with an **illustrative parameter set**: NACA **2412**, $W = 100$ N, $c = 0.25$ m, $U = 20$ m/s, sample $\alpha = 4^\circ$, $C_{D_P} = 0.008$. Substitute your own values into the same steps.

## Part B: UAV wing preliminary design
Data: $\rho = 1.25$ kg/m³, $\nu = 1.5\times10^{-5}$ m²/s, $Re_{tr} = 2.5\times10^5$. For NACA 2412: $m = 0.02$, $p = 0.4$, $t = 0.12$.

### 1. Zero-lift angle (TAT)
The camber slope, with $x = \frac c2(1-\cos\theta_0)$, is

$$
\frac{dz}{dx} = \begin{cases}\dfrac{2m}{p^2}\left(p-\dfrac xc\right) & 0\le x/c\le p\\[2mm] \dfrac{2m}{(1-p)^2}\left(p-\dfrac xc\right) & p\le x/c\le1\end{cases}
$$

It is continuous, but its formula switches at $\theta_p = \cos^{-1}(1-2p) = \cos^{-1}(0.2) = 78.46^\circ$, so every integral is split at $\theta_p$ (see [[Glauert Integrals]]):

$$
\alpha_{L=0} = -\frac1\pi\left[\int_0^{\theta_p}+\int_{\theta_p}^{\pi}\right]\frac{dz}{dx}(\cos\theta_0-1)\,d\theta_0 = \boxed{-2.08^\circ}
$$

The integrals are polynomials in $\cos\theta_0$ and can be done by hand. Values were checked with `scipy.integrate.quad`.

### 2. Quarter-chord moment

$$
A_1 = \frac2\pi\int_0^\pi\frac{dz}{dx}\cos\theta_0\,d\theta_0 = 0.08150,\qquad A_2 = \frac2\pi\int_0^\pi\frac{dz}{dx}\cos2\theta_0\,d\theta_0 = 0.01386
$$

$$
C_{m,c/4} = \frac\pi4(A_2-A_1) = \boxed{-0.0531}
$$

### 3. Centre of pressure at $\alpha = 4^\circ$
$C_l = 2\pi(\alpha-\alpha_{L=0}) = 2\pi(0.06981+0.03625) = 0.666$. Taking moments about the LE (see [[Aerodynamic Centre and Centre of Pressure]]):

$$
\frac{x_{cp}}{c} = \frac14-\frac{C_{m,c/4}}{C_l} = 0.25+\frac{0.0531}{0.666} = 0.330\;\Rightarrow\;x_{cp} = \boxed{0.0824\text{ m}}
$$

The centre of pressure moves aft as $\alpha$ falls, which is why structures teams ask for a specific $\alpha$.

### 4. Skin-friction and zero-lift drag
$Re_c = Uc/\nu = 3.33\times10^5>2.5\times10^5$, so transition occurs on the wing at $x_T = Re_{tr}\nu/U = 0.1875$ m ($0.75c$). Using the flat-plate model with a [[Virtual Origin Method|virtual origin]]:

1. **Laminar at $x_T$**: $\theta_T = 0.664x_T/\sqrt{Re_{tr}} = 2.490\times10^{-4}$ m.
2. **Virtual origin**: $x_0 = x_T\left(1-38.22Re_{tr}^{-3/8}\right) = 0.1197$ m. Check: the turbulent $\theta(x_T) = 2.490\times10^{-4}$ ✔.
3. **Turbulent at the TE**:

$$
\theta_{TE} = 0.036(c-x_0)\left(\frac{U(c-x_0)}{\nu}\right)^{-1/5} = 4.200\times10^{-4}\text{ m}
$$

4. Both surfaces, referred to the planform area $S = bc$:

$$
C_F = \frac{2\rho U^2\theta_{TE}}{\frac12\rho U^2c} = \frac{4\theta_{TE}}{c} = 0.00672
$$

$$
C_{D_0} = C_F+C_{D_P} = 0.00672+0.008 = \boxed{0.0147}
$$

### 5. Span for maximum aerodynamic efficiency
For $(L/D)_{max}$ we need $C_{D_i} = C_{D_0}$ (see [[Maximum Lift-to-Drag Ratio]]). The wing has elliptic loading ($e = 1$), $S = bc$ and $AR = b/c$. With $q = \frac12\rho U^2 = 250$ Pa and $C_L = W/(qbc)$:

$$
\frac{C_L^2}{\pi AR} = C_{D_0}\;\Rightarrow\;\frac{W^2}{q^2b^2c^2}\cdot\frac{c}{\pi b} = C_{D_0}\;\Rightarrow\;\boxed{b = \left(\frac{W^2}{\pi q^2cC_{D_0}}\right)^{1/3} = 2.40\text{ m}}
$$

This gives $AR = 9.60$, $S = 0.600$ m², $C_L = 0.666$ and $(L/D)_{max} = 22.6$.

> [!note] A subtlety
> If $U$ and $c$ are fixed and only $b$ is free, minimising $D(b) = qbcC_{D_0}+\dfrac{W^2}{\pi qb^2}$ gives $D_0 = 2D_i$ and $b = 2^{1/3}\times$ the value above (3.02 m). The paper asks for "highest efficiency" in the sense of the $(L/D)_{max}$ result from the notes, so the $C_{D_i} = C_{D_0}$ answer is the one expected.

### 6. Representative (mean) geometric angle
Take $a_0 = 2\pi$ and $\tau = 0$ for an ELD:

$$
a = \frac{2\pi}{1+\frac{2\pi}{\pi AR}} = \frac{2\pi}{1+2/9.60} = 5.200\text{ rad}^{-1}
$$

$$
\alpha = \frac{C_L}{a}+\alpha_{L=0} = 0.1282-0.0363 = 0.0919\text{ rad} = \boxed{5.27^\circ}
$$

### 7. Root and tip angles
With an elliptic loading on a rectangular wing, $C_l(0) = \frac4\pi C_L = 0.848$. The induced angle is uniform: $\alpha_i = \dfrac{C_L}{\pi AR} = 0.0221$ rad $= 1.27^\circ$.

$$
\alpha_{root} = \frac{C_l(0)}{2\pi}+\alpha_{L=0}+\alpha_i = 7.74^\circ-2.08^\circ+1.27^\circ = \boxed{6.93^\circ}
$$

$$
\alpha_{tip} = 0+\alpha_{L=0}+\alpha_i = \boxed{-0.81^\circ}
$$

The washout is $7.74^\circ$, which equals $2C_L/\pi^2$ in radians and is independent of $AR$ (see [[SESA2022 Exam 2019-20 Solutions]] Q3(iv)).

### 8. Keeping an ELD without geometric twist
- **Planform taper**: make the chord vary elliptically (or approximate it with a tapered, double-tapered or curved tip). Then $C_l$ is constant along the span and no twist is needed, because $\Gamma\propto cC_l$.
- **Aerodynamic twist**: vary the section along the span, with more camber (a more negative $\alpha_{L=0}$) at the root and less or reflexed camber at the tip. The effective angle $\alpha-\alpha_{L=0}$ then falls towards the tip even though $\alpha$ is constant.

## Part C: Vortex in a 90° corner
Floor $z = 0$, wall $x = 0$, corner at the origin, vortex $+\Gamma$ (clockwise positive, formula-sheet convention) at $(-b,a)$, with $a = b$. See [[Method of Images]].

### 1. Streamfunction and image signs
Three images are needed:

| Vortex | Position | Strength | Reason |
|---|---|---|---|
| real | $(-a,a)$ | $+\Gamma$ | the starting vortex |
| floor image | $(-a,-a)$ | $-\Gamma$ | a mirror reverses the sense of rotation, so the floor normal velocity cancels |
| wall image | $(a,a)$ | $-\Gamma$ | mirror in $x = 0$, so the wall normal velocity cancels |
| corner image | $(a,-a)$ | $+\Gamma$ | image of an image (two reflections restore the sense), needed so the floor and wall images don't themselves violate the other wall |

With $\psi_{vortex} = \frac{\Gamma}{2\pi}\ln r = \frac{\Gamma}{4\pi}\ln r^2$:

$$
\boxed{\psi = \frac{\Gamma}{4\pi}\ln\frac{\left[(x+a)^2+(z-a)^2\right]\left[(x-a)^2+(z+a)^2\right]}{\left[(x+a)^2+(z+a)^2\right]\left[(x-a)^2+(z-a)^2\right]}}
$$

**Check**: on $z = 0$, numerator and denominator are identical, so $\psi = 0$. On $x = 0$, the same holds. Both walls are the streamline $\psi = 0$ ✔.

### 2. Streamlines
The plot verifies the images: the walls coincide with $\psi = 0$, streamlines run parallel to both walls, and nothing crosses the corner. The closed streamlines round the vortex are squashed towards the corner.

![[e2021_c_corner_streamlines.png|520]]

### 3. Wall velocity and $c_p$ on the floor
Differentiate at $z = 0$, with $U_\Gamma = \Gamma/(2\pi a)$ and $\xi = x/a$:

$$
u = \frac{\partial\psi}{\partial z}\Big|_{z=0} = \frac{\Gamma a}{\pi}\left[\frac{1}{(x-a)^2+a^2}-\frac{1}{(x+a)^2+a^2}\right]
$$

$$
\boxed{\frac{u}{U_\Gamma} = 2\left[\frac1{(\xi-1)^2+1}-\frac1{(\xi+1)^2+1}\right]},\qquad \boxed{c_p = \frac{p-p_\infty}{\frac12\rho U_\Gamma^2} = -\left(\frac u{U_\Gamma}\right)^2}
$$

The pressure uses steady Bernoulli, with the velocity zero far away.

![[e2021_c_corner_floor.png|650]]

### 4. Is the peak $U_\Gamma$ at $x = -a$?
**No.**
- Directly beneath the vortex the real vortex and its floor image each contribute $U_\Gamma$ in the same direction, giving $2U_\Gamma$. The wall and corner images then oppose this, contributing $-0.4U_\Gamma$, so $u(-a) = -1.6U_\Gamma$.
- The opposing images are stronger closer to the wall, so the extremum shifts slightly **away** from the wall: $u_{peak} = -1.612U_\Gamma$ at $x = -1.075a$. The negative sign means the floor flow runs away from the corner.

On the wall:
- **Minimum** $c_p = -2.60$ at $x\approx-1.08a$ (peak speed, strongest suction).
- **Maximum** $c_p = 0$ at the corner $x = 0$, a stagnation point where $u = 0$. $c_p$ also tends to 0 far upstream.

## Sources
- `03 - Exams & Past Papers/SESA2022-202021-01-SESA2022.pdf`. Numbers verified in Python (`scipy.integrate.quad` for the NACA integrals).
- The Part B per-student parameter file is not in the vault, so an example set is used.
