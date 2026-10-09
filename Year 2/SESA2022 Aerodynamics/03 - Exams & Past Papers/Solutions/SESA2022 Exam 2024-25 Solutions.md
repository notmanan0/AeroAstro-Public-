---
title: "SESA2022 Exam 2024-25 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2024-25"
tags: [sesa2022, exam-solutions, past-papers]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-202425-01-SESA2022.pdf"]
---

# SESA2022 Exam 2024-25 Solutions

> [!info] Paper: 2 hours, closed book (back to in-person), 4 × 25 marks, answers to **4 d.p.** A full formula sheet is attached as the rubric, so this is the most representative paper for current exams. The turbulent correlations come from the rubric table: $\theta/x = 0.037Re_x^{-1/5}$ and $C_f = 0.059Re_x^{-1/5}$.

## Q1: Near-laminar boundary layer, $U/U_\infty = 2\eta-\eta^2$ ($\eta = y/\delta$)

### (a) Shape factor

$$
\frac{\delta^*}{\delta} = \int_0^1(1-2\eta+\eta^2)\,d\eta = 1-1+\frac13 = \frac13
$$

$$
\frac\theta\delta = \int_0^1(2\eta-\eta^2)(1-2\eta+\eta^2)\,d\eta = \int_0^1\left(2\eta-5\eta^2+4\eta^3-\eta^4\right)d\eta = 1-\frac53+1-\frac15 = \frac{2}{15}
$$

$$
H = \frac{1/3}{2/15} = \boxed{2.5000}
$$

This is close to Blasius (2.59), consistent with "near-laminar" flow. See [[Displacement and Momentum Thickness]].

### (b) $\theta/x$ and $C_f$ via the momentum integral equation
Wall shear:

$$
\tau_w = \mu\frac{U_\infty}{\delta}\left.\frac{d(2\eta-\eta^2)}{d\eta}\right|_0 = \frac{2\mu U_\infty}{\delta}\;\Rightarrow\;C_f = \frac{2\tau_w}{\rho U_\infty^2} = \frac{4\nu}{U_\infty\delta}
$$

Apply the MIE, $C_f = 2\,d\theta/dx$, with $\theta = \frac{2}{15}\delta$ (see [[Momentum Integral Equation]]):

$$
\frac{4\nu}{U_\infty\delta} = \frac{4}{15}\frac{d\delta}{dx}\;\Rightarrow\;\delta\,d\delta = \frac{15\nu}{U_\infty}dx\;\Rightarrow\;\delta^2 = \frac{30\nu x}{U_\infty}\quad(\delta = 0\text{ at }x = 0)
$$

$$
\frac\delta x = \frac{\sqrt{30}}{\sqrt{Re_x}} = \frac{5.4772}{\sqrt{Re_x}}
$$

$$
\boxed{\frac\theta x = \frac{2}{15}\frac{\sqrt{30}}{\sqrt{Re_x}} = \frac{0.7303}{\sqrt{Re_x}}},\qquad \boxed{C_f = \frac{4\nu}{U_\infty\delta} = \frac{4}{\sqrt{30}\sqrt{Re_x}} = \frac{0.7303}{\sqrt{Re_x}}}\;✔
$$

### (c) $L = 6$ m, $U_\infty = 150$ m/s, transition at $x_T = 3.4$ m ($\rho = 1.2$, $\nu = 1.5\times10^{-5}$)
1. **Near-laminar $\theta$ at transition**: $Re_{x_T} = 3.4\times10^7$, so $\theta_T = \dfrac{0.73(3.4)}{\sqrt{3.4\times10^7}} = 4.2566\times10^{-4}$ m.
2. **Virtual origin.** The turbulent layer must reach $\theta_T$ after a length $x_T-x_0$ (see [[Virtual Origin Method]]):

