---
title: "SESA3029 Past Paper 2015-16 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, pitot-probe, prandtl-glauert, shock-expansion, ackeret, shock-reflection, method-of-characteristics, heat-transfer, richardson-extrapolation]
paper: "2015-16"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]", "[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-201516-01-SESA3029W1.pdf"]
---

# SESA3029 Past Paper 2015-16 - Solutions

> [!abstract] Paper info
> 2015-16 Semester 1 examination (SESA3029W1, 2 hours). No formula sheet; the IFT, NST and oblique-shock chart are provided. Four questions of 30 marks; the rubric asks for three, for 90 marks, and all four are solved here. Front-page constants: $R=287\ \text{J/(kg K)}$, $\gamma=1.4$, $\rho=1.225\ \text{kg/m}^3$, $\mu=1.79\times 10^{-5}\ \text{N s/m}^2$, $1\ \text{bar}=10^5\ \text{N/m}^2$; $c_p=\gamma R/(\gamma-1)=1004.5\ \text{J/(kg K)}$ is used where needed. Q4(i)–(iii) are heat transfer and re-entry radiation (Weeks 9–12, not yet lectured); Q4(iv)–(v) are CFD verification. Table values are the course IFT and NST at 4 d.p., and every number below was rechecked in Python against the exact relations.

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 30 | Supersonic and subsonic Pitot readings, Prandtl–Glauert $C_p$ derivation, wave patterns on a cambered aerofoil, $M_{\text{crit}}$ for $C_{p,\min,0}=-1.8$ | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes\|W01]], [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils\|W07a]], [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation\|W07b]] |
| 2 | 30 | $8^\circ$ diamond aerofoil at $M_\infty=1.6$ with face A along the stream: shock-expansion $p_{A,B,C,D}$, lift and drag for $c=0.3$ m, Ackeret comparison | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves\|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method\|W03]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils\|W07c]] |
| 3 | 30 | Oblique shock ($\beta=48^\circ$, $M_\infty=2.2$) meeting a $25^\circ$ convex corner; corner angle for no reflection; MoC invariants, wall conditions and the unit process at point R | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves\|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method\|W03]], [[SESA3029 W05a - Method of Characteristics\|W05a]], [[SESA3029 W05b - Minimum-Length Nozzle Design\|W05b]] |
| 4 | 30 | (i)–(iii) $\text{Nu}=\text{St}\,\text{Re}\,\text{Pr}$, laminar plate heat flux, lunar re-entry; heat transfer (Weeks 9–12, not yet lectured). (iv)–(v) third-order Richardson extrapolation and CFD checks | not yet lectured (i–iii) |

---

## Q1. Pitot probes, Prandtl–Glauert transformation and critical Mach number (30 marks)

> (i) A Pitot probe is in a wind tunnel with $T_0 = 300\ \text{K}$. Find freestream $M$ and $V$ for: (a) $p = 80\ \text{kN/m}^2, p_0 = 2.12\ \text{bar}$; (b) $p = 103\ \text{kN/m}^2, p_0 = 1.67\ \text{bar}$. [8]
> (ii) From $(1 - M_\infty^2)\phi_{xx} + \phi_{yy} = 0$, derive $C_p = C_{p0}/\sqrt{1 - M_\infty^2}$. [8]
> (iii) Sketch shock and expansion wave patterns around a cambered aerofoil in the transonic and supersonic regimes. [6]
> (iv) Estimate $M_{\text{crit}}$ for an aerofoil with incompressible $C_{p,\min,0} = -1.8$. [8]

### (i) Free-stream Mach number and velocity from Pitot readings [8 marks]

A Pitot probe in subsonic flow brings the stream to rest isentropically, and the largest ratio it can then read is the sonic one,

$$
\left.\frac{p_0}{p}\right|_{M=1}=\left(1+\frac{\gamma-1}{2}\right)^{\gamma/(\gamma-1)}=1.2^{3.5}=1.893 .
$$

A larger reading means the stream is supersonic, a bow shock stands ahead of the probe, and the probe reads $p_{02}$ behind a normal shock ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]]). The stagnation temperature, $T_0=300$ K, is the same either way, because the flow is adiabatic.

#### Case (a): p = 80 kPa, probe reading 2.12 bar

The reading is 212 kPa, and

$$
\frac{p_{\text{probe}}}{p_1}=\frac{212}{80}=2.650>1.893,
$$

so the flow is supersonic and the ratio is the Rayleigh Pitot ratio $p_{02}/p_1$. The NST's last column has $p_{02}/p_1=2.5875$ at $M_1=1.26$ and $2.6500$ at $M_1=1.28$; the reading falls on the second row, so

$$
M_1=\boxed{1.28} .
$$

The static temperature and sound speed are

$$
T_1=\frac{T_0}{1+0.2M_1^2}=\frac{300}{1+0.2(1.6384)}=\frac{300}{1.32768}=225.96\ \text{K},
$$

$$
a_1=\sqrt{\gamma RT_1}=\sqrt{1.4(287)(225.96)}=\sqrt{90\,791}=301.3\ \text{m/s},
$$

so

$$
V_1=M_1a_1=1.28(301.3)=\boxed{385.7\ \text{m/s}} .
$$

