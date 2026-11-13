---
title: "SESA3029 Past Paper 2019-20 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, shock-expansion, ackeret, prandtl-glauert, method-of-characteristics, minimum-length-nozzle, boundary-layer, finite-difference]
paper: "2019-20"
theory_notes: ["[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-201920-01-SESA3029.pdf"]
---

# SESA3029 Past Paper 2019-20 - Solutions

> [!abstract] Paper info
> 2019-20 Semester 1 Examination (SESA3029W1): 120 minutes, four questions worth 32, 16, 20 and 32 marks, with a formula sheet on pp. 7–8 and the isentropic and normal-shock tables and oblique-shock chart provided. The front page gives $R=287\ \text{J/(kg K)}$, $c_p=1004.5\ \text{J/(kg K)}$, $\gamma=1.4$, $\text{Pr}=0.7$, $\rho=1.225\ \text{kg/m}^3$ and $\mu=1.8\times 10^{-5}\ \text{N s/m}^2$. Nearest table values are acceptable unless a question says otherwise, so each answer gives the interpolated or exact value and, where it differs, the nearest-row value. Every number was recomputed in Python. Question 4 is heat transfer (Weeks 9–12, not yet lectured).

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 32 | Flat plate with a $c/4$ trailing-edge flap ($\eta=9^\circ$, $M_\infty=2.4$): nozzle $A/A^*$, $p_0$, $T_0$, shock-expansion, $C_L$, Ackeret flap effectiveness and its error | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 2 | 16 | Prandtl–Glauert derivation, subsonic flap effectiveness at $M_\infty=0.75$, supersonic against subsonic flaps | [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 3 | 20 | Planar minimum-length nozzle ($M_e=2.2$): Riemann invariants and $(M,\theta)$ at point 2, coordinates of points 1 and 2 | [[SESA3029 W05a - Method of Characteristics|W05a]], [[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]] |
| 4 | 32 | $\text{Nu}=\text{St}\,\text{Re}\,\text{Pr}$, laminar plate convection, $5\times3$ tapered-block 2D finite differences, grid convergence and Richardson extrapolation. Heat transfer (Weeks 9–12, not yet lectured) | Not yet lectured |

---

## Q1. Flat plate with trailing-edge flap in supersonic flow (32 marks)

> A flat plate of chord $c$ with a trailing-edge flap of length $c/4$ is placed at zero incidence in a uniform air stream with $M_\infty=2.4$, $p_\infty=60\ \text{kN/m}^2$, $T_\infty=244\ \text{K}$ (Figure Q.1 prints $M_\infty=2.9$; see [[#Paper slips and ambiguities]]).
> (i) Find the nozzle area ratio $A/A^*$ and required stagnation conditions $p_0, T_0$. [6]
> (ii) Using the shock-expansion method, find the static pressure and Mach number on the upper and lower sides of the flap for $\eta=9^\circ$. [10]
> (iii) Find the lift coefficient $C_L$ using $c$ as reference length. [6]
> (iv) Use Ackeret's equation to show $\mathrm{d}C_L/\mathrm{d}\eta = 0.458$ for small deflections. [6]
> (v) Find the relative error of Ackeret's method relative to shock-expansion at $\eta=9^\circ$ and discuss how the error depends on $\eta$. [4]

![[at_pp_201920_q1_flapped_plate.png|820]]

### (i) Nozzle area ratio and stagnation conditions [6 marks]

The tunnel nozzle expands the flow isentropically from the reservoir to the test section, and a supersonic test section needs a sonic throat ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]). The IFT row $M=2.40$ reads

$$
\frac{A}{A^*}=2.4031,
\qquad
\frac{p}{p_0}=0.0684,
\qquad
\frac{T}{T_0}=0.4647 .
$$

The formulae give the same. With $1+0.2M_\infty^2=1+0.2\times2.4^2=2.152$,

$$
\frac{A}{A^*}=\frac{1}{M_\infty}\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M_\infty^2\right)\right]^{(\gamma+1)/(2(\gamma-1))}=\frac{1}{2.4}\left(\frac{2.152}{1.2}\right)^{3}=\frac{1.79333^3}{2.4}=\frac{5.76744}{2.4}=\boxed{2.403},
$$

$$
p_0=p_\infty\left(1+0.2M_\infty^2\right)^{3.5}=60\times2.152^{3.5}=60\times14.620=\boxed{877.2\ \text{kPa}},
$$

$$
T_0=T_\infty\left(1+0.2M_\infty^2\right)=244\times2.152=\boxed{525.1\ \text{K}} .
$$

### (ii) Flap pressures and Mach numbers by shock-expansion [10 marks]

The forward $3c/4$ of the plate lies along the stream at zero incidence, so it produces no waves and both faces reach the hinge at $M_\infty=2.4$, $p_\infty=60$ kPa. At the hinge the flap turns down by $\eta=9^\circ$: the upper flow turns away from itself through an expansion fan and the lower flow turns into itself through an oblique shock ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]]).

#### Upper side of the flap: expansion fan

The IFT row $M=2.40$ gives $\nu=36.747^\circ$. The fan adds $9^\circ$.

$$
\nu_u=\nu(M_\infty)+\eta=36.747^\circ+9^\circ=45.747^\circ .
$$

The IFT rows bracketing this are $M=2.80$ ($\nu=45.7459^\circ$, $p/p_0=0.0368$) and $M=2.82$ ($46.1611^\circ$, $0.0357$). The fraction is $(45.7465-45.7459)/0.4152=0.0015$, so

