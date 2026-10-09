---
title: "SESA2022 Exam 2022-23 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2022-23"
tags: [sesa2022, exam-solutions, past-papers, open-book]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-202223-01-SESA2022.pdf"]
---

# SESA2022 Exam 2022-23 Solutions

> [!info] Paper: online assessment.
> - **Part A** (50 %) is boundary-layer data analysis and a fan by the method of images.
> - **Part B** (50 %) is TAT and lifting line.
>
> Parameters depend on whether the last digit of the student ID is **even or odd**. Both sets are given where the data is available.

> [!warning] Part A Q1 data
> `file1.csv`/`file2.csv` are not in the vault. The method is run on an **illustrative tripped turbulent profile** ($U_\infty\approx20$ m/s, $n\approx7$, small measurement scatter), using the even-ID value $\delta_{TE} = 35$ mm. The code is written so you can paste in the real arrays.

## Part A

### Q1: Tripped turbulent boundary layer ($\rho = 1.225$, $\nu = 1.5\times10^{-5}$)

#### (i) $U_\infty$ and $\delta_{99}$
- $U_\infty$ is the mean of the plateau readings: $\boxed{U_\infty = 20.016\text{ m/s}}$.
- $\delta$ is where $U = 0.99U_\infty = 19.815$ m/s. That lies between the 18 mm and 20 mm readings, so interpolate linearly: $\boxed{\delta = 18.899\text{ mm}}$.

#### (ii) $\delta^*$ and $\theta$
Trapezium rule, including the no-slip point $(0,0)$ (see [[Displacement and Momentum Thickness]]):

$$
\delta^* = \int_0^{y_{max}}\left(1-\frac U{U_\infty}\right)dy = \boxed{2.638\text{ mm}},\qquad \theta = \int_0^{y_{max}}\frac U{U_\infty}\left(1-\frac U{U_\infty}\right)dy = \boxed{1.898\text{ mm}}
$$

This gives $H = 1.39$, which is typical of a turbulent layer.

#### (iii) Power-law fit
Fit $U/U_\infty = (y/\delta)^{1/n}$ to the points with $y<\delta$ (`scipy.optimize.curve_fit`, or a straight-line fit of $\ln(U/U_\infty)$ against $\ln(y/\delta)$, whose slope is $1/n$). This gives $\boxed{n = 6.76}$, close to the classic 1/7 law.

![[e2223_a_q1_profile_fit.png|620]]

```python
Uinf  = U[y >= 0.75*y.max()].mean()
i     = np.argmax(U >= 0.99*Uinf);  d99 = np.interp(0.99*Uinf, U[i-1:i+1], y[i-1:i+1])
yy, uu = np.r_[0, y], np.r_[0, U]/Uinf
dstar = np.trapezoid(1-uu, yy);     theta = np.trapezoid(uu*(1-uu), yy)
n = curve_fit(lambda y, n: (y/d99)**(1/n), y[y<d99], U[y<d99]/Uinf, p0=[7])[0][0]
```

#### (iv) Skin-friction drag from $\delta_{TE}$
For a self-similar power-law profile:

$$
\frac\theta\delta = \int_0^1\eta^{1/n}\left(1-\eta^{1/n}\right)d\eta = \frac{n}{n+1}-\frac{n}{n+2} = \frac{n}{(n+1)(n+2)}
$$

$$
\theta_{TE} = 35\times\frac{6.76}{7.76\times8.76} = 3.480\text{ mm}
$$

The drag on one side is $D' = \rho U_\infty^2\theta_{TE}$ per unit width, so for both sides:

$$
D = 2\rho U_\infty^2\theta_{TE}\,w = 2(1.225)(20.016^2)(0.003480) = \boxed{3.416\text{ N per metre of plate width}}
$$

The plate width $w$ isn't stated in the paper; multiply by it if your notebook gives one.

