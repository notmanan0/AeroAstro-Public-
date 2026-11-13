---
title: "SESA3029 Past Paper 2017-18 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, shock-expansion, ackeret, prandtl-glauert, method-of-characteristics, heat-transfer, cfd, euler-equations, richardson-extrapolation]
paper: "2017-18"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]", "[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-201718-01-SESA3029W1.pdf"]
---

# SESA3029 Past Paper 2017-18 - Solutions

> [!abstract] Paper info
> 2017-18 Semester 1 examination (SESA3029W1, 2 hours, formula sheet on pp. 8–9). All five questions are compulsory, 100 marks in total (36 + 16 + 16 + 16 + 16). Front-page constants: $R=287\ \text{J/(kg K)}$, $c_p=1005\ \text{J/(kg K)}$, $\gamma=1.4$, $\text{Pr}=0.7$, $\rho=1.225\ \text{kg/m}^3$, $\mu=1.79\times 10^{-5}\ \text{N s/m}^2$. Question 4 is heat transfer and re-entry radiation (Weeks 9–12, not yet lectured). Table values are the course IFT and NST at 4 d.p., and every number below was rechecked in Python against the exact relations.

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 36 | Wind-tunnel nozzle at $M=2.5$ and a flat plate at $\alpha=5^\circ$: $A/A^*$ and stagnation state, shock-expansion against Ackeret, $\alpha_{\max}$, transonic and supersonic aerofoil design | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves\|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method\|W03]], [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow\|W04]], [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils\|W07a]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils\|W07c]] |
| 2 | 16 | Prandtl–Glauert reduction to Laplace's equation and $C_p=C_{p0}/\sqrt{1-M_\infty^2}$; $C_{p,\min,0}$ from $M_{\text{crit}}=0.45$ | [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation\|W07b]] |
| 3 | 16 | Mach 3 minimum-length nozzle: interior point 8 from points 4 and 7; the simple region | [[SESA3029 W05a - Method of Characteristics\|W05a]], [[SESA3029 W05b - Minimum-Length Nozzle Design\|W05b]] |
| 4 | 16 | Laminar flat-plate heat transfer (plate width for 20 W) and lunar re-entry radiation; heat transfer (Weeks 9–12, not yet lectured) | not yet lectured |
| 5 | 16 | 1D isentropic Euler flux Jacobian and characteristic speeds $u\pm a$; Richardson extrapolation | [[SESA3029 W05a - Method of Characteristics\|W05a]] |

---

## Q1. Supersonic wind tunnel and flat plate at incidence (36 marks)

> A converging-diverging nozzle delivers air into a test section with uniform $M=2.5$ flow at $T=160\ \text{K}$ and $p=20\ \text{kN/m}^2$. A flat plate is inserted at angle of attack $\alpha = 5^\circ$ (Figure Q.1).
> (i) Find the nozzle area ratio and upstream stagnation $p_0, T_0, \rho_0$. [6]
> (ii) Use shock-expansion theory to find $p$ and $M$ on the upper and lower sides. [10]
> (iii) Find $p$ on the upper and lower sides by Ackeret's theory. [8]
> (iv) Find $\alpha_{\max}$ for an attached oblique shock and sketch the wave patterns for $\alpha < \alpha_{\max}$ and $\alpha > \alpha_{\max}$. [6]
> (v) Discuss design requirements for efficient aerofoils in (a) transonic and (b) supersonic flight regimes. [6]

### (i) Nozzle area ratio and stagnation properties [6 marks]

The nozzle flow is steady, one-dimensional and isentropic, with $\gamma=1.4$ and a sonic throat ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]). The temperature ratio at $M=2.5$ is

$$
\frac{T_0}{T}=1+\frac{\gamma-1}{2}M^2=1+0.2(2.5^2)=1+1.25=2.25 .
$$

The area ratio follows from the area–Mach relation,

$$
\frac{A}{A^*}=\frac{1}{M}\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{\frac{\gamma+1}{2(\gamma-1)}}
$$

$$
=\frac{1}{2.5}\left[\frac{2}{2.4}(2.25)\right]^{3}
$$

$$
=0.4\,(1.875)^3=0.4(6.5918)=\boxed{2.637},
$$

which is the IFT entry at $M=2.50$ (2.6367). The stagnation temperature is

$$
T_0=2.25\,T=2.25(160)=\boxed{360.0\ \text{K}} .
$$

The stagnation pressure uses the isentropic exponent $\gamma/(\gamma-1)=3.5$,

$$
p_0=p\left(\frac{T_0}{T}\right)^{3.5}=20\,(2.25)^{3.5}=20(17.086)=\boxed{341.7\ \text{kPa}} .
$$

Reading $p/p_0=0.0585$ from the IFT instead gives $20/0.0585=341.9$ kPa, which differs only through the rounding of the table entry. The stagnation density comes from the equation of state at the stagnation condition,

