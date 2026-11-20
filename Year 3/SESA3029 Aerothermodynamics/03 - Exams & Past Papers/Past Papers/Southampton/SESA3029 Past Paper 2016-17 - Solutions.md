---
title: "SESA3029 Past Paper 2016-17 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, laval-nozzle, oblique-shock, shock-reflection, swbli, ackeret, method-of-characteristics, minimum-length-nozzle, heat-transfer, euler-equations]
paper: "2016-17"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-201617-01-SESA3029W1.pdf"]
---

# SESA3029 Past Paper 2016-17 - Solutions

> [!abstract] Paper info
> 2016-17 Semester 1 examination (SESA3029W1, 2 hours, formula sheet on pp. 8–9). Four questions of 30 marks; the rubric asks for three, for 90 marks, and all four are solved here. Front-page constants: $R=287\ \text{J/(kg K)}$, $\gamma=1.4$, $\rho=1.225\ \text{kg/m}^3$, $\mu=1.79\times 10^{-5}\ \text{N s/m}^2$. No $c_p$ is printed, so $c_p=\gamma R/(\gamma-1)=1004.5\ \text{J/(kg K)}$ is used. Q4(i)–(ii) are heat transfer (Weeks 9–12, not yet lectured); Q4(iii) is the 1D Euler characteristic analysis. Table values are the course IFT and NST at 4 d.p., and every number below was rechecked in Python against the exact relations.

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 30 | $M=3.0$ wind tunnel ($p_0=500\ \text{kPa}$, $T_0=420\ \text{K}$) with a shock generator of $13^\circ$ and $26^\circ$: regular and Mach reflection, viscous shock–boundary-layer interaction | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves\|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method\|W03]], [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow\|W04]] |
| 2 | 30 | Derivation of Ackeret's $C_p=2\theta/\sqrt{M_\infty^2-1}$, flat-plate $\mathrm{d}C_L/\mathrm{d}\alpha$, plano-convex aerofoil $C_D$ at $M_\infty=3.0$ | [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils\|W07c]] |
| 3 | 30 | Two-wave minimum-length nozzle ($M_e=1.5$): flow regions, $\theta_{\max}=\nu(M_e)/2$, MoC states and coordinates at points 1–4 | [[SESA3029 W05a - Method of Characteristics\|W05a]], [[SESA3029 W05b - Minimum-Length Nozzle Design\|W05b]] |
| 4 | 30 | (i)–(ii) $\text{Nu}=\text{St}\,\text{Re}\,\text{Pr}$ and heat-transfer rate from a tripped flat plate; heat transfer (Weeks 9–12, not yet lectured). (iii) 1D Euler characteristic speeds | not yet lectured (i–ii); [[SESA3029 W05a - Method of Characteristics\|W05a]] (iii) |

---

## Q1. Supersonic wind tunnel, shock reflections and SWBLI (30 marks)

> A C-D nozzle generates $M_1 = 3.0$ in a test section from $p_0 = 500\ \text{kPa}$, $T_0 = 420\ \text{K}$ (Figure Q.1). A test plate (upper face aligned with flow) and a shock generator (upper face aligned with flow, included LE angle $13^\circ$) are inserted.
> (i) $p$ and $T$ in the throat. [3]
> (ii) $p$ and $T$ in the test section. [3]
> (iii) $p$ and $T$ immediately after the oblique shock from the shock generator. [6]
> (iv) Sketch & explain the inviscid flow pattern on the test plate. [2]
> (v) $p$ and $T$ after interaction with the test plate. [6]
> (vi) Sketch & explain the viscous flow pattern on the test plate. [4]
> (vii) For LE angle $26^\circ$, find $M$ after the incident shock and sketch the wall interaction with supporting calculations. [6]

### (i) Throat pressure and temperature [3 marks]

The nozzle flow is steady and isentropic, and the throat is sonic because the test section is supersonic ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]). At $M=1$,

$$
\frac{T^*}{T_0}=\frac{1}{1+\frac{\gamma-1}{2}}=\frac{1}{1.2}=0.8333,\qquad \frac{p^*}{p_0}=(0.8333)^{3.5}=0.5283,
$$

which are the IFT entries at $M=1.00$. Hence

$$
p^*=0.5283\times500=\boxed{264.1\ \text{kPa}},\qquad T^*=0.8333\times420=\boxed{350.0\ \text{K}} .
$$

### (ii) Test-section pressure and temperature [3 marks]

At $M_1=3.0$,

$$
\frac{T_0}{T_1}=1+0.2(3.0^2)=1+1.8=2.8 .
$$

The temperature and pressure are

$$
T_1=\frac{420}{2.8}=\boxed{150.0\ \text{K}},
$$

$$
p_1=\frac{p_0}{(T_0/T_1)^{3.5}}=\frac{500}{2.8^{3.5}}=\frac{500}{36.733}=\boxed{13.61\ \text{kPa}} .
$$

The IFT row ($p/p_0=0.0272$) gives $0.0272\times500=13.60$ kPa, the same to table accuracy.

### (iii) Conditions after the incident oblique shock [6 marks]

The upper face of the shock generator is aligned with the stream, so its lower face, at the included angle of $13^\circ$, turns the flow downward by $\theta=13^\circ$ ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]]). The shock angle satisfies

$$
\tan\theta=2\cot\beta\,\frac{M_1^2\sin^2\beta-1}{M_1^2(\gamma+\cos2\beta)+2}
$$

with $M_1=3.0$, $\theta=13^\circ$. Two trial angles bracket the weak solution.

| $\beta$ | $M_1^2\sin^2\beta-1$ | $M_1^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ |
|---:|---:|---:|---:|---:|---:|
| $30^\circ$ | 1.25000 | 19.10000 | 3.46410 | 0.22671 | $12.7735^\circ$ |
| $31^\circ$ | 1.38738 | 18.82524 | 3.32856 | 0.24531 | $13.7829^\circ$ |