#### Case (b): p = 103 kPa, probe reading 1.67 bar

The reading is 167 kPa, and

$$
\frac{p_{\text{probe}}}{p_1}=\frac{167}{103}=1.6214<1.893,
$$

so the flow is subsonic and the probe reads the free-stream $p_0$. Then $p/p_0=103/167=0.6168$, which lies between two IFT rows, $p/p_0=0.6170$ at $M=0.86$ and $0.6041$ at $M=0.88$,

$$
M_1=0.86+0.02\times\frac{0.6170-0.6168}{0.6170-0.6041}=0.86+0.02(0.018)=0.8604 .
$$

The isentropic relation can also be inverted directly,

$$
M_1=\sqrt{\frac{2}{\gamma-1}\left[\left(\frac{p_0}{p}\right)^{(\gamma-1)/\gamma}-1\right]}=\sqrt{5\left[(1.6214)^{0.2857}-1\right]}
$$

$$
=\sqrt{5(1.14806-1)}=\sqrt{0.74031}=\boxed{0.860} .
$$

The static temperature and sound speed are

$$
T_1=\frac{300}{1+0.2(0.8604^2)}=\frac{300}{1.14806}=261.31\ \text{K},
$$

$$
a_1=\sqrt{1.4(287)(261.31)}=\sqrt{104\,994}=324.0\ \text{m/s},
$$

so

$$
V_1=0.8604(324.0)=\boxed{278.8\ \text{m/s}} .
$$

> [!warning] Test before choosing a formula
> Treating case (a) as subsonic, $p_0/p=2.65$ in the isentropic relation gives $M=1.27$, which happens to be close here only because the shock is weak at $M_1=1.28$ ($p_{02}/p_{01}=0.9827$). At higher Mach numbers the error is large.

### (ii) Derivation of the Prandtl–Glauert relation [8 marks]

For $M_\infty<1$ write $\beta=\sqrt{1-M_\infty^2}>0$, so the potential equation is

$$
\beta^2\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0 .
$$

Introduce the transformed coordinates and potential of [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]],

$$
x_0=x,\qquad y_0=\beta y,\qquad \phi_0=\beta\phi .
$$

Since $x_0=x$ and $\phi=\phi_0/\beta$,

$$
\frac{\partial^2\phi}{\partial x^2}=\frac{1}{\beta}\frac{\partial^2\phi_0}{\partial x_0^2} .
$$

Since $y_0=\beta y$, the chain rule gives $\partial/\partial y=\beta\,\partial/\partial y_0$, and applying it twice,

$$
\frac{\partial^2\phi}{\partial y^2}=\beta^2\frac{\partial^2}{\partial y_0^2}\left(\frac{\phi_0}{\beta}\right)=\beta\frac{\partial^2\phi_0}{\partial y_0^2} .
$$

Substituting both,

$$
\beta^2\cdot\frac1\beta\frac{\partial^2\phi_0}{\partial x_0^2}+\beta\frac{\partial^2\phi_0}{\partial y_0^2}=0,
$$

$$
\beta\left(\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\partial^2\phi_0}{\partial y_0^2}\right)=0,
$$

and since $\beta\neq0$, $\phi_0$ satisfies Laplace's equation: it is an incompressible potential flow.

The aerofoil is the same in both planes. Tangency on a thin aerofoil $y=f(x)$ is applied on the axis, $\partial\phi/\partial y=U_\infty f'(x)$ at $y=0$, and

$$
\frac{\partial\phi}{\partial y}=\frac{\partial(\phi_0/\beta)}{\partial(y_0/\beta)}=\frac{\partial\phi_0}{\partial y_0},
$$

so $\phi_0$ satisfies the same condition, $\partial\phi_0/\partial y_0=U_\infty f'(x_0)$ on $y_0=0$.

The streamwise perturbation velocity is

$$
u'=\frac{\partial\phi}{\partial x}=\frac{1}{\beta}\frac{\partial\phi_0}{\partial x_0}=\frac{u_0'}{\beta},
$$

and the linearised pressure coefficient $C_p=-2u'/U_\infty$ becomes

$$
C_p=\frac1\beta\left(-\frac{2u_0'}{U_\infty}\right)=\frac{C_{p0}}{\beta},
$$

$$
\boxed{C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}}} .
$$

### (iii) Wave patterns round a cambered aerofoil [6 marks]

In the transonic regime, just above $M_{\text{crit}}$, the upper surface of a positively cambered section is where the flow first becomes sonic, because its suction is stronger than on the lower surface. A supersonic pocket forms there and ends in a nearly normal shock, which thickens the boundary layer and may separate it. As $M_\infty$ rises towards 1 a smaller pocket and a weaker shock appear on the lower surface, and both shocks move aft towards the trailing edge. Just above $M_\infty=1$ a detached bow shock appears ahead of the rounded leading edge, with the two shocks now at the trailing edge ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils|W07a]]).

In the supersonic regime, with a sharp leading edge, an oblique shock is attached at the leading edge on the side that turns into the stream; at small incidence that is the lower surface, and both surfaces can carry one. Over the convex upper surface a continuous set of expansion waves turns the flow round the camber. At the trailing edge the upper and lower streams meet at different directions and pressures, and trailing-edge shocks turn them into a common direction, separated by a slip line. A rounded leading edge carries a detached bow shock instead.