$$
\rho_0=\frac{p_0}{RT_0}=\frac{341.7\times10^3}{287(360.0)}=\boxed{3.307\ \text{kg/m}^3} .
$$

### (ii) Upper and lower conditions by shock-expansion theory [10 marks]

At a nose-up incidence of $5^\circ$ the upper surface turns away from the stream and the lower surface turns into it, each by $5^\circ$ ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]]). The upper side therefore sees a centred Prandtl–Meyer expansion at the leading edge, and the lower side an attached oblique shock.

#### Upper surface: Prandtl–Meyer expansion through 5°

The IFT at $M_\infty=2.50$ gives $\nu_\infty=39.1236^\circ$ and $p/p_0=0.0585$. An expansion through $5^\circ$ raises $\nu$ by $5^\circ$,

$$
\nu_u=\nu_\infty+\alpha=39.1236^\circ+5^\circ=44.1236^\circ .
$$

This lies between two IFT rows.

| $M$ | $\nu$ (deg) | $p/p_0$ |
|---:|---:|---:|
| 2.72 | 44.0529 | 0.0417 |
| 2.74 | 44.4810 | 0.0404 |

The interpolation fraction is

$$
f=\frac{44.1236-44.0529}{44.4810-44.0529}=\frac{0.0707}{0.4281}=0.1651,
$$

so

$$
M_u=2.72+0.02(0.1651)=\boxed{2.723},
$$

$$
\left(\frac{p}{p_0}\right)_u=0.0417+0.1651(0.0404-0.0417)=0.0417-0.000215=0.04149 .
$$

The expansion is isentropic, so $p_0$ is unchanged and

$$
p_u=0.04149\times341.7=\boxed{14.18\ \text{kPa}} .
$$

#### Lower surface: oblique shock with θ = 5°

The shock angle comes from the $\theta$–$\beta$–$M$ relation ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]]),

$$
\tan\theta=2\cot\beta\,\frac{M_1^2\sin^2\beta-1}{M_1^2(\gamma+\cos2\beta)+2},
$$

with $M_1=2.5$ and $\theta=5^\circ$ ($\tan5^\circ=0.08749$). The weak solution lies a little above the Mach angle ($23.58^\circ$). Evaluating the right-hand side at two trial angles brackets it.

| $\beta$ | $M_1^2\sin^2\beta-1$ | $M_1^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ |
|---:|---:|---:|---:|---:|---:|
| $27^\circ$ | 0.28817 | 14.42366 | 3.92522 | 0.07842 | $4.4841^\circ$ |
| $28^\circ$ | 0.37752 | 14.24496 | 3.76145 | 0.09969 | $5.6928^\circ$ |

Interpolating linearly to $\theta=5^\circ$,

$$
\beta=27^\circ+1^\circ\times\frac{5-4.4841}{5.6928-4.4841}=27^\circ+\frac{0.5159}{1.2087}=27.43^\circ .
$$

A root-finder on the full relation gives $\beta=27.4227^\circ$, which is used below. The normal Mach number ahead of the shock is

$$
M_{n1}=M_1\sin\beta=2.5\sin27.4227^\circ=2.5(0.46055)=1.1514 .
$$

This lies between two NST rows.

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ |
|---:|---:|---:|
| 1.14 | 0.8820 | 1.3495 |
| 1.16 | 0.8682 | 1.4032 |

With $f=(1.1514-1.14)/0.02=0.569$,

$$
M_{n2}=0.8820+0.569(0.8682-0.8820)=0.8820-0.0079=0.8741,
$$

$$
\frac{p_l}{p_\infty}=1.3495+0.569(1.4032-1.3495)=1.3495+0.0306=1.3801 .
$$

The downstream Mach number uses the angle between the shock and the deflected stream, $\beta-\theta=22.4227^\circ$,

$$
M_l=\frac{M_{n2}}{\sin(\beta-\theta)}=\frac{0.8741}{\sin22.4227^\circ}=\frac{0.8741}{0.38144}=\boxed{2.292},
$$

$$
p_l=1.3801\times20=\boxed{27.60\ \text{kPa}} .
$$

> [!check] Exact values and ordering
> The exact relations give $M_u=2.7233$, $p_u=14.16$ kPa, $M_l=2.2915$ and $p_l=27.60$ kPa. The ordering is right for a $5^\circ$ turn either way: $p_u<p_\infty<p_l$ and $M_u>M_\infty>M_l$.

### (iii) Upper and lower pressures by Ackeret's theory [8 marks]

Ackeret's formula is $C_p=2\theta/\sqrt{M_\infty^2-1}$ with $\theta$ in radians, positive where the surface turns into the stream ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]]). The three ingredients are

$$
q_\infty=\tfrac12\gamma p_\infty M_\infty^2=\tfrac12(1.4)(20)(2.5^2)=87.50\ \text{kPa},
$$

