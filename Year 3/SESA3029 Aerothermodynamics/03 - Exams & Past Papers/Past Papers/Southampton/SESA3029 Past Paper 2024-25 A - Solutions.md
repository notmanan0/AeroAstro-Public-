---
title: "SESA3029 Past Paper 2024-25 A - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, oblique-shock, shock-expansion, ackeret, prandtl-glauert, moc, heat-exchanger, finite-difference]
paper: "2024-25 Paper A (Closed Book)"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-202425-01-SESA3029-A.pdf"]
---

# SESA3029 Past Paper 2024-25 A - Solutions

> [!abstract] Paper info
> 2024-25 Paper A is a closed-book paper of 120 minutes with five questions worth 34, 16, 20, 20 and 10 marks. The IFT, NST and OSC are provided, nearest table values are acceptable, and a formula sheet is attached on pp. 8–9. The front-page constants are $R=287\ \text{J/(kg K)}$, $c_p=1005\ \text{J/(kg K)}$, $\gamma=1.4$, $\text{Pr}=0.7$, $\rho=1.225\ \text{kg/m}^3$ and $\mu=1.79\times10^{-5}\ \text{N s/m}^2$. Every number below was recomputed in Python with $\gamma=1.4$; table rows are quoted to the IFT and NST's four decimal places, with the exact value from the relation given as a check. Questions 4 and 5 are heat transfer (Weeks 9–12, not yet lectured).

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 34 | Nozzle, shock reflection, shock-expansion, pitching moment, Ackeret | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]], [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 2 | 16 | Prandtl–Glauert derivation and critical Mach number | [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]] |
| 3 | 20 | Method of Characteristics for an under-expanded nozzle jet | [[SESA3029 W05a - Method of Characteristics|W05a]] |
| 4 | 20 | Shell-and-tube heat exchanger ($\varepsilon$–NTU, Dittus–Boelter) | Heat transfer (Weeks 9–12, not yet lectured) |
| 5 | 10 | 2D steady conduction, finite-difference stencil at an internal corner | Heat transfer (Weeks 9–12, not yet lectured) |

---

## Q1. Nozzle flow, wall shock reflection and half-diamond aerofoil (34 marks)

> A converging–diverging nozzle generates a $M_1=2.4$, $p_1=55\ \text{kPa}$, $T_1=170\ \text{K}$ test-section air flow. A symmetric half-diamond aerofoil of chord $l=0.2\ \text{m}$ and nose angle $\phi=12^\circ$ is installed as a shock generator. Its upper surface A is the chord, its lower forward surface B is parallel to the flow, and its lower aft surface C meets A at the trailing edge at angle $\phi$. The walls are far enough away to avoid further interactions.
> (i) Find reservoir $p_0, T_0$ and throat $p_t, T_t$. [4]
> (ii) Sketch the upper-wall reflection and find $p_3, M_3$ after reflection. [10]
> (iii) Find $p$ and $M$ on surfaces A, B, C using shock-expansion theory. [8]
> (iv) Estimate the pitching moment per unit span about the leading edge (thin-aerofoil approximation). [4]
> (v) Repeat (iii) with Ackeret linearised theory and comment on applicability. [8]

![[at_pp_202425_q1_wave_reflection.png|900]]

The geometry fixes every wave. Surface B is horizontal and surface A rises from the leading edge at $\phi=12^\circ$ above it, so A is the chord line at $12^\circ$ to the flow. Because the section is half of a symmetric diamond about A, B and C each make $12^\circ$ with A, and C therefore rises at $2\phi=24^\circ$ to the horizontal. The flow above the aerofoil meets A as a $12^\circ$ compression corner and passes through an oblique shock. The flow below runs along B undisturbed and then expands through $24^\circ$ at the B–C corner. The leading-edge shock on A is the shock that travels up to the tunnel wall in part (ii).

### (i) Reservoir and throat conditions [4 marks]

The nozzle flow is steady, adiabatic and isentropic for a calorically perfect gas with $\gamma=1.4$, so the reservoir is the stagnation state of the test-section flow. The temperature factor at $M_1=2.4$ is

$$
1+\frac{\gamma-1}{2}M_1^2=1+0.2\times2.4^2=1+0.2\times5.76=2.152.
$$

The stagnation pressure ratio raises this to the power $\gamma/(\gamma-1)=3.5$,

$$
\frac{p_0}{p_1}=2.152^{3.5}=14.620,
$$

$$
p_0=14.620\times55\ \text{kPa}=\boxed{804.1\ \text{kPa}}.
$$

The stagnation temperature uses the factor itself,

$$
T_0=2.152\times170\ \text{K}=\boxed{365.8\ \text{K}}.
$$

The IFT row $M=2.40$ gives the same results to table accuracy: $p/p_0=0.0684$ gives $p_0=55/0.0684=804.1$ kPa, and $T/T_0=0.4647$ gives $T_0=170/0.4647=365.8$ K.

At the throat $M_t=1$, where the IFT row $M=1.00$ gives $p^*/p_0=0.5283$ and $T^*/T_0=0.8333$ (the exact values are $1.2^{-3.5}=0.52828$ and $1/1.2$),

$$
p_t=0.52828\times804.1\ \text{kPa}=\boxed{424.8\ \text{kPa}},
$$

$$
T_t=\frac{365.84\ \text{K}}{1.2}=\boxed{304.9\ \text{K}}.
$$

### (ii) Oblique shock reflection at the upper test-section wall [10 marks]

Surface A turns the upper flow up into itself by $\theta_1=\phi=12^\circ$, so an attached weak oblique shock leaves the leading edge (region 1 to region 2). The shock meets the horizontal upper wall, where the flow in region 2 is still inclined at $12^\circ$ towards the wall. The wall forces the flow back to horizontal, so a reflected oblique shock turns region 2 down by $\theta_2=12^\circ$ into region 3 ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#1. Regular shock reflection from a wall|W03 §1]]). Both shocks are solved with the θ–β–M relation ([[Theta-Beta-Mach Relation]])