![[at_pp_201516_q1_regimes.png|900]]

### (iv) Critical Mach number for Cp,min,0 = −1.8 [8 marks]

![[at_pp_201516_q1_mcrit.png|900]]

At $M_{\text{crit}}$ the Prandtl–Glauert-corrected suction peak equals the sonic pressure coefficient ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#8. Estimating the critical Mach number|W07b §8]]),

$$
\frac{-1.8}{\sqrt{1-M^2}}=\frac{2}{\gamma M^2}\left[\left(\frac{2+(\gamma-1)M^2}{\gamma+1}\right)^{\gamma/(\gamma-1)}-1\right].
$$

The two sides are evaluated at trial Mach numbers until the difference changes sign. At $M=0.50$, for example, the left-hand side is $-1.8/\sqrt{0.75}=-1.8/0.86603=-2.0785$. On the right, $(2+0.4\times0.25)/2.4=0.875$, $0.875^{3.5}=0.62665$ and $2/(1.4\times0.25)=5.7143$, so $C_{p,\text{cr}}=5.7143(0.62665-1)=-2.1334$.

| $M$ | $-1.8/\sqrt{1-M^2}$ | $C_{p,\text{cr}}$ | difference |
|---:|---:|---:|---:|
| 0.45 | −2.0156 | −2.7722 | +0.7566 |
| 0.48 | −2.0518 | −2.3654 | +0.3136 |
| 0.50 | −2.0785 | −2.1334 | +0.0549 |
| 0.51 | −2.0926 | −2.0273 | −0.0653 |
| 0.52 | −2.1073 | −1.9272 | −0.1801 |

The sign changes between 0.50 and 0.51. Interpolating linearly,

$$
M_{\text{crit}}=0.50+0.01\times\frac{0.0549}{0.0549+0.0653}=0.50+0.01(0.457)=\boxed{0.505} .
$$

A root-finder gives 0.5045, where both sides equal $-2.085$.

---

## Q2. 8° diamond aerofoil at Mach 1.6 (30 marks)

> An $8^\circ$ diamond-shaped aerofoil (Figure Q.2, face A parallel to oncoming $M_\infty = 1.6$ flow, total included LE and TE wedge angles $8^\circ$) is tested at $p_\infty = 100\ \text{kN/m}^2$.
> (i) Sketch the expected shock and expansion wave pattern. [4]
> (ii) Use shock-expansion to find $p_A, p_B, p_C, p_D$. [12]
> (iii) Determine lift and drag forces for chord $c = 0.3\ \text{m}$. [4]
> (iv) Repeat (ii) using Ackeret's theory and comment on its applicability. [10]

### (i) Expected wave pattern [4 marks]

In Figure Q.2 the diamond has an included angle of $8^\circ$ at both the leading and the trailing edge. Face A (upper front) lies along the stream, face B (upper rear) slopes down at $8^\circ$, face C (lower front) slopes down at $8^\circ$ and face D (lower rear) is horizontal. The section is a rhombus with semi-angle $4^\circ$, its chord line at $4^\circ$ nose-up incidence.

Face A causes no wave at the leading edge, because it does not turn the flow. Face C turns the stream $8^\circ$ into itself; this is less than $\theta_{\max}(1.6)=14.65^\circ$, so an oblique shock is attached at the leading edge. At the upper crest the flow turns $8^\circ$ away from itself onto face B through a centred expansion fan, and at the lower crest it turns $8^\circ$ back to horizontal onto face D through a second fan. At the trailing edge the flow from B, inclined at $-8^\circ$ and at low pressure, meets the horizontal flow from D: the upper stream is turned up through a shock and the lower one through an expansion, until both have the same pressure and direction either side of a slip line. The lower expansion is negligible: $p_D=100.1$ kPa is almost equal to the pressure behind the upper trailing-edge shock, so the lower stream turns by only about $0.007^\circ$, and at any true scale the fan is a single Mach line.

![[at_pp_201516_q2_diamond.png|880]]

### (ii) Static pressures by shock-expansion theory [12 marks]

The flow is steady, inviscid and two-dimensional with $\gamma=1.4$ ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]]). The IFT at $M=1.60$ gives $\nu=14.8604^\circ$ and $p/p_0=0.2353$.

#### Face A

Face A does not turn the flow, so

$$
M_A=1.60,\qquad p_A=p_\infty=\boxed{100.0\ \text{kPa}} .
$$

#### Face B: expansion through 8° from face A

$$
\nu_B=\nu_A+8^\circ=14.8604^\circ+8^\circ=22.8604^\circ .
$$

This lies between two IFT rows.

| $M$ | $\nu$ (deg) | $p/p_0$ |
|---:|---:|---:|
| 1.86 | 22.4492 | 0.1587 |
| 1.88 | 23.0190 | 0.1539 |

With $f=(22.8604-22.4492)/(23.0190-22.4492)=0.4112/0.5698=0.7217$,

$$
M_B=1.86+0.02(0.7217)=1.874,
$$

$$
\left(\frac{p}{p_0}\right)_B=0.1587+0.7217(0.1539-0.1587)=0.1587-0.0035=0.15524 .
$$