$$
M_u=2.80+0.02\times0.0015=\boxed{2.800} .
$$

The fan is isentropic, so $p_0=877.2$ kPa still holds on the upper side.

$$
p_u=p_0\left(1+0.2M_u^2\right)^{-3.5}=877.2\times\left(1+0.2\times2.8^2\right)^{-3.5}=877.2\times2.568^{-3.5}=\frac{877.2}{27.139}=\boxed{32.32\ \text{kPa}} .
$$

The nearest-row value is $877.2\times0.0368=32.28$ kPa.

#### Lower side of the flap: oblique shock

Trial values of $\beta$ in the θ–β–M relation at $M_\infty=2.4$ bracket $\theta=9^\circ$.

| $\beta$ (°) | $M^2\sin^2\beta-1$ | $M^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ (°) |
|---:|---:|---:|---:|---:|---:|
| 32 | 0.61749 | 12.58902 | 3.20067 | 0.15699 | 8.922 |
| 33 | 0.70860 | 12.40680 | 3.07973 | 0.17590 | 9.976 |

Interpolating,

$$
\beta\approx32+\frac{9-8.922}{9.976-8.922}=32+0.074=32.07^\circ,
$$

and the exact root is $32.073^\circ$. The normal Mach number is

$$
M_{n1}=M_\infty\sin\beta=2.4\sin32.073^\circ=2.4\times0.53100=1.2744 .
$$

The NST rows bracketing it are

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ |
|---:|---:|---:|
| 1.26 | 0.8071 | 1.6855 |
| 1.28 | 0.7963 | 1.7448 |

With fraction $(1.2744-1.26)/0.02=0.720$,

$$
\frac{p_l}{p_\infty}=1.6855+0.720\times0.0593=1.7282,
\qquad
M_{n2}=0.8071-0.720\times0.0108=0.7993 .
$$

The normal-shock formulae confirm them.

$$
\frac{p_l}{p_\infty}=1+\frac{2\gamma}{\gamma+1}\left(M_{n1}^2-1\right)=1+\frac76\left(1.2744^2-1\right)=1+1.16667\times0.62408=1.7281,
$$

$$
M_{n2}=\sqrt{\frac{2+(\gamma-1)M_{n1}^2}{2\gamma M_{n1}^2-(\gamma-1)}}=\sqrt{\frac{2.6496}{4.1474}}=\sqrt{0.63886}=0.7993 .
$$

The lower-side pressure and Mach number are

$$
p_l=60\times1.7281=\boxed{103.69\ \text{kPa}},
$$

$$
M_l=\frac{M_{n2}}{\sin(\beta-\eta)}=\frac{0.7993}{\sin23.073^\circ}=\frac{0.7993}{0.39190}=\boxed{2.040} .
$$

### (iii) Lift coefficient [6 marks]

Ahead of the hinge both faces are at $p_\infty$, so only the flap carries load. Its net pressure $p_l-p_u$ acts normal to the flap over a length $c/4$, and the lift is the component of that force normal to the free stream, which is a factor $\cos\eta$ smaller.

$$
L'=(p_l-p_u)\,\frac{c}{4}\cos\eta=(103.685-32.322)\times\frac{c}{4}\times\cos9^\circ=71.363\times0.25\times0.98769\,c=17.621\,c\ \text{kN/m}.
$$

The free-stream dynamic pressure, written as $\tfrac12\gamma p_\infty M_\infty^2$, is

$$
q_\infty=\tfrac12\times1.4\times60\times2.4^2=241.92\ \text{kPa}.
$$

With $c$ as the reference length,

