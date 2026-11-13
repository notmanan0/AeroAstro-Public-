---
title: "SESA3029 Past Paper 2018-19 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, laval-nozzle, shock-expansion, ackeret, method-of-characteristics, minimum-length-nozzle, reynolds-analogy, cfd, maccormack]
paper: "2018-19"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-201819-01-SESA3029W1.pdf"]
---

# SESA3029 Past Paper 2018-19 - Solutions

> [!abstract] Paper info
> 2018-19 Semester 1 examination (SESA3029W1, 2 hours, formula sheet on pp. 10–11), five questions worth 36 + 16 + 16 + 12 + 20 = 100 marks. Front-page constants: $R=287\ \text{J/(kg K)}$, $c_p=1005\ \text{J/(kg K)}$, $\gamma=1.4$, $\text{Pr}=0.7$, $\rho=1.225\ \text{kg/m}^3$, $\mu=1.79\times10^{-5}\ \text{N s/m}^2$. Question 4 is heat transfer (Weeks 9–12, not yet lectured). Table values are the IFT and NST rows at their 0.02 spacing, interpolated linearly; $p/p_0$ at Mach numbers between rows comes from the formula-sheet isentropic relation. Every number was checked in Python against the exact relations.

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 36 | Planar C-D nozzle ($A_e/A^*=2.4$, $p_{\text{atm}}=100\ \text{kPa}$) exit shock; diamond aerofoil ($5^\circ$ semi-angle, $\alpha=5^\circ$, $M_\infty=1.9$) by shock-expansion; $C_L(M_\infty)$ | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]], [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils|W07a]] |
| 2 | 16 | Ackeret's formula $C_p=2\theta/\sqrt{M_\infty^2-1}$ from $\eta=x-\lambda y$, applied to the Q1 diamond | [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 3 | 16 | Planar minimum-length nozzle ($M_e=1.8$): $\theta_{\max}=\nu(M_e)/2$, MoC table for points 1–5, coordinates of points 1 and 2 | [[SESA3029 W05a - Method of Characteristics|W05a]], [[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]] |
| 4 | 12 | Reynolds analogy and scaling of a cooled turbine blade (heat transfer, Weeks 9–12, not yet lectured) | Not yet lectured |
| 5 | 20 | Quasi-1D MacCormack nozzle code ($A_e/A^*=2.28$): normalisation, $p_b/p_0$ regimes, outflow boundary condition | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]], [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]] |

---

## Q1. Over-expanded nozzle and diamond aerofoil (36 marks)

> **(a)** A planar C-D nozzle ($A_e/A^* = 2.4$) operates with $p_0 = 600\ \text{kN/m}^2$, $T_0 = 1200\ \text{K}$, exhausting into $p_{\text{atm}} = 100\ \text{kN/m}^2$.
> (i) Find $p_{\text{throat}}, T_{\text{throat}}, p_{\text{exit}}, T_{\text{exit}}$. [6]
> (ii) Find the exit shock angle $\beta$ and jet edge deflection angle $\Delta$. [6]
> (iii) Classify as over- or under-expanded and sketch two ways the wave pattern continues downstream. [6]
>
> **(b)** A symmetric diamond aerofoil of chord $c=1\ \text{m}$ and leading-edge semi-angle $5^\circ$ is at incidence $\alpha = 5^\circ$ in an $M_\infty = 1.9$, $p_\infty = 70\ \text{kN/m}^2$ flow.
> (iv) Use shock-expansion to find the static pressures on all four faces and the resulting forces $F_x, F_y$ defined in Figure Q.1(b). [15]
> (v) Sketch $C_L$ vs $M_\infty$ for a thin aerofoil, including theoretical curves in the subsonic and supersonic regimes. [3]

![[at_pp_201819_q1_overexpanded_diamond.png|900]]

### (i) Throat and exit conditions [6 marks]

The nozzle flow is taken as steady, quasi-one-dimensional and isentropic, with $\gamma=1.4$. The nozzle exhausts a supersonic jet, so it is choked and the throat is sonic ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]). The IFT row $M=1.00$ gives $p/p_0=0.5283$ and $T/T_0=0.8333$:

$$
p_{\text{throat}}=0.5283\times600=\boxed{317.0\ \text{kPa}},
$$

$$
T_{\text{throat}}=0.8333\times1200=\boxed{1000\ \text{K}}.
$$

The exit is on the supersonic branch at $A_e/A^*=2.4$. The IFT rows that bracket it are

| $M$ | $A/A^*$ | $p/p_0$ | $T/T_0$ |
|---:|---:|---:|---:|
| 2.38 | 2.3593 | 0.0706 | 0.4688 |
| 2.40 | 2.4031 | 0.0684 | 0.4647 |

with

$$
f=\frac{2.4000-2.3593}{2.4031-2.3593}=\frac{0.0407}{0.0438}=0.9292,
$$

$$
M_{\text{exit}}=2.38+0.02\times0.9292=2.3986,
$$

$$
\frac{p_{\text{exit}}}{p_0}=0.0706-0.9292\times(0.0706-0.0684)=0.06856,
$$

$$
\frac{T_{\text{exit}}}{T_0}=0.4688-0.9292\times(0.4688-0.4647)=0.4650.
$$

Hence

$$
p_{\text{exit}}=0.06856\times600=\boxed{41.13\ \text{kPa}},
$$

$$
T_{\text{exit}}=0.4650\times1200=\boxed{558.0\ \text{K}}.
$$

The exact isentropic relations give the same values to the figures quoted.

### (ii) Exit shock angle and jet edge deflection [6 marks]

The exit shock raises the static pressure from $p_{\text{exit}}$ to the atmospheric pressure at the jet edge:

$$
\frac{p_2}{p_1}=\frac{p_{\text{atm}}}{p_{\text{exit}}}=\frac{100}{41.13}=2.4313.
$$