$$
0.037(x_T-x_0)^{0.8}\left(\frac{\nu}{U_\infty}\right)^{0.2} = \theta_T\;\Rightarrow\;x_T-x_0 = 0.2119\text{ m},\quad x_0 = 3.1881\text{ m}
$$

3. **Turbulent $\theta$ at the TE**:

$$
\theta_L = 0.037(L-x_0)^{0.8}\left(\frac{\nu}{U_\infty}\right)^{0.2} = 3.3682\times10^{-3}\text{ m}
$$

4. **Drag, one side**:

$$
D' = \rho U_\infty^2\theta_L = 1.2(150^2)(3.3682\times10^{-3}) = \boxed{90.9415\text{ N/m}}
$$

For context, a fully near-laminar plate would give 15.27 N/m and a fully turbulent one 166.76 N/m.

## Q2: Martian slope, $\psi = U_\infty r^n\sin n\theta+\dfrac{Q\theta}{2\pi}$ ($n = 1.5$, $U_\infty = 2$, $Q = 4$)
This is a corner flow in a $2\pi/3$ wedge plus a source at the origin. See [[Elementary Potential Flows]].

$$
u_r = \frac1r\frac{\partial\psi}{\partial\theta} = U_\infty nr^{n-1}\cos n\theta+\frac{Q}{2\pi r},\qquad u_\theta = -\frac{\partial\psi}{\partial r} = -U_\infty nr^{n-1}\sin n\theta
$$

### (a) Slope streamline through $(0,1)$
Here $r = 1$ and $\theta = \pi/2$, so $\psi = 2\sin\frac{3\pi}{4}+\frac{4}{2\pi}\cdot\frac\pi2 = \sqrt2+1$:

$$
\boxed{2r^{1.5}\sin(1.5\theta)+\frac{2\theta}{\pi} = 1+\sqrt2 = 2.4142}
$$

### (b) Normal velocity at $(r,\theta) = (2.051,\pi/12)$
Check: $\psi(2.051,\pi/12) = 2.4148\approx2.4142$, so the point lies **on the slope streamline** (to the rounding of $r$). The normal to a streamline is $\hat n\propto\nabla\psi = (-u_\theta,u_r)$, so

$$
\mathbf V\cdot\hat n\propto u_r(-u_\theta)+u_\theta u_r = \boxed{0.0000\text{ m/s}}
$$

No flow crosses a streamline, which is exactly why it can represent the ground. The flow there is purely tangential: $u_r = 4.2797$, $u_\theta = -1.6442$, $|V| = 4.5847$ m/s.

### (c) Erosion at $(0,1)$?

$$
u_r = 1.5(2)\cos\frac{3\pi}4+\frac{4}{2\pi} = -2.1213+0.6366 = -1.4847,\qquad u_\theta = -3\sin\frac{3\pi}4 = -2.1213
$$

$$
|V| = \sqrt{1.4847^2+2.1213^2} = \boxed{2.5893\text{ m/s}>U_\infty = 2}\;\Rightarrow\;\textbf{erosion occurs}
$$

### (d) $C_p$ at $(\sqrt2,\pi/4)$, i.e. $(x,z) = (1,1)$

$$
u_r = 3(2^{1/4})\cos\frac{3\pi}8+\frac{2}{\pi\sqrt2} = 1.3653+0.4502 = 1.8154,\qquad u_\theta = -3(2^{1/4})\sin\frac{3\pi}8 = -3.2961
$$

$$
C_p = 1-\frac{u_r^2+u_\theta^2}{U_\infty^2} = 1-\frac{14.1597}{4} = \boxed{-2.5399}
$$

![[e2425_q2_slope.png|700]]

## Q3: AUV hydrofoil, $z/c = \epsilon\frac xc\left(1-\frac xc\right)$
$dz/dx = \epsilon\cos\theta_0$, so $A_0 = \alpha$, $A_1 = \epsilon$ and $A_2 = 0$. The same camber line appeared in [[SESA2022 Exam 2019-20 Solutions]] Q2.