$$
C_L=\frac{L'}{q_\infty c}=\frac{17.621}{241.92}=\boxed{0.0728} .
$$

The flap force also has a drag component $(p_l-p_u)(c/4)\sin\eta$. Dropping the $\cos\eta$ (taking lift equal to the normal force) gives $C_L=71.363/(4\times241.92)=0.0737$.

### (iv) Ackeret flap effectiveness [6 marks]

Ackeret's formula ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]]) gives the pressure coefficient on a surface that turns the flow by $\theta$ (radians, positive into the flow).

$$
C_p=\frac{2\theta}{\sqrt{M_\infty^2-1}} .
$$

Ahead of the hinge $\theta=0$ on both faces, so $C_p=0$ there. On the flap the lower face turns the flow into itself by $+\eta$ and the upper face away from itself by $-\eta$.

$$
C_{p,l}=+\frac{2\eta}{\sqrt{M_\infty^2-1}},
\qquad
C_{p,u}=-\frac{2\eta}{\sqrt{M_\infty^2-1}} .
$$

In linear theory the force on the flap is taken as normal to the chord, so the lift coefficient is the chordwise integral of the pressure difference, which is non-zero only over the last quarter.

$$
C_L=\frac1c\int_{3c/4}^{c}\left(C_{p,l}-C_{p,u}\right)\mathrm dx=\frac14\cdot\frac{4\eta}{\sqrt{M_\infty^2-1}}=\frac{\eta}{\sqrt{M_\infty^2-1}} .
$$

Differentiating with respect to $\eta$ in radians at $M_\infty=2.4$,

$$
\frac{\mathrm dC_L}{\mathrm d\eta}=\frac{1}{\sqrt{M_\infty^2-1}}=\frac{1}{\sqrt{2.4^2-1}}=\frac{1}{\sqrt{4.76}}=\frac{1}{2.1817}=\boxed{0.458\ \text{rad}^{-1}} .
$$

### (v) Relative error of Ackeret's method and its dependence on η [4 marks]

At $\eta=9^\circ=0.15708$ rad Ackeret's theory gives

$$
C_{L,\text{Ack}}=\frac{0.15708}{2.1817}=0.07200,
$$

and the relative error against the shock-expansion value of part (iii) is

$$
\varepsilon=\frac{C_{L,\text{Ack}}-C_{L,\text{SE}}}{C_{L,\text{SE}}}=\frac{0.07200-0.07284}{0.07284}=\boxed{-1.16\,\%} .
$$

If $C_{L,\text{SE}}$ is taken without the $\cos\eta$ factor (0.07375), the error is $-2.37\,\%$.

The small size of this error hides much larger errors in the separate surface pressures. Ackeret gives $p_l=60+241.92\times0.1440=94.84$ kPa against $103.69$ kPa, and $p_u=60-34.84=25.16$ kPa against $32.32$ kPa, each about 7–9 kPa too low. Both shock and expansion pressures expand in powers of the turning angle as

$$
C_p=C_1\theta+C_2\theta^2+\dots,
\qquad
C_1=\frac{2}{\sqrt{M_\infty^2-1}},
\qquad
C_2=\frac{(\gamma+1)M_\infty^4-4M_\infty^2+4}{2\left(M_\infty^2-1\right)^2},
$$

which is Busemann's second-order theory. Ackeret keeps only the $C_1$ term. The $C_2\theta^2$ term has the same sign for $\theta=+\eta$ and $\theta=-\eta$, so it raises the pressure on both faces by the same amount and cancels in $C_{p,l}-C_{p,u}$. At $M_\infty=2.4$,

$$
C_1=\frac{2}{2.1817}=0.9167,
\qquad
C_2=\frac{2.4\times33.178-23.04+4}{2\times4.76^2}=\frac{60.586}{45.315}=1.337,
$$

so at $\eta=0.15708$ rad the second-order term is $C_2\eta^2=1.337\times0.02467=0.0330$, which is $C_2\eta/C_1=23\,\%$ of the first-order term on each face. The shock-expansion values $C_{p,l}=0.1806$ and $C_{p,u}=-0.1144$ match $\pm0.1440+0.0330$ to within 0.004.

Because the second-order terms cancel, the lift error starts at third order. The normal-force coefficient carries an error of order $\eta^3$, a relative error of order $\eta^2$, and the $\cos\eta=1-\eta^2/2+\dots$ projection adds another relative term of order $\eta^2$ of the opposite sign. The two together give a relative error close to $-0.47\eta^2$ (with $\eta$ in radians), as the exact calculation shows.

| $\eta$ (°) | 2 | 4 | 6 | 9 | 12 | 15 | 20 |
|---|---:|---:|---:|---:|---:|---:|---:|
| $C_{L,\text{SE}}$ | 0.01601 | 0.03208 | 0.04826 | 0.07284 | 0.09793 | 0.12365 | 0.16846 |
| $C_{L,\text{Ack}}$ | 0.01600 | 0.03200 | 0.04800 | 0.07200 | 0.09600 | 0.12000 | 0.15999 |
| $\varepsilon$ (%) | $-0.06$ | $-0.24$ | $-0.53$ | $-1.16$ | $-1.97$ | $-2.96$ | $-5.02$ |
| $\varepsilon/\eta^2$ (rad⁻²) | $-0.50$ | $-0.50$ | $-0.49$ | $-0.47$ | $-0.45$ | $-0.43$ | $-0.41$ |

Ackeret always underestimates $C_L$ here, and the error roughly quadruples each time $\eta$ doubles. The shock-expansion solution itself ends when the lower shock detaches, at $\eta=\theta_{\max}(2.4)=28.7^\circ$.

> [!warning] A small lift error does not mean small perturbations
> At $\eta=9^\circ$ Ackeret's surface pressure coefficients are 20–26 % off ($0.1440$ against $0.1806$ and $-0.1440$ against $-0.1144$; the ratio $C_2\eta/C_1=0.23$), so the flow is not in the small-disturbance regime in any strict sense. The lift comes out within 1.2 % only because the leading nonlinear error is the same on both faces and cancels. Drag, moment about a point other than the flap, or a single-surface pressure do not benefit from this cancellation.

---

## Q2. Prandtl–Glauert derivation and subsonic flap effectiveness (16 marks)

> (i) Starting from $(1 - M_\infty^2)\dfrac{\partial^2\phi}{\partial x^2} + \dfrac{\partial^2\phi}{\partial y^2} = 0$, derive $C_p = \dfrac{C_{p0}}{\sqrt{1-M_\infty^2}}$, stating all assumptions and explaining how the relation is useful. [10]
> (ii) Given incompressible flap effectiveness $(\mathrm{d}C_L/\mathrm{d}\eta)_0 = 3.826$, estimate $\mathrm{d}C_L/\mathrm{d}\eta$ at $M_\infty = 0.75$. [4]
> (iii) Discuss why trailing-edge flaps are less effective in supersonic flow than subsonic flow. [2]

### (i) Derivation of the Prandtl–Glauert rule [10 marks]

The working follows [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]]. The starting equation already contains these assumptions.