Interpolating to $13^\circ$,

$$
\beta_1=30^\circ+1^\circ\times\frac{13-12.7735}{13.7829-12.7735}=30^\circ+\frac{0.2265}{1.0094}=30.22^\circ,
$$

and the exact root is $30.2221^\circ$. The normal Mach number is

$$
M_{n1}=3.0\sin30.2221^\circ=3.0(0.50335)=1.5101 .
$$

The NST rows either side are these.

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ | $T_2/T_1$ |
|---:|---:|---:|---:|
| 1.50 | 0.7011 | 2.4583 | 1.3202 |
| 1.52 | 0.6941 | 2.5288 | 1.3336 |

With $f=(1.5101-1.50)/0.02=0.503$,

$$
M_{n2}=0.7011+0.503(0.6941-0.7011)=0.7011-0.0035=0.6976,
$$

$$
\frac{p_2}{p_1}=2.4583+0.503(2.5288-2.4583)=2.4583+0.0355=2.4938,
$$

$$
\frac{T_2}{T_1}=1.3202+0.503(1.3336-1.3202)=1.3202+0.0067=1.3269 .
$$

Behind the incident shock (region 2),

$$
p_2=2.4938\times13.61=\boxed{33.94\ \text{kPa}},\qquad T_2=1.3269\times150.0=\boxed{199.0\ \text{K}},
$$

$$
M_2=\frac{M_{n2}}{\sin(\beta_1-\theta)}=\frac{0.6976}{\sin17.2221^\circ}=\frac{0.6976}{0.29608}=2.356 .
$$

### (iv) Inviscid flow pattern on the test plate [2 marks]

Region 2 flows downward at $13^\circ$, but at the plate the flow must be parallel to the horizontal surface. The plate therefore reflects the shock: a reflected oblique shock turns the flow back up through $13^\circ$ and leaves a uniform, higher-pressure region 3 parallel to the wall. A regular reflection is possible because the required turn is less than the largest attached deflection at $M_2=2.356$, $\theta_{\max}=28.16^\circ$ (the peak of the $M=2.36$ curve on the oblique-shock chart). Panel (a) of the figure below shows the pattern ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]]).

### (v) Conditions after shock reflection from the test plate [6 marks]

The reflected shock turns the $M_2=2.356$ stream through $13^\circ$. Bracketing the weak solution as before,

| $\beta$ | $M_2^2\sin^2\beta-1$ | $M_2^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ |
|---:|---:|---:|---:|---:|---:|
| $36^\circ$ | 0.91772 | 11.48626 | 2.75276 | 0.21994 | $12.4041^\circ$ |
| $37^\circ$ | 1.01036 | 11.30097 | 2.65409 | 0.23729 | $13.3488^\circ$ |

$$
\beta_2=36^\circ+1^\circ\times\frac{13-12.4041}{13.3488-12.4041}=36^\circ+\frac{0.5959}{0.9447}=36.63^\circ,
$$

with the exact root $36.6274^\circ$. This angle is measured from the region-2 flow direction, so the reflected shock makes $36.63^\circ-13^\circ=23.63^\circ$ with the plate. The normal Mach number into it is

$$
M_{n2}'=M_2\sin\beta_2=2.356\sin36.6274^\circ=2.356(0.59661)=1.4056 .
$$

The NST rows either side are these.

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ | $T_2/T_1$ |
|---:|---:|---:|---:|
| 1.40 | 0.7397 | 2.1200 | 1.2547 |
| 1.42 | 0.7314 | 2.1858 | 1.2676 |

With $f=(1.4056-1.40)/0.02=0.280$,

$$
M_{n3}=0.7397+0.280(0.7314-0.7397)=0.7397-0.0023=0.7374,
$$

$$
\frac{p_3}{p_2}=2.1200+0.280(2.1858-2.1200)=2.1200+0.0184=2.1384,
$$

$$
\frac{T_3}{T_2}=1.2547+0.280(1.2676-1.2547)=1.2547+0.0036=1.2583 .
$$

Behind the reflected shock (region 3),

$$
p_3=2.1384\times33.94=\boxed{72.58\ \text{kPa}},\qquad T_3=1.2583\times199.04=\boxed{250.5\ \text{K}},
$$

$$
M_3=\frac{M_{n3}}{\sin(\beta_2-\theta)}=\frac{0.7374}{\sin23.6274^\circ}=\frac{0.7374}{0.40079}=1.840 .
$$

> [!check] Stagnation-pressure route
> The two shocks keep $p_{02}/p_{01}=0.9266$ and $p_{03}/p_{02}=0.9568$, so $p_{03}=500(0.9266)(0.9568)=443.3$ kPa. At $M_3=1.840$ the isentropic ratio is $p_3/p_{03}=0.16375$, giving $p_3=72.58$ kPa again. Similarly $T_3=150(1.3269)(1.2583)=250.5$ K, and $T_0$ is unchanged: $250.5(1+0.2\times1.840^2)=420.0$ K.

### (vi) Viscous flow pattern on the test plate [4 marks]

With viscosity the plate carries a boundary layer, and its subsonic inner part cannot sustain the sudden pressure rise $p_3/p_2=2.14$ of the inviscid reflection. The pressure rise is fed upstream through that subsonic layer, the boundary layer thickens ahead of the inviscid impingement point and, for a shock this strong, separates into a shallow bubble (panel (b) below; [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]]).