The expansion is isentropic, so $p_0$ is the same on A and B, and

$$
p_B=p_A\,\frac{(p/p_0)_B}{(p/p_0)_A}=100\times\frac{0.15524}{0.2353}=\boxed{65.97\ \text{kPa}} .
$$

#### Face C: oblique shock with θ = 8°

The $\theta$–$\beta$–$M$ relation at $M_1=1.6$, evaluated at two trial angles, brackets the weak solution ($\tan8^\circ=0.14054$).

| $\beta$ | $M_1^2\sin^2\beta-1$ | $M_1^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ |
|---:|---:|---:|---:|---:|---:|
| $48^\circ$ | 0.41380 | 5.31641 | 1.80081 | 0.14016 | $7.9788^\circ$ |
| $49^\circ$ | 0.45814 | 5.22772 | 1.73857 | 0.15236 | $8.6632^\circ$ |

$$
\beta_C=48^\circ+1^\circ\times\frac{8-7.9788}{8.6632-7.9788}=48^\circ+\frac{0.0212}{0.6844}=48.03^\circ,
$$

and the exact root is $48.0302^\circ$. Then

$$
M_{n1}=1.6\sin48.0302^\circ=1.6(0.74350)=1.1896 .
$$

The NST rows either side are these.

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ |
|---:|---:|---:|
| 1.18 | 0.8549 | 1.4578 |
| 1.20 | 0.8422 | 1.5133 |

With $f=(1.1896-1.18)/0.02=0.480$,

$$
M_{n2}=0.8549+0.480(0.8422-0.8549)=0.8549-0.0061=0.8488,
$$

$$
\frac{p_C}{p_\infty}=1.4578+0.480(1.5133-1.4578)=1.4578+0.0266=1.4844 .
$$

So

$$
p_C=1.4844\times100=\boxed{148.4\ \text{kPa}},
$$

$$
M_C=\frac{M_{n2}}{\sin(\beta_C-\theta)}=\frac{0.8488}{\sin40.0302^\circ}=\frac{0.8488}{0.64319}=1.3197 .
$$

#### Face D: expansion through 8° from face C

The IFT gives $\nu$ and $p/p_0$ at $M_C=1.3197$ by interpolation between $M=1.30$ ($\nu=6.1703^\circ$, $p/p_0=0.3609$) and $M=1.32$ ($\nu=6.7213^\circ$, $p/p_0=0.3512$), with $f=0.985$,

$$
\nu_C=6.1703^\circ+0.985(0.5510^\circ)=6.7130^\circ,
$$

$$
\left(\frac{p}{p_0}\right)_C=0.3609-0.985(0.0097)=0.35135 .
$$

Then

$$
\nu_D=\nu_C+8^\circ=14.7130^\circ,
$$

which lies between $M=1.58$ ($\nu=14.2686^\circ$, $p/p_0=0.2423$) and $M=1.60$ ($\nu=14.8604^\circ$, $p/p_0=0.2353$). With $f=(14.7130-14.2686)/0.5918=0.7510$,

$$
M_D=1.58+0.02(0.7510)=1.595,
$$

$$
\left(\frac{p}{p_0}\right)_D=0.2423-0.7510(0.0070)=0.23704 .
$$

The stagnation pressure is constant from C to D, so

$$
p_D=p_C\,\frac{(p/p_0)_D}{(p/p_0)_C}=148.44\times\frac{0.23704}{0.35135}=\boxed{100.1\ \text{kPa}} .
$$

> [!check] Exact values
> The exact relations give $p_B=65.99$, $p_C=148.43$ and $p_D=100.13$ kPa. $p_D$ is slightly above $p_\infty$ although face D is parallel to the stream, because the leading-edge shock has lowered the stagnation pressure on the lower side ($p_{02}/p_{01}=0.9937$) while the flow on D has returned almost to $M_\infty$.

### (iii) Lift and drag per unit span [4 marks]

The chord $c=0.3$ m joins the leading and trailing edges, the long diagonal of the rhombus, so each face has length

$$
s=\frac{c/2}{\cos4^\circ}=\frac{0.15}{0.99756}=0.15037\ \text{m} .
$$

Faces A and D are horizontal: A is pushed down by $p_As$ and D up by $p_Ds$. Faces B and C are inclined at $8^\circ$. The outward normal of B points up and back, so its pressure force $p_Bs$ acts down and forwards; the outward normal of C points down and forwards, so $p_Cs$ acts up and back. Resolving perpendicular and parallel to the stream,

$$
L'=(p_D-p_A)s+(p_C-p_B)s\cos8^\circ,
$$

$$
D'=(p_C-p_B)s\sin8^\circ .
$$

The uniform $p_\infty$ contributes nothing to either, because it acts on a closed surface. Substituting,

$$
L'=(100.15-100.00)(0.15037)+(148.44-65.97)(0.15037)(0.99027)
$$

$$
=0.022+12.401(0.99027)=0.022+12.280=\boxed{12.30\ \text{kN/m}},
$$

$$
D'=12.401\sin8^\circ=12.401(0.13917)=\boxed{1.726\ \text{kN/m}} .
$$