- steady, two-dimensional, inviscid, irrotational and isentropic flow of a perfect gas, so a perturbation potential $\phi$ exists with $u'=\partial\phi/\partial x$ and $v'=\partial\phi/\partial y$;
- small perturbations about a uniform stream, $|u'|,|v'|\ll U_\infty$, which needs a thin aerofoil at small incidence;
- $M_\infty$ subsonic and not close to 1, so that the neglected nonlinear terms stay small (no transonic flow);
- the linearised pressure coefficient $C_p=-2u'/U_\infty$ and the tangency condition applied on the axis, $\partial\phi/\partial y=U_\infty f'(x)$ at $y=0$ for a surface $y=f(x)$.

For $M_\infty<1$ write $\beta=\sqrt{1-M_\infty^2}$, which is real and positive (it is not the shock angle here). The equation becomes

$$
\beta^2\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0 .
$$

Define new variables

$$
\phi_0=\beta\phi,
\qquad
x_0=x,
\qquad
y_0=\beta y .
$$

Since $x_0=x$,

$$
\frac{\partial^2\phi}{\partial x^2}=\frac{\partial^2}{\partial x_0^2}\left(\frac{\phi_0}{\beta}\right)=\frac1\beta\frac{\partial^2\phi_0}{\partial x_0^2} .
$$

Since $y_0=\beta y$, the chain rule gives $\partial/\partial y=\beta\,\partial/\partial y_0$, and applying it twice,

$$
\frac{\partial^2\phi}{\partial y^2}=\beta^2\frac{\partial^2}{\partial y_0^2}\left(\frac{\phi_0}{\beta}\right)=\beta\frac{\partial^2\phi_0}{\partial y_0^2} .
$$

Substituting both into the potential equation,

$$
\beta^2\cdot\frac1\beta\frac{\partial^2\phi_0}{\partial x_0^2}+\beta\frac{\partial^2\phi_0}{\partial y_0^2}=0,
$$

$$
\beta\left(\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\partial^2\phi_0}{\partial y_0^2}\right)=0 .
$$

$\beta\neq0$, so

$$
\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\partial^2\phi_0}{\partial y_0^2}=0,
$$

which is Laplace's equation: $\phi_0$ is an incompressible potential flow in the $(x_0,y_0)$ plane.

The boundary condition shows which incompressible flow. On the axis,

$$
\frac{\partial\phi}{\partial y}=\frac{\partial(\phi_0/\beta)}{\partial(y_0/\beta)}=\frac{\partial\phi_0}{\partial y_0},
$$

so $\partial\phi_0/\partial y_0=U_\infty f'(x_0)$ at $y_0=0$. The incompressible problem has the same surface slope at every $x$, which means the same aerofoil.

The compressible pressure coefficient, written in the new variables, is

$$
C_p=-\frac{2}{U_\infty}\frac{\partial\phi}{\partial x}=-\frac{2}{U_\infty}\frac{\partial(\phi_0/\beta)}{\partial x_0}=\frac1\beta\left(-\frac{2}{U_\infty}\frac{\partial\phi_0}{\partial x_0}\right).
$$

The bracket is the incompressible pressure coefficient $C_{p0}$ of the same aerofoil at the same point, so

$$
\boxed{C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}}} . \qquad\blacksquare
$$

The rule is useful because one incompressible solution, from thin-aerofoil theory, a panel method or a low-speed wind-tunnel test, gives the pressure distribution at any subsonic Mach number up to about 0.7–0.8 by a single division. The lift and moment coefficients are integrals of $C_p$ over the same chord, so they scale by the same factor, $C_L=C_{L0}/\sqrt{1-M_\infty^2}$. Combined with the isentropic $C_{p,\text{cr}}$ curve, the rule also estimates the critical Mach number.

### (ii) Flap effectiveness at M = 0.75 [4 marks]

$C_L$ is the chordwise integral of $C_{p,l}-C_{p,u}$, and every $C_p$ scales by $1/\sqrt{1-M_\infty^2}$, so $C_L$ and its derivative with respect to $\eta$ scale by the same factor.

$$
\left(\frac{\mathrm dC_L}{\mathrm d\eta}\right)_{M_\infty=0.75}=\frac{(\mathrm dC_L/\mathrm d\eta)_0}{\sqrt{1-M_\infty^2}}=\frac{3.826}{\sqrt{1-0.75^2}}=\frac{3.826}{\sqrt{0.4375}}=\frac{3.826}{0.66144}=\boxed{5.78\ \text{rad}^{-1}} .
$$

### (iii) Why trailing-edge flaps are less effective in supersonic flow [2 marks]

In subsonic flow the potential equation is elliptic: a disturbance at the flap is felt everywhere, including upstream. Deflecting the flap moves the rear stagnation point, and the Kutta condition then changes the circulation of the whole aerofoil, so the loading changes over the entire chord, not only on the flap. That is why the incompressible effectiveness is 3.83 per radian and rises to 5.78 at $M_\infty=0.75$. In supersonic flow the equation is hyperbolic and disturbances travel only downstream, inside the Mach lines from the hinge. The forward three-quarters of the plate never feels the flap, so only the flap itself is loaded, and the effectiveness is $0.458$ per radian at $M_\infty=2.4$, about one-eighth of the incompressible value.

---

## Q3. Minimum-length supersonic nozzle by Method of Characteristics (20 marks)