$$
\sqrt{M_\infty^2-1}=\sqrt{6.25-1}=\sqrt{5.25}=2.2913,
$$

$$
\alpha=5^\circ\times\frac{\pi}{180}=0.087266\ \text{rad}.
$$

The upper surface has $\theta_u=-\alpha$ and the lower surface $\theta_l=+\alpha$, so

$$
C_{p,l}=\frac{2(0.087266)}{2.2913}=+0.07617,\qquad C_{p,u}=-0.07617 .
$$

The pressures follow from $p=p_\infty+q_\infty C_p$,

$$
p_u=20+87.50(-0.07617)=20-6.665=\boxed{13.33\ \text{kPa}},
$$

$$
p_l=20+87.50(0.07617)=20+6.665=\boxed{26.67\ \text{kPa}} .
$$

Both linear values lie below the shock-expansion ones (14.18 and 27.60 kPa). The neglected term is second order in $\alpha$ and has the same sign on both faces, so it raises the pressure on the expansion side as well as on the compression side.

> [!check] Second-order (Busemann) correction, not lectured
> Writing $C_p=C_1\theta+C_2\theta^2$ with $C_2=\dfrac{(\gamma+1)M_\infty^4-4(M_\infty^2-1)}{2(M_\infty^2-1)^2}=\dfrac{2.4(39.0625)-4(5.25)}{2(27.5625)}=1.3197$ adds $q_\infty C_2\alpha^2=87.50(1.3197)(0.0076154)=0.88$ kPa to both faces. That gives $p_u=14.21$ kPa and $p_l=27.54$ kPa, within 0.4 % of the shock-expansion values.

### (iv) Maximum deflection angle for an attached shock and wave sketches [6 marks]

The largest deflection with an attached shock is $\theta_{\max}$ at $M_\infty=2.5$; on the oblique-shock chart it is the peak of the $M_1=2.5$ curve, near $30^\circ$. Setting $\mathrm d\theta/\mathrm d\beta=0$ in the $\theta$–$\beta$–$M$ relation gives the shock angle at the peak,

$$
\sin^2\beta_{\max}=\frac{1}{\gamma M^2}\left[\frac{\gamma+1}{4}M^2-1+\sqrt{(\gamma+1)\left(\frac{\gamma+1}{16}M^4+\frac{\gamma-1}{2}M^2+1\right)}\right].
$$

With $M^2=6.25$ and $M^4=39.0625$, the pieces are $\tfrac{2.4}{4}(6.25)=3.75$, $\tfrac{2.4}{16}(39.0625)=5.859$ and $0.2(6.25)=1.25$. Then

$$
\sin^2\beta_{\max}=\frac{1}{8.75}\left[3.75-1+\sqrt{2.4(5.859+1.25+1)}\right]
$$

$$
=\frac{1}{8.75}\left[2.75+\sqrt{19.4625}\right]=\frac{2.75+4.4116}{8.75}=0.81847,
$$

so $\beta_{\max}=64.78^\circ$. Putting this angle back into the relation, with $\cos2\beta_{\max}=-0.63694$,

$$
\tan\theta_{\max}=2\cot64.78^\circ\,\frac{6.25(0.81847)-1}{6.25(1.4-0.63694)+2}=0.94189\times\frac{4.1155}{6.7691}=0.57265,
$$

$$
\alpha_{\max}=\theta_{\max}=\arctan0.57265=\boxed{29.80^\circ} .
$$

For $\alpha<\alpha_{\max}$ the lower surface carries a straight oblique shock attached at the leading edge, with supersonic flow behind it on the weak branch, and a centred Prandtl–Meyer fan turns the flow round the leading edge onto the upper surface. At the trailing edge the two streams meet at different pressures and directions: the upper stream is turned back through a trailing-edge shock, the lower stream through an expansion fan, and a slip line separates them.

For $\alpha>\alpha_{\max}$ no attached solution exists, and a curved bow shock stands off ahead of the leading edge. It is nearly normal in front of the nose, with a subsonic pocket behind that part, and weakens to an oblique shock and a Mach wave far from the plate. Sonic lines bound the subsonic pocket, and the flow re-accelerates to supersonic speed along both surfaces.

![[at_pp_201718_q1_plate_waves.png|850]]

### (v) Design requirements for transonic and supersonic aerofoils [6 marks]

See [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils|W07a]] and [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]].

In the transonic regime ($M_{\text{crit}}<M_\infty\lesssim1.2$) the aim is to delay the drag rise. A pocket of supersonic flow forms over the upper surface and ends in a shock, and both the wave drag and the boundary-layer separation caused by that shock grow quickly with its strength. A modest thickness ratio and low upper-surface curvature raise $M_{\text{crit}}$ and the drag-divergence Mach number. A supercritical section goes further: its flat upper surface holds the local Mach number nearly constant over the pocket, so the pocket ends in a weak shock, and aft camber recovers the lift lost by flattening the upper surface. On a wing, sweep reduces the Mach number normal to the leading edge to $M_\infty\cos\Lambda$, which raises the flight Mach number at which the section becomes critical.