$$
\tan\theta=2\cot\beta\,\frac{M^2\sin^2\beta-1}{M^2(\gamma+\cos2\beta)+2}.
$$

#### Incident shock at M = 2.4 and θ = 12°

Given $M$ and $\theta$, the relation has to be solved for $\beta$ by trial. Evaluating $\theta(\beta)$ at two trial shock angles brackets the target ($M_1^2=5.76$).

| $\beta$ | $M_1^2\sin^2\beta-1$ | $M_1^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ |
|---:|---:|---:|---:|---:|---:|
| $35^\circ$ | 0.89498 | 12.03404 | 2.85630 | 0.21243 | $11.9928^\circ$ |
| $36^\circ$ | 0.99003 | 11.84394 | 2.75276 | 0.23010 | $12.9584^\circ$ |

Linear interpolation to $\theta=12^\circ$ gives

$$
\beta_1=35^\circ+1^\circ\times\frac{12-11.9928}{12.9584-11.9928}=35^\circ+1^\circ\times\frac{0.0072}{0.9656}=35.0075^\circ.
$$

At $\beta=35.0075^\circ$ the relation returns $\theta=12.0001^\circ$, and one more secant step gives $\beta_1=35.0073^\circ$, which is the exact weak-shock root. The normal Mach number is

$$
M_{n1}=M_1\sin\beta_1=2.4\sin35.007^\circ=2.4\times0.57368=1.3768.
$$

$M_{n1}=1.3768$ lies between the NST rows $1.36$ and $1.38$.

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ |
|---:|---:|---:|
| 1.36 | 0.7572 | 1.9912 |
| 1.38 | 0.7483 | 2.0551 |

The interpolation fraction is $(1.3768-1.36)/0.02=0.842$, so

$$
M_{n2}=0.7572+0.842\times(0.7483-0.7572)=0.7572-0.0075=0.7497,
$$

$$
\frac{p_2}{p_1}=1.9912+0.842\times(2.0551-1.9912)=1.9912+0.0538=2.0450.
$$

The normal-shock formulas give the same values to four decimal places: $M_{n2}=\sqrt{(1+0.2\times1.3768^2)/(1.4\times1.3768^2-0.2)}=0.7497$ and $p_2/p_1=1+\tfrac{2.8}{2.4}(1.3768^2-1)=2.0450$. The downstream flow leaves the shock at $\beta_1-\theta_1=23.007^\circ$ to the shock, so

$$
M_2=\frac{M_{n2}}{\sin(\beta_1-\theta_1)}=\frac{0.7497}{\sin23.007^\circ}=\frac{0.7497}{0.39085}=1.918,
$$

$$
p_2=2.0450\times55\ \text{kPa}=112.47\ \text{kPa}.
$$

#### Reflected shock at M = 1.918 and θ = 12°

The same trial procedure at $M_2=1.9181$ ($M_2^2=3.6791$) gives

| $\beta$ | $M_2^2\sin^2\beta-1$ | $M_2^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ |
|---:|---:|---:|---:|---:|---:|
| $43^\circ$ | 0.71123 | 7.40739 | 2.14474 | 0.20593 | $11.6363^\circ$ |
| $44^\circ$ | 0.77535 | 7.27915 | 2.07106 | 0.22060 | $12.4404^\circ$ |

$$
\beta_2=43^\circ+1^\circ\times\frac{12-11.6363}{12.4404-11.6363}=43^\circ+1^\circ\times\frac{0.3637}{0.8041}=43.452^\circ.
$$

At $43.452^\circ$ the relation returns $\theta=12.0037^\circ$, and a secant step through the $44^\circ$ point gives $\beta_2=43.448^\circ$, the exact root. This angle is measured from the region-2 flow direction, which is itself inclined at $12^\circ$ towards the wall, so the reflected shock sits at $\beta_2-\theta_2=31.448^\circ$ to the wall. The normal Mach number is

$$
M_{n,r}=M_2\sin\beta_2=1.9181\sin43.448^\circ=1.9181\times0.68770=1.3191.
$$

The NST rows that bracket it are $1.30$ and $1.32$.

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ |
|---:|---:|---:|
| 1.30 | 0.7860 | 1.8050 |
| 1.32 | 0.7760 | 1.8661 |

The fraction is $(1.3191-1.30)/0.02=0.953$, so

$$
M_{n3}=0.7860+0.953\times(0.7760-0.7860)=0.7860-0.0095=0.7765,
$$

$$
\frac{p_3}{p_2}=1.8050+0.953\times(1.8661-1.8050)=1.8050+0.0582=1.8632.
$$

The flow in region 3 is parallel to the wall, at $31.448^\circ$ to the reflected shock, so

$$
M_3=\frac{M_{n3}}{\sin(\beta_2-\theta_2)}=\frac{0.7765}{\sin31.448^\circ}=\frac{0.7765}{0.52172}=\boxed{1.488},
$$

$$
p_3=1.8632\times112.47\ \text{kPa}=\boxed{209.6\ \text{kPa}}.
$$

> [!check] Regular reflection is possible
> At $M_2=1.918$ the maximum deflection for an attached shock is $\theta_{\max}=21.5^\circ$ (at $\beta=64.8^\circ$). The required $12^\circ$ is well below it, so the reflection is regular and there is no Mach stem.

### (iii) Surface pressures and Mach numbers by shock-expansion theory [8 marks]

Surface A sits directly behind the leading-edge shock solved in (ii), so

$$
M_A=\boxed{1.918},\qquad p_A=\boxed{112.5\ \text{kPa}}.
$$

Surface B is parallel to the free stream, so no wave forms at the lower leading edge and

$$
M_B=\boxed{2.40},\qquad p_B=\boxed{55.0\ \text{kPa}}.
$$

At the B–C corner the lower surface turns up through $2\phi=24^\circ$, away from the lower flow, so the flow expands isentropically through a Prandtl–Meyer fan ([[Prandtl-Meyer Function]]). From the IFT row $M=2.40$, $\nu_B=36.7465^\circ$, and the turn adds to $\nu$,