> A symmetric 2D C-D minimum-length nozzle accelerates air to $M_e = 2.2$ with $\theta_{\max} = \nu(M_e)/2$. Starting characteristic lines at point $0 = (0,1)$ have flow angles $\theta_{\max}/2$ (line 0-1-2-4) and $\theta_{\max}$ (line 0-2-3-5), with centreline at $y=0$.
> (i) Find the Riemann invariants $R^+$ and $R^-$ at point 2. [4]
> (ii) Find $\theta_2$ and $M_2$ at point 2. [4]
> (iii) Compute the coordinates $(x,y)$ of points 1 and 2. [10]
> (iv) Explain how to extend this prototype calculation to obtain the full nozzle geometry. [2]

![[at_pp_201920_q3_moc_nozzle.png|820]]

### (i) Riemann invariants at point 2 [4 marks]

The working uses the course invariants ([[SESA3029 W05a - Method of Characteristics|W05a]])

$$
R^+=\nu-\theta\ \text{ constant along } C^+,
\qquad
R^-=\nu+\theta\ \text{ constant along } C^- .
$$

The IFT row $M=2.20$ gives $\nu(M_e)=31.7325^\circ$, so ([[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]])

$$
\theta_{\max}=\frac{\nu(M_e)}{2}=\frac{31.7325^\circ}{2}=15.866^\circ .
$$

The flow approaching the corner at 0 is sonic and parallel ($\nu=0$, $\theta=0$), and every $C^+$ line crossing the corner fan starts in that flow, so throughout the fan

$$
R^+=\nu-\theta=0,
\qquad\text{i.e.}\qquad
\nu=\theta .
$$

Along the first ray, 0–1, the flow angle is $\theta_{\max}/2=7.933^\circ$, so $\nu=7.933^\circ$ and

$$
R^-_{01}=\nu+\theta=7.933^\circ+7.933^\circ=15.866^\circ .
$$

Point 1 is on the centreline, where symmetry forces $\theta_1=0$. It lies on that $C^-$ ray, so

$$
\nu_1=R^-_{01}-\theta_1=15.866^\circ,
\qquad
R^+_1=\nu_1-\theta_1=15.866^\circ .
$$

Along the second ray, 0–2, $\theta=\theta_{\max}=15.866^\circ$ and $\nu=15.866^\circ$, so

$$
R^-_{02}=15.866^\circ+15.866^\circ=31.733^\circ .
$$

Point 2 lies on the $C^+$ line from point 1 and on the $C^-$ ray 0–2, so it carries both invariants.

$$
R^+_2=R^+_1=\boxed{15.87^\circ},
\qquad
R^-_2=R^-_{02}=\boxed{31.73^\circ} .
$$

In Anderson's notation, $K^-=\theta+\nu=31.73^\circ$ and $K^+=\theta-\nu=-15.87^\circ$.

### (ii) Flow angle and Mach number at point 2 [4 marks]

Adding and subtracting $\nu_2-\theta_2=R^+_2$ and $\nu_2+\theta_2=R^-_2$,

$$
\theta_2=\frac{R^-_2-R^+_2}{2}=\frac{31.733^\circ-15.866^\circ}{2}=\boxed{7.93^\circ},
$$

$$
\nu_2=\frac{R^+_2+R^-_2}{2}=\frac{15.866^\circ+31.733^\circ}{2}=23.799^\circ .
$$

The IFT rows $M=1.90$ ($\nu=23.5861^\circ$) and $M=1.92$ ($24.1506^\circ$) bracket $\nu_2$.

$$
M_2=1.90+0.02\times\frac{23.7994-23.5861}{24.1506-23.5861}=1.90+0.02\times\frac{0.2133}{0.5645}=1.90+0.02\times0.378=\boxed{1.908} .
$$

The exact inverse of $\nu$ gives $1.9075$.

### (iii) Coordinates of points 1 and 2 [10 marks]

#### States at each point

The Mach numbers at the other points come from the IFT in the same way. For $\nu=7.933^\circ$ the rows $1.36$ ($7.8435^\circ$) and $1.38$ ($8.4130^\circ$) give

$$
M=1.36+0.02\times\frac{7.9331-7.8435}{8.4130-7.8435}=1.36+0.02\times0.157=1.3631,
$$

and for $\nu=15.866^\circ$ the rows $1.62$ ($15.4518^\circ$) and $1.64$ ($16.0427^\circ$) give

$$
M=1.62+0.02\times\frac{15.8662-15.4518}{16.0427-15.4518}=1.62+0.02\times0.701=1.6340 .
$$

The Mach angle is $\mu=\arcsin(1/M)$, and the characteristic slopes are $\theta+\mu$ for $C^+$ and $\theta-\mu$ for $C^-$.

| Point | $\theta$ (°) | $\nu$ (°) | $R^+$ (°) | $R^-$ (°) | $M$ | $\mu$ (°) | $\theta+\mu$ (°) | $\theta-\mu$ (°) |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 0, ray 0–1 | 7.933 | 7.933 | 0 | 15.866 | 1.363 | 47.188 | 55.121 | $-39.255$ |
| 0, ray 0–2 | 15.866 | 15.866 | 0 | 31.733 | 1.634 | 37.733 | 53.599 | $-21.867$ |
| 1 | 0 | 15.866 | 15.866 | 15.866 | 1.634 | 37.733 | 37.733 | $-37.733$ |
| 2 | 7.933 | 23.799 | 15.866 | 31.733 | 1.908 | 31.617 | 39.550 | $-23.684$ |

#### Point 1

Point 1 is where the $C^-$ ray 0–1 reaches the centreline $y_1=0$. The formula-sheet slope averages the two ends of the segment.