- **(a)** $C_l = \pi(2\alpha+\epsilon) = 0.5$ at $\alpha = 2^\circ = 0.034907$ rad, so $\epsilon = \dfrac{0.5}{\pi}-2\alpha = \boxed{0.0893}$ (0.08934).
- **(b)** $C_{m,c/4} = \frac\pi4(A_2-A_1) = -\dfrac{\pi\epsilon}{4} = \boxed{-0.0702}$.
- **(c)** $dz/dx = 0$ at $x = c/2$, so the maximum camber is $\epsilon c/4 = \boxed{2.2335\,\%\text{ of }c\text{ at mid-chord}}$.
- **(d)** The steep adverse pressure gradient behind the suction peak separates the boundary layer at the leading edge (a laminar bubble that bursts), causing **stall**: loss of lift and a rise in drag. On a hydrofoil the low pressure can also cause **cavitation**. See [[Aerofoil Stall]].
- **(e)** At **4°** the flow is attached on both surfaces, the stagnation point is just under the LE, the flow leaves the TE smoothly (Kutta condition), and the wake is thin. At **14°**, near or past stall, the upper-surface flow separates (from the TE, creeping forward, or abruptly from the LE), leaving a large recirculation region and a thick unsteady wake.

## Q4: Non-elliptic wing, $V = 120$ m/s, $b = 12$ m, $AR = 4$

### (a) $C_L = \pi AR\,B_1$
With $dy = \frac b2\sin\theta\,d\theta$:

$$
L = \rho V_\infty\int\Gamma\,dy = \rho V_\infty^2b^2\sum B_n\int_0^\pi\sin n\theta\sin\theta\,d\theta = \frac\pi2\rho V_\infty^2b^2B_1
$$

$$
\boxed{C_L = \frac{2L}{\rho V_\infty^2S} = \pi\frac{b^2}{S}B_1 = \pi AR\,B_1}
$$

### (b) Lift coefficient
$B_1 = 0.0152$, so $C_L = \pi(4)(0.0152) = \boxed{0.1910}$.

### (c) Sectional lift-curve slope ($\alpha = 5^\circ$, $\alpha_{L=0} = -2^\circ$, $\tau = \delta$)

$$
\delta = \sum_{n\ge2}n\left(\frac{B_n}{B_1}\right)^2 = 3\left(\frac{0.0013}{0.0152}\right)^2 = 0.0219
$$

$$
a = \frac{0.1910}{7^\circ} = \frac{0.1910}{0.12217} = 1.5634\text{ rad}^{-1}
$$

$$
a_0 = \frac{a}{1-\frac{a(1+\tau)}{\pi AR}} = \frac{1.5634}{1-0.1271} = \boxed{1.7912\text{ rad}^{-1}}
$$

This is unrealistically low compared with $2\pi$, but it follows from the given data.

### (d) Power for total drag
$\rho$ is not given in the question, so take sea level, $\rho = 1.225$ kg/m³. $S = b^2/AR = 36$ m² and $q = 8820$ Pa.

$$
C_{D_i} = \frac{C_L^2}{\pi AR}(1+\delta) = 0.0030,\qquad C_D = 0.006+0.002967 = 0.0090
$$

$$
D = qSC_D = 2847.2\text{ N}\;\Rightarrow\;P = DV = \boxed{341.6660\text{ kW}}
$$

### (e) Oswald factor
$e = 1/(1+\delta) = \boxed{0.9785}$, so the loading is nearly elliptic and efficient. $B_3>0$ reduces the mid-span loading relative to an ellipse and pushes lift outboard. That's typical of a **low-taper or rectangular-ish** planform, whose chord near the tips is larger than elliptic. See [[Oswald Efficiency Factor]].

## Sources
- `03 - Exams & Past Papers/SESA2022-202425-01-SESA2022.pdf`. All numbers verified in Python.