> [!check] Lift-to-drag ratio
> Because $p_D\approx p_A$, nearly all of both forces comes from $p_C-p_B$ acting on the two inclined faces, so $L'/D'=12.30/1.726=7.13\approx\cot8^\circ=7.12$.

### (iv) Ackeret's linearised theory and its applicability [10 marks]

Ackeret's formula is $C_p=2\theta/\lambda$, $\lambda=\sqrt{M_\infty^2-1}$, with $\theta$ in radians, positive where the surface turns into the stream ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]]). Here

$$
q_\infty=\tfrac12\gamma p_\infty M_\infty^2=\tfrac12(1.4)(100)(1.6^2)=179.2\ \text{kPa},
$$

$$
\lambda=\sqrt{1.6^2-1}=\sqrt{1.56}=1.2490,
$$

$$
\theta=8^\circ\times\frac{\pi}{180}=0.13963\ \text{rad}.
$$

Faces A and D are parallel to the stream ($\theta=0$), face B turns away from it ($\theta_B=-8^\circ$) and face C into it ($\theta_C=+8^\circ$). With $2(0.13963)/1.2490=0.22358$,

$$
C_{p,A}=C_{p,D}=0\quad\Rightarrow\quad p_A=p_D=\boxed{100.0\ \text{kPa}},
$$

$$
C_{p,B}=-0.22358\quad\Rightarrow\quad p_B=100+179.2(-0.22358)=100-40.07=\boxed{59.93\ \text{kPa}},
$$

$$
C_{p,C}=+0.22358\quad\Rightarrow\quad p_C=100+179.2(0.22358)=100+40.07=\boxed{140.07\ \text{kPa}} .
$$

Ackeret's theory is too low on both inclined faces: $p_B$ by 9.2 % (59.93 against 65.99 kPa) and $p_C$ by 5.6 % (140.07 against 148.43 kPa). The linear theory keeps only the first-order term in $\theta$. The next term is quadratic in $\theta$, so it has the same sign on a compression and an expansion face and raises both pressures. Its size relative to the linear term is a direct measure of the error. With $C_p=C_1\theta+C_2\theta^2$, $C_1=2/\lambda=1.6013$ and the second-order (Busemann) coefficient, which was not lectured,

$$
C_2=\frac{(\gamma+1)M_\infty^4-4(M_\infty^2-1)}{2(M_\infty^2-1)^2}=\frac{2.4(6.5536)-4(1.56)}{2(2.4336)}=1.9495,
$$

the ratio is $C_2\theta/C_1=1.9495(0.13963)/1.6013=0.17$, a 17 % correction. Adding $q_\infty C_2\theta^2=179.2(1.9495)(0.019496)=6.81$ kPa to both faces gives $p_B=66.7$ kPa and $p_C=146.9$ kPa, much closer to the exact values.

The linear theory works when the waves are weak: $\theta$ small compared with $\lambda$, and $M_\infty$ neither close to 1 nor hypersonic. Here $\theta/\lambda=0.11$, and $M_\infty=1.6$ is fairly close to 1, where $C_2$ grows as $1/\lambda^4$; an $8^\circ$ turn is also more than half of $\theta_{\max}=14.65^\circ$. The theory also misses the entropy rise through the leading-edge shock, which is why it gives $p_D=p_\infty$ instead of 100.13 kPa. Ackeret's forces are $L'=(140.07-59.93)(0.15037)\cos8^\circ=11.93$ kN/m and $D'=1.677$ kN/m, 3 % low, because the pressure errors on B and C partly cancel in $p_C-p_B$.

---

## Q3. Shock impingement on a convex corner and Method of Characteristics (30 marks)

> (i) An oblique shock ($\beta = 48^\circ$) in $M_\infty = 2.2$ impinges on a convex corner of angle $\theta = 25^\circ$ (Figure Q.3). Calculate downstream $M$ and sketch the wave pattern. [10]
> (ii) For which value of $\theta$ is there no reflected wave? [2]
> (iii) For weak waves and small turning angles: (a) define Riemann invariants and boundary conditions for reflecting and non-reflecting walls; (b) explain how non-reflection is used in nozzle design. [8]
> (iv) $P$ and $R$ lie on $C^-$, $Q$ and $R$ lie on $C^+$ ($R$ downstream): (a)–(c) sketch characteristics, invariants, and zones of influence/dependence; (d) given $P(M=4,\theta=10^\circ)$ and $Q(M=4.3,\theta=12^\circ)$, find $M_R, \theta_R$ by linear table interpolation. [10]

### (i) Downstream Mach number and wave pattern for a 25° corner [10 marks]

In Figure Q.3 the shock rises from below and meets the upper wall at the corner, where the wall turns up by $\theta=25^\circ$. With the shock angle given, the flow deflection $\delta$ follows directly from the $\theta$–$\beta$–$M$ relation ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]]). At $M_1=2.2$ and $\beta=48^\circ$, $\sin^2\beta=0.55226$ and $\cos2\beta=\cos96^\circ=-0.10453$, so

$$
\tan\delta=2\cot\beta\,\frac{M_1^2\sin^2\beta-1}{M_1^2(\gamma+\cos2\beta)+2}=1.80081\times\frac{4.84(0.55226)-1}{4.84(1.4-0.10453)+2}
$$