$$
\alpha_{01}=\tfrac12\left[(\theta-\mu)_0+(\theta-\mu)_1\right]=\tfrac12\left[-39.255^\circ-37.733^\circ\right]=-38.494^\circ .
$$

Along this line $y_1=y_0+(x_1-x_0)\tan\alpha_{01}$, so

$$
x_1=x_0+\frac{y_1-y_0}{\tan\alpha_{01}}=0+\frac{0-1}{\tan(-38.494^\circ)}=\frac{-1}{-0.79527}=\boxed{1.257},
\qquad
y_1=\boxed{0} .
$$

#### Point 2

Point 2 is the intersection of the $C^+$ line from point 1 (point A on the formula sheet) and the $C^-$ ray from point 0 (point B). The averaged slopes are

$$
\alpha_{12}=\tfrac12\left[(\theta+\mu)_1+(\theta+\mu)_2\right]=\tfrac12\left[37.733^\circ+39.550^\circ\right]=38.642^\circ,
\qquad
\tan\alpha_{12}=0.79948,
$$

$$
\alpha_{02}=\tfrac12\left[(\theta-\mu)_0+(\theta-\mu)_2\right]=\tfrac12\left[-21.867^\circ-23.684^\circ\right]=-22.775^\circ,
\qquad
\tan\alpha_{02}=-0.41985 .
$$

The two straight segments are

$$
y=y_1+(x-x_1)\tan\alpha_{12},
\qquad
y=y_0+(x-x_0)\tan\alpha_{02} .
$$

Setting them equal and solving for $x$ gives the formula-sheet expression

$$
x_2=\frac{x_0\tan\alpha_{02}-x_1\tan\alpha_{12}+y_1-y_0}{\tan\alpha_{02}-\tan\alpha_{12}}
$$

$$
=\frac{0\times(-0.41985)-1.2574\times0.79948+0-1}{-0.41985-0.79948}
$$

$$
=\frac{-1.00527-1}{-1.21933}=\frac{-2.00527}{-1.21933}=\boxed{1.645} .
$$

Then

$$
y_2=y_1+(x_2-x_1)\tan\alpha_{12}=0+(1.6446-1.2574)\times0.79948=0.3872\times0.79948=\boxed{0.310} .
$$

The $C^-$ line gives the same height, $y_2=1+1.6446\times(-0.41985)=0.3095$.

> [!check] Exit height from the full two-wave network
> Continuing the same unit processes to the centreline point 3 ($\nu_3=2\theta_{\max}$, $M_3=2.2$), the wall point 4 ($\theta_4=7.93^\circ$) and the exit wall point 5 ($\theta_5=0$) gives an exit half-height of about 1.89. The exact value for $M_e=2.2$ is $A_e/A^*=2.005$. The difference, about 6 %, is the error of a network with only two waves; more waves bring the exit height towards 2.005.

### (iv) Extending to the full nozzle [2 marks]

The corner fan is split into $N$ $C^-$ rays instead of two, at $\theta_k=k\,\theta_{\max}/N$ for $k=1,\dots,N$, each with $\nu_k=\theta_k$. Each ray is followed to the centreline, where $\theta=0$ fixes the reflected $C^+$ line, and the interior points where the rays cross are found with the same unit process as point 2. The wall is then built from point 0 outwards: each $C^+$ line leaving the last interior point on its row meets the wall, the wall angle there is set to the local flow angle so that the wave is cancelled and nothing reflects, and each wall segment is drawn at the average of the wall angles at its two ends. The last $C^+$ line, from the centreline point where $\nu=\nu(M_e)$, ends at the exit, where the wall is parallel to the axis.

---

## Q4. High-temperature block convection, 2D finite difference and grid convergence (32 marks)

> [!warning] Heat transfer (Weeks 9–12)
> This question uses material from Weeks 9–12, which have not yet been lectured. Check the notation, the correlations and the node numbering against those lectures when they are written up.

> (i) Define $\text{Nu}, \text{St}, \text{Pr}, \text{Re}$ and prove $\text{Nu} = \text{St}\,\text{Re}\,\text{Pr}$. [4]
> (ii) Tangential air ($\text{Pr}=0.71$, $u_\infty=40\ \text{m/s}$, $T_\infty=1200\ \text{K}$, $p_\infty=150\ \text{kPa}$) flows over a block ($L=80\ \text{cm}$, $w=20\ \text{cm}$, $d=10\ \text{cm}$) with underside at $300\ \text{K}$ and $\mu/\mu_{\text{ref}} = (T/T_{\text{ref}})^{0.75}$ ($\mu_{\text{ref}} = 1.8\times 10^{-5}\ \text{N s/m}^2$, $T_{\text{ref}} = 288\ \text{K}$). Confirm $\text{Re}_L < 3\times 10^5$ (laminar). [4]
> (iii) Uniform convective heat transfer $\dot{Q}=1400\ \text{W}$ enters the top face; the right face is adiabatic and all other boundaries are $300\ \text{K}$. Using the $5\times 3$ grid in Figure Q.4: (a) find $T_1, T_2, T_7$ [8]; (b) construct FD stencils at nodes 5 and 11, find $T_5, T_{11}$ given $T_4=879.94\ \text{K}$, $T_8=553.94\ \text{K}$, $T_{10}=747.36\ \text{K}$, and verify $T_8$ with the node-8 stencil [10].
> (iv) Grid refinement gives $430.1716\ \text{K}$ ($33\times 17$), $429.2628\ \text{K}$ ($65\times 33$), and $429.0301\ \text{K}$ ($129\times 65$). Confirm $p\approx 2$ and estimate the grid-independent temperature. [6]