In the supersonic regime the aim is low wave drag. A sharp leading edge keeps the shock attached; a blunt nose carries a detached bow shock with a normal-shock portion and large drag. Ackeret's theory gives thickness drag proportional to the mean square of the surface slope, so the section must be thin: for a given thickness ratio the double wedge has the least drag, $C_d=4(t/c)^2/\sqrt{M_\infty^2-1}$, and the biconvex section has $4/3$ of it. Camber and incidence add their own drag terms in linear theory, so camber is kept small. A sharp, thin leading edge is a structural and heating compromise, and it gives poor low-speed lift, which is why such sections need high-lift devices.

---

## Q2. Prandtl–Glauert transformation and critical Mach number (16 marks)

> (i) For $M_\infty^2 < 1$, show how $(1-M_\infty^2)\phi_{xx} + \phi_{yy} = 0$ reduces to Laplace's equation and derive $C_p = C_{p0}/\sqrt{1 - M_\infty^2}$. [10]
> (ii) A multi-element aerofoil has $M_{\text{crit}} = 0.45$. Find $C_{p,\min,0}$ in incompressible flow. [6]

### (i) Reduction to Laplace's equation and derivation of the Prandtl–Glauert rule [10 marks]

For $M_\infty<1$ write $\beta=\sqrt{1-M_\infty^2}$, which is real and positive, so the potential equation is

$$
\beta^2\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0 .
$$

Introduce the transformed coordinates and potential of [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]],

$$
x_0=x,\qquad y_0=\beta y,\qquad \phi_0=\beta\phi .
$$

The $x$-derivative is unchanged by the transformation, and $\phi=\phi_0/\beta$, so

$$
\frac{\partial^2\phi}{\partial x^2}=\frac{1}{\beta}\frac{\partial^2\phi_0}{\partial x_0^2} .
$$

Since $y_0=\beta y$, the chain rule gives $\partial/\partial y=\beta\,\partial/\partial y_0$. Applying it twice,

$$
\frac{\partial^2\phi}{\partial y^2}=\beta^2\frac{\partial^2}{\partial y_0^2}\left(\frac{\phi_0}{\beta}\right)
$$

$$
=\beta\frac{\partial^2\phi_0}{\partial y_0^2} .
$$

Substituting both into the potential equation,

$$
\beta^2\cdot\frac{1}{\beta}\frac{\partial^2\phi_0}{\partial x_0^2}+\beta\frac{\partial^2\phi_0}{\partial y_0^2}=0
$$

$$
\beta\left(\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\partial^2\phi_0}{\partial y_0^2}\right)=0 .
$$

Because $\beta\neq0$ for $M_\infty<1$,

$$
\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\partial^2\phi_0}{\partial y_0^2}=0,
$$

which is Laplace's equation: $\phi_0$ is an incompressible potential flow in the $(x_0,y_0)$ plane.

The body is the same in both planes. Thin-aerofoil theory applies tangency on the axis, $\partial\phi/\partial y=U_\infty f'(x)$ at $y=0$ for a surface $y=f(x)$. In the transformed variables

$$
\frac{\partial\phi}{\partial y}=\frac{\partial(\phi_0/\beta)}{\partial(y_0/\beta)}=\frac{\partial\phi_0}{\partial y_0},
$$

so the incompressible flow satisfies $\partial\phi_0/\partial y_0=U_\infty f'(x_0)$ on $y_0=0$: the same slope, hence the same aerofoil.

The streamwise perturbation velocity is

$$
u'=\frac{\partial\phi}{\partial x}=\frac{\partial(\phi_0/\beta)}{\partial x_0}=\frac{1}{\beta}\frac{\partial\phi_0}{\partial x_0}=\frac{u_0'}{\beta}.
$$

Substituting into the linearised pressure coefficient $C_p=-2u'/U_\infty$,

$$
C_p=-\frac{2u'}{U_\infty}=\frac{1}{\beta}\left(-\frac{2u_0'}{U_\infty}\right)=\frac{C_{p0}}{\beta},
$$

$$
\boxed{C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}}} .
$$

### (ii) Minimum incompressible pressure coefficient for Mcrit = 0.45 [6 marks]

![[at_pp_201718_q2_mcrit.png|900]]

At $M_\infty=M_{\text{crit}}$ the local Mach number at the suction peak just reaches 1. Isentropic flow from the free stream to that sonic point gives the critical pressure coefficient ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#8. Estimating the critical Mach number|W07b §8]]),