$$
\nu_C=\nu_B+2\phi=36.7465^\circ+24^\circ=60.7465^\circ.
$$

The target lies between two IFT rows.

| $M$ | $\nu$ | $p/p_0$ |
|---:|---:|---:|
| 3.64 | $60.6998^\circ$ | 0.0108 |
| 3.66 | $61.0005^\circ$ | 0.0105 |

The fraction is $(60.7465-60.6998)/(61.0005-60.6998)=0.0467/0.3007=0.155$, so

$$
M_C=3.64+0.02\times0.155=\boxed{3.643}.
$$

The fan is isentropic, so the lower flow keeps the reservoir pressure $p_0=804.1$ kPa. Evaluating the isentropic ratio at $M_C=3.6431$,

$$
\frac{p_C}{p_0}=\left(1+0.2\times3.6431^2\right)^{-3.5}=3.65443^{-3.5}=0.010719,
$$

$$
p_C=0.010719\times804.1\ \text{kPa}=\boxed{8.62\ \text{kPa}}.
$$

Interpolating the four-decimal $p/p_0$ column instead gives $0.0108-0.155\times0.0003=0.01075$ and $p_C=8.65$ kPa; the nearest row alone ($M=3.64$) gives $8.68$ kPa.

### (iv) Pitching moment about the leading edge [4 marks]

For a thin aerofoil every surface pressure is taken to act normal to the chord over the surface's projection on the chord, with $x$ measured from the leading edge. Surface A covers $0\le x\le l$ and pushes down; B covers $0\le x\le l/2$ and C covers $l/2\le x\le l$, and both push up. Nose-up is positive, and a downward force behind the leading edge pitches the nose up. Each force acts at the midpoint of its projection, so

$$
M'_{\text{LE}}=p_A\,l\left(\frac{l}{2}\right)-p_B\left(\frac{l}{2}\right)\left(\frac{l}{4}\right)-p_C\left(\frac{l}{2}\right)\left(\frac{3l}{4}\right).
$$

Multiplying out each term,

$$
M'_{\text{LE}}=\frac{p_Al^2}{2}-\frac{p_Bl^2}{8}-\frac{3p_Cl^2}{8}.
$$

Taking out $l^2/8$,

$$
M'_{\text{LE}}=\frac{l^2}{8}\left(4p_A-p_B-3p_C\right).
$$

A uniform pressure gives $4p-p-3p=0$, so the absolute pressures can be used directly. Substituting $l=0.2$ m and the pressures in kPa,

$$
M'_{\text{LE}}=\frac{0.2^2}{8}\left(4\times112.473-55.000-3\times8.619\right)\times10^3\ \text{N m/m}
$$

$$
=0.005\times(449.890-55.000-25.856)\times10^3\ \text{N m/m}
$$

$$
=0.005\times369.034\times10^3\ \text{N m/m}=\boxed{+1845\ \text{N m/m (nose-up)}}.
$$

> [!check] Exact geometry
> Using the true surface lengths, $s=(l/2)/\cos12^\circ=0.10223$ m for B and C, and the true lines of action gives $M'_{\text{LE}}=2249.5-287.4-127.3=1834.7$ N m/m. The thin-aerofoil estimate is 0.57 % higher.

### (v) Ackeret linearised theory and applicability [8 marks]

Ackeret's formula is $C_p=2\theta/\sqrt{M_\infty^2-1}$, with $\theta$ in radians and positive where the surface turns into the local flow ([[Ackeret Theory]]). At $M_\infty=2.4$ the factor and the free-stream dynamic pressure are

$$
\lambda=\sqrt{M_\infty^2-1}=\sqrt{5.76-1}=\sqrt{4.76}=2.1817,
$$

$$
q_\infty=\tfrac12\gamma p_\infty M_\infty^2=0.5\times1.4\times55\times5.76=221.76\ \text{kPa}.
$$

Surface A turns the upper flow into itself by $\phi=12^\circ=0.20944$ rad, so

$$
C_{p,A}=\frac{2\times0.20944}{2.1817}=+0.1920,
$$

$$
p_A=p_\infty+q_\infty C_{p,A}=55.00+221.76\times0.1920=55.00+42.58=\boxed{97.6\ \text{kPa}}.
$$

Surface B is parallel to the stream, so $C_{p,B}=0$ and $p_B=\boxed{55.0\ \text{kPa}}$.

Surface C turns away from the lower flow by $2\phi=0.41888$ rad, so $\theta_C=-0.41888$ rad and

$$
C_{p,C}=\frac{2\times(-0.41888)}{2.1817}=-0.3840,
$$

$$
p_C=55.00+221.76\times(-0.3840)=55.00-85.15=\boxed{-30.2\ \text{kPa}}.
$$

A negative absolute pressure is impossible, so linear theory has failed on C.

Linear theory gives Mach numbers from the same velocity perturbation. Writing $M=V/a$ and taking logarithmic differentials,

$$
\frac{\mathrm{d}M}{M}=\frac{\mathrm{d}V}{V}-\frac{\mathrm{d}a}{a}.
$$

The adiabatic energy equation $a^2/(\gamma-1)+V^2/2=\text{const}$ differentiates to

$$
\frac{2a\,\mathrm{d}a}{\gamma-1}+V\,\mathrm{d}V=0.
$$

Dividing by $2a^2/(\gamma-1)$,

$$
\frac{\mathrm{d}a}{a}=-\frac{\gamma-1}{2}M^2\frac{\mathrm{d}V}{V}.
$$

Substituting back,

$$
\frac{\mathrm{d}M}{M}=\left(1+\frac{\gamma-1}{2}M^2\right)\frac{\mathrm{d}V}{V}.
$$

The linearised pressure coefficient gives $\mathrm{d}V/V=u'/U_\infty=-C_p/2$, and $1+0.2\times2.4^2=2.152$, so