The NST $p_2/p_1$ column is read backwards for the normal Mach number. The bracketing rows are

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ |
|---:|---:|---:|
| 1.48 | 0.7083 | 2.3888 |
| 1.50 | 0.7011 | 2.4583 |

so

$$
f=\frac{2.4313-2.3888}{2.4583-2.3888}=\frac{0.0425}{0.0695}=0.6115,
$$

$$
M_{n1}=1.48+0.02\times0.6115=1.4922.
$$

The shock angle follows from $M_{n1}=M_{\text{exit}}\sin\beta$:

$$
\sin\beta=\frac{M_{n1}}{M_{\text{exit}}}=\frac{1.4922}{2.3986}=0.6221,
$$

$$
\beta=\boxed{38.47^\circ}.
$$

The deflection $\Delta$ is the flow turning across this shock, so it is the $\theta$ of the θ–β–M relation ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]]). With $M_{\text{exit}}^2\sin^2\beta=M_{n1}^2$,

$$
\tan\Delta=2\cot\beta\,\frac{M_{n1}^2-1}{M_{\text{exit}}^2(\gamma+\cos2\beta)+2}.
$$

Substitute $\cot38.47^\circ=1.2585$, $M_{n1}^2-1=1.2267$, $M_{\text{exit}}^2=5.7533$ and $\cos76.94^\circ=0.2260$:

$$
\tan\Delta=2\times1.2585\times\frac{1.2267}{5.7533\times(1.4+0.2260)+2}=2.5170\times\frac{1.2267}{11.355}=0.2719,
$$

$$
\Delta=\boxed{15.21^\circ}.
$$

### (iii) Over-expanded jet and two downstream patterns [6 marks]

The exit pressure, $41.13$ kPa, is below the atmospheric $100$ kPa, so the nozzle is over-expanded: the jet is compressed by oblique shocks from the lips and its edges turn inwards.

The two lip shocks meet on the jet centreline, and the pattern continues in one of two ways ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]). In a regular reflection the shocks cross at a point on the centreline, which acts like a plane of symmetry, and the transmitted shocks turn the flow back parallel to the axis. They then reach the free jet boundaries, where the pressure is fixed at $p_{\text{atm}}$; a shock arriving at a constant-pressure boundary reflects as an expansion fan, which turns the jet edge outwards again. The fans reflect from the opposite boundaries as compressions, and the cycle repeats as the familiar train of shock diamonds.

In a Mach reflection the lip shocks cannot be reflected regularly. A near-normal shock, the Mach disc, stands across the core of the jet between two triple points. Reflected oblique shocks leave the triple points, and slip lines run downstream from them, separating the subsonic flow behind the Mach disc from the supersonic flow behind the reflected shocks.

Which pattern occurs here can be checked. Behind the lip shock the normal component is, from the same NST rows as (ii), $M_{n2}=0.7083-0.6115\times(0.7083-0.7011)=0.7039$, so

$$
M_2=\frac{M_{n2}}{\sin(\beta-\Delta)}=\frac{0.7039}{\sin23.26^\circ}=1.782.
$$

The largest deflection an attached shock can give at $M=1.782$ is $\theta_{\max}=18.81^\circ$. The reflection at the centreline has to turn the flow back by $\Delta=15.21^\circ<18.81^\circ$, so a regular reflection is possible at this back pressure. Raising $p_{\text{atm}}$ strengthens the lip shocks; the regular reflection can no longer exist once $\Delta=\theta_{\max}(M_2)$, which happens at $p_{\text{atm}}\approx110$ kPa ($p_{\text{atm}}/p_{\text{exit}}\approx2.68$).

### (iv) Diamond aerofoil pressures and forces by shock-expansion [15 marks]

In Figure Q.1(b) the chord is horizontal and the stream approaches from below at $\alpha=5^\circ$. The semi-angle is $\varepsilon=5^\circ$. Measured from the stream direction, the upper front face (1U) lies at $\varepsilon-\alpha=0^\circ$, so no wave forms on it. The lower front face (1L) turns the stream into itself by $\varepsilon+\alpha=10^\circ$, through an oblique shock. At each crest the surface turns away from the flow by $2\varepsilon=10^\circ$, through a Prandtl–Meyer fan.

#### Upper front face

$$
M_{1U}=1.90,\qquad p_{1U}=\boxed{70.0\ \text{kPa}}.
$$

#### Upper rear face: 10° expansion from M = 1.9

The IFT row $M=1.90$ gives $\nu_{1U}=23.5861^\circ$. The fan adds $10^\circ$:

$$
\nu_{2U}=23.5861^\circ+10^\circ=33.5861^\circ.
$$

The IFT rows $M=2.26$ ($\nu=33.2730^\circ$) and $M=2.28$ ($\nu=33.7796^\circ$) bracket it:

$$
f=\frac{33.5861-33.2730}{33.7796-33.2730}=\frac{0.3131}{0.5066}=0.6180,
$$

$$
M_{2U}=2.26+0.02\times0.6180=2.2724.
$$

The isentropic relation $p/p_0=\left(1+0.2M^2\right)^{-3.5}$ gives

$$
\frac{p_{1U}}{p_0}=\left(1+0.2\times1.90^2\right)^{-3.5}=1.722^{-3.5}=0.14924,
$$

$$
\frac{p_{2U}}{p_0}=\left(1+0.2\times2.2724^2\right)^{-3.5}=2.0328^{-3.5}=0.08350.
$$

$p_0$ is unchanged through the fan, so

$$
p_{2U}=p_{1U}\,\frac{p_{2U}/p_0}{p_{1U}/p_0}=70.0\times\frac{0.08350}{0.14924}=\boxed{39.17\ \text{kPa}}.
$$

#### Lower front face: oblique shock with M = 1.9 and θ = 10°

