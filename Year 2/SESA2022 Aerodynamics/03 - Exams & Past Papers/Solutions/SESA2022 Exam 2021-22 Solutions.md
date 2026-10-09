---
title: "SESA2022 Exam 2021-22 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2021-22"
tags: [sesa2022, exam-solutions, past-papers, open-book]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-202122-01-SESA2022.pdf"]
---

# SESA2022 Exam 2021-22 Solutions

> [!info] Paper: 8-hour online assessment.
> - **Part A** (20 %) was a Blackboard quiz and isn't in the paper, so it isn't covered here.
> - **Part B** (40 %) is TAT and lifting line, with answers to 4 d.p.
> - **Part C** (40 %) is notebook-based: a boundary-layer profile and a rounded wall via images.

> [!warning] Part C Q1 data
> The measured $(y, u)$ profile was supplied in the exam's Jupyter notebook, which isn't in the vault. (The CSVs in `02 - Sources/BL` are the lecture examples at 14.43 m/s, not this data.) The method below is run on an **illustrative 1/7-power-law profile** consistent with the stated conditions. Paste your own arrays into the same code.

## Part B

### Q1: Modified NACA camber line
$$
\frac zc = \begin{cases}\frac14\left[\frac xc-2\left(\frac xc\right)^2\right] & 0\le x/c\le0.25\\[1mm] \frac1{36}\left[1+\frac xc-2\left(\frac xc\right)^2\right] & 0.25\le x/c\le1\end{cases}
$$

#### (i) Shape
$\dfrac{dz}{dx} = k\left(1-4\dfrac xc\right)$ with $k = \frac14$ (front) and $k = \frac1{36}$ (rear).
- Both pieces have zero slope at $x = 0.25c$, where $z = 0.03125c$. The **maximum camber is $0.03125c$ (3.125 %) at $x = 0.25c$**, and the line is continuous there ($0.25\times0.125 = 1.125/36$ ✔).
- **LE slope** $= \frac14 = 0.2500$ (14.0°). **TE slope** $= \frac{1}{36}(1-4) = -\frac1{12} = -0.0833$ ($-4.76^\circ$).

![[e2122_b_q1_camber.png|650]]

#### (ii) Zero-lift angle
Substituting $x/c = \frac12(1-\cos\theta_0)$ gives $1-4x/c = 2\cos\theta_0-1$. The break at $x/c = 0.25$ is at $\cos\theta_0 = \frac12$, i.e. $\theta_p = \pi/3$:

$$
\alpha_{L=0} = -\frac1\pi\left[\int_0^{\pi/3}\frac{2\cos\theta_0-1}{4}(\cos\theta_0-1)\,d\theta_0+\int_{\pi/3}^{\pi}\frac{2\cos\theta_0-1}{36}(\cos\theta_0-1)\,d\theta_0\right] = \frac{15\sqrt3-11\pi}{54\pi}
$$

$$
\boxed{\alpha_{L=0} = -0.0506\text{ rad} = -2.8967^\circ}
$$

Fourier coefficients (exact, checked symbolically):

$$
A_0 = \alpha-\frac{24\sqrt3-11\pi}{108\pi} = 0.10472-0.02067 = 0.0841,\qquad A_1 = \frac{11}{54}-\frac{\sqrt3}{9\pi} = 0.1424,\qquad A_2 = \frac{\sqrt3}{9\pi} = 0.0613
$$

$$
C_l = \pi(2A_0+A_1) = 2\pi(\alpha-\alpha_{L=0}) = 0.9756\quad(\alpha = 6^\circ)
$$

#### (iii) Leading-edge moment

$$
C_{m,LE} = -\frac\pi2\left(A_0+A_1-\frac{A_2}{2}\right) = \boxed{-0.3077}
$$

Equivalently $C_{m,LE} = C_{m,c/4}-C_l/4$ with $C_{m,c/4} = \frac\pi4(A_2-A_1) = -0.0638$.

#### (iv) Centre of pressure

$$
\frac{x_{cp}}{c} = -\frac{C_{m,LE}}{C_l} = \frac14-\frac{C_{m,c/4}}{C_l} = \boxed{0.3154}
$$

See [[Aerodynamic Centre and Centre of Pressure]].

#### (v) Real lift curve (10 % thick)
- Linear, with slope just under $2\pi$ (about 0.1/deg), crossing zero at about $-2.9^\circ$.
- $C_{l,max}\approx1.3$–$1.5$ at $\alpha\approx13$–$15^\circ$.
- A 10 % section with a fairly sharp nose typically shows **leading-edge stall**: an abrupt loss of lift when the laminar separation bubble near the nose bursts, with hysteresis on recovery. Thicker (>12 %) sections stall more gently from the trailing edge. See [[Aerofoil Stall]].

#### (vi) Flow patterns
- **6°**: attached flow on both surfaces. The stagnation point is slightly below the LE, the flow leaves the TE smoothly (Kutta condition), and the wake is thin.
- **16°**: beyond stall. The flow separates from near the LE on the upper surface, leaving a large recirculating region over most of the chord, a thick unsteady wake, and loss of lift with a sharp rise in pressure drag.