#### (v) Untripped plate: where is the same profile found?
Transition happens at $Re_t = 7.5\times10^5$, so $x_t = Re_t\nu/U_\infty = 0.562$ m.
1. Laminar $\theta$ at transition: $\theta_t = 0.664x_t/\sqrt{Re_t} = 0.431$ mm.
2. **Equivalent turbulent length.** Find the distance $x_e$ that a fully turbulent layer would need to reach $\theta_t$: $0.037x_e^{0.8}(\nu/U_\infty)^{0.2} = \theta_t$, which gives $x_e = 0.130$ m. This is the [[Virtual Origin Method|virtual-origin]] idea, with $\theta$ continuous at $x_t$.
3. Turbulent length needed to reach the measured $\theta = 1.898$ mm: $x_{turb} = 0.830$ m.
4. Therefore

$$
x = x_t+(x_{turb}-x_e) = 0.562+(0.830-0.130) = \boxed{1.262\text{ m}}
$$

The untripped layer spends its first 0.56 m laminar, growing $\theta$ slowly, so the same profile appears 0.43 m further downstream than in the tripped case.

### Q2: Fan near a vertical wall
The fan is a doublet $\kappa$ at $(a,0)$ pointing towards the wall. The wall is $x = 0$ (the $z$-axis). See [[Method of Images]] and [[Elementary Potential Flows]].

#### (i) Streamfunction
The image is a reversed doublet $-\kappa$ at $(-a,0)$:

$$
\boxed{\psi = -\frac{\kappa z}{2\pi}\left[\frac{1}{(x-a)^2+z^2}-\frac{1}{(x+a)^2+z^2}\right]}
$$

**Ingredients**
- The first term is the fan: fluid is drawn in from the far side ($x>a$) and pushed out towards the wall.
- The second term is the image, which makes $x = 0$ a streamline. At $x = 0$ the two denominators are equal, so $\psi = 0$ for all $z$ and the wall normal velocity $u(0,z) = 0$.

**Plot check**
- The wall coincides with a streamline, and no arrow crosses it.
- On the axis, flow runs from the fan towards the wall and then splits up and down along it.
- There is a stagnation point on the wall at $z = 0$.

![[e2223_a_q2_fan_streamlines.png|520]]

#### (ii) $C_p$ along the wall

$$
w(0,z) = -\left.\frac{\partial\psi}{\partial x}\right|_{x=0} = \frac{2\kappa az}{\pi(a^2+z^2)^2}
$$

With $U_{ref} = \kappa/(2\pi a^2)$ and $\zeta = z/a$:

$$
\frac{w}{U_{ref}} = \frac{4\zeta}{(1+\zeta^2)^2}
$$

The pressure is $p_\infty$ where the speed equals $U_{ref}$, so Bernoulli gives $p+\frac12\rho w^2 = p_\infty+\frac12\rho U_{ref}^2$:

$$
\boxed{C_p = 1-\left(\frac{w}{U_{ref}}\right)^2 = 1-\frac{16\zeta^2}{(1+\zeta^2)^4}}
$$

- $C_p = 1$ at the stagnation point $\zeta = 0$, and $C_p\to1$ far along the wall.
- $|w|_{max} = 1.299U_{ref}$ and $C_{p,min} = -0.6875$ at $\zeta = \pm1/\sqrt3$.

#### (iii) Analytic against a gridded potential-flow code (even ID: $\kappa = 4\pi$, $a = 1$ m)
![[e2223_a_q2_wall_w.png|620]]
![[e2223_a_q2_wall_cp.png|620]]

The code evaluates $w = -\partial\psi/\partial x$ by a **one-sided finite difference** at the wall.
- With $\Delta x = 0.05$ m it matches the analytic curve closely.
- With $\Delta x = 0.2$ m it overshoots the velocity peak ($1.33$ against $1.30$) and underestimates $C_p$ near $\zeta\approx\pm0.4$. The truncation error $\propto\Delta x\,\partial^2\psi/\partial x^2$ is largest where the velocity changes fastest.

Refining the grid (or using a central difference) removes the discrepancy. The physics is identical because the code superposes the same analytic elements.

For odd IDs ($\kappa = 2\pi$, $a = 0.5$): $U_{ref} = \kappa/(2\pi a^2) = 4$ m/s, and the dimensionless curves are identical.

## Part B