The weak-shock angle comes from the θ–β–M relation by the secant rule, starting from $40^\circ$ and $43^\circ$ either side of the OSC reading:

| Iterate | $\beta$ (°) | $\theta(\beta)$ (°) |
|---:|---:|---:|
| 0 | 40.0000 | 8.6731 |
| 1 | 43.0000 | 11.2745 |
| 2 | 41.5302 | 10.0345 |
| 3 | 41.4894 | 9.9991 |
| 4 | 41.4904 | 10.0000 |

The first update is

$$
\beta_2=43+(10-11.2745)\,\frac{43-40}{11.2745-8.6731}=43-1.4698=41.5302^\circ,
$$

and the exact weak root is $\beta=41.49^\circ$. The normal Mach number is

$$
M_{n1}=1.9\sin41.49^\circ=1.9\times0.66249=1.25874.
$$

The NST rows $M_{n1}=1.24$ ($M_{n2}=0.8183$, $p_2/p_1=1.6272$) and $1.26$ ($0.8071$, $1.6855$) bracket it, with $f=(1.25874-1.24)/0.02=0.937$:

$$
M_{n2}=0.8183-0.937\times(0.8183-0.8071)=0.8078,
$$

$$
\frac{p_{1L}}{p_\infty}=1.6272+0.937\times(1.6855-1.6272)=1.6818.
$$

The flow behind the shock is parallel to the face, at $\beta-\theta=31.49^\circ$ to the shock:

$$
M_{1L}=\frac{M_{n2}}{\sin(\beta-\theta)}=\frac{0.8078}{\sin31.49^\circ}=\frac{0.8078}{0.5224}=1.5465,
$$

$$
p_{1L}=70.0\times1.6818=\boxed{117.73\ \text{kPa}}.
$$

#### Lower rear face: 10° expansion from M = 1.5465

The IFT rows $M=1.54$ ($\nu=13.0856^\circ$) and $M=1.56$ ($\nu=13.6770^\circ$) give, with $f=(1.5465-1.54)/0.02=0.325$,

$$
\nu_{1L}=13.0856+0.325\times(13.6770-13.0856)=13.2778^\circ.
$$

The fan adds $10^\circ$:

$$
\nu_{2L}=13.2778^\circ+10^\circ=23.2778^\circ.
$$

The rows $M=1.88$ ($\nu=23.0190^\circ$) and $M=1.90$ ($\nu=23.5861^\circ$) bracket it:

$$
f=\frac{23.2778-23.0190}{23.5861-23.0190}=\frac{0.2588}{0.5671}=0.4564,
$$

$$
M_{2L}=1.88+0.02\times0.4564=1.8891.
$$

The isentropic pressure ratios are

$$
\frac{p_{1L}}{p_{0L}}=\left(1+0.2\times1.5465^2\right)^{-3.5}=1.4783^{-3.5}=0.25456,
$$

$$
\frac{p_{2L}}{p_{0L}}=\left(1+0.2\times1.8891^2\right)^{-3.5}=1.7137^{-3.5}=0.15177,
$$

so

$$
p_{2L}=117.73\times\frac{0.15177}{0.25456}=\boxed{70.19\ \text{kPa}}.
$$

The rear lower pressure ends slightly above $p_\infty$ although the lower stream was turned by $+10^\circ$ and then $-10^\circ$. The shock is not reversible: it reduced the stagnation pressure, and the isentropic fan cannot restore it.

#### Forces on the diamond

In Figure Q.1(b), $F_x$ is along the chord, positive towards the trailing edge, and $F_y$ is normal to it, positive upwards. Each face has length $(c/2)/\cos5^\circ$, so its projections are $c/2=0.5$ m along the chord and $(c/2)\tan5^\circ=0.5\times0.08749=0.04374$ m normal to it. The front faces face forwards, so their pressures push aft; the rear faces push forwards. The lower faces push up and the upper faces push down. Hence

$$
F_x=\left[(p_{1U}+p_{1L})-(p_{2U}+p_{2L})\right]\frac{c}{2}\tan5^\circ,
$$

$$
F_x=\left[(70.00+117.73)-(39.17+70.19)\right]\times0.04374=78.37\times0.04374=\boxed{3.43\ \text{kN/m}},
$$

and

$$
F_y=\left[(p_{1L}+p_{2L})-(p_{1U}+p_{2U})\right]\frac{c}{2},
$$

$$
F_y=\left[(117.73+70.19)-(70.00+39.17)\right]\times0.5=78.75\times0.5=\boxed{39.38\ \text{kN/m}}.
$$

> [!check] Lift, drag and the exact chain
> The stream is inclined at $+5^\circ$ to the chord, so $L=F_y\cos\alpha-F_x\sin\alpha=38.93$ kN/m and $D=F_x\cos\alpha+F_y\sin\alpha=6.847$ kN/m. With $q_\infty=\tfrac12\gamma p_\infty M_\infty^2=176.89$ kPa these are $C_L=0.220$ and $C_D=0.0387$. Repeating the whole chain with the exact relations gives $F_x=3.428$ kN/m and $F_y=39.374$ kN/m.

### (v) Lift coefficient against Mach number [3 marks]

The right-hand panel of the figure shows the two theoretical curves; the measured curve joins them through the transonic range ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#8. Lift, drag and the mechanism of drag divergence|W07a §8]]). In subsonic flow $C_L$ starts from the incompressible thin-aerofoil value $C_{L0}=2\pi\alpha$ and rises with Mach number along the Prandtl–Glauert curve $C_L=C_{L0}/\sqrt{1-M_\infty^2}$, which tends to infinity as $M_\infty\to1$. The real curve follows it up to about the critical Mach number, then rises a little faster as a supersonic region forms on the upper surface, peaks in the transonic range (around $M_\infty\approx0.85$ for a typical section) and drops sharply. In supersonic flow $C_L$ falls slowly and approaches Ackeret's result $C_L=4\alpha/\sqrt{M_\infty^2-1}$, which also tends to infinity as $M_\infty\to1$ and decays like $4\alpha/M_\infty$ at high Mach number. Neither linear theory applies near $M_\infty=1$.