The thickening near separation deflects the outer flow and generates compression waves that merge into a separation shock ahead of the impingement point. The incident shock meets the edge of the separated shear layer, where the pressure is nearly constant, and reflects from it as an expansion fan that turns the outer flow round the crest of the bubble. Downstream of the crest the flow turns back parallel to the wall and reattaches through a second set of compression waves, the reattachment shock. The single reflected shock of the inviscid picture is thus spread into a separation shock, an expansion fan and a reattachment shock, and the boundary layer leaves the interaction much thicker than it arrived.

### (vii) Incident shock for a 26° wedge and Mach reflection [6 marks]

At $M_1=3.0$ the largest attached deflection is $\theta_{\max}=34.07^\circ$, so a $26^\circ$ generator still carries an attached shock. Bracketing its angle,

| $\beta$ | $M_1^2\sin^2\beta-1$ | $M_1^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ |
|---:|---:|---:|---:|---:|---:|
| $45^\circ$ | 3.50000 | 14.60000 | 2.00000 | 0.47945 | $25.6155^\circ$ |
| $46^\circ$ | 3.65705 | 14.28590 | 1.93138 | 0.49441 | $26.3084^\circ$ |

$$
\beta_1=45^\circ+1^\circ\times\frac{26-25.6155}{26.3084-25.6155}=45^\circ+\frac{0.3845}{0.6929}=45.55^\circ,
$$

with the exact root $45.5512^\circ$. Then

$$
M_{n1}=3.0\sin45.5512^\circ=3.0(0.71388)=2.1416 .
$$

The NST gives $M_{n2}=0.5554$ at 2.14 and $0.5525$ at 2.16. With $f=(2.1416-2.14)/0.02=0.081$,

$$
M_{n2}=0.5554+0.081(0.5525-0.5554)=0.5554-0.0002=0.5552,
$$

$$
M_2=\frac{M_{n2}}{\sin(\beta_1-\theta)}=\frac{0.5552}{\sin19.5512^\circ}=\frac{0.5552}{0.33465}=\boxed{1.659} .
$$

A regular reflection would need a second shock that turns this $M_2=1.659$ stream back through $26^\circ$. The largest attached deflection at $M_2$ follows from the $\beta_{\max}$ condition used in [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]]. With $M_2^2=2.7520$ and $M_2^4=7.5733$,

$$
\sin^2\beta_{\max}=\frac{1}{\gamma M^2}\left[\frac{\gamma+1}{4}M^2-1+\sqrt{(\gamma+1)\left(\frac{\gamma+1}{16}M^4+\frac{\gamma-1}{2}M^2+1\right)}\right]
$$

$$
=\frac{1}{3.8527}\left[1.6512-1+\sqrt{2.4(1.1360+0.5504+1)}\right]=\frac{0.6512+2.5392}{3.8527}=0.82807,
$$

so $\beta_{\max}=65.50^\circ$. At that angle $\cos2\beta_{\max}=-0.65614$ and

$$
\tan\theta_{\max}=2\cot65.50^\circ\,\frac{2.7520(0.82807)-1}{2.7520(1.4-0.65614)+2}=0.91133\times\frac{1.2788}{4.0471}=0.28796,
$$

$$
\theta_{\max}(1.659)=\arctan0.28796=16.06^\circ<26^\circ .
$$

No attached reflected shock can turn the flow through $26^\circ$, so regular reflection is impossible and a Mach reflection forms (panel (c) below). The incident shock ends at a triple point above the plate. From the triple point a nearly normal Mach stem runs down to the wall, meeting it at right angles, and a reflected shock runs up into the stream. Flow through the Mach stem becomes subsonic, while flow through the incident and reflected shocks stays supersonic; the two streams leave the triple point at the same pressure but different velocities, separated by a slip line.

![[at_pp_201617_q1_shock_reflection.png|920]]

---

## Q2. Ackeret's theory and supersonic aerofoils (30 marks)

> (i) Starting from $(1 - M_\infty^2)\phi_{xx} + \phi_{yy} = 0$, derive Ackeret's relation $C_p = 2\theta/\sqrt{M_\infty^2 - 1}$. [10]
> (ii) Derive flat-plate lift curve slope $\mathrm{d}C_L/\mathrm{d}\alpha$ and sketch vs $M_\infty$, discussing $M\to 1$, $M\to\infty$, and physical behaviour for $M\to 1$. [6]
> (iii) Find $C_D$ for a $c=1.0\ \text{m}$ aerofoil with flat lower surface and parabolic upper surface $y_u = 0.2x(1-x)\ \text{m}$ at $\alpha = 0^\circ$, $M_\infty = 3.0$ (Figure Q.2). [10]
> (iv) Discuss whether this would be a suitable aerofoil for a supersonic aircraft. [4]

### (i) Derivation of Ackeret's formula [10 marks]

For $M_\infty>1$ write $\lambda=\sqrt{M_\infty^2-1}$, so that $1-M_\infty^2=-\lambda^2$ and the potential equation becomes the wave equation ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]]),

$$
\lambda^2\frac{\partial^2\phi}{\partial x^2}-\frac{\partial^2\phi}{\partial y^2}=0 .
$$

Its general (d'Alembert) solution is

$$
\phi(x,y)=f(x-\lambda y)+g(x+\lambda y).
$$

The function $f$ is constant along lines $x-\lambda y=\text{const}$, which rise downstream with slope $1/\lambda=\tan\mu$; $g$ is constant along lines that fall downstream. Above the aerofoil, disturbances can only travel downstream and away from the surface, so the solution there is

$$
\phi(x,y)=f(x-\lambda y).
$$

Differentiating,

$$
u'=\frac{\partial\phi}{\partial x}=f'(x-\lambda y),
$$

$$
v'=\frac{\partial\phi}{\partial y}=-\lambda f'(x-\lambda y),
$$

so the two perturbation velocities are tied together,

$$
u'=-\frac{v'}{\lambda} .
$$

The linearised tangency condition on the upper surface $y=y_u(x)$, applied at $y=0$, is