$$
=1.80081\times\frac{1.67296}{8.27008}=0.36429,
$$

$$
\delta=\arctan0.36429=20.02^\circ,
$$

upward, towards the wall. The normal Mach number is

$$
M_{n1}=2.2\sin48^\circ=2.2(0.74314)=1.6349 .
$$

The NST gives $M_{n2}=0.6625$ at 1.62 and $0.6568$ at 1.64. With $f=(1.6349-1.62)/0.02=0.746$,

$$
M_{n2}=0.6625+0.746(0.6568-0.6625)=0.6625-0.0042=0.6583,
$$

$$
M_2=\frac{M_{n2}}{\sin(\beta-\delta)}=\frac{0.6583}{\sin27.984^\circ}=\frac{0.6583}{0.46922}=1.403 .
$$

Behind the shock the flow rises at $20.02^\circ$, but beyond the corner the wall rises at $25^\circ$. The flow must turn a further

$$
\Delta\theta=25^\circ-20.02^\circ=4.98^\circ
$$

upward, away from itself and towards the receding wall. That turn is an expansion, so the corner reflects the shock as a centred Prandtl–Meyer fan, not as a shock (left panel of the figure below).

At $M_2=1.403$ the IFT rows $M=1.40$ ($\nu=8.9870^\circ$) and $1.42$ ($\nu=9.5650^\circ$) give, with $f=0.150$,

$$
\nu_2=8.9870^\circ+0.150(0.5780^\circ)=9.0737^\circ,
$$

$$
\nu_3=\nu_2+\Delta\theta=9.0737^\circ+4.984^\circ=14.0577^\circ .
$$

This lies between $M=1.56$ ($\nu=13.6770^\circ$) and $M=1.58$ ($\nu=14.2686^\circ$),

$$
M_3=1.56+0.02\times\frac{14.0577-13.6770}{14.2686-13.6770}=1.56+0.02\times\frac{0.3807}{0.5916}=1.56+0.02(0.6435)=\boxed{1.573} .
$$

The exact relations give $M_2=1.4028$ and $M_3=1.5726$.

### (ii) Corner angle for no reflected wave [2 marks]

No wave is needed when the wall beyond the corner is already parallel to the flow behind the incident shock,

$$
\theta=\delta=\boxed{20.0^\circ} .
$$

A smaller corner angle turns the flow back towards itself and reflects a shock; a larger one reflects an expansion fan, as in (i).

### (iii) Riemann invariants, wall conditions and non-reflection in nozzle design [8 marks]

For weak waves the flow is nearly isentropic and irrotational, and the method of characteristics applies ([[SESA3029 W05a - Method of Characteristics|W05a]]). In the course convention the invariants are

$$
R^+=\nu-\theta\ \ \text{constant along }C^+\ (\text{slope }\theta+\mu),\qquad R^-=\nu+\theta\ \ \text{constant along }C^-\ (\text{slope }\theta-\mu).
$$