---

## Q2. Ackeret's formula derivation and application (16 marks)

> (i) Starting from $(1 - M_\infty^2)\dfrac{\partial^2\phi}{\partial x^2} + \dfrac{\partial^2\phi}{\partial y^2} = 0$, derive $C_p = \dfrac{2\theta}{\sqrt{M_\infty^2 - 1}}$ using the characteristic coordinate $\eta = x - \lambda y$ ($\lambda = \sqrt{M_\infty^2 - 1}$), assuming $C_p = -2u'/U_\infty$. [10]
> (ii) Apply Ackeret's theory to the diamond aerofoil of Figure Q.1(b) ($M_\infty=1.9$, $p_\infty=70\ \text{kN/m}^2$, $\alpha=5^\circ$, semi-angle $5^\circ$) to find $p_{1L}, p_{1U}, p_{2L}, p_{2U}$. [6]

### (i) Derivation of Ackeret's formula [10 marks]

The derivation follows [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]]. For $M_\infty>1$ the coefficient $1-M_\infty^2$ is negative. Write $\lambda=\sqrt{M_\infty^2-1}>0$, so that $1-M_\infty^2=-\lambda^2$:

$$
-\lambda^2\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0.
$$

$$
\lambda^2\frac{\partial^2\phi}{\partial x^2}-\frac{\partial^2\phi}{\partial y^2}=0.
$$

This has the form of the wave equation, with $x$ in the role of time. Try a potential that is constant along the lines $\eta=x-\lambda y=\text{const}$:

$$
\phi(x,y)=f(\eta),\qquad \eta=x-\lambda y.
$$

Since $\partial\eta/\partial x=1$, the chain rule gives

$$
\frac{\partial\phi}{\partial x}=f'(\eta),
$$

$$
\frac{\partial^2\phi}{\partial x^2}=f''(\eta).
$$

Since $\partial\eta/\partial y=-\lambda$,

$$
\frac{\partial\phi}{\partial y}=-\lambda f'(\eta),
$$

$$
\frac{\partial^2\phi}{\partial y^2}=(-\lambda)^2f''(\eta)=\lambda^2f''(\eta).
$$

Substitute into the governing equation:

$$
\lambda^2f''(\eta)-\lambda^2f''(\eta)=0,
$$

which holds for any twice-differentiable $f$. A potential constant along $x-\lambda y=\text{const}$ therefore satisfies the equation. These lines are inclined at $\arctan(1/\lambda)=\mu$, the Mach angle, and run downstream and upwards, so they carry disturbances from the body into the flow above it. The other family, $g(x+\lambda y)$, would carry disturbances upstream above the body, which supersonic flow cannot do, so it is discarded above the aerofoil.

On the upper surface $y=y_u(x)$ the linearised tangency condition, applied on $y=0$, is

$$
v'=\left.\frac{\partial\phi}{\partial y}\right|_{y=0}=U_\infty\frac{\mathrm{d}y_u}{\mathrm{d}x}.
$$

With $\partial\phi/\partial y=-\lambda f'$:

$$
-\lambda f'(x)=U_\infty\frac{\mathrm{d}y_u}{\mathrm{d}x},
$$

$$
f'(x)=-\frac{U_\infty}{\lambda}\frac{\mathrm{d}y_u}{\mathrm{d}x}.
$$

The streamwise perturbation is $u'=\partial\phi/\partial x=f'$, so