![[at_pp_201920_q4_fd_block.png|820]]

### (i) Dimensionless groups [4 marks]

With heat transfer coefficient $h$, length $L$, fluid conductivity $k$, specific heat $c_p$, density $\rho$, viscosity $\mu$ and free-stream speed $u_\infty$, the four groups are

$$
\text{Nu}=\frac{hL}{k},
\qquad
\text{St}=\frac{h}{\rho c_pu_\infty},
\qquad
\text{Pr}=\frac{\mu c_p}{k},
\qquad
\text{Re}=\frac{\rho u_\infty L}{\mu}.
$$

The Nusselt number compares convective with conductive heat transfer across the fluid, the Stanton number compares the heat transferred with the heat carried by the flow, the Prandtl number compares momentum with thermal diffusivity, and the Reynolds number compares inertial with viscous forces. Multiplying the last three,

$$
\text{St}\,\text{Re}\,\text{Pr}=\frac{h}{\rho c_pu_\infty}\cdot\frac{\rho u_\infty L}{\mu}\cdot\frac{\mu c_p}{k} .
$$

$\rho$, $u_\infty$, $\mu$ and $c_p$ each appear once above and once below the line and cancel.

$$
\text{St}\,\text{Re}\,\text{Pr}=\frac{hL}{k}=\text{Nu} . \qquad\blacksquare
$$

### (ii) Reynolds number at the end of the surface [4 marks]

The air properties at $T_\infty=1200$ K and $p_\infty=150$ kPa are

$$
\rho=\frac{p_\infty}{RT_\infty}=\frac{150\times10^3}{287\times1200}=0.43554\ \text{kg/m}^3,
$$

$$
\mu=\mu_{\text{ref}}\left(\frac{T_\infty}{T_{\text{ref}}}\right)^{0.75}=1.8\times10^{-5}\left(\frac{1200}{288}\right)^{0.75}=1.8\times10^{-5}\times2.9164=5.2495\times10^{-5}\ \text{N s/m}^2 .
$$

At the end of the surface, $x=L=0.80$ m,

$$
\text{Re}_L=\frac{\rho u_\infty L}{\mu}=\frac{0.43554\times40\times0.80}{5.2495\times10^{-5}}=\frac{13.937}{5.2495\times10^{-5}}=\boxed{2.655\times10^5}<3\times10^5,
$$

so the boundary layer stays laminar over the whole top surface.

### (iii) Surface temperatures and the FD check [18 marks]

#### (a) Surface temperatures at nodes 1, 2 and 7 [8 marks]

The uniform flux into the top face and the air conductivity are

$$
q''=\frac{\dot Q}{Lw}=\frac{1400}{0.80\times0.20}=8750\ \text{W/m}^2,
$$

$$
k=\frac{\mu c_p}{\text{Pr}}=\frac{5.2495\times10^{-5}\times1004.5}{0.71}=0.07427\ \text{W/(m K)}.
$$

Heat flows from the hot air into the block, $q''=h_x(T_\infty-T_s)$, and the formula sheet (p. 8) gives the laminar uniform-heat-flux correlation, so

$$
\text{Nu}_x=0.453\,\text{Re}_x^{1/2}\text{Pr}^{1/3},
\qquad
h_x=\frac{\text{Nu}_x\,k}{x},
\qquad
T_s(x)=T_\infty-\frac{q''}{h_x}.
$$

Here $\text{Pr}^{1/3}=0.71^{1/3}=0.89211$ and $\text{Re}_x=\text{Re}_L\,x/L$.

At node 1, the leading edge, the boundary layer has zero thickness and $h_x\to\infty$, so

$$
T_1=T_\infty=\boxed{1200\ \text{K}} .
$$

At node 2, $x=L/4=0.20$ m,

$$
\text{Re}_x=\tfrac14\times2.6550\times10^5=66\,375,
\qquad
\text{Nu}_x=0.453\times66\,375^{1/2}\times0.89211=0.453\times257.63\times0.89211=104.12,
$$

$$
h_x=\frac{104.12\times0.07427}{0.20}=38.66\ \text{W/(m}^2\text{ K)},
\qquad
T_2=1200-\frac{8750}{38.66}=1200-226.3=\boxed{973.7\ \text{K}} .
$$

At node 7, $x=3L/4=0.60$ m,

$$
\text{Re}_x=\tfrac34\times2.6550\times10^5=199\,125,
\qquad
\text{Nu}_x=0.453\times446.23\times0.89211=180.34,
$$

$$
h_x=\frac{180.34\times0.07427}{0.60}=22.32\ \text{W/(m}^2\text{ K)},
\qquad
T_7=1200-\frac{8750}{22.32}=1200-392.0=\boxed{808.0\ \text{K}} .
$$

The same steps at $x=0.40$ m and $0.80$ m give $879.94$ K and $747.37$ K, which reproduce the program values $T_4=879.94$ K and $T_{10}=747.36$ K, so the program uses the same correlation and property values.

#### (b) Stencils at nodes 5 and 11, and the check at node 8 [10 marks]

The grid spacings are

$$
\Delta x=\frac{L}{4}=0.20\ \text{m},
\qquad
\Delta y=\frac{d}{2}=0.05\ \text{m}.
$$

"Equidistant" means uniform in each direction, not $\Delta x=\Delta y$, so the stencil keeps both spacings. Central differences in $\nabla^2T=0$ at node P with neighbours W, E, S, N give