### Q2: Non-elliptic wing, $V = 100$ m/s, $b = 10$ m, $AR = 3$
$\Gamma = 2bV_\infty[0.0163\sin\theta-0.0011\sin3\theta]$, so $B_1 = 0.0163$ and $B_3 = -0.0011$. $S = b^2/AR = 33.33$ m² and $q = \frac12(1.255)(100^2) = 6275$ Pa.

#### (i) Induced drag coefficient

$$
C_L = \pi AR\,B_1 = 0.1536,\qquad \delta = 3\left(\frac{B_3}{B_1}\right)^2 = 0.0137
$$

$$
C_{D_i} = \frac{C_L^2}{\pi AR}(1+\delta) = \boxed{0.0025}\;(0.002538)
$$

#### (ii) Induced power

$$
P_i = qSC_{D_i}V = 6275(33.33)(0.002538)(100) = \boxed{53.09\text{ kW}}
$$

#### (iii) Oswald factor
$e = 1/(1+\delta) = 0.9865$, so the loading is very nearly elliptic (see [[Oswald Efficiency Factor]]). $B_3<0$ adds loading at mid-span relative to an ellipse (since $\sin3\theta = -1$ at $\theta = \pi/2$). That fits a well-tapered planform, taper ratio roughly 0.3–0.4, rather than a rectangle, which would have $B_3>0$ with the loading pushed outboard.

#### (iv) Deploying flaps in flight
Flaps raise $C_L$ at a given $\alpha$ by adding camber. They also add profile/pressure drag, and part-span flaps distort the spanwise loading ($\delta$ rises, $e$ falls). At the same speed the aircraft must either reduce $\alpha$ or climb. Either way the drag and the **power required increase**, which is why flaps are only used for take-off and landing, at low speed.

#### (v) Second aircraft: $AR = 6$, same section, $V$, $b$ and $\alpha$; $\tau = \delta = 0.2$; $C_{D,0} = 0.007$
**Section slope from aircraft 1** (with $\tau_1 = \delta_1 = 0.0137$ and $\alpha-\alpha_{L=0} = 5^\circ$):

$$
a_1 = \frac{0.1536}{0.08727} = 1.760\text{ rad}^{-1},\qquad a_0 = \frac{a_1}{1-\frac{a_1(1+\tau_1)}{\pi AR}} = 2.172\text{ rad}^{-1}
$$

**Aircraft 2**: $S = 16.67$ m².

$$
a_2 = \frac{2.172}{1+\frac{2.172(1.2)}{6\pi}} = 1.908\text{ rad}^{-1},\qquad C_L = 1.908(0.08727) = 0.1665
$$

$$
C_{D_i} = \frac{0.1665^2(1.2)}{6\pi} = 0.001765,\qquad C_D = 0.007+0.001765 = 0.008765
$$

| | $C_{D_i}$ | $C_D$ | $P_{induced}$ | $P_{total} = qSC_DV$ |
|---|---|---|---|---|
| Aircraft 1 ($AR = 3$) | 0.002538 | 0.007538 | 53.09 kW | **157.68 kW** |
| Aircraft 2 ($AR = 6$) | 0.001765 | 0.008765 | 18.45 kW | **91.66 kW** |

Aircraft 2 needs **less** power: its higher aspect ratio cuts induced drag, and its wing area is half. The comparison isn't like for like, though. At the same $\alpha$, aircraft 2 generates only 17.4 kN of lift against 32.1 kN for aircraft 1.

> [!note] Per unit lift
> $P/L$ = 157.68/32.13 = 4.91 W/N for aircraft 1 and 91.66/17.41 = 5.26 W/N for aircraft 2. Per unit lift, aircraft 2 is actually slightly *worse*, because its higher $C_{D,0}$ outweighs its lower $C_{D_i}$ at this low $C_L$. Worth stating in an exam answer.

## Part C

### Q1: Turbulent BL at $x = 1.5$ m, $U = 10$ m/s
$\nu = \mu/\rho = 1.469\times10^{-5}$ m²/s and $Re_x = 1.02\times10^6$.

#### (i) Profile, $\delta$, $\delta^*$, $\theta$
**Why it's turbulent**
- The profile is "full": $u\approx0.5U$ within 0.25 mm and $0.8U$ by $y\approx0.2\delta$, with a very steep wall gradient (high $\tau_w$).
- $H = \delta^*/\theta\approx1.3$, against 2.59 for Blasius.
- $\delta\approx25$ mm is about 3× the laminar $\delta = 5x/\sqrt{Re_x} = 7.4$ mm.
- $Re_x\approx10^6>5\times10^5$.

**Thicknesses.** Integrate with the trapezium rule (`np.trapezoid`) over the data (see [[Displacement and Momentum Thickness]]):