### Q1: $z = \epsilon x(1-x/c)$
$\dfrac{dz}{dx} = \epsilon\cos\theta_0$, so $A_0 = \alpha$, $A_1 = \epsilon$ and $A_{n\ge2} = 0$. See [[SESA2022 T4 - Thin Aerofoil Theory]].

| | Even ($\alpha = 2^\circ$, $\epsilon = 0.1$, $c = 5$ m) | Odd ($\alpha = 5^\circ$, $\epsilon = 0.2$, $c = 10$ m) |
|---|---|---|
| (i) $\alpha_{L=0} = -\epsilon/2$ | $-0.0500$ rad $= \mathbf{-2.8648^\circ}$ | $-0.1000$ rad $= \mathbf{-5.7296^\circ}$ |
| (ii) $C_{m,c/4} = -\pi\epsilon/4$ | $\mathbf{-0.0785}$ | $\mathbf{-0.1571}$ |
| $C_l = \pi(2\alpha+\epsilon)$ | 0.5335 | 1.1766 |

#### (iii) Vortex-sheet strength

$$
\boxed{\gamma(\theta) = 2V_\infty\left[\alpha\frac{1+\cos\theta}{\sin\theta}+\epsilon\sin\theta\right]},\qquad x = \frac c2(1-\cos\theta)
$$

#### (iv) Load distribution
$\Delta C_p = C_{p,l}-C_{p,u} = \dfrac{2\gamma}{V_\infty}$:

$$
\Delta C_p = 4\alpha\frac{1+\cos\theta}{\sin\theta}+4\epsilon\sin\theta
$$

The first term is the flat-plate part, singular at the LE. The second is the camber part, an elliptic "hump" peaking at mid-chord. $c$ only scales the $x$-axis.

![[e2223_b_q1_dcp.png|650]]

#### (v) Real aerofoil
The very high leading-edge suction peak leads to a steep adverse gradient, then **leading-edge separation or bubble bursting, i.e. stall**. See [[Aerofoil Stall]].

### Q2: Elliptic loading on a rectangular wing, symmetric section, $\rho = 1.225$
Thrust equals drag in steady flight, so $D = P/U_\infty$. See [[Elliptic Lift Distribution]].

| | Even: $P = 300$ kW, $U = 75$, $b = 10$, $c = 3$, $C_L = 0.35$, $\tau = 0.1$ | Odd: $P = 200$ kW, $U = 60$, $b = 8$, $c = 4$, $C_L = 0.4$, $\tau = 0.2$ |
|---|---|---|
| $AR = b/c$ | 3.333 | 2.000 |
| $\alpha_i = C_L/(\pi AR)$ | $1.9150^\circ$ | $3.6476^\circ$ |
| $C_l(0) = \frac4\pi C_L$ | 0.4456 | 0.5093 |
| **(i)** $\alpha(0) = \frac{C_l(0)}{2\pi}+\alpha_i$ | $\mathbf{5.9787^\circ}$ | $\mathbf{8.2918^\circ}$ |
| $D = P/U$ | 4000 N | 3333 N |
| $D_i = qSC_L^2/(\pi AR)$ | 1209.1 N | 1796.8 N |
| **(ii)** $D_i/D$ | $\mathbf{0.3023}$ | $\mathbf{0.5390}$ |
| $a = \dfrac{2\pi}{1+2(1+\tau)/AR}$ | 3.7851 rad⁻¹ | 2.8560 rad⁻¹ |
| **(v)** $\alpha_{rep} = C_L/a$ | $\mathbf{5.2981^\circ}$ | $\mathbf{8.0246^\circ}$ |

- **(iii)** Increase the span (aspect ratio), or add winglets.
- **(iv)** Yes. Taper the planform towards an elliptic chord, or vary camber along the span (aerodynamic twist) so $\alpha-\alpha_{L=0}$ falls towards the tips.

Note that (v) uses $\tau\ne0$ as instructed, even though a true ELD has $\tau = 0$. The low aspect ratios make induced drag a large share of the total, especially for the odd set (54 %).

## Sources
- `03 - Exams & Past Papers/SESA2022-202223-01-SESA2022.pdf`. Numbers verified in Python.
- Part A Q1 uses illustrative data because the `.csv` files aren't in the vault.