$$
\frac{T_W-2T_P+T_E}{\Delta x^2}+\frac{T_S-2T_P+T_N}{\Delta y^2}=0 .
$$

Multiply by $\Delta y^2$ and write $s=(\Delta y/\Delta x)^2$.

$$
s\left(T_W-2T_P+T_E\right)+T_S-2T_P+T_N=0 .
$$

Collect the $T_P$ terms.

$$
T_P=\frac{s\left(T_W+T_E\right)+T_N+T_S}{2(1+s)} .
$$

Here $s=(0.05/0.20)^2=1/16$. Multiplying top and bottom by 16,

$$
T_P=\frac{T_W+T_E+16\left(T_N+T_S\right)}{34} .
$$

Node 5 has W $=T_3=300$ K (on the tapered underside), E $=T_8=553.94$ K, N $=T_4=879.94$ K and S $=T_6=300$ K.

$$
T_5=\frac{300+553.94+16\,(879.94+300)}{34}=\frac{853.94+18\,879.04}{34}=\frac{19\,732.98}{34}=\boxed{580.38\ \text{K}} .
$$

Node 11 sits on the adiabatic right face. $\partial T/\partial x=0$ is represented by a mirror node outside the face with the value of the node inside, so E $=$ W $=T_8$. With N $=T_{10}=747.36$ K and S $=T_{12}=300$ K,

$$
T_{11}=\frac{2\times553.94+16\,(747.36+300)}{34}=\frac{1107.88+16\,757.76}{34}=\frac{17\,865.64}{34}=\boxed{525.46\ \text{K}} .
$$

Node 8 has W $=T_5$, E $=T_{11}$, N $=T_7=808.01$ K and S $=T_9=300$ K. Inserting the values just found,

$$
T_8=\frac{580.38+525.46+16\,(808.01+300)}{34}=\frac{1105.84+17\,728.16}{34}=\frac{18\,834.00}{34}=\boxed{553.94\ \text{K}},
$$

which matches the program's value, so the program's stencils are verified.

The equal-spacing stencil $T_P=\tfrac14(T_W+T_E+T_N+T_S)$ with the same given values gives $T_5=508.5$ K and $T_{11}=538.8$ K, and then $T_8=538.8$ K instead of 553.94 K. The match therefore confirms that the program uses the unequal spacings.

### (iv) Order of accuracy and extrapolation [6 marks]

Each grid halves the spacing of the one before (32, 64 and 128 intervals along the length), so the refinement ratio is 2. Call the results on spacings $4h$, $2h$ and $h$

$$
T_{4h}=430.1716\ \text{K},
\qquad
T_{2h}=429.2628\ \text{K},
\qquad
T_h=429.0301\ \text{K}.
$$

For a method of order $p$ the error is $Ch^p$, so successive differences shrink by $2^p$.

$$
\frac{T_{4h}-T_{2h}}{T_{2h}-T_h}=2^p .
$$

Taking logarithms,

$$
p=\frac{\ln\left[(T_{4h}-T_{2h})/(T_{2h}-T_h)\right]}{\ln2}=\frac{\ln(0.9088/0.2327)}{\ln2}=\frac{\ln3.9055}{0.69315}=\frac{1.3624}{0.69315}=\boxed{1.97\approx2} .
$$

With $p=2$ the remaining error on the finest grid is $(T_h-T_{2h})/(2^2-1)$, so the Richardson estimate is

$$
T_{\text{exact}}\approx T_h+\frac{T_h-T_{2h}}{2^2-1}=429.0301+\frac{429.0301-429.2628}{3}=429.0301-0.0776=\boxed{428.95\ \text{K}} .
$$

---

## Paper slips and ambiguities

- Q1: the text gives $M_\infty=2.4$, and part (iv)'s $0.458=1/\sqrt{2.4^2-1}$ confirms it, but Figure Q.1 prints $M_\infty=2.9$ (which would give $1/\sqrt{2.9^2-1}=0.367$). These solutions use 2.4 throughout.
- Q1(iii) does not say whether to project the flap force onto the lift direction. With the $\cos\eta$ factor $C_L=0.0728$; without it $C_L=0.0737$. Ackeret's linear theory has no such factor.
- Q4(iii) calls the $5\times3$ grid "equidistant". The spacings are uniform in each direction ($\Delta x=20$ cm, $\Delta y=5$ cm), not equal to each other, and only the unequal-spacing stencil reproduces the program's $T_8=553.94$ K.
- Corrections to the earlier draft of these solutions. The draft wrote the Riemann invariants in Anderson's form ($R^+=\theta-\nu=-15.87^\circ$); with the course convention $R^+=\nu-\theta$ the value at point 2 is $+15.87^\circ$, and $\theta_2$, $M_2$ and the coordinates are unchanged. The draft's check that the two-wave network gives an exit half-height equal to $A_e/A^*=2.005$ was wrong: it gives about 1.89. In Q1(v) the draft said the second-order terms "have opposite signs and partly cancel"; they have the same sign on both faces and cancel completely in the lift. It also explained the small error by $M_\infty\sin\eta\approx0.375<1$, which is not a valid small-disturbance criterion; the error is small because of that cancellation, while each surface $C_p$ is 20–26 % off. The detachment angle is $\theta_{\max}(2.4)=28.7^\circ$, not $28.6^\circ$. The NST $p_2/p_1$ at $M_{n1}=1.28$ is $1.7448$, not $1.7450$.