$$
M_A\approx2.4-2.4\times2.152\times\frac{0.1920}{2}=2.4-0.496=\boxed{1.90},
$$

$$
M_B=\boxed{2.40},
$$

$$
M_C\approx2.4+2.4\times2.152\times\frac{0.3840}{2}=2.4+0.992=\boxed{3.39}.
$$

Converting the Ackeret pressure on A to a Mach number through the isentropic relation instead gives $p_A/p_0=97.58/804.1=0.1213$ and $M_A=2.03$; the same route is impossible on C because $p_C<0$.

| Surface | Shock-expansion $p$ | Ackeret $p$ | Error in $p$ | Shock-expansion $M$ | Ackeret $M$ (linear) |
|---|---:|---:|---:|---:|---:|
| A ($\theta=+12^\circ$) | 112.5 kPa | 97.6 kPa | $-13\%$ | 1.92 | 1.90 |
| B ($\theta=0^\circ$) | 55.0 kPa | 55.0 kPa | 0 | 2.40 | 2.40 |
| C ($\theta=-24^\circ$) | 8.62 kPa | $-30.2$ kPa | impossible | 3.64 | 3.39 |

Ackeret theory assumes the disturbance is small, which means the pressure change must be small compared with the free-stream pressure. That ratio is

$$
\frac{|\Delta p|}{p_\infty}=\frac{q_\infty|C_p|}{p_\infty}=\frac{\gamma M_\infty^2|\theta|}{\sqrt{M_\infty^2-1}}.
$$

On A it is $1.4\times5.76\times0.20944/2.1817=0.77$, which is not small. Linear theory then predicts a pressure rise of 42.6 kPa against the shock's 57.5 kPa, 26 % too small, and the surface pressure is 13 % low. On C the ratio is $1.55$: the predicted drop of 85.2 kPa is larger than the 55 kPa available, which is why the pressure goes negative. The theory is usable for the trend on A but not for C, where the $24^\circ$ turn is far outside the small-angle range.

---

## Q2. Prandtl-Glauert derivation and critical Mach number (16 marks)

> (i) Starting from $\left(1-M_\infty^2\right)\dfrac{\partial^2\phi}{\partial x^2}+\dfrac{\partial^2\phi}{\partial y^2}=0$, derive $C_p=\dfrac{C_{p,0}}{\sqrt{1-M_\infty^2}}$. [8]
> (ii) Estimate $M_{\text{crit}}$ for an aerofoil whose incompressible minimum pressure coefficient is $C_{p,\min}=-1.2$. [8]

### (i) Derivation of the Prandtl–Glauert rule [8 marks]

Here $\phi$ is the perturbation potential for subsonic flow ($M_\infty<1$) past a thin body $y_b(x)$ with small slope. With $\beta=\sqrt{1-M_\infty^2}$ the equation reads

$$
\beta^2\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0.
$$

Introduce stretched coordinates and a scaled potential, with $A$ a constant still to be found ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]]),

$$
\bar x=x,\qquad\bar y=\beta y,\qquad\bar\phi(\bar x,\bar y)=A\,\phi(x,y).
$$

Since $\partial\bar x/\partial x=1$, the $x$-derivatives are

$$
\frac{\partial\phi}{\partial x}=\frac{1}{A}\frac{\partial\bar\phi}{\partial\bar x},
$$

$$
\frac{\partial^2\phi}{\partial x^2}=\frac{1}{A}\frac{\partial^2\bar\phi}{\partial\bar x^2}.
$$

Since $\partial\bar y/\partial y=\beta$, each $y$-derivative brings a factor $\beta$,

$$
\frac{\partial\phi}{\partial y}=\frac{\beta}{A}\frac{\partial\bar\phi}{\partial\bar y},
$$

$$
\frac{\partial^2\phi}{\partial y^2}=\frac{\beta^2}{A}\frac{\partial^2\bar\phi}{\partial\bar y^2}.
$$

Substituting both second derivatives into the equation,

$$
\frac{\beta^2}{A}\frac{\partial^2\bar\phi}{\partial\bar x^2}+\frac{\beta^2}{A}\frac{\partial^2\bar\phi}{\partial\bar y^2}=0.
$$

Dividing by $\beta^2/A$, which is non-zero for $M_\infty<1$,

$$
\frac{\partial^2\bar\phi}{\partial\bar x^2}+\frac{\partial^2\bar\phi}{\partial\bar y^2}=0,
$$

so $\bar\phi$ satisfies Laplace's equation and is an incompressible flow in the $(\bar x,\bar y)$ plane.

The constant $A$ follows from requiring that this incompressible flow passes the same aerofoil shape, $\bar y_b(\bar x)=y_b(x)$. The linearised tangency conditions applied on the axis are

$$
\left.\frac{\partial\phi}{\partial y}\right|_{y=0}=U_\infty\frac{\mathrm{d}y_b}{\mathrm{d}x},\qquad\left.\frac{\partial\bar\phi}{\partial\bar y}\right|_{\bar y=0}=U_\infty\frac{\mathrm{d}\bar y_b}{\mathrm{d}\bar x}=U_\infty\frac{\mathrm{d}y_b}{\mathrm{d}x}.
$$

Writing the compressible condition with the $y$-derivative from above,

$$
\frac{\beta}{A}\left.\frac{\partial\bar\phi}{\partial\bar y}\right|_{\bar y=0}=U_\infty\frac{\mathrm{d}y_b}{\mathrm{d}x}.
$$

Replacing $\partial\bar\phi/\partial\bar y$ by the incompressible condition,

$$
\frac{\beta}{A}U_\infty\frac{\mathrm{d}y_b}{\mathrm{d}x}=U_\infty\frac{\mathrm{d}y_b}{\mathrm{d}x},
$$

$$
A=\beta.
$$

On the surface the compressible streamwise perturbation velocity is then