$$
\frac{v'}{U_\infty}=\frac{\mathrm dy_u}{\mathrm dx}=\theta,
$$

where $\theta$ is the surface angle to the free stream, positive when the surface turns into the flow. Substituting $v'=U_\infty\theta$,

$$
\frac{u'}{U_\infty}=-\frac{\theta}{\lambda} .
$$

The linearised pressure coefficient is $C_p=-2u'/U_\infty$, so

$$
C_p=-2\left(-\frac{\theta}{\lambda}\right)=\boxed{\frac{2\theta}{\sqrt{M_\infty^2-1}}} .
$$

Below the aerofoil the solution is $\phi=g(x+\lambda y)$, which gives $u'=+v'/\lambda$. There $v'/U_\infty=\mathrm dy_l/\mathrm dx$ and a surface turning into the flow has $\mathrm dy_l/\mathrm dx=-\theta$, so the same formula results with $\theta$ positive for compression on either side.

### (ii) Flat-plate lift slope and its variation with Mach number [6 marks]

A flat plate at a small incidence $\alpha$ (radians) turns away from the stream on its upper surface and into it on its lower surface, so $\theta_u=-\alpha$ and $\theta_l=+\alpha$,

$$
C_{p,u}=-\frac{2\alpha}{\lambda},\qquad C_{p,l}=+\frac{2\alpha}{\lambda} .
$$

For small $\alpha$ the lift coefficient is the chordwise integral of the pressure difference,

$$
C_L=\frac1c\int_0^c\left(C_{p,l}-C_{p,u}\right)\mathrm dx=\frac1c\int_0^c\frac{4\alpha}{\lambda}\,\mathrm dx=\frac{4\alpha}{\lambda},
$$

$$
\frac{\mathrm dC_L}{\mathrm d\alpha}=\boxed{\frac{4}{\sqrt{M_\infty^2-1}}} .
$$

As $M_\infty\to1^+$, $\lambda\to0$ and the formula predicts an infinite lift slope. That is not physical. The linear equation drops the nonlinear term in $\phi_x\phi_{xx}$, which is small only while $|1-M_\infty^2|$ is large compared with the perturbation; near $M_\infty=1$ the coefficient $1-M_\infty^2$ vanishes, the dropped term dominates and the flow is transonic, with shocks and mixed subsonic and supersonic regions. The real lift slope rises to a finite peak near $M_\infty=1$ and then falls.

As $M_\infty\to\infty$, $\lambda\to M_\infty$ and $\mathrm dC_L/\mathrm d\alpha\approx4/M_\infty\to0$. Linear theory also needs $M_\infty\alpha\ll1$, so at hypersonic speeds it fails for any fixed incidence; there the pressure coefficients become independent of Mach number and the lift does not keep falling as $4\alpha/M_\infty$.

![[at_pp_201617_q2_cl_slope.png|760]]

### (iii) Drag coefficient of the plano-convex aerofoil at zero incidence and Mach 3 [10 marks]

The lower surface is flat, $y_l=0$, and the upper surface is $y_u=0.2x(1-x)$ with $c=1$ m. The surface slopes are

$$
\frac{\mathrm dy_u}{\mathrm dx}=0.2(1-2x),\qquad \frac{\mathrm dy_l}{\mathrm dx}=0 .
$$

At $\alpha=0$ the lower surface lies along the stream, so $C_{p,l}=0$. On the upper surface Ackeret's formula gives

$$
C_{p,u}=\frac{2}{\lambda}\frac{\mathrm dy_u}{\mathrm dx} .
$$

The pressure on an element of surface $\mathrm ds$ has streamwise component $(p-p_\infty)\,\mathrm dy_u$, so the drag per unit span of the upper surface is

$$
D'=\int_0^c(p-p_\infty)\frac{\mathrm dy_u}{\mathrm dx}\,\mathrm dx .
$$

Dividing by $q_\infty c$,

$$
C_D=\frac1c\int_0^cC_{p,u}\frac{\mathrm dy_u}{\mathrm dx}\,\mathrm dx=\frac{2}{\lambda c}\int_0^c\left(\frac{\mathrm dy_u}{\mathrm dx}\right)^2\mathrm dx .
$$

The integral is

$$
\int_0^1 0.04(1-2x)^2\,\mathrm dx=0.04\left[-\frac{(1-2x)^3}{6}\right]_0^1=0.04\left(\frac16+\frac16\right)=\frac{0.04}{3}=0.013333 .
$$

At $M_\infty=3.0$, $\lambda=\sqrt{9-1}=\sqrt8=2.8284$, so

$$
C_D=\frac{2}{2.8284}(0.013333)=\boxed{0.00943} .
$$

> [!check] Thickness plus camber
> The section has thickness $t(x)=y_u$ and camber line $y_c=y_u/2$, so the half-thickness $h=y_u/2$ and the camber line have the same slope, $0.1(1-2x)$, with mean square $0.01/3=0.003333$. The general result $C_d=\frac{4}{\lambda}\left[\alpha^2+\overline{(h')^2}+\overline{(y_c')^2}\right]$ of [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#8. Drag coefficient|W07c §8]] gives $\frac{4}{2.8284}(0.006667)=0.00943$. Half of the drag is thickness drag and half is camber drag.

### (iv) Suitability for a supersonic aircraft [4 marks]

The section has two features a supersonic aerofoil needs. Its leading edge is sharp, so the bow wave stays attached instead of standing off as a detached shock, and it is thin, with $t/c=0.2(0.25)=0.05$ at mid-chord, which keeps the wave drag small.

It is still a poor choice. Being flat on one side, it is cambered, and the check above shows that camber doubles its drag: a symmetric biconvex section of the same $t/c=0.05$ has $C_d=\frac{16}{3}(0.05)^2/2.8284=0.00471$, and a diamond of the same thickness has $4(0.05)^2/2.8284=0.00354$ ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#9. Thickness drag and the optimum section|W07c §9]]). In supersonic linear theory camber produces no lift, since $C_L=4\alpha/\lambda$ whatever the shape, so the extra drag buys nothing. The camber does produce a pitching moment. The front half of the upper surface has $C_p>0$, pushing down, and the rear half $C_p<0$, pulling up. The loading is

$$
C_{p,l}-C_{p,u}=0-\frac{2}{\lambda}(0.2)(1-2x)=-\frac{0.4}{\lambda}(1-2x),
$$

so the moment about the leading edge (nose-up positive) is

$$
C_{m,LE}=-\int_0^1\left(C_{p,l}-C_{p,u}\right)x\,\mathrm dx=\frac{0.4}{\lambda}\int_0^1\left(x-2x^2\right)\mathrm dx
$$

$$
=\frac{0.4}{2.8284}\left(\frac12-\frac23\right)=0.14142\left(-\frac16\right)=-0.0236 .
$$

That is a nose-down moment at zero lift, which would have to be trimmed. A thin symmetric section (diamond or biconvex) is the better choice, with high-lift devices for low-speed flight.

---

## Q3. Prototype two-wave minimum-length nozzle (30 marks)

> Prototype MoC calculation for an MLN with $M_e = 1.5$ using two characteristic waves from $0 = (0,1)$ with $\theta = 3^\circ$ and $\theta_{\max}$ (Figure Q.3).
> (i) Identify complex, simple and uniform flow regions. [3]
> (ii) Define $R^-$ connecting 0 and 3 and show $\theta_{\max} = \nu(M_e)/2$. [5]
> (iii) Symmetry at 1 and 3; find $x_1$. [6]
> (iv) Explain wave cancellation at 4 and relate $(M_4, \theta_4)$ to $(M_2, \theta_2)$. [4]
> (v) Find $M, \theta$ at points 1, 2, 3 and $(x,y)$ coordinates of point 2. [12]

The course invariants are used throughout: $R^+=\nu-\theta$ is constant along a $C^+$ (slope $\theta+\mu$) and $R^-=\nu+\theta$ along a $C^-$ (slope $\theta-\mu$) ([[SESA3029 W05a - Method of Characteristics|W05a]]).

### (i) Flow regions in Figure Q.3 [3 marks]

Upstream of the first wave $0$–$1$ the flow is uniform and sonic. The complex region, where characteristics of both families cross, is bounded by the first $C^-$ from the corner ($0$–$1$), the centreline ($1$–$3$) and the last $C^-$ from the corner ($0$–$2$–$3$); it contains point 2, where the $C^+$ reflected from point 1 crosses the second wave. The simple region lies between the last $C^-$ ($0$–$2$–$3$), the wall ($0$–$4$–$5$) and the last $C^+$ ($3$–$5$). Only $C^+$ waves cross it, because the wall cancels them instead of reflecting $C^-$ waves, so each $C^+$ in it ($2$–$4$ and $3$–$5$) is straight. Downstream of $3$–$5$ the flow is uniform at $M_e=1.5$, $\theta=0$ ([[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]]).

### (ii) Riemann invariant from 0 to 3 and proof that θmax = ν(Me)/2 [5 marks]

Points 0 and 3 are joined by the last right-running characteristic, $0$–$2$–$3$, along which

$$
R^-=\nu+\theta=\text{const}.
$$

The flow reaching the corner is uniform and sonic, with $\nu=0$ and $\theta=0$, so every $C^+$ entering the corner fan carries $R^+=\nu-\theta=0$. On each ray leaving the corner, therefore, $\nu=\theta$. On the last ray the flow angle is $\theta_{\max}$, so

$$
\nu_0=\theta_{\max},
$$

$$
R^-_0=\nu_0+\theta_{\max}=2\theta_{\max} .
$$

At point 3, on the centreline, symmetry gives $\theta_3=0$, and point 3 starts the uniform exit flow, so $M_3=M_e$,

$$
R^-_3=\nu(M_e)+0=\nu(M_e) .
$$

Equating the invariant at the two ends of the characteristic,

$$
2\theta_{\max}=\nu(M_e),
$$

$$
\boxed{\theta_{\max}=\frac{\nu(M_e)}{2}} .
$$

### (iii) Symmetry at 1 and 3 and the x-coordinate of point 1 [6 marks]

The centreline is a streamline of a symmetric flow, so the flow crossing it has no normal component: $\theta_1=\theta_3=0$. It acts as a wall that reflects each arriving $C^-$ as a $C^+$ of the same strength.

On the first ray from the corner, $\theta=3^\circ$ and $\nu=\theta=3^\circ$, so $R^-=6^\circ$. Its Mach number follows by inverse interpolation in the IFT between $M=1.16$ ($\nu=2.6073^\circ$) and $M=1.18$ ($\nu=3.0743^\circ$),

$$
M_{0a}=1.16+0.02\times\frac{3-2.6073}{3.0743-2.6073}=1.16+0.02\times\frac{0.3927}{0.4670}=1.16+0.02(0.8409)=1.1768,
$$

$$
\mu_{0a}=\arcsin\frac{1}{1.1768}=58.18^\circ .
$$

At point 1, $\theta_1=0$ and the $C^-$ from the corner carries $R^-=6^\circ$, so

$$
\nu_1=R^--\theta_1=6^\circ,\qquad R^+_1=\nu_1-\theta_1=6^\circ .
$$

Between $M=1.28$ ($\nu=5.6272^\circ$) and $M=1.30$ ($\nu=6.1703^\circ$),

$$
M_1=1.28+0.02\times\frac{6-5.6272}{6.1703-5.6272}=1.28+0.02\times\frac{0.3728}{0.5431}=1.28+0.02(0.6864)=1.2937,
$$

$$
\mu_1=\arcsin\frac{1}{1.2937}=50.62^\circ .
$$

The segment $0$–$1$ is a $C^-$, and its slope is the average of $\theta-\mu$ at its ends,

$$
\alpha_{01}=\tfrac12\left[(\theta-\mu)_{0a}+(\theta-\mu)_1\right]=\tfrac12\left[(3^\circ-58.18^\circ)+(0^\circ-50.62^\circ)\right]=-52.90^\circ .
$$

The line leaves $(0,1)$ and reaches $y=0$ at point 1,

$$
0=1+x_1\tan\alpha_{01},
$$

$$
x_1=-\frac{1}{\tan(-52.90^\circ)}=\frac{1}{1.32235}=\boxed{0.756} .
$$

### (iv) Wave cancellation at point 4 and its link to point 2 [4 marks]

The $C^+$ from point 2 arrives at the wall at point 4. At a prescribed wall the flow would have to turn to follow the wall, and the turn would send a reflected $C^-$ back into the nozzle. Instead the wall at point 4 is given the flow angle carried by the arriving wave, $\theta_W=\theta_2$, so the flow does not turn and no wave is reflected (BC 2 of [[SESA3029 W05b - Minimum-Length Nozzle Design#BC 2: a designed wall is non-reflecting|W05b]]). With $R^+_4=R^+_2$ and $\theta_4=\theta_2$,

$$
\nu_4=R^+_2+\theta_4=(\nu_2-\theta_2)+\theta_2=\nu_2,
$$

$$
\boxed{\theta_4=\theta_2,\qquad M_4=M_2} .
$$

The segment $2$–$4$ is then a straight characteristic of uniform state, inclined at $(\theta+\mu)_2$.

### (v) Properties at points 1, 2 and 3 and the coordinates of point 2 [12 marks]

The IFT gives $\nu(1.50)=11.9052^\circ$, so

$$
\theta_{\max}=\frac{11.9052^\circ}{2}=5.9526^\circ .
$$

On the last ray from the corner $\nu=\theta=5.9526^\circ$ and $R^-=11.9052^\circ$. Between $M=1.28$ and $M=1.30$,

$$
M_{0b}=1.28+0.02\times\frac{5.9526-5.6272}{0.5431}=1.28+0.02(0.5992)=1.2920,\qquad \mu_{0b}=50.71^\circ .
$$

Point 2 receives $R^+_1=6^\circ$ along the $C^+$ from point 1 and $R^-=11.9052^\circ$ along the $C^-$ from the corner. Adding and subtracting,

$$
\nu_2=\tfrac12(R^++R^-)=\tfrac12(6^\circ+11.9052^\circ)=8.9526^\circ,
$$

$$
\theta_2=\tfrac12(R^--R^+)=\tfrac12(11.9052^\circ-6^\circ)=2.9526^\circ .
$$

Between $M=1.38$ ($\nu=8.4130^\circ$) and $M=1.40$ ($\nu=8.9870^\circ$),

$$
M_2=1.38+0.02\times\frac{8.9526-8.4130}{8.9870-8.4130}=1.38+0.02\times\frac{0.5396}{0.5740}=1.38+0.02(0.9401)=1.3988,
$$

$$
\mu_2=\arcsin\frac{1}{1.3988}=45.63^\circ .
$$

Point 3 lies on the same $C^-$ ($R^-=11.9052^\circ$) and on the centreline ($\theta_3=0$), so $\nu_3=11.9052^\circ$ and $M_3=1.50$. The states are collected below.

| Point | $M$ | $\nu$ | $\theta$ | $\mu$ | $R^+$ | $R^-$ | $\theta+\mu$ | $\theta-\mu$ |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 0a (first ray) | 1.1768 | 3.0000 | 3.0000 | 58.18 | 0 | 6.0000 | | −55.18 |
| 0b (last ray) | 1.2920 | 5.9526 | 5.9526 | 50.71 | 0 | 11.9052 | | −44.76 |
| 1 | 1.2937 | 6.0000 | 0 | 50.62 | 6.0000 | 6.0000 | 50.62 | −50.62 |
| 2 | 1.3988 | 8.9526 | 2.9526 | 45.63 | 6.0000 | 11.9052 | 48.59 | −42.68 |
| 3 | 1.5000 | 11.9052 | 0 | 41.81 | 11.9052 | 11.9052 | 41.81 | |

(angles in degrees). The answers are

$$
\theta_1=\boxed{0^\circ},\ M_1=\boxed{1.294};\qquad \theta_2=\boxed{2.95^\circ},\ M_2=\boxed{1.399};\qquad \theta_3=\boxed{0^\circ},\ M_3=\boxed{1.500} .
$$

Point 2 is the intersection of the $C^+$ from point 1 (A in the formula-sheet notation) and the $C^-$ from the corner on the last ray (B). The averaged slopes are

$$
\alpha_{12}=\tfrac12\left[(\theta+\mu)_1+(\theta+\mu)_2\right]=\tfrac12(50.62^\circ+48.59^\circ)=49.60^\circ,
$$

$$
\alpha_{02}=\tfrac12\left[(\theta-\mu)_{0b}+(\theta-\mu)_2\right]=\tfrac12(-44.76^\circ-42.68^\circ)=-43.72^\circ,
$$

with $\tan\alpha_{12}=1.17516$ and $\tan\alpha_{02}=-0.95636$. With $(x_A,y_A)=(0.7562,0)$ and $(x_B,y_B)=(0,1)$,

$$
x_2=\frac{x_B\tan\alpha_{02}-x_A\tan\alpha_{12}+y_A-y_B}{\tan\alpha_{02}-\tan\alpha_{12}}=\frac{0-0.7562(1.17516)+0-1}{-0.95636-1.17516}=\frac{-1.88866}{-2.13152}=\boxed{0.886},
$$

$$
y_2=y_A+(x_2-x_A)\tan\alpha_{12}=0+(0.8861-0.7562)(1.17516)=\boxed{0.153} .
$$

Along the $C^-$ from the corner, $y_2=1+0.8861(-0.95636)=0.153$ as well.

![[at_pp_201617_q3_mln_2wave.png|880]]

---

## Q4. Dimensionless heat-transfer groups, tripped flat plate and 1D Euler characteristics (30 marks)

> [!warning] Partly not yet lectured
> Parts (i) and (ii), 21 marks, are convective heat transfer (Weeks 9–12), not yet lectured as of 12 Nov 2026. Part (iii), 9 marks, is the 1D Euler characteristic analysis.

> (i) Define $\text{Nu}, \text{St}, \text{Pr}, \text{Re}$ and show $\text{Nu} = \text{St}\,\text{Re}\,\text{Pr}$. [4]
> (ii) Flat plate ($30\ \text{cm} \times 10\ \text{cm}$, $T_w = 50^\circ\text{C}$) in air ($\text{Pr}=0.7, U_\infty=60\ \text{m/s}, T_\infty=20^\circ\text{C}$) with trip wire at $x=5\ \text{cm}$: (a) verify $\text{Re}_x < 300\,000$ at $x=5\ \text{cm}$ [2]; (b) heat flux from $x=0$ to $5\ \text{cm}$ [7]; (c) total heat flux over entire plate assuming abrupt transition at $x=5\ \text{cm}$ [8].
> (iii) Show 1D isentropic Euler equations $\partial q/\partial t + \partial f(q)/\partial x = 0$ reduce to $\partial q/\partial t + A\,\partial q/\partial x = 0$ and find characteristic speeds $u\pm a$. [9]

### (i) Dimensionless numbers and the relation Nu = St Re Pr [4 marks]

For a length $x$, velocity $U$, density $\rho$, viscosity $\mu$, specific heat $c_p$, conductivity $k$ and heat-transfer coefficient $h$, the four groups are

- the Nusselt number $\text{Nu}=hx/k$, convective heat transfer relative to conduction across a fluid layer of thickness $x$;
- the Stanton number $\text{St}=h/(\rho Uc_p)$, the wall heat flux relative to the enthalpy flux carried by the stream;
- the Reynolds number $\text{Re}=\rho Ux/\mu$, inertial relative to viscous forces;
- the Prandtl number $\text{Pr}=\mu c_p/k$, momentum diffusivity relative to thermal diffusivity.

Multiplying the last three,

$$
\text{St}\,\text{Re}\,\text{Pr}=\frac{h}{\rho Uc_p}\cdot\frac{\rho Ux}{\mu}\cdot\frac{\mu c_p}{k} .
$$

The factors $\rho U$, $\mu$ and $c_p$ cancel,

$$
\text{St}\,\text{Re}\,\text{Pr}=\frac{hx}{k}=\boxed{\text{Nu}} .
$$

### (ii) Heat transfer from the tripped flat plate [17 marks]

The data are $\rho=1.225\ \text{kg/m}^3$, $\mu=1.79\times10^{-5}\ \text{N s/m}^2$, $\text{Pr}=0.7$, $U_\infty=60$ m/s, plate length $L=0.30$ m, width $w=0.10$ m, trip at $x_t=0.05$ m and $\Delta T=50-20=30$ K. With $c_p=\gamma R/(\gamma-1)=1.4(287)/0.4=1004.5\ \text{J/(kg K)}$, the conductivity is

$$
k=\frac{\mu c_p}{\text{Pr}}=\frac{1.79\times10^{-5}(1004.5)}{0.7}=0.02569\ \text{W/(m K)} .
$$

#### (a) Reynolds number at the trip [2 marks]

$$
\text{Re}_{x_t}=\frac{\rho U_\infty x_t}{\mu}=\frac{1.225(60)(0.05)}{1.79\times10^{-5}}=\frac{3.675}{1.79\times10^{-5}}=\boxed{2.053\times10^5},
$$

which is below 300 000, so the boundary layer is laminar up to the trip wire.

#### (b) Heat-transfer rate from the leading edge to the trip [7 marks]

The formula sheet gives $\text{Nu}_x=0.332\,\text{Re}_x^{1/2}\text{Pr}^{1/3}$ for a laminar layer at uniform wall temperature. With $\text{Re}_x=(\rho U_\infty/\mu)x$ the local coefficient is

$$
h_x=\frac{k}{x}\text{Nu}_x=0.332\,k\left(\frac{\rho U_\infty}{\mu}\right)^{1/2}\text{Pr}^{1/3}x^{-1/2} .
$$

Averaging from $0$ to $x_t$, with $\int_0^{x_t}x^{-1/2}\,\mathrm dx=2x_t^{1/2}$,

$$
\bar h_{\text{lam}}=\frac{1}{x_t}\int_0^{x_t}h_x\,\mathrm dx=0.664\,k\left(\frac{\rho U_\infty}{\mu}\right)^{1/2}\text{Pr}^{1/3}x_t^{-1/2}=0.664\,\frac{k}{x_t}\text{Re}_{x_t}^{1/2}\text{Pr}^{1/3},
$$

so the mean Nusselt number is twice the local value at $x_t$,

$$
\overline{\text{Nu}}_{x_t}=0.664\,\text{Re}_{x_t}^{1/2}\text{Pr}^{1/3}=0.664(2.0531\times10^5)^{1/2}(0.7)^{1/3}
$$

$$
=0.664(453.11)(0.88790)=267.14 .
$$

The mean heat-transfer coefficient over the laminar part is

$$
\bar h_{\text{lam}}=\frac{\overline{\text{Nu}}_{x_t}k}{x_t}=\frac{267.14(0.02569)}{0.05}=137.2\ \text{W/(m}^2\text{ K)},
$$

and the heat-transfer rate through the area $x_tw$ is the flux $\bar h_{\text{lam}}\Delta T=137.2(30)=4116\ \text{W/m}^2$ multiplied by that area,

$$
q_{\text{lam}}=\bar h_{\text{lam}}\,x_tw\,\Delta T=137.2(0.05)(0.10)(30)=\boxed{20.6\ \text{W}} .
$$

#### (c) Total heat-transfer rate over the whole plate [8 marks]

Downstream of the trip the boundary layer is turbulent, and the formula sheet gives $\text{Nu}_x=0.029\,\text{Re}_x^{0.8}\text{Pr}^{0.6}$ with $x$ measured from the leading edge. Writing $\text{Re}_x=(\rho U_\infty/\mu)x$, the local coefficient is

$$
h_x=\frac{k}{x}\,0.029\left(\frac{\rho U_\infty}{\mu}x\right)^{0.8}\text{Pr}^{0.6}=0.029\,k\left(\frac{\rho U_\infty}{\mu}\right)^{0.8}\text{Pr}^{0.6}\,x^{-0.2} .
$$

The constant factor is evaluated first. With $\rho U_\infty/\mu=73.5/(1.79\times10^{-5})=4.1061\times10^6\ \text{m}^{-1}$, $(4.1061\times10^6)^{0.8}=1.9532\times10^5$ and $0.7^{0.6}=0.80734$,

$$
K=0.029(0.02569)(1.9532\times10^5)(0.80734)=117.47\ \text{W/(m}^{1.8}\text{ K)} .
$$

The turbulent heat-transfer rate is the integral of $h_x\Delta T$ over the strip of width $w$ from $x_t$ to $L$,

$$
q_{\text{turb}}=w\,\Delta T\,K\int_{x_t}^{L}x^{-0.2}\,\mathrm dx=w\,\Delta T\,K\,\frac{L^{0.8}-x_t^{0.8}}{0.8} .
$$

The integral is

$$
\frac{0.30^{0.8}-0.05^{0.8}}{0.8}=\frac{0.38168-0.09103}{0.8}=0.36331\ \text{m}^{0.8},
$$

so

$$
q_{\text{turb}}=0.10(30)(117.47)(0.36331)=128.0\ \text{W} .
$$

Adding the laminar part,

$$
q_{\text{total}}=q_{\text{lam}}+q_{\text{turb}}=20.6+128.0=\boxed{148.6\ \text{W}} .
$$

With $c_p=1005\ \text{J/(kg K)}$ the totals are 20.6 W and 148.7 W. The turbulent strip, five-sixths of the area, carries 86 % of the heat.

### (iii) 1D isentropic Euler Jacobian and characteristic speeds [9 marks]

With $q_1=\rho$ and $q_2=\rho u$, so that $u=q_2/q_1$ and $p=Cq_1^\gamma$, the fluxes are

$$
f_1=q_2,\qquad f_2=\frac{q_2^2}{q_1}+Cq_1^\gamma .
$$

The chain rule gives $\partial f/\partial x=A\,\partial q/\partial x$ with $A=\partial f/\partial q$, so the equations take the form $\partial q/\partial t+A\,\partial q/\partial x=0$. The entries of $A$ are

$$
\frac{\partial f_1}{\partial q_1}=0,\qquad \frac{\partial f_1}{\partial q_2}=1,\qquad \frac{\partial f_2}{\partial q_2}=\frac{2q_2}{q_1}=2u,
$$

$$
\frac{\partial f_2}{\partial q_1}=-\frac{q_2^2}{q_1^2}+\gamma Cq_1^{\gamma-1}=-u^2+\frac{\gamma C\rho^\gamma}{\rho}=-u^2+\frac{\gamma p}{\rho}=a^2-u^2,
$$

so

$$
A=\begin{pmatrix}0&1\\a^2-u^2&2u\end{pmatrix}.
$$

The characteristic speeds are the eigenvalues of $A$,

$$
\det(A-\lambda I)=-\lambda(2u-\lambda)-(a^2-u^2)=0,
$$

$$
\lambda^2-2u\lambda+u^2-a^2=0,
$$

$$
(\lambda-u)^2=a^2,
$$

$$
\lambda=\boxed{u-a,\ u+a} .
$$

---

## Paper slips and ambiguities

- The front page gives $R$ and $\gamma$ but not $c_p$, and $\text{Pr}=0.7$ appears only in Q4(ii). Using $c_p=\gamma R/(\gamma-1)=1004.5\ \text{J/(kg K)}$ instead of 1005 changes the heat-transfer rates by 0.05 %.
- Q4(ii)(c) says only that transition is abrupt at the trip. The answer above uses the formula-sheet correlation with $x$ from the leading edge (148.6 W). Starting a new turbulent layer at the trip, with $x$ measured from the wire, gives a thinner layer and higher $h$: $q_{\text{turb}}=145.3$ W and a total of 165.9 W.
- Corrections to the earlier draft of this note: the IFT entries used in Q3(iii) are $\nu(1.16)=2.6073^\circ$ and $\nu(1.18)=3.0743^\circ$ (the draft had 2.553 and 3.081; the interpolated $M_{0a}=1.177$ was unaffected); the $C^+$ and $C^-$ invariants now follow the course convention $R^+=\nu-\theta$, $R^-=\nu+\theta$ in place of Anderson's $\theta\mp\nu$; the drag check in Q2(iii) was rewritten because it contained an unfinished formula; and the claims in Q2(iv) that the section is "close to minimum wave drag" in a "Sears–Haack family" were wrong, since its drag is twice that of a symmetric biconvex section of the same thickness.