$$
C_{p,\text{cr}}=\frac{2}{\gamma M_{\text{crit}}^2}\left[\left(\frac{2+(\gamma-1)M_{\text{crit}}^2}{\gamma+1}\right)^{\frac{\gamma}{\gamma-1}}-1\right].
$$

With $M_{\text{crit}}=0.45$, $M_{\text{crit}}^2=0.2025$. The bracketed ratio is

$$
\frac{2+0.4(0.2025)}{2.4}=\frac{2.0810}{2.4}=0.867083,
$$

and raised to the power 3.5 it is $0.607034$. Hence

$$
C_{p,\text{cr}}=\frac{2}{1.4(0.2025)}\left[0.607034-1\right]=7.05467(-0.392966)=-2.7722 .
$$

At $M_{\text{crit}}$ the Prandtl–Glauert-corrected suction peak equals $C_{p,\text{cr}}$,

$$
\frac{C_{p,\min,0}}{\sqrt{1-M_{\text{crit}}^2}}=C_{p,\text{cr}} .
$$

Solving for the incompressible value,

$$
C_{p,\min,0}=C_{p,\text{cr}}\sqrt{1-M_{\text{crit}}^2}=-2.7722\sqrt{0.7975}=-2.7722(0.89303)=\boxed{-2.476} .
$$

A suction peak this strong is typical of a multi-element aerofoil at high lift, which is why sonic flow appears at a free-stream Mach number as low as 0.45.

---

## Q3. Method of characteristics in a Mach 3 minimum-length nozzle (16 marks)

> Figure Q.3 shows four characteristic lines in a 2D C-D nozzle accelerating air to $M=3$.
> (i) Define the Riemann invariants at point 8 and state how they relate to points 4 and 7. [4]
> (ii) At point 4: $M=1.96, \theta=24.5^\circ, x=0.90, y=0.90$; at point 7: $M=1.96, \theta=8.2^\circ, x=1.74, y=0.33$. Find $M, \theta, x, y$ at point 8. [10]
> (iii) Define the simple region for Figure Q.3. [2]

### (i) Riemann invariants at point 8 [4 marks]

In steady, planar, irrotational supersonic flow the course invariants are ([[SESA3029 W05a - Method of Characteristics|W05a]])

$$
R^+=\nu-\theta\ \ \text{constant along }C^+\ (\text{slope }\theta+\mu),\qquad R^-=\nu+\theta\ \ \text{constant along }C^-\ (\text{slope }\theta-\mu).
$$

In Figure Q.3, point 8 lies on the last right-running characteristic from the throat corner, $0$–$4$–$8$–$11$–$13$, and on the left-running characteristic $6$–$7$–$8$–$9$. The $C^-$ through 4 and the $C^+$ through 7 therefore carry their invariants to 8,

$$
R^-_8=\nu_8+\theta_8=R^-_4=\nu_4+\theta_4,
$$

$$
R^+_8=\nu_8-\theta_8=R^+_7=\nu_7-\theta_7 .
$$

### (ii) Flow properties and coordinates at point 8 [10 marks]

The IFT row at $M=1.96$ gives $\nu=25.2711^\circ$, and the Mach angle is $\mu=\arcsin(1/1.96)=30.6774^\circ$, the same at both known points. The invariants are

$$
R^-_4=\nu_4+\theta_4=25.2711^\circ+24.5^\circ=49.7711^\circ,
$$

$$
R^+_7=\nu_7-\theta_7=25.2711^\circ-8.2^\circ=17.0711^\circ .
$$

Adding and subtracting the two invariant equations at point 8,

$$
\nu_8=\tfrac12\left(R^+_7+R^-_4\right)=\tfrac12(17.0711^\circ+49.7711^\circ)=33.4211^\circ,
$$

$$
\theta_8=\tfrac12\left(R^-_4-R^+_7\right)=\tfrac12(49.7711^\circ-17.0711^\circ)=\boxed{16.35^\circ} .
$$

The Mach number comes from the IFT by inverse interpolation.

| $M$ | $\nu$ (deg) |
|---:|---:|
| 2.26 | 33.2730 |
| 2.28 | 33.7796 |

$$
M_8=2.26+0.02\times\frac{33.4211-33.2730}{33.7796-33.2730}=2.26+0.02\times\frac{0.1481}{0.5066}=2.26+0.02(0.2923)=\boxed{2.266},
$$

and the Mach angle there is $\mu_8=\arcsin(1/2.2658)=26.189^\circ$. The nearest table row, $M=2.26$, is also acceptable.

The state at the three points is then complete.