$$
\delta^* = \int_0^\infty\left(1-\frac uU\right)dy = 3.14\text{ mm},\qquad \theta = \int_0^\infty\frac uU\left(1-\frac uU\right)dy = 2.37\text{ mm},\qquad \delta_{99}\approx25\text{ mm}
$$

![[e2122_c_q1_profile.png|620]]

```python
d_star = np.trapezoid(1 - u/U, y)
theta  = np.trapezoid(u/U*(1 - u/U), y)
```

#### (ii) Virtual origin and transition
**Concept** (see [[Virtual Origin Method]]):
- Upstream of $x_t$ the BL is laminar and $\theta$ grows as $0.664x/\sqrt{Re_x}$.
- After transition, $\theta$ grows faster, following the turbulent law. That law behaves as if it had started from zero at a fictitious point $x_0<x_t$, the **virtual origin**.
- The two curves are matched by requiring $\theta$ to be continuous at $x_t$ (momentum can't jump).

**Step 1: $x_0$ from the measured $\theta$.**

$$
\theta = 0.036(x-x_0)\left(\frac{U(x-x_0)}{\nu}\right)^{-1/5}
$$

Solving numerically: $x-x_0 = 0.959$ m, so $\boxed{x_0 = 0.541\text{ m}}$.

**Step 2: $x_t$ from $x_0 = x_t\left(1-38.22Re_{x_t}^{-3/8}\right)$.** Solving with `brentq`: $\boxed{x_t = 0.748\text{ m}}$ ($Re_{x_t} = 5.09\times10^5$).

**Checks**
- $x_0<x_t<x$ ✔.
- $Re_{x_t}\approx5\times10^5$ is a typical flat-plate transition Reynolds number ✔.
- Laminar and turbulent $\theta$ at $x_t$ agree: $6.96\times10^{-4}$ m each ✔.

![[e2122_c_q1_virtual_origin.png|650]]

### Q2: Rounded wall via a vortex and its image
Uniform flow $U$ over the ground $z = 0$, with a vortex $+\Gamma$ (clockwise positive) at $(0,a)$ and its image $-\Gamma$ at $(0,-a)$. See [[Method of Images]].

#### (i) $\psi$, $\phi$, signs, and the governing group

$$
\psi = Uz+\frac{\Gamma}{4\pi}\ln\frac{x^2+(z-a)^2}{x^2+(z+a)^2},\qquad \phi = Ux-\frac{\Gamma}{2\pi}\left[\tan^{-1}\frac{z-a}{x}-\tan^{-1}\frac{z+a}{x}\right]
$$

**Signs**
- The real vortex is clockwise, so beneath it (near the ground) it drives flow in $-x$, against $U$. That creates stagnation points on the ground and a closed recirculating "body".
- The image is anticlockwise (a mirror reverses the rotation), so the ground-normal velocities cancel and $z = 0$ is the streamline $\psi = 0$.

**Why $\Pi$ governs everything.** Non-dimensionalise with $\tilde x = x/a$ and $\tilde z = z/a$:

$$
\frac{\psi}{Ua} = \tilde z+\frac{\Pi}{4}\ln\frac{\tilde x^2+(\tilde z-1)^2}{\tilde x^2+(\tilde z+1)^2},\qquad \Pi = \frac{\Gamma}{\pi Ua}
$$

The body shape ($\psi = 0$) and $C_p = 1-|\mathbf V|^2/U^2$ therefore depend only on $\Pi$.

The ground stagnation points follow from $u(x,0) = U-\frac{\Gamma}{\pi}\frac{a}{x^2+a^2} = 0$, which gives $x = \pm a\sqrt{\Pi-1}$. A body exists only for $\Pi>1$.

#### (ii) Body streamline in polar form
With $x = r\cos\theta$ and $z = r\sin\theta$:

$$
\frac{r}{a}\sin\theta+\frac\Pi4\ln\frac{(r/a)^2-2(r/a)\sin\theta+1}{(r/a)^2+2(r/a)\sin\theta+1} = 0
$$

This is **transcendental** ($r$ appears both algebraically and inside a log), so it can't be rearranged into $r/a = f(\Pi,\theta)$. Instead solve it numerically for each $\theta$ with a root-finder (`fsolve`/`brentq`), using the bracket $r/a>0$ on the outer branch. Alternatively, contour $\psi = 0$ on a grid.

#### (iii) $\Pi = 4/3$
- Ground stagnation points at $x = \pm0.577a$.
- Top of the body at $z = 1.320a$ (from $\tilde z+\frac\Pi2\ln\frac{\tilde z-1}{\tilde z+1} = 0$).

The body is taller (1.32a) than it is wide (1.15a), as the question sketch requires.

![[e2122_c_q2_rounded_wall.png|700]]

## Sources
- `03 - Exams & Past Papers/SESA2022-202122-01-SESA2022.pdf`. Numbers verified in Python (SymPy for the exact TAT integrals).
- Part C Q1 uses an illustrative profile because the notebook data isn't in the vault.