$$
C_p=-\frac{2u'}{U_\infty}=-\frac{2}{U_\infty}\left(-\frac{U_\infty}{\lambda}\frac{\mathrm{d}y_u}{\mathrm{d}x}\right),
$$

$$
C_p=\frac{2}{\lambda}\frac{\mathrm{d}y_u}{\mathrm{d}x}.
$$

On the upper surface a positive slope turns the flow into itself. Writing $\theta=\mathrm{d}y_u/\mathrm{d}x$ for this local inclination, in radians and positive for compression:

$$
\boxed{C_p=\frac{2\theta}{\sqrt{M_\infty^2-1}}}
$$

Below the body the same steps with $\phi=g(x+\lambda y)$ give $\partial\phi/\partial y=+\lambda g'$, hence $C_p=-(2/\lambda)\,\mathrm{d}y_l/\mathrm{d}x$. A lower surface compresses the flow when it slopes downwards, so with $\theta=-\mathrm{d}y_l/\mathrm{d}x$ the formula is the same.

### (ii) Ackeret pressures on the diamond aerofoil [6 marks]

![[at_pp_201819_q2_ackeret_diamond.png|900]]

At $M_\infty=1.9$,

$$
\lambda=\sqrt{1.9^2-1}=\sqrt{2.61}=1.6155,
$$

and the free-stream dynamic pressure, written with $\rho U^2=\gamma pM^2$, is

$$
q_\infty=\tfrac12\gamma p_\infty M_\infty^2=0.5\times1.4\times70\times1.9^2=176.89\ \text{kPa}.
$$

Ackeret's $\theta$ is each face's inclination to the free stream, positive when the face turns the stream into itself. The front faces have $\theta_{1U}=\varepsilon-\alpha=0$ and $\theta_{1L}=\varepsilon+\alpha=+10^\circ=+0.17453$ rad. The upper rear face slopes down at $\varepsilon$ to the chord, so $\theta_{2U}=-(\varepsilon+\alpha)=-10^\circ$, and the lower rear face rises at $\varepsilon$ to the chord, parallel to the stream, so $\theta_{2L}=-(\varepsilon-\alpha)=0$. A face with $\theta=0$ has $C_p=0$:

$$
p_{1U}=\boxed{70.0\ \text{kPa}},\qquad p_{2L}=\boxed{70.0\ \text{kPa}}.
$$

On the lower front face,

$$
C_{p,1L}=\frac{2\times0.17453}{1.6155}=+0.21607,
$$

$$
p_{1L}=70+176.89\times0.21607=70+38.22=\boxed{108.22\ \text{kPa}}.
$$

On the upper rear face,

$$
C_{p,2U}=\frac{2\times(-0.17453)}{1.6155}=-0.21607,
$$

$$
p_{2U}=70-176.89\times0.21607=70-38.22=\boxed{31.78\ \text{kPa}}.
$$

> [!check] Against shock-expansion, Q1(iv)
> Both methods give $70.0$ kPa on face 1U. On 2L Ackeret gives $70.0$ kPa against $70.19$ kPa, missing only the entropy rise through the shock. The $10^\circ$ compression is under-predicted ($108.2$ against $117.7$ kPa) and the $10^\circ$ expansion is over-predicted ($31.8$ against $39.2$ kPa), because linear theory treats $\pm\theta$ symmetrically. In the normal force $F_y=\tfrac{c}{2}\left[(p_{1L}+p_{2L})-(p_{1U}+p_{2U})\right]$ the two errors act in opposite directions: the low $p_{1L}$ reduces $F_y$ and the low $p_{2U}$ increases it. Ackeret gives $F_y=38.22$ kN/m against $39.38$ kN/m, only $3\,\%$ lower, although the individual pressures are wrong by up to $19\,\%$.

---

## Q3. Minimum-length supersonic nozzle by Method of Characteristics (16 marks)

> A symmetric 2D minimum-length nozzle accelerates air to $M_e = 1.8$ at point 5, with initial $C^-$ rays $0\text{–}2$ at $\theta_{\max}$ and $0\text{–}1$ at $0.5\theta_{\max}$.
> (i) Show that $\theta_{\max} = \nu(M_e)/2$. [4]
> (ii) Complete the MoC table for points 1–5 ($R^+, R^-, \theta, \nu, M$). [6]
> (iii) With $0 = (0,1)$ and centreline $y=0$, compute the $(x,y)$ coordinates of points 1 and 2. [6]

![[at_pp_201819_q3_mln.png|820]]

### (i) Proof that the maximum wall angle is half the exit Prandtl–Meyer angle [4 marks]

The course invariants are $R^+=\nu-\theta$, constant along $C^+$, and $R^-=\nu+\theta$, constant along $C^-$ ([[SESA3029 W05a - Method of Characteristics|W05a]]). The argument follows [[SESA3029 W05b - Minimum-Length Nozzle Design#13. The minimum-length nozzle|W05b §13]]. At the sonic throat

$$
M=1,\qquad \nu=0,\qquad \theta=0.
$$

The corner at 0 expands the flow in a centred fan of $C^-$ waves. Every $C^+$ line crossing the fan comes from the uniform sonic flow and carries

$$
R^+=\nu-\theta=0,
$$

so on every ray of the fan $\nu=\theta$. The last ray, 0–2–3, leaves at the wall angle $\theta_{\max}$, so it carries

$$
R^-_{023}=\nu+\theta=\theta_{\max}+\theta_{\max}=2\theta_{\max}.
$$

It reaches the centreline at point 3, where symmetry gives $\theta_3=0$. Downstream of the $C^+$ line 3–5 the flow is uniform at the design condition, so point 3 already has $\nu_3=\nu(M_e)$:

$$
R^-_3=\nu(M_e)+0=\nu(M_e).
$$

$R^-$ is constant along 0–2–3:

$$
2\theta_{\max}=\nu(M_e),
$$

$$
\boxed{\theta_{\max}=\frac{\nu(M_e)}{2}}
$$

### (ii) Completed MoC table [6 marks]

The IFT row $M=1.80$ gives $\nu(M_e)=20.7251^\circ$, so

$$
\theta_{\max}=\frac{20.7251^\circ}{2}=10.3626^\circ,\qquad \frac{\theta_{\max}}{2}=5.1813^\circ.
$$

Ray 0–1 has $\theta=\nu=5.1813^\circ$, so $R^-_{01}=10.3626^\circ$; ray 0–2 has $\theta=\nu=10.3626^\circ$, so $R^-_{02}=20.7251^\circ$.

Point 1 is on the centreline ($\theta_1=0$) at the end of ray 0–1:

$$
\nu_1=R^-_{01}-\theta_1=10.3626^\circ,\qquad R^+_1=\nu_1-\theta_1=10.3626^\circ.
$$

Point 2 is on the $C^+$ line from 1 and on ray 0–2:

$$
\nu_2=\frac{R^+_1+R^-_{02}}{2}=\frac{10.3626+20.7251}{2}=15.5438^\circ,
$$

$$
\theta_2=\frac{R^-_{02}-R^+_1}{2}=\frac{20.7251-10.3626}{2}=5.1813^\circ.
$$

Point 3 is on the centreline at the end of ray 0–2:

$$
\nu_3=R^-_{02}-0=20.7251^\circ,\qquad R^+_3=20.7251^\circ,
$$

so $M_3=1.80$. Points 4 and 5 are on the designed, non-reflecting wall, so each copies the state of the point below it on its $C^+$ line: point 4 has the state of point 2, point 5 that of point 3. No $C^-$ line leaves a non-reflecting wall point, so their $R^-$ entries are just $\nu+\theta$ at the point and are carried by no line.

The Mach numbers come from inverting $\nu$ in the IFT. For point 1 the rows $M=1.44$ ($\nu=10.1464^\circ$) and $M=1.46$ ($\nu=10.7305^\circ$) bracket $10.3626^\circ$:

$$
M_1=1.44+0.02\times\frac{10.3626-10.1464}{10.7305-10.1464}=1.44+0.02\times0.3701=1.4474.
$$

For point 2 the rows $M=1.62$ ($\nu=15.4518^\circ$) and $M=1.64$ ($\nu=16.0427^\circ$) bracket $15.5438^\circ$:

$$
M_2=1.62+0.02\times\frac{15.5438-15.4518}{16.0427-15.4518}=1.62+0.02\times0.1557=1.6231.
$$

| Point | $R^+$ (°) | $R^-$ (°) | $\theta$ (°) | $\nu$ (°) | $M$ |
|---:|---:|---:|---:|---:|---:|
| 1 | 10.36 | 10.36 | 0.00 | 10.36 | 1.447 |
| 2 | 10.36 | 20.73 | 5.18 | 15.54 | 1.623 |
| 3 | 20.73 | 20.73 | 0.00 | 20.73 | 1.800 |
| 4 | 10.36 | (20.73) | 5.18 | 15.54 | 1.623 |
| 5 | 20.73 | (20.73) | 0.00 | 20.73 | 1.800 |

### (iii) Coordinates of points 1 and 2 [6 marks]

The slopes need the Mach angles $\mu=\arcsin(1/M)$. On ray 0–1 at the corner, $\nu=5.1813^\circ$ lies between the IFT rows $M=1.26$ ($\nu=5.0931^\circ$) and $M=1.28$ ($\nu=5.6272^\circ$):

$$
M_{01}=1.26+0.02\times\frac{5.1813-5.0931}{5.6272-5.0931}=1.26+0.02\times0.1651=1.2633,
$$

$$
\mu_{01}=\arcsin\frac{1}{1.2633}=52.33^\circ.
$$

Ray 0–2 at the corner has $\nu=10.3626^\circ$, the same as point 1, so $M_{02}=1.4474$ and

$$
\mu_{02}=\mu_1=\arcsin\frac{1}{1.4474}=43.70^\circ.
$$

At point 2,

$$
\mu_2=\arcsin\frac{1}{1.6231}=38.03^\circ.
$$

| Point | $\theta$ (°) | $\mu$ (°) | $\theta+\mu$ (°) | $\theta-\mu$ (°) | $x$ | $y$ |
|---|---:|---:|---:|---:|---:|---:|
| 0 (ray 0–1) | 5.181 | 52.333 | 57.514 | −47.152 | 0 | 1 |
| 0 (ray 0–2) | 10.363 | 43.701 | 54.064 | −33.338 | 0 | 1 |
| 1 | 0 | 43.701 | 43.701 | −43.701 | 0.9852 | 0 |
| 2 | 5.181 | 38.032 | 43.213 | −32.851 | 1.2090 | 0.2120 |

Point 1 lies on the centreline at the end of the $C^-$ segment from 0, whose averaged slope is

$$
\alpha_{01}=\tfrac12\left[(\theta-\mu)_{0}+(\theta-\mu)_1\right]=\tfrac12\left[-47.152+(-43.701)\right]=-45.426^\circ.
$$

With $\tan\alpha_{01}=-1.0150$ and $y_1=0$:

$$
x_1=x_0+\frac{y_1-y_0}{\tan\alpha_{01}}=0+\frac{0-1}{-1.0150}=\boxed{0.985},\qquad y_1=\boxed{0}.
$$

Point 2 is the intersection of the $C^+$ segment from $A=1$ and the $C^-$ segment from $B=0$ along ray 0–2. The averaged slopes are

$$
\alpha_{12}=\tfrac12\left[(\theta+\mu)_1+(\theta+\mu)_2\right]=\tfrac12(43.701+43.213)=43.457^\circ,
$$

$$
\alpha_{02}=\tfrac12\left[(\theta-\mu)_{0}+(\theta-\mu)_2\right]=\tfrac12\left[-33.338+(-32.851)\right]=-33.094^\circ,
$$

with $\tan\alpha_{12}=0.9475$ and $\tan\alpha_{02}=-0.6518$. The formula-sheet intersection is

$$
x_2=\frac{x_B\tan\alpha_{BP}-x_A\tan\alpha_{AP}+y_A-y_B}{\tan\alpha_{BP}-\tan\alpha_{AP}}=\frac{0\times(-0.6518)-0.9852\times0.9475+0-1}{-0.6518-0.9475},
$$

$$
x_2=\frac{-1.9335}{-1.5993}=\boxed{1.209},
$$

$$
y_2=y_A+(x_2-x_A)\tan\alpha_{AP}=0+(1.2090-0.9852)\times0.9475=\boxed{0.212}.
$$

> [!check] The other characteristic
> Along the $C^-$ segment from 0, $y_2=1+1.2090\times(-0.6518)=0.2120$, the same point.

---

## Q4. Reynolds analogy and turbine blade cooling (12 marks)

> [!warning] Not yet lectured
> Heat transfer (Weeks 9–12, not yet lectured). Check the notation and correlations against those lectures when they are written up.

> (i) Define $\text{Nu}, \text{Re}, \text{Pr}$ and state how they relate via Reynolds analogy. [4]
> (ii) For air at $V=160\ \text{m/s}$, $T_\infty=1150^\circ\text{C}$ over a turbine blade of chord $L=40\ \text{mm}$, measured $\dot{q}(x^*) = 95{,}000\ \text{W/m}^2$ at $T_s = 800^\circ\text{C}$. Find $\dot{q}(x^*)$ when $T_s$ is reduced to $700^\circ\text{C}$. [3]
> (iii) Use Reynolds analogy to find $\dot{q}(x^*)$ on a geometrically similar blade with $L=80\ \text{mm}$, $V=80\ \text{m/s}$, $T_\infty = 1150^\circ\text{C}$, $T_s = 800^\circ\text{C}$. [5]

### (i) Dimensionless groups and Reynolds analogy [4 marks]

With convective coefficient $h$, length $L$, fluid conductivity $k$, density $\rho$, viscosity $\mu$, specific heat $c_p$ and speed $V$,

$$
\text{Nu}=\frac{hL}{k},\qquad \text{Re}=\frac{\rho VL}{\mu},\qquad \text{Pr}=\frac{\mu c_p}{k}.
$$

The **Nusselt number** compares convective with conductive heat transfer across the fluid, the **Reynolds number** compares inertial with viscous forces, and the **Prandtl number** compares momentum diffusivity with thermal diffusivity. Reynolds analogy rests on momentum and heat being carried across the boundary layer by the same mechanism. It links the Stanton number, $\text{St}=h/(\rho c_pV)=\text{Nu}/(\text{Re}\,\text{Pr})$, to the skin-friction coefficient:

$$
\text{St}=\frac{\text{Nu}}{\text{Re}\,\text{Pr}}=\frac{C_f}{2}.
$$

This form holds for $\text{Pr}\approx1$. For other Prandtl numbers the Chilton–Colburn form $\text{St}\,\text{Pr}^{2/3}=C_f/2$ is used.

### (ii) Lower surface temperature [3 marks]

With $V$, $T_\infty$ and $L$ unchanged, and fluid properties taken as constant, the coefficient $h(x^*)$ does not depend on $T_s$. Newton's law of cooling, $\dot q=h\,(T_\infty-T_s)$, then scales with the temperature difference:

$$
\dot q_2=\dot q_1\,\frac{T_\infty-T_{s,2}}{T_\infty-T_{s,1}}=95\,000\times\frac{1150-700}{1150-800}=95\,000\times\frac{450}{350}=\boxed{122.1\ \text{kW/m}^2}.
$$

### (iii) Geometrically similar blade [5 marks]

The air temperatures are unchanged, so $\rho$, $\mu$, $c_p$, $k$ and $\text{Pr}$ are the same. The Reynolds number ratio is

$$
\frac{\text{Re}_3}{\text{Re}_1}=\frac{V_3L_3}{V_1L_1}=\frac{80\times0.080}{160\times0.040}=\frac{6.4}{6.4}=1.
$$

The blades are geometrically similar and run at the same Reynolds number, so the skin-friction coefficient at the same non-dimensional position $x^*$ is the same. By Reynolds analogy, with $\text{Pr}$ also unchanged, the Stanton number at $x^*$ is the same:

$$
\frac{h_3}{\rho c_pV_3}=\frac{h_1}{\rho c_pV_1},
$$

$$
h_3=h_1\,\frac{V_3}{V_1}=h_1\times\frac{80}{160}=\tfrac12h_1.
$$

The temperature difference is again $1150-800=350$ K, so

$$
\dot q_3=\tfrac12\dot q_1=\frac{95\,000}{2}=\boxed{47.5\ \text{kW/m}^2}.
$$

The Nusselt number gives the same factor: equal $\text{Re}$ and $\text{Pr}$ mean equal $\text{Nu}$ at $x^*$, so $h_3=h_1L_1/L_3=\tfrac12h_1$.

---

## Q5. Quasi-1D MacCormack nozzle CFD simulation (20 marks)

> The Python code (pp. 8–9) solves the quasi-1D Euler equations in an asymmetric C-D nozzle using MacCormack's scheme with normalisation $x^\dagger=x/L$, $V^\dagger=V/a_0$, $\rho^\dagger=\rho/\rho_0$, $p^\dagger=p/(\rho_0 a_0^2)$, $T^\dagger=T/T_0$, $E^\dagger=E/a_0^2$, $t^\dagger=ta_0/L$, $A^\dagger=A/A^*$.
> (i) Prove $\dfrac{p}{p_0} = \gamma p^\dagger = \rho^\dagger T^\dagger$. [4]
> (ii) Find $p_b/p_0$ values (using linear interpolation of IFT and NST) for: (a) supersonic outflow, (b) subsonic flow throughout, (c) a shock wave in the divergent section. [10]
> (iii) Relate (ii) to the printed code output, explain why that regime occurs, and explain why/how to alter the outflow BC citing line numbers. [6]

### (i) Normalisation [4 marks]

The stagnation state obeys the perfect-gas law, and the stagnation sound speed is $a_0^2=\gamma RT_0$:

$$
p_0=\rho_0RT_0,
$$

$$
a_0^2=\gamma RT_0=\frac{\gamma p_0}{\rho_0},
$$

$$
\rho_0a_0^2=\gamma p_0.
$$

Substitute into the definition of $p^\dagger$:

$$
p^\dagger=\frac{p}{\rho_0a_0^2}=\frac{p}{\gamma p_0},
$$

$$
\frac{p}{p_0}=\gamma p^\dagger.
$$

Divide $p=\rho RT$ by $p_0=\rho_0RT_0$:

$$
\frac{p}{p_0}=\frac{\rho RT}{\rho_0RT_0}=\frac{\rho}{\rho_0}\,\frac{T}{T_0}=\rho^\dagger T^\dagger.
$$

Together, $p/p_0=\gamma p^\dagger=\rho^\dagger T^\dagger$.

### (ii) Back-pressure ranges [10 marks]

Lines 20 and 29–33 of the code set $L_x=3.0$, put the throat at $x^\dagger=1.0$ with $A^\dagger=1$, and give the divergent section $A^\dagger=1+0.16(x^\dagger-1)^3$. At the exit $x^\dagger=3.0$:

$$
\frac{A_e}{A^*}=1+0.16\times(3.0-1.0)^3=1+0.16\times8=2.28.
$$

#### (a) Supersonic outflow

The isentropic supersonic exit state lies between the IFT rows

| $M$ | $A/A^*$ | $p/p_0$ |
|---:|---:|---:|
| 2.34 | 2.2744 | 0.0751 |
| 2.36 | 2.3164 | 0.0728 |

with

$$
f=\frac{2.2800-2.2744}{2.3164-2.2744}=\frac{0.0056}{0.0420}=0.1333,
$$

$$
M_e=2.34+0.02\times0.1333=2.3427,
$$

$$
\frac{p_e}{p_0}=0.0751-0.1333\times(0.0751-0.0728)=0.07479.
$$

At $p_b/p_0=\boxed{0.0748}$ the jet leaves perfectly expanded. The flow at the exit plane stays supersonic and shock-free inside the nozzle for every back pressure below the exit-shock value found in (c), $p_b/p_0<0.4664$; between $0.0748$ and $0.4664$ the jet is over-expanded and adjusts through oblique shocks outside, and below $0.0748$ it is under-expanded and adjusts through expansion fans outside.

#### (b) Subsonic flow throughout

The highest back pressure at which the nozzle is just choked, with $M=1$ at the throat and subsonic flow everywhere else, is the subsonic-branch exit state for $A/A^*=2.28$. The bracketing IFT rows are

| $M$ | $A/A^*$ | $p/p_0$ |
|---:|---:|---:|
| 0.26 | 2.3173 | 0.9541 |
| 0.28 | 2.1656 | 0.9470 |

so

$$
f=\frac{2.2800-2.3173}{2.1656-2.3173}=\frac{-0.0373}{-0.1517}=0.2459,
$$

$$
M_e=0.26+0.02\times0.2459=0.2649,
$$

$$
\frac{p_b}{p_0}=0.9541-0.2459\times(0.9541-0.9470)=0.9524.
$$

The flow is subsonic throughout for

$$
\boxed{0.9524\le\frac{p_b}{p_0}<1}
$$

and is unchoked for $p_b/p_0>0.9524$. The exact value is $0.9525$.

#### (c) Shock in the divergent section

As $p_b/p_0$ falls below $0.9524$, a normal shock appears just downstream of the throat and moves downstream as the back pressure falls, until it stands at the exit plane. There the upstream state is the supersonic exit state of (a), $M_1=2.3427$ and $p_1/p_0=0.07479$. The NST rows $M_1=2.34$ ($p_2/p_1=6.2215$) and $M_1=2.36$ ($p_2/p_1=6.3312$) give, with the same $f=0.1333$,

$$
\frac{p_2}{p_1}=6.2215+0.1333\times(6.3312-6.2215)=6.2361,
$$

$$
\frac{p_b}{p_0}=\frac{p_1}{p_0}\,\frac{p_2}{p_1}=0.07479\times6.2361=0.4664.
$$

A normal shock stands inside the divergent section for

$$
\boxed{0.4664<\frac{p_b}{p_0}<0.9524}.
$$

The exact lower limit is $0.4665$.

### (iii) The printed output and the outflow boundary condition [6 marks]

At $x^\dagger=3.0000$ the printed output has $A^\dagger=2.2800$, `pp` $=p/p_0=0.0748$ and `Mp` $=2.3431$. This is case (a), the shock-free supersonic outflow at the design pressure ratio.

It occurs because no back pressure is imposed. Line 10 sets `p_p0 = 0.` and line 11 sets `pe = p_p0/gamma = 0.`, so the test `if pe>0.0:` on line 82 is false and line 83 never runs. All three conserved variables at the outlet are then extrapolated linearly from the two interior points by line 81, `U[Nx-1] = 2*U[Nx-2] - U[Nx-3]`. For supersonic outflow this is the correct treatment. All three characteristic speeds, $V$ and $V\pm a$, are positive at the exit, so every characteristic leaves the domain there and no physical condition may be imposed; the interior determines the outlet state, and the scheme converges to the isentropic supersonic solution.

In regimes (b) and (c) the exit flow is subsonic. The characteristic with speed $V-a<0$ then enters the domain from downstream, so one physical condition must be imposed at the outlet: the back pressure. The code does this when `p_p0` on line 10 is set to the required ratio, between $0.9524$ and $1$ for (b) or between $0.4664$ and $0.9524$ for (c). Line 11 converts it to `pe` $=p^\dagger=p_b/(\gamma p_0)$, which is now positive. Line 81 still extrapolates density and momentum, and lines 82–83 overwrite the energy,

`U[Nx-1][2] = pe*A[Nx-1]/(gamma-1.0) + 0.5*U[Nx-1][1]**2/U[Nx-1][0]`,

so that the outlet static pressure equals the imposed $p_b$. Line 55 copies the outlet values into the predictor array, `Up[Nx-1] = U[Nx-1]`, because the forward-difference predictor loop on lines 51–53 stops at $Nx-2$ and would otherwise leave the outlet predictor values undefined.

---

## Paper slips and ambiguities

- Q1(iv), force axes. Figure Q.1(b) defines $F_x$ along the chord and $F_y$ normal to it (body axes), not drag and lift. Both pairs are given above.
- Q1(iii), Mach-reflection limit. An earlier draft said the pattern changes to Mach reflection "closer to $p_{\text{atm}}/p_e\sim2.6$–$3$". The detachment condition $\Delta=\theta_{\max}(M_2)$ gives $p_{\text{atm}}\approx110$ kPa, $p_{\text{atm}}/p_{\text{exit}}\approx2.68$.
- Q5(ii)(a). An earlier draft said supersonic outflow needs $p_b/p_0\le0.0748$. The exit-plane flow is supersonic, with no shock in the nozzle, for any $p_b/p_0<0.4664$; $0.0748$ is the perfectly expanded case.
- Q3, sign convention. An earlier draft tabulated Anderson's $K^+=\theta-\nu$ under the heading $R^+$, which made the $R^+$ column negative. The table above uses the course's $R^+=\nu-\theta$.
- Q5, printed output. The code prints an exit Mach number of $2.3431$ against the exact isentropic $2.3427$, and $p/p_0=0.0748$; the small difference is discretisation error on the 121-point grid.