At a wall only one characteristic arrives, so the wall supplies the second condition, the flow angle. At an upper wall a $C^+$ arrives from point A carrying $R^+_A$ ([[SESA3029 W05b - Minimum-Length Nozzle Design#11. Boundary conditions|W05b §11]]).

For a reflecting (prescribed) wall the slope $\theta_W$ is fixed by the geometry. Then

$$
\nu_W=R^+_A+\theta_W,
$$

and the $C^-$ that leaves the wall carries

$$
R^-_W=\nu_W+\theta_W=R^+_A+2\theta_W .
$$

If $\theta_W$ differs from the flow angle $\theta_A$ carried by the arriving wave, the wall makes the flow turn, and a reflected wave of the same kind leaves it (shock from shock, fan from fan). A symmetry plane is the special case $\theta_W=0$, where $R^-=R^+$.

For a non-reflecting wall the slope is chosen equal to the flow angle carried by the arriving wave, $\theta_W=\theta_A$. Then

$$
\nu_W=R^+_A+\theta_A=(\nu_A-\theta_A)+\theta_A=\nu_A,
$$

so the state at the wall equals the state behind the arriving wave, the flow is not turned, and no wave is reflected.

In a minimum-length nozzle the throat corner sends an expansion fan towards the centreline, which reflects it as $C^+$ waves running back to the wall. If the wall were straight, these would reflect again and the waves would persist into the test section. Instead the wall is turned back towards the axis at each point where a $C^+$ arrives, by the flow angle that wave carries, so each wave is cancelled. Downstream of the last cancellation the flow is uniform and parallel at the design Mach number, and the nozzle is as short as the wave pattern allows ([[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]]).

### (iv) Characteristics through R and the state at R [10 marks]

#### (a)–(c) Sketch, invariants, and zones of dependence and influence

The right panel of the figure below shows the construction. The $C^-$ through P and R descends to the right at $\theta-\mu$ and carries $R^-=\nu+\theta$; the $C^+$ through Q and R rises to the right at $\theta+\mu$ and carries $R^+=\nu-\theta$.

The domain of dependence of R is the region upstream between the $C^+$ and $C^-$ traced backwards from R. It contains P and Q, and only conditions inside it can affect the flow at R. The zone of influence of R is the region downstream between the $C^+$ and $C^-$ that leave R. A disturbance at R can be felt only inside it, because in supersonic flow signals travel along Mach lines and only downstream.

![[at_pp_201516_q3_corner_char.png|900]]

#### (d) State at R

The IFT gives $\nu_P=\nu(4.00)=65.7848^\circ$ and $\nu_Q=\nu(4.30)=69.5406^\circ$. The invariants carried to R are

$$
R^-_P=\nu_P+\theta_P=65.7848^\circ+10^\circ=75.7848^\circ,
$$

$$
R^+_Q=\nu_Q-\theta_Q=69.5406^\circ-12^\circ=57.5406^\circ .
$$

At R both hold, so adding and subtracting them,

$$
\nu_R=\tfrac12\left(R^-_P+R^+_Q\right)=\tfrac12(75.7848^\circ+57.5406^\circ)=66.6627^\circ,
$$

$$
\theta_R=\tfrac12\left(R^-_P-R^+_Q\right)=\tfrac12(75.7848^\circ-57.5406^\circ)=\boxed{9.12^\circ} .
$$

Interpolating linearly in the IFT between $M=4.06$ ($\nu=66.5688^\circ$) and $M=4.08$ ($\nu=66.8263^\circ$),

$$
M_R=4.06+0.02\times\frac{66.6627-66.5688}{66.8263-66.5688}=4.06+0.02\times\frac{0.0939}{0.2575}=4.06+0.02(0.3647)=\boxed{4.067} .
$$

---

## Q4. Dimensionless heat-transfer numbers, laminar plate, lunar re-entry and CFD checks (30 marks)

> [!warning] Partly not yet lectured
> Parts (i)–(iii), 19 marks, are heat transfer and re-entry radiation (Weeks 9–12), not yet lectured as of 12 Nov 2026. Parts (iv)–(v), 11 marks, are CFD verification.

> (i) Define $\text{Nu}, \text{St}, \text{Pr}, \text{Re}$ and show $\text{Nu} = \text{St}\,\text{Re}\,\text{Pr}$. [4]
> (ii) Laminar BL over a $10\ \text{cm} \times 10\ \text{cm}$ flat plate at $T_w = 50^\circ\text{C}$ in air ($\text{Pr}=0.7, T_\infty=15^\circ\text{C}, U_\infty=5\ \text{m/s}$) with $\text{Nu}_x = 0.332\,\text{Re}_x^{1/2}\text{Pr}^{1/3}$: find total heat flux. [10]
> (iii) Sketch shock layer near leading edge during lunar re-entry peak heating, discuss radiation, and write surface thermal-equilibrium equation. [5]
> (iv) Uniformly third-order CFD gives average $\text{Nu} = 82.1$ ($100\times 100$) and $79.1$ ($150\times 150$). Estimate exact $\text{Nu}$. [5]
> (v) Besides grid refinement, what other checks ensure a CFD solution is correct? [6]

### (i) Dimensionless groups and the identity [4 marks]

For a length $L$, velocity $U$, density $\rho$, viscosity $\mu$, specific heat $c_p$, conductivity $k$ and heat-transfer coefficient $h$,

$$
\text{Nu}=\frac{hL}{k},\qquad \text{St}=\frac{h}{\rho Uc_p},\qquad \text{Re}=\frac{\rho UL}{\mu},\qquad \text{Pr}=\frac{\mu c_p}{k}.
$$

The Nusselt number compares convective heat transfer with conduction across a layer of thickness $L$, the Stanton number compares the wall heat flux with the enthalpy flux of the stream, the Reynolds number compares inertial with viscous forces, and the Prandtl number compares momentum diffusivity with thermal diffusivity. Multiplying,

$$
\text{St}\,\text{Re}\,\text{Pr}=\frac{h}{\rho Uc_p}\cdot\frac{\rho UL}{\mu}\cdot\frac{\mu c_p}{k}=\frac{hL}{k}=\boxed{\text{Nu}} .
$$

### (ii) Total laminar heat flux from the 10 cm square plate [10 marks]

The data are $L=w=0.10$ m, $U_\infty=5$ m/s, $\Delta T=50-15=35$ K, $\text{Pr}=0.7$, and with $c_p=1004.5\ \text{J/(kg K)}$ the conductivity is

$$
k=\frac{\mu c_p}{\text{Pr}}=\frac{1.79\times10^{-5}(1004.5)}{0.7}=0.02569\ \text{W/(m K)} .
$$

The Reynolds number at the trailing edge is

$$
\text{Re}_L=\frac{\rho U_\infty L}{\mu}=\frac{1.225(5)(0.10)}{1.79\times10^{-5}}=\frac{0.6125}{1.79\times10^{-5}}=3.422\times10^4,
$$

below $3\times10^5$, so the layer is laminar throughout. With $\text{Re}_x=(\rho U_\infty/\mu)x$ the given correlation makes the local coefficient

$$
h_x=\frac{k}{x}\text{Nu}_x=0.332\,k\left(\frac{\rho U_\infty}{\mu}\right)^{1/2}\text{Pr}^{1/3}x^{-1/2},
$$

and averaging over the plate, with $\int_0^Lx^{-1/2}\,\mathrm dx=2L^{1/2}$,

$$
\bar h=\frac1L\int_0^Lh_x\,\mathrm dx=0.664\,\frac{k}{L}\,\text{Re}_L^{1/2}\text{Pr}^{1/3} .
$$

Numerically,

$$
\overline{\text{Nu}}_L=0.664(3.4218\times10^4)^{1/2}(0.7)^{1/3}=0.664(184.98)(0.88790)=109.06,
$$

$$
\bar h=\frac{109.06(0.02569)}{0.10}=28.01\ \text{W/(m}^2\text{ K)},
$$

$$
q=\bar h\,Lw\,\Delta T=28.01(0.10)(0.10)(35)=\boxed{9.80\ \text{W}} .
$$

With $c_p=1005\ \text{J/(kg K)}$ the result is 9.81 W.

### (iii) Lunar re-entry shock layer, radiation and surface thermal equilibrium [5 marks]

The sketch shows a blunt heat shield with a detached bow shock standing a short distance ahead of it, normal on the axis and oblique round the shoulders, and between them a thin shock layer of hot gas with a boundary layer at the wall. At lunar-return speed, about 11 km/s, the air behind the normal part of the shock reaches about 10 000 K and is dissociated and partly ionised. That gas radiates strongly, and the radiative flux it sends to the wall, $q_{\text{rad,gas}}$, is comparable with the convective flux $q_{\text{conv}}$ at peak heating. The hot surface in turn loses heat by radiating to space, $\varepsilon\sigma T_w^4$, which at radiative equilibrium balances most of the incoming heat.

For a surface in thermal equilibrium the heat in equals the heat out. For a non-ablating wall,

$$
q_{\text{conv}}+\alpha_wq_{\text{rad,gas}}=\varepsilon\sigma T_w^4+q_{\text{cond}},
$$

where $\alpha_w$ is the surface absorptivity and $q_{\text{cond}}$ the heat conducted into the structure (zero for an insulated back face). On an ablating heat shield a further loss, $\dot m\,\Delta h_{\text{abl}}$, appears on the right.

### (iv) Third-order Richardson extrapolation [5 marks]

For a uniformly third-order method the error on a grid of spacing $h$ is $Ch^3$ to leading order,

$$
\text{Nu}_1=\text{Nu}_{\text{exact}}+Ch_1^3,\qquad \text{Nu}_2=\text{Nu}_{\text{exact}}+Ch_2^3 .
$$

The refinement ratio is $r=h_1/h_2=150/100=1.5$. With $h_1=rh_2$, subtracting the two equations gives

$$
\text{Nu}_1-\text{Nu}_2=Ch_2^3(r^3-1),
$$

$$
Ch_2^3=\frac{\text{Nu}_1-\text{Nu}_2}{r^3-1},
$$

and then

$$
\text{Nu}_{\text{exact}}=\text{Nu}_2-Ch_2^3=\text{Nu}_2+\frac{\text{Nu}_2-\text{Nu}_1}{r^3-1}
$$

$$
=79.1+\frac{79.1-82.1}{1.5^3-1}=79.1-\frac{3.0}{2.375}=79.1-1.26=\boxed{77.8} .
$$

### (v) Other checks on a CFD solution [6 marks]

Grid refinement checks only the discretisation error. The other checks are these.

- Iterative convergence: the residuals fall by several orders of magnitude and the quantities of interest (here the average Nusselt number) stop changing with further iterations.
- Global conservation: the mass, momentum and energy fluxes balance over the domain, for example the heat leaving the wall equals the enthalpy gained by the flow.
- Domain size and boundary conditions: the far-field boundaries are far enough away not to affect the solution or reflect waves back into it, and the inflow, outflow and wall conditions match the physical problem.
- Time-step independence for an unsteady solution, and for a turbulent one the near-wall resolution ($y^+$) appropriate to the turbulence model and a check on the sensitivity to that model.
- Validation: comparison with an analytical solution, a correlation such as $\text{Nu}_x=0.332\,\text{Re}_x^{1/2}\text{Pr}^{1/3}$ in the laminar limit, or experimental data.

---

## Paper slips and ambiguities

- Figure Q.2 marks three angles of $8^\circ$: the included angle at the leading edge (between A and C), the included angle at the trailing edge (between B and D), and the slope of face B below face A. The solution reads the section as a rhombus of semi-angle $4^\circ$ at $4^\circ$ incidence, with $c$ the leading-edge-to-trailing-edge diagonal. Reading $8^\circ$ as a semi-angle would make face C turn the flow $16^\circ$, more than $\theta_{\max}(1.6)=14.65^\circ$, and the shock would detach.
- Corrections to the earlier draft of this note: the $C_{p,\text{cr}}$ values in the Q1(iv) table were wrong at $M=0.50$ ($-2.1334$, not $-2.1328$) and $0.52$ ($-1.9272$, not $-1.9288$), and the table listed the answer as if it were a table row; the interpolation is now shown. The Ackeret applicability comment in Q2(iv) gave $\theta$ as 18 % of the Mach angle (it is 21 %) and used $M_\infty\theta\ll1$ as the test; it now measures the error by the second-order term, $C_2\theta/C_1=0.17$. Q3 now uses the course invariants $R^+=\nu-\theta$, $R^-=\nu+\theta$ in place of Anderson's $\theta\mp\nu$, with unchanged results.