| Point | $M$ | $\nu$ | $\theta$ | $\mu$ | $R^+=\nu-\theta$ | $R^-=\nu+\theta$ | $\theta+\mu$ | $\theta-\mu$ |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 4 | 1.96 | 25.2711 | 24.50 | 30.6774 | 0.7711 | 49.7711 | 55.1774 | −6.1774 |
| 7 | 1.96 | 25.2711 | 8.20 | 30.6774 | 17.0711 | 33.4711 | 38.8774 | −22.4774 |
| 8 | 2.2658 | 33.4211 | 16.35 | 26.1892 | 17.0711 | 49.7711 | 42.5392 | −9.8392 |

(angles in degrees). The formula-sheet slopes average the end values of each segment. Point 7 plays the role of A (on the $C^+$) and point 4 the role of B (on the $C^-$),

$$
\alpha_{78}=\tfrac12\left[(\theta+\mu)_7+(\theta+\mu)_8\right]=\tfrac12(38.8774^\circ+42.5392^\circ)=40.7083^\circ,
$$

$$
\alpha_{48}=\tfrac12\left[(\theta-\mu)_4+(\theta-\mu)_8\right]=\tfrac12(-6.1774^\circ-9.8392^\circ)=-8.0083^\circ .
$$

Their tangents are $\tan\alpha_{78}=0.86039$ and $\tan\alpha_{48}=-0.14069$. The intersection formula is

$$
x_8=\frac{x_4\tan\alpha_{48}-x_7\tan\alpha_{78}+y_7-y_4}{\tan\alpha_{48}-\tan\alpha_{78}} .
$$

The three numerator terms are $x_4\tan\alpha_{48}=0.90(-0.14069)=-0.12662$, $x_7\tan\alpha_{78}=1.74(0.86039)=1.49707$ and $y_7-y_4=0.33-0.90=-0.57$. So

$$
x_8=\frac{-0.12662-1.49707-0.57}{-0.14069-0.86039}=\frac{-2.19369}{-1.00108}=\boxed{2.191},
$$

$$
y_8=y_7+(x_8-x_7)\tan\alpha_{78}=0.33+(2.1913-1.74)(0.86039)=0.33+0.3883=\boxed{0.718} .
$$

> [!check] The other line
> Along the $C^-$ from point 4, $y_8=y_4+(x_8-x_4)\tan\alpha_{48}=0.90+(1.2913)(-0.14069)=0.7183$, the same value. Point 8 lies downstream of both parents and between them in height, as it should.

### (iii) Simple region in Figure Q.3 [2 marks]

A simple region is one crossed by characteristics of one family only, so one Riemann invariant has the same value throughout it ([[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]]). In Figure Q.3 it is bounded by the last $C^-$ from the corner, $0$–$4$–$8$–$11$–$13$, by the contoured wall $0$–$5$–$9$–$12$–$14$, and by the last $C^+$, $13$–$14$. The wall is shaped to cancel each arriving $C^+$ wave, so no $C^-$ waves leave it, and every point of the region carries $R^-=2\theta_{\max}=\nu(M_e)$. Along each $C^+$ ($4$–$5$, $8$–$9$, $11$–$12$, $13$–$14$) $R^+$ is also constant, so $\nu$ and $\theta$ are both constant and the line is straight. Downstream of $13$–$14$ the flow is uniform at $M=3$, $\theta=0$.

![[at_pp_201718_q3_moc_grid.png|850]]

---

## Q4. Laminar flat-plate heat transfer and lunar re-entry radiation (16 marks)

> [!warning] Not yet lectured
> Both parts are heat transfer and re-entry heating (Weeks 9–12), not yet lectured as of 12 Nov 2026.

> (i) Air flow at $5\ \text{m/s}$, $T_\infty = 15^\circ\text{C}$ develops a laminar BL over a $12\ \text{cm}$ long flat plate at constant $T_w = 40^\circ\text{C}$. For total heat flux $20\ \text{W}$, find the plate width $w$. [10]
> (ii) Sketch the shock layer near the leading edge of a spacecraft at peak heating during lunar re-entry and discuss the role of radiation from (a) the spacecraft and (b) the gas. [6]

### (i) Required plate width for 20 W [10 marks]

The front-page properties are $\rho=1.225\ \text{kg/m}^3$, $\mu=1.79\times10^{-5}\ \text{N s/m}^2$, $c_p=1005\ \text{J/(kg K)}$ and $\text{Pr}=0.7$. The plate has $L=0.12$ m, the flow $U_\infty=5$ m/s, and the temperature difference is $\Delta T=40-15=25$ K. The thermal conductivity follows from the Prandtl number,

$$
k=\frac{\mu c_p}{\text{Pr}}=\frac{1.79\times10^{-5}(1005)}{0.7}=0.02570\ \text{W/(m K)} .
$$

The Reynolds number at the trailing edge is

$$
\text{Re}_L=\frac{\rho U_\infty L}{\mu}=\frac{1.225(5)(0.12)}{1.79\times10^{-5}}=\frac{0.735}{1.79\times10^{-5}}=4.106\times10^4,
$$