$$
u'=\frac{\partial\phi}{\partial x}=\frac{1}{\beta}\frac{\partial\bar\phi}{\partial\bar x}=\frac{\bar u'}{\beta}.
$$

The linearised pressure coefficient is $C_p=-2u'/U_\infty$, so

$$
C_p=-\frac{2u'}{U_\infty}=-\frac{2\bar u'}{\beta U_\infty}=\frac{1}{\beta}\left(-\frac{2\bar u'}{U_\infty}\right)=\frac{C_{p,0}}{\beta},
$$

$$
\boxed{C_p=\frac{C_{p,0}}{\sqrt{1-M_\infty^2}}}.
$$

### (ii) Critical Mach number [8 marks]

![[at_pp_202425_q2_mcrit.png|900]]

At $M_{\text{crit}}$ the flow first reaches $M=1$ at the minimum-pressure point ([[Critical Mach Number]]). The pressure coefficient there is

$$
C_p=\frac{p-p_\infty}{\tfrac12\gamma p_\infty M_\infty^2}=\frac{2}{\gamma M_\infty^2}\left(\frac{p}{p_\infty}-1\right).
$$

The flow is isentropic from the free stream to the sonic point, so with both pressures referred to the same $p_0$,

$$
\frac{p^*}{p_\infty}=\frac{p^*/p_0}{p_\infty/p_0}=\left(\frac{1+\frac{\gamma-1}{2}M_\infty^2}{\frac{\gamma+1}{2}}\right)^{\gamma/(\gamma-1)}=\left(\frac{1+0.2M_\infty^2}{1.2}\right)^{3.5}.
$$

Substituting into $C_p$,

$$
C_{p,\text{crit}}=\frac{2}{1.4M_\infty^2}\left[\left(\frac{1+0.2M_\infty^2}{1.2}\right)^{3.5}-1\right].
$$

$M_{\text{crit}}$ is where the Prandtl–Glauert peak $C_{p,\text{PG}}=-1.2/\sqrt{1-M_\infty^2}$ falls to this value. At the trial $M_\infty=0.57$ the two sides are

$$
C_{p,\text{PG}}=\frac{-1.2}{\sqrt{1-0.57^2}}=\frac{-1.2}{0.82164}=-1.4605,
$$

$$
C_{p,\text{crit}}=\frac{2}{1.4\times0.3249}\left[\left(\frac{1.06498}{1.2}\right)^{3.5}-1\right]=4.39696\times(0.65851-1)=-1.5015.
$$

The other trials are evaluated in the same way.

| $M_\infty$ | $C_{p,\text{PG}}$ | $C_{p,\text{crit}}$ | $C_{p,\text{PG}}-C_{p,\text{crit}}$ |
|---:|---:|---:|---:|
| 0.50 | $-1.3856$ | $-2.1334$ | $+0.7478$ |
| 0.55 | $-1.4368$ | $-1.6583$ | $+0.2214$ |
| 0.57 | $-1.4605$ | $-1.5015$ | $+0.0410$ |
| 0.58 | $-1.4731$ | $-1.4290$ | $-0.0441$ |

The difference changes sign between 0.57 and 0.58. Interpolating linearly,

$$
M_{\text{crit}}=0.57+0.01\times\frac{0.0410}{0.0410+0.0441}=0.57+0.01\times0.482=0.5748,
$$

$$
M_{\text{crit}}=\boxed{0.575}.
$$

> [!check] Both sides at the root
> At $M_\infty=0.5748$, $C_{p,\text{PG}}=-1.2/\sqrt{1-0.5748^2}=-1.4664$ and $C_{p,\text{crit}}=\frac{2}{1.4\times0.5748^2}\left[(1.06607/1.2)^{3.5}-1\right]=-1.4664$. A root-finder gives the same $M_{\text{crit}}=0.5748$.

---

## Q3. Method of Characteristics for an under-expanded nozzle exit (20 marks)

> Supersonic flow leaves a nozzle at $M_a$, $p_a$ and expands to the back pressure $p_b$ (Mach number $M_b$) through a centred Prandtl–Meyer fan whose first and last characteristic lines are $a$ and $b$. Points 1 and 3 lie on the centreline; point 2 is where the characteristic reflected from point 1 crosses line $b$. The flow is homentropic.
> (i) Complete the table of $R^+$, $R^-$, $\theta$ and $\nu$ for lines $a$, $b$ and points 1–3 in terms of $\nu_a$ and $\nu_b$ (printed entries: $R^+=0$ on lines $a$ and $b$, $\theta_a=0$, $\nu_a$, $\nu_b$, and $\nu_3=2\nu_b-\nu_a$). [14]
> (ii) Given $M_a=1.5$, $p_a=200\ \text{kPa}$, $p_b=99.85\ \text{kPa}$, find $M_3$ and $p_3$. [6]

![[at_pp_202425_q3_moc_expansion.png|900]]

### (i) Method of Characteristics table [14 marks]

The module's invariants ([[SESA3029 W05a - Method of Characteristics|W05a]]) are

$$
R^+=\nu-\theta\ \text{constant along }C^+\ (\text{slope }\theta+\mu),\qquad R^-=\nu+\theta\ \text{constant along }C^-\ (\text{slope }\theta-\mu).
$$

The fan is centred on the nozzle lip and its rays run down towards the centreline, so lines $a$ and $b$ are $C^-$ characteristics. Every $C^+$ characteristic that crosses the fan comes from the uniform exit flow, where $\theta=0$ and $\nu=\nu_a$, so the whole fan is a simple wave with

$$
R^+=\nu_a-0=\nu_a.
$$

On line $a$ the flow is still the exit flow, so

$$
R^+_a=\nu_a,\qquad R^-_a=\nu_a+0=\nu_a.
$$

On line $b$, $\nu=\nu_b$ and $R^+=\nu_a$ still holds, so the flow angle is

$$
\theta_b=\nu_b-R^+=\nu_b-\nu_a.
$$

The $C^-$ invariant on line $b$ is then

$$
R^-_b=\nu_b+\theta_b=\nu_b+(\nu_b-\nu_a)=2\nu_b-\nu_a.
$$

Point 1 is where line $a$ meets the centreline. It carries $R^-_1=R^-_a=\nu_a$, and symmetry gives $\theta_1=0$, so

$$
\nu_1=R^-_1-\theta_1=\nu_a,\qquad R^+_1=\nu_1-\theta_1=\nu_a.
$$

Point 2 lies on the $C^+$ from point 1 and on line $b$, so $R^+_2=\nu_a$ and $R^-_2=2\nu_b-\nu_a$. Adding and subtracting the two invariants,

$$
\nu_2=\frac{R^-_2+R^+_2}{2}=\frac{(2\nu_b-\nu_a)+\nu_a}{2}=\nu_b,
$$

$$
\theta_2=\frac{R^-_2-R^+_2}{2}=\frac{(2\nu_b-\nu_a)-\nu_a}{2}=\nu_b-\nu_a.
$$

Point 3 is where line $b$, continued through point 2, meets the centreline. It carries $R^-_3=2\nu_b-\nu_a$ and has $\theta_3=0$, so

$$
\nu_3=R^-_3-\theta_3=2\nu_b-\nu_a,\qquad R^+_3=\nu_3-\theta_3=2\nu_b-\nu_a,
$$

which agrees with the printed $\nu_3$.

The printed table puts $R^+=0$ on lines $a$ and $b$, which does not match $R^+=\nu-\theta=\nu_a$. It does match invariants measured from the exit state, $R^\pm_{\text{sh}}=(\nu-\nu_a)\mp\theta$, and both versions give the same $\theta$ and $\nu$ everywhere (see [[#Paper slips and ambiguities]]). Both are tabulated.

| Point | $R^+=\nu-\theta$ | $R^+_{\text{sh}}$ | $R^-=\nu+\theta$ | $R^-_{\text{sh}}$ | $\theta$ | $\nu$ |
|---|---|---|---|---|---|---|
| a (line) | $\nu_a$ | $0$ | $\nu_a$ | $0$ | $0$ | $\nu_a$ |
| b (line) | $\nu_a$ | $0$ | $2\nu_b-\nu_a$ | $2(\nu_b-\nu_a)$ | $\nu_b-\nu_a$ | $\nu_b$ |
| 1 | $\nu_a$ | $0$ | $\nu_a$ | $0$ | $0$ | $\nu_a$ |
| 2 | $\nu_a$ | $0$ | $2\nu_b-\nu_a$ | $2(\nu_b-\nu_a)$ | $\nu_b-\nu_a$ | $\nu_b$ |
| 3 | $2\nu_b-\nu_a$ | $2(\nu_b-\nu_a)$ | $2\nu_b-\nu_a$ | $2(\nu_b-\nu_a)$ | $0$ | $2\nu_b-\nu_a$ |

### (ii) Numerical values at Point 3 [6 marks]

The IFT row $M=1.50$ gives $p/p_0=0.2724$ and $\nu_a=11.9052^\circ$. The stagnation pressure of the jet is

$$
p_0=\frac{p_a}{p_a/p_0}=\frac{200\ \text{kPa}}{0.2724}=734.2\ \text{kPa}.
$$

The flow is homentropic, so $p_0$ is also the stagnation pressure at the jet boundary, where $p=p_b$. There

$$
\frac{p_b}{p_0}=\frac{99.85}{734.2}=0.1360.
$$

This is the IFT entry at $M=1.96$ (the neighbouring rows are $0.1403$ at $1.94$ and $0.1318$ at $1.98$), so $M_b=1.96$ and $\nu_b=25.2711^\circ$. From part (i),

$$
\nu_3=2\nu_b-\nu_a=2\times25.2711^\circ-11.9052^\circ=50.5422^\circ-11.9052^\circ=38.6370^\circ.
$$

The target lies between two IFT rows.

| $M$ | $\nu$ | $p/p_0$ |
|---:|---:|---:|
| 2.46 | $38.1831^\circ$ | 0.0623 |
| 2.48 | $38.6551^\circ$ | 0.0604 |

The fraction is $(38.6370-38.1831)/(38.6551-38.1831)=0.4539/0.4720=0.962$, so

$$
M_3=2.46+0.02\times0.962=2.4792,
$$

$$
\frac{p_3}{p_0}=0.0623+0.962\times(0.0604-0.0623)=0.0623-0.00183=0.06047,
$$

$$
p_3=0.06047\times734.2\ \text{kPa}=44.40\ \text{kPa}.
$$

$$
M_3=\boxed{2.48},\qquad p_3=\boxed{44.4\ \text{kPa}}.
$$

The exact relations give $M_3=2.4792$ and $p_3=44.38$ kPa, and the nearest row ($M=2.48$) gives $0.0604\times734.2=44.35$ kPa.

The table below collects the full state at each point.

| Point | $R^+$ | $R^-$ | $\theta$ | $\nu$ | $M$ | $\mu$ | $\theta+\mu$ | $\theta-\mu$ |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| a, 1 | $11.905^\circ$ | $11.905^\circ$ | $0$ | $11.905^\circ$ | 1.500 | $41.810^\circ$ | $41.810^\circ$ | $-41.810^\circ$ |
| b, 2 | $11.905^\circ$ | $38.637^\circ$ | $13.366^\circ$ | $25.271^\circ$ | 1.960 | $30.677^\circ$ | $44.044^\circ$ | $-17.311^\circ$ |
| 3 | $38.637^\circ$ | $38.637^\circ$ | $0$ | $38.637^\circ$ | 2.479 | $23.788^\circ$ | $23.788^\circ$ | $-23.788^\circ$ |

Here $\mu=\sin^{-1}(1/M)$; for example $\mu_2=\sin^{-1}(1/1.96)=30.677^\circ$. The paper gives no lip height, so the coordinates of points 1–3 cannot be found; with a lip height $h$ they would follow from these slopes and the formula-sheet intersection equations.

> [!check] Turning angles
> The fan turns the jet outwards by $\theta_b=25.271^\circ-11.905^\circ=13.366^\circ$. Between point 2 and the centreline at point 3 the flow is turned back by $13.366^\circ$ to $\theta_3=0$, and the expansion adds another $13.366^\circ$ to $\nu$: $25.271^\circ+13.366^\circ=38.637^\circ=\nu_3$.

---

## Q4. Shell-and-tube heat exchanger (20 marks)

> A shell-and-tube heat exchanger consists of $N=135$ thin-walled tubes in a double-pass arrangement, each of diameter $D=12.5\ \text{mm}$, with total heat-transfer area $A=47.5\ \text{m}^2$ and overall coefficient $U=200\ \text{W/(m}^2\text{ K)}$. Water enters the tubes at $T_{c,\text{in}}=15^\circ\text{C}$ and $\dot m_c=6.5\ \text{kg/s}$ ($c_{p,c}=4179\ \text{J/(kg K)}$, $\mu=8.55\times10^{-4}\ \text{N s/m}^2$, $k=0.613\ \text{W/(m K)}$, $\text{Pr}=5.83$). Exhaust gas with the properties of air ($c_{p,h}=1005\ \text{J/(kg K)}$) enters the shell at $T_{h,\text{in}}=200^\circ\text{C}$ and $\dot m_h=5\ \text{kg/s}$.
> (i) Calculate the effectiveness using $\epsilon=\dfrac{1-\exp[-\text{NTU}(1-C_r)]}{1-C_r\exp[-\text{NTU}(1-C_r)]}$. [6]
> (ii) Find the gas and water outlet temperatures. [6]
> (iii) Assuming fully developed flow, find the tube Reynolds number $Re_D$ and the tube-side convective coefficient $h_i$. [8]

This is heat transfer (Weeks 9–12, not yet lectured); check the notation against those lectures when they are written up.

### (i) Heat exchanger effectiveness [6 marks]

The heat capacity rates of the cold water and the hot gas are

$$
C_c=\dot m_cc_{p,c}=6.5\times4179=27\,163.5\ \text{W/K},
$$

$$
C_h=\dot m_hc_{p,h}=5.0\times1005=5025.0\ \text{W/K}.
$$

The gas has the smaller rate, so $C_{\min}=C_h$ and $C_{\max}=C_c$. The capacity ratio and the number of transfer units are

$$
C_r=\frac{C_{\min}}{C_{\max}}=\frac{5025.0}{27\,163.5}=0.18499,
$$

$$
\text{NTU}=\frac{UA}{C_{\min}}=\frac{200\times47.5}{5025.0}=\frac{9500}{5025.0}=1.89055.
$$

The exponent in the given relation is

$$
\text{NTU}(1-C_r)=1.89055\times(1-0.18499)=1.89055\times0.81501=1.54081,
$$

$$
\exp(-1.54081)=0.21421.
$$

Substituting,

$$
\epsilon=\frac{1-0.21421}{1-0.18499\times0.21421}=\frac{0.78579}{1-0.03963}=\frac{0.78579}{0.96037}=\boxed{0.818}.
$$

### (ii) Gas and water outlet temperatures [6 marks]

The largest possible heat transfer would cool the gas all the way to the water inlet temperature,

$$
\dot Q_{\max}=C_{\min}(T_{h,\text{in}}-T_{c,\text{in}})=5025.0\times(200-15)=929\,625\ \text{W}.
$$

The actual rate is

$$
\dot Q=\epsilon\dot Q_{\max}=0.81822\times929\,625\ \text{W}=760\,634\ \text{W}=760.6\ \text{kW}.
$$

An energy balance on each stream gives the outlet temperatures,

$$
T_{h,\text{out}}=T_{h,\text{in}}-\frac{\dot Q}{C_h}=200-\frac{760\,634}{5025.0}=200-151.37=\boxed{48.6^\circ\text{C}},
$$

$$
T_{c,\text{out}}=T_{c,\text{in}}+\frac{\dot Q}{C_c}=15+\frac{760\,634}{27\,163.5}=15+28.00=\boxed{43.0^\circ\text{C}}.
$$

### (iii) Tube-side Reynolds number and convective heat transfer coefficient [8 marks]

Each of the 135 tubes runs through both passes, so each carries an equal share of the water,

$$
\dot m_{\text{tube}}=\frac{\dot m_c}{N}=\frac{6.5}{135}=0.048148\ \text{kg/s}.
$$

With $\dot m=\rho V\pi D^2/4$, the Reynolds number $\rho VD/\mu$ becomes $4\dot m/(\pi D\mu)$,

$$
Re_D=\frac{4\dot m_{\text{tube}}}{\pi D\mu}=\frac{4\times0.048148}{\pi\times0.0125\times8.55\times10^{-4}}=\frac{0.192593}{3.35758\times10^{-5}}=\boxed{5736}.
$$

$Re_D$ is above the laminar limit of about 2300, so the formula-sheet turbulent pipe correlation is the one to use. Dittus–Boelter is normally quoted for $Re_D\gtrsim10^4$, so at 5736 it is an estimate. Each tube is $47.5/(135\pi\times0.0125)=8.96$ m long, over 700 diameters, which supports the fully developed assumption. The water is being heated, so $n=0.4$ and

$$
Nu_D=0.023\,Re_D^{4/5}\,\text{Pr}^{0.4}=0.023\times5736.1^{0.8}\times5.83^{0.4}=0.023\times1016.0\times2.0243=47.30.
$$

The convective coefficient is

$$
h_i=\frac{Nu_D\,k}{D}=\frac{47.30\times0.613}{0.0125}=\boxed{2320\ \text{W/(m}^2\text{ K)}}.
$$

---

## Q5. Finite-difference stencil at an internal corner with boundary heat flux (10 marks)

> The steady 2D heat diffusion equation $\nabla^2T=0$ is solved with finite differences at an internal corner node $P$ on a uniform grid ($\Delta x=\Delta y=0.04\ \text{m}$, $k=0.05\ \text{W/(m K)}$). The solid fills three quadrants around $P$; the neighbours are $T_N=240^\circ\text{C}$ and $T_W=250^\circ\text{C}$ inside the solid, and $T_E=360^\circ\text{C}$ and $T_S=380^\circ\text{C}$ on the two boundary edges that meet at $P$. A heat flux $\dot q=50\ \text{W/m}^2$ enters the solid through both boundary edges (Figure Q5). Derive the stencil equation at $P$ and evaluate $T_P$. [10]

This is heat transfer (Weeks 9–12, not yet lectured); check the notation against those lectures when they are written up.

![[at_pp_202425_q5_internal_corner.png|750]]

The control volume around $P$ extends half a cell in every direction that stays inside the solid, which makes it an L-shaped three-quarter cell, of unit depth. Heat flowing into it is counted positive, and the conduction rate across each face is $k\times(\text{face length})\times(\text{temperature difference})/(\text{node spacing})$. The faces are as follows.

The north face, at $y=+\Delta y/2$, is a full cell width $\Delta x$ long,

$$
Q_N=k\,\Delta x\,\frac{T_N-T_P}{\Delta y}.
$$

The west face, at $x=-\Delta x/2$, is a full cell height $\Delta y$ long,

$$
Q_W=k\,\Delta y\,\frac{T_W-T_P}{\Delta x}.
$$

The east face, at $x=+\Delta x/2$, only reaches from the horizontal boundary up to $y=\Delta y/2$, so its length is $\Delta y/2$,

$$
Q_E=k\,\frac{\Delta y}{2}\,\frac{T_E-T_P}{\Delta x}.
$$

The south face, at $y=-\Delta y/2$, only reaches from $x=-\Delta x/2$ to the vertical boundary, so its length is $\Delta x/2$,

$$
Q_S=k\,\frac{\Delta x}{2}\,\frac{T_S-T_P}{\Delta y}.
$$

The two boundary pieces of the control volume are $\Delta x/2$ of the horizontal edge and $\Delta y/2$ of the vertical edge, and the heat flux enters through both,

$$
Q_{\dot q}=\dot q\left(\frac{\Delta x}{2}+\frac{\Delta y}{2}\right).
$$

In steady state with no generation the inflows sum to zero,

$$
Q_N+Q_W+Q_E+Q_S+Q_{\dot q}=0.
$$

With $\Delta x=\Delta y$ the ratios $\Delta x/\Delta y$ cancel and the flux term becomes $\dot q\,\Delta x$,

$$
k(T_N-T_P)+k(T_W-T_P)+\frac{k}{2}(T_E-T_P)+\frac{k}{2}(T_S-T_P)+\dot q\,\Delta x=0.
$$

Multiplying by $2/k$,

$$
2(T_N-T_P)+2(T_W-T_P)+(T_E-T_P)+(T_S-T_P)+\frac{2\dot q\,\Delta x}{k}=0.
$$

Collecting the $T_P$ terms ($2+2+1+1=6$),

$$
\boxed{6T_P=2T_N+2T_W+T_E+T_S+\frac{2\dot q\,\Delta x}{k}}.
$$

The flux term is

$$
\frac{2\dot q\,\Delta x}{k}=\frac{2\times50\times0.04}{0.05}=80\ \text{K},
$$

so

$$
T_P=\frac{2\times240+2\times250+360+380+80}{6}=\frac{480+500+360+380+80}{6}=\frac{1800}{6}=\boxed{300^\circ\text{C}}.
$$

> [!check] Face-by-face balance
> At $T_P=300^\circ$C: $Q_N=0.05\times(240-300)=-3.0$ W/m, $Q_W=0.05\times(250-300)=-2.5$ W/m, $Q_E=0.025\times(360-300)=+1.5$ W/m, $Q_S=0.025\times(380-300)=+2.0$ W/m and $Q_{\dot q}=50\times(0.02+0.02)=+2.0$ W/m. The sum is $-3.0-2.5+1.5+2.0+2.0=0$.

---

## Paper slips and ambiguities

- Q3(i): the printed table puts $R^+=0$ on lines $a$ and $b$. With the module's $R^+=\nu-\theta$, line $a$ has $R^+=\nu_a$, which is zero only when the expansion starts from $M=1$, as in a minimum-length nozzle. Reading the printed cells as invariants measured from the exit state, $R^\pm_{\text{sh}}=(\nu-\nu_a)\mp\theta$, makes the zeros consistent, and both readings give the same $\theta$ and $\nu$ at every point.
- Q4(i): the exchanger is described as double-pass, but the question prescribes the counterflow relation, which gives $\epsilon=0.818$. The one-shell, two-tube-pass relation would give $\epsilon=0.784$. The answer above follows the question. The odd tube count (135) rules out reading it as 67.5 tubes per pass, so each tube makes both passes and carries $1/135$ of the water.
- Corrections to the earlier draft of this note: the $C_{p,\text{crit}}$ column of the Q2(ii) table was slightly wrong in every row (for example $-2.1328$ at $M_\infty=0.50$ instead of $-2.1334$; $M_{\text{crit}}=0.575$ is unchanged); in Q4(iii) $Re_D^{0.8}=1016.0$ and $\text{Pr}^{0.4}=2.0243$, not 1014.4 and 2.0273 (the product, $Nu_D=47.30$, was right); $\theta_{\max}$ at $M_2=1.918$ is $21.5^\circ$, not $21.4^\circ$; the IFT value of $\nu$ at $M=2.46$ is $38.1831^\circ$, not $38.1844^\circ$. The Ackeret validity test was stated as $M_\infty|\theta|\ll1$. That condition is the hypersonic-similarity limit and does not explain the failure here; the relevant test is that the pressure perturbation $\gamma M_\infty^2|\theta|/\sqrt{M_\infty^2-1}$ must be small compared with 1, which (v) now uses.