well below $3\times10^5$, so the boundary layer is laminar over the whole plate. The formula sheet gives the local Nusselt number for a uniform wall temperature, $\text{Nu}_x=h_xx/k=0.332\,\text{Re}_x^{1/2}\text{Pr}^{1/3}$. Writing $\text{Re}_x=\rho U_\infty x/\mu$, the local coefficient is

$$
h_x=\frac{k}{x}\,0.332\left(\frac{\rho U_\infty x}{\mu}\right)^{1/2}\text{Pr}^{1/3}=0.332\,k\left(\frac{\rho U_\infty}{\mu}\right)^{1/2}\text{Pr}^{1/3}\,x^{-1/2} .
$$

Its average over the plate is

$$
\bar h=\frac1L\int_0^Lh_x\,\mathrm dx=0.332\,k\left(\frac{\rho U_\infty}{\mu}\right)^{1/2}\text{Pr}^{1/3}\,\frac{1}{L}\left[2x^{1/2}\right]_0^L
$$

$$
=0.664\,k\left(\frac{\rho U_\infty}{\mu}\right)^{1/2}\text{Pr}^{1/3}L^{-1/2}=0.664\,\frac{k}{L}\,\text{Re}_L^{1/2}\text{Pr}^{1/3},
$$

so $\overline{\text{Nu}}_L=0.664\,\text{Re}_L^{1/2}\text{Pr}^{1/3}$, twice the local value at $x=L$. Numerically,

$$
\overline{\text{Nu}}_L=0.664\,(4.1061\times10^4)^{1/2}(0.7)^{1/3}=0.664(202.64)(0.88790)=119.47,
$$

$$
\bar h=\frac{\overline{\text{Nu}}_L\,k}{L}=\frac{119.47(0.02570)}{0.12}=25.59\ \text{W/(m}^2\text{ K)} .
$$

Newton's law of cooling for one heated face of area $wL$ is $q=\bar h\,wL\,\Delta T$. Solving for the width,

$$
w=\frac{q}{\bar hL\,\Delta T}=\frac{20}{25.59(0.12)(25)}=\frac{20}{76.76}=\boxed{0.261\ \text{m}} .
$$

If both faces of the plate transfer heat, the area doubles and the width halves to 0.130 m; see [[#Paper slips and ambiguities]].

### (ii) Lunar re-entry shock layer and radiative heating [6 marks]

On return from the Moon the capsule enters at about 11 km/s ($M_\infty\approx30$–35). The sketch shows a blunt heat shield with a detached bow shock a small stand-off distance $\Delta$ ahead of it, normal on the stagnation streamline and curving to an oblique shock round the shoulders. Between the shock and the wall lies the shock layer: an inviscid region of compressed, dissociated and partly ionised air at about 10 000–12 000 K, and a thin boundary layer next to the ablating surface.

Radiation from the spacecraft is a cooling term. The heat shield runs at roughly 2000–3000 K and emits $\varepsilon\sigma T_w^4$ to space. This is far below the gas temperature, so the surface cannot radiate back into the shock layer to any useful extent, but at radiative equilibrium the emitted flux balances much of the incoming heat and reduces the heat conducted into the structure.

Radiation from the gas is a heating term. Behind the normal part of the shock the air is hot enough to excite electronic states and to dissociate and ionise ($\text{N}_2$, $\text{O}_2$, NO, N, O, $\text{N}^+$, $\text{O}^+$, $e^-$), and the shock layer radiates onto the wall. At lunar-return speed this radiative flux becomes comparable with the convective flux at peak heating; at orbital entry (about 7.8 km/s) convection dominates. Nose radius sets the balance: convective heating scales as $R_n^{-1/2}$, while the stand-off distance, and with it the volume of radiating gas, grows in proportion to $R_n$. A lunar-return capsule therefore cannot be made arbitrarily blunt, and its ablator's pyrolysis gases in the boundary layer absorb part of the incoming radiation.

---

## Q5. 1D isentropic Euler characteristics and Richardson extrapolation (16 marks)

> (i) Show $\partial q/\partial t + \partial f(q)/\partial x = 0$ with $q=(\rho,\rho u)^T$, $f(q)=(\rho u, \rho u^2 + p)^T$, and $p=C\rho^\gamma$ becomes $\partial q/\partial t + A\,\partial q/\partial x = 0$ with $A = \begin{pmatrix} 0 & 1 \\ a^2 - u^2 & 2u \end{pmatrix}$, and find characteristic speeds $u-a, u+a$. [10]
> (ii) A uniformly second-order CFD code gives $M_e = 4.21$ ($80\times 80$) and $M_e = 4.35$ ($120\times 120$). Estimate the exact jet Mach number. [6]

### (i) Flux Jacobian and characteristic speeds [10 marks]

Name the conserved variables $q_1=\rho$ and $q_2=\rho u$. Then $u=q_2/q_1$, $\rho u^2=q_2^2/q_1$ and $p=Cq_1^\gamma$, so the flux components in terms of $q_1$ and $q_2$ are

$$
f_1=q_2,\qquad f_2=\frac{q_2^2}{q_1}+Cq_1^\gamma .
$$

By the chain rule $\partial f/\partial x=A\,\partial q/\partial x$ with $A=\partial f/\partial q$, so the conservation law becomes $\partial q/\partial t+A\,\partial q/\partial x=0$. The four entries of $A$ are

$$
A_{11}=\frac{\partial f_1}{\partial q_1}=0,\qquad A_{12}=\frac{\partial f_1}{\partial q_2}=1,
$$

$$
A_{21}=\frac{\partial f_2}{\partial q_1}=-\frac{q_2^2}{q_1^2}+\gamma Cq_1^{\gamma-1},
$$

$$
A_{22}=\frac{\partial f_2}{\partial q_2}=\frac{2q_2}{q_1}=2u .
$$

In $A_{21}$, the first term is $-u^2$. The second is

$$
\gamma Cq_1^{\gamma-1}=\gamma\frac{C\rho^\gamma}{\rho}=\frac{\gamma p}{\rho}=a^2,
$$

so $A_{21}=a^2-u^2$ and

$$
A=\begin{pmatrix}0&1\\a^2-u^2&2u\end{pmatrix}.
$$

The characteristic speeds are the eigenvalues $\lambda$ of $A$, the roots of $\det(A-\lambda I)=0$,

$$
\det\begin{pmatrix}-\lambda&1\\a^2-u^2&2u-\lambda\end{pmatrix}=-\lambda(2u-\lambda)-(a^2-u^2)=0 .
$$

Expanding,

$$
\lambda^2-2u\lambda+u^2-a^2=0 .
$$

The first three terms form a square,

$$
(\lambda-u)^2=a^2,
$$

so

$$
\lambda=\boxed{u-a,\ u+a} .
$$

### (ii) Richardson extrapolation for the jet Mach number [6 marks]

For a uniformly second-order method the error on a grid of spacing $h$ is $Ch^2$ to leading order, so the coarse ($80\times80$, spacing $h_1$) and fine ($120\times120$, spacing $h_2$) results are

$$
M_1=M_{\text{exact}}+Ch_1^2,\qquad M_2=M_{\text{exact}}+Ch_2^2 .
$$

The spacing is inversely proportional to the number of cells along a side, so the refinement ratio is

$$
r=\frac{h_1}{h_2}=\frac{120}{80}=1.5 .
$$

Putting $h_1=rh_2$ in the coarse-grid equation gives $M_1=M_{\text{exact}}+Cr^2h_2^2$. Subtracting the fine-grid equation,

$$
M_1-M_2=Ch_2^2(r^2-1),
$$

$$
Ch_2^2=\frac{M_1-M_2}{r^2-1} .
$$

The fine-grid equation then gives the extrapolated value,

$$
M_{\text{exact}}=M_2-Ch_2^2=M_2+\frac{M_2-M_1}{r^2-1}
$$

$$
=4.35+\frac{4.35-4.21}{1.5^2-1}=4.35+\frac{0.14}{1.25}=4.35+0.112=\boxed{4.46} .
$$

> [!warning] The ratio is in spacing, not cell count
> The fine grid has $2.25$ times as many cells as the coarse one, but in 2D the spacing ratio is only $\sqrt{2.25}=1.5$. Using 2.25 as $r$ would give $r^2-1=4.06$ and $M_{\text{exact}}=4.38$.

---

## Paper slips and ambiguities

- Q3(ii) gives $M_4=M_7=1.96$, and the data are consistent with an ordinary characteristic net. Point 4 has $R^-=49.7711^\circ\approx\nu(3)=49.757^\circ$, as the last ray from the corner must, and the two invariants imply corner rays at about $0.39^\circ$, $8.54^\circ$, $16.74^\circ$ and $24.89^\circ$, with $\nu_4=\theta_a+\theta_d$ and $\nu_7=\theta_b+\theta_c$ almost equal. An earlier version of this note claimed $M_7$ should exceed $M_4$; that claim was wrong and has been removed.
- Q4(i) does not say whether one or both faces of the plate transfer heat. One face gives $w=0.261$ m; both faces give $w=0.130$ m.
- Corrections to the earlier draft of this note: the IFT row at $M=2.74$ is $\nu=44.4810^\circ$, $p/p_0=0.0404$ (the draft had 44.5256 and 0.0402), which changes the interpolated $p_u$ in Q1(ii) from 14.16 to 14.18 kPa (exact 14.16 kPa); and Q3 now uses the course invariants $R^+=\nu-\theta$, $R^-=\nu+\theta$ in place of Anderson's $\theta\mp\nu$ form, with unchanged results.
