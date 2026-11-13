---
title: "SESA3029 Past Paper 2022-23 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, shock-expansion, ackeret, prandtl-glauert, moc, mln, finite-difference, heat-exchanger, lmtd]
paper: "2022-23"
theory_notes: ["[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-202223-01-SESA3029.pdf"]
---

# SESA3029 Past Paper 2022-23 - Solutions

> [!abstract] Paper info
> 2022-23 Semester 1 examination (120 min, formula sheet on pp. 7–8), five questions worth 36 + 16 + 16 + 14 + 18 = 100 marks. The front-page constants are the same as in 2023-24 and 2024-25. Question 1 is the triangular wing of [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing#Part 2. The isosceles triangular wing|Tutorial Lecture 1 Part 2]]. Questions 4 and 5 are heat transfer (Weeks 9–12, not yet lectured). Table values below are the IFT and NST rows at their 0.02 spacing, interpolated linearly; every number was checked in Python against the exact relations with $\gamma=1.4$.

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 36 | Triangular aerofoil: shock-expansion, pitching moment, Ackeret, $x_{\text{ac}}$ | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 2 | 16 | Prandtl–Glauert derivation and critical Mach number ($C_{p0,\min}=-5.4$) | [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]] |
| 3 | 16 | Minimum-length nozzle ($\theta_{\max}=\nu(M_e)/2$, interior point, characteristic angles) | [[SESA3029 W05a - Method of Characteristics|W05a]], [[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]] |
| 4 | 14 | 2D Laplace conduction by finite differences on a symmetric $20\times20\ \text{cm}$ block (heat transfer, Weeks 9–12, not yet lectured) | Not yet lectured |
| 5 | 18 | Counterflow oil–water heat exchanger by the LMTD method (heat transfer, Weeks 9–12, not yet lectured) | Not yet lectured |

---

## Q1. Supersonic triangular aerofoil (36 marks)

> A triangular thin aerofoil of chord $c=15\ \text{cm}$ has a straight lower surface at incidence $\alpha=10^\circ$ to an approaching flow with $M_1=1.7$ and $p_1=20\ \text{kPa}$. Maximum thickness is at half-chord, and both leading- and trailing-edge internal angles are $\phi=\alpha=10^\circ$.
> (i) Sketch the flow and identify all shock and expansion waves. [4]
> (ii) Find $p$ and $M$ on each surface by shock-expansion theory. [14]
> (iii) Find the pitching moment about the leading edge. [4]
> (iv) Repeat for surface pressures and pitching moment using Ackeret theory and comment. [10]
> (v) Explain without calculations how to find the aerodynamic centre ($x_{\text{ac}}/c=-\mathrm{d}C_{M,\text{LE}}/\mathrm{d}C_L$) and state where it is expected to lie. [4]

![[at_pp_202223_q1_triangular_wing.png|900]]

### (i) Wave pattern [4 marks]

The lower surface is the chord, inclined at $\alpha=10^\circ$ to the stream. The upper forward face (UF) rises from the leading edge at $\phi=10^\circ$ to the chord, so it lies at $\phi-\alpha=0^\circ$ to the free stream: the flow slides along it and no wave forms at the upper leading edge. The upper aft face (UA) runs from the apex at mid-chord down to the trailing edge, at $\phi$ below the chord. At the apex the surface therefore turns away from the flow by $\phi+\phi=20^\circ$ (the exterior angle of an isosceles triangle with base angles of $10^\circ$), and a centred Prandtl–Meyer expansion fan stands there. The lower surface (L) turns the stream into itself by $\alpha=10^\circ$, so an attached oblique shock sits at the leading edge.

At the trailing edge the upper stream arrives at $20^\circ$ below the free-stream direction with $p_{UA}\approx6.3$ kPa, and the lower stream at $10^\circ$ below it with $p_L\approx32.9$ kPa. The two must leave with equal pressure and a common direction, separated by a slip line. The upper stream is compressed through an oblique shock and the lower stream is expanded through a fan. Solving for equal pressure puts the slip line at $0.08^\circ$ above the free-stream direction, so the upper trailing-edge shock turns its stream by $20.08^\circ$ and the lower fan turns its stream by $10.08^\circ$.

### (ii) Pressures and Mach numbers by shock-expansion theory [14 marks]

#### Upper forward face

With no wave, the free-stream state persists:

$$
M_{UF}=\boxed{1.70},\qquad p_{UF}=\boxed{20.0\ \text{kPa}}.
$$

#### Lower surface: oblique shock with M = 1.7 and θ = 10°

The weak-shock angle comes from the θ–β–M relation,

$$
\tan\theta=2\cot\beta\,\frac{M_1^2\sin^2\beta-1}{M_1^2(\gamma+\cos2\beta)+2},
$$

evaluated at trial values of $\beta$ and updated by the secant rule until $\theta(\beta)=10^\circ$. The OSC reads about $47^\circ$, so start from $45^\circ$ and $48^\circ$:

| Iterate | $\beta$ (°) | $\theta(\beta)$ (°) |
|---:|---:|---:|
| 0 | 45.0000 | 8.3741 |
| 1 | 48.0000 | 10.5847 |
| 2 | 47.2065 | 10.0283 |
| 3 | 47.1661 | 9.9995 |
| 4 | 47.1668 | 10.0000 |

The first update is

$$
\beta_2=48+(10-10.5847)\,\frac{48-45}{10.5847-8.3741}=48-0.7935=47.2065^\circ,
$$

and the exact weak root is $\beta=47.17^\circ$. The normal Mach number is

$$
M_{n1}=M_1\sin\beta=1.7\sin47.17^\circ=1.7\times0.73334=1.24667.
$$

The NST rows that bracket it are

| $M_{n1}$ | $M_{n2}$ | $p_2/p_1$ |
|---:|---:|---:|
| 1.24 | 0.8183 | 1.6272 |
| 1.26 | 0.8071 | 1.6855 |

with interpolation fraction $f=(1.24667-1.24)/0.02=0.3336$:

$$
M_{n2}=0.8183-0.3336\times(0.8183-0.8071)=0.8183-0.0037=0.8146,
$$

$$
\frac{p_L}{p_1}=1.6272+0.3336\times(1.6855-1.6272)=1.6272+0.0195=1.6467.
$$

The flow behind the shock is parallel to the lower surface, at $\beta-\theta=37.17^\circ$ to the shock:

$$
M_L=\frac{M_{n2}}{\sin(\beta-\theta)}=\frac{0.8146}{\sin37.17^\circ}=\frac{0.8146}{0.6041}=\boxed{1.348},
$$

$$
p_L=1.6467\times20=\boxed{32.93\ \text{kPa}}.
$$

The exact relations give $M_L=1.3482$ and $p_L=32.931$ kPa.

#### Upper aft face: 20° Prandtl–Meyer expansion from M = 1.7

The IFT row $M=1.70$ gives $\nu_1=17.8099^\circ$ and $p_1/p_0=0.2026$. The fan adds the turning angle:

$$
\nu_{UA}=\nu_1+2\phi=17.8099^\circ+20^\circ=37.8099^\circ.
$$

The IFT rows that bracket this value are

| $M$ | $\nu$ (°) | $p/p_0$ |
|---:|---:|---:|
| 2.44 | 37.7077 | 0.0643 |
| 2.46 | 38.1831 | 0.0623 |

so

$$
f=\frac{37.8099-37.7077}{38.1831-37.7077}=\frac{0.1022}{0.4754}=0.2150,
$$

$$
M_{UA}=2.44+0.02\times0.2150=\boxed{2.444},
$$

$$
\frac{p_{UA}}{p_0}=0.0643-0.2150\times(0.0643-0.0623)=0.06387.
$$

The stagnation pressure is constant through the fan, so

$$
p_{UA}=p_1\,\frac{p_{UA}/p_0}{p_1/p_0}=20\times\frac{0.06387}{0.2026}=\boxed{6.30\ \text{kPa}}.
$$

The exact values are $M_{UA}=2.4443$ and $p_{UA}=6.302$ kPa.

### (iii) Pitching moment about the leading edge [4 marks]

Take nose-up as positive, as in [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#Lift and moment coefficients|W07b §7]]. In the thin-aerofoil treatment each face's pressure acts normal to the chord on the chord projection of the face, with its resultant at the middle of that projection. The lower surface pushes up over the full chord with arm $c/2$, which is nose-down. The upper forward face pushes down over $[0,c/2]$ with arm $c/4$, and the upper aft face pushes down over $[c/2,c]$ with arm $3c/4$; both are nose-up. Hence

$$
M'_{\text{LE}}=-p_L\,c\,\frac{c}{2}+p_{UF}\,\frac{c}{2}\,\frac{c}{4}+p_{UA}\,\frac{c}{2}\,\frac{3c}{4}.
$$

Collect the factor $c^2/8$:

$$
M'_{\text{LE}}=\frac{c^2}{8}\left(p_{UF}+3p_{UA}-4p_L\right).
$$

A uniform pressure gives $1+3-4=0$, so the free-stream pressure drops out, as it must for a closed body. Substitute:

$$
M'_{\text{LE}}=\frac{0.15^2}{8}\left(20.00+3\times6.305-4\times32.93\right)\times10^3,
$$

$$
M'_{\text{LE}}=0.0028125\times(-92.81)\times10^3=\boxed{-261.0\ \text{N m/m}}\quad(\text{nose-down}).
$$

> [!check] Exact face geometry
> With each face's force normal to the face itself, the moment of a uniform pressure $p$ on a straight face from $A$ to $B$ about the leading edge is $\tfrac12p\left(|OB|^2-|OA|^2\right)$. The upper faces have length $\ell=(c/2)/\cos10^\circ=0.07616$ m, so $M'_{\text{LE}}=\tfrac12\left[-p_Lc^2+p_{UF}\ell^2+p_{UA}(c^2-\ell^2)\right]=-259.8$ N m/m, $0.5\,\%$ below the thin-aerofoil value.

### (iv) Ackeret theory and comparison [10 marks]

Ackeret's formula is $C_p=2\theta/\sqrt{M_1^2-1}$, with $\theta$ in radians and positive when the surface turns the flow into itself. At $M_1=1.7$,

$$
\sqrt{M_1^2-1}=\sqrt{1.7^2-1}=\sqrt{1.89}=1.3748,
$$

and the free-stream dynamic pressure, written with $\rho U^2=\gamma pM^2$, is

$$
q_1=\tfrac12\gamma p_1M_1^2=0.5\times1.4\times20\times1.7^2=40.46\ \text{kPa}.
$$

The three faces have $\theta_{UF}=0$, $\theta_L=+10^\circ=+0.17453$ rad and $\theta_{UA}=-20^\circ=-0.34907$ rad. The upper forward face has $C_{p,UF}=0$, so $p_{UF}=\boxed{20.0\ \text{kPa}}$. On the lower surface,

$$
C_{p,L}=\frac{2\times0.17453}{1.3748}=+0.2539,
$$

$$
p_L=p_1+q_1C_{p,L}=20+40.46\times0.2539=20+10.27=\boxed{30.27\ \text{kPa}}.
$$

On the upper aft face,

$$
C_{p,UA}=\frac{2\times(-0.34907)}{1.3748}=-0.5078,
$$

$$
p_{UA}=20+40.46\times(-0.5078)=20-20.55=\boxed{-0.55\ \text{kPa}}.
$$

The same moment expression as in (iii) gives

$$
M'_{\text{LE,Ack}}=0.0028125\times\left(20.00+3\times(-0.546)-4\times30.27\right)\times10^3,
$$

$$
M'_{\text{LE,Ack}}=0.0028125\times(-102.73)\times10^3=\boxed{-288.9\ \text{N m/m}}\quad(\text{nose-down}).
$$

Ackeret theory predicts a lower-surface pressure $8\,\%$ below the shock-expansion value and a negative absolute pressure on the upper aft face, which is impossible. The cause is the size of the turning angles: linear theory needs $|\theta|\ll1$, and the $20^\circ$ apex turn is $0.35$ rad. The linear expansion is also unbounded, whereas a real Prandtl–Meyer expansion can only bring the pressure towards zero. The moment is $11\,\%$ larger in magnitude than the shock-expansion value. The two pressure errors push the moment in opposite directions (a lower $p_L$ is less nose-down, a lower $p_{UA}$ is less nose-up), so they partly cancel and the moment error is smaller than the pressure errors suggest.

### (v) Locating the aerodynamic centre [4 marks]

Repeat the shock-expansion calculation at a second incidence close to $10^\circ$, say $9^\circ$ and $11^\circ$. At $11^\circ$ the upper forward face lies $1^\circ$ away from the stream and carries a weak expansion fan; at $9^\circ$ it turns the stream into itself by $1^\circ$ and carries a weak shock. The apex turn stays at $20^\circ$ in both cases. At each incidence, resolve the face forces into lift, $C_L=L'/(q_1c)$, and find $C_{M,\text{LE}}=M'_{\text{LE}}/(q_1c^2)$. A finite difference then approximates the derivative:

$$
\frac{x_{\text{ac}}}{c}=-\frac{\mathrm{d}C_{M,\text{LE}}}{\mathrm{d}C_L}\approx-\frac{C_{M,\text{LE}}(11^\circ)-C_{M,\text{LE}}(9^\circ)}{C_L(11^\circ)-C_L(9^\circ)}.
$$

In Ackeret theory $C_{M,\text{LE}}$ is a thickness-and-camber constant minus $C_L/2$, so the aerodynamic centre of any thin aerofoil in supersonic flow is at mid-chord, $x_{\text{ac}}/c=0.5$, against $0.25$ in subsonic flow. The shock-expansion result should lie close to mid-chord, slightly forward of it.

> [!check] The finite difference evaluated
> Shock-expansion with exact face geometry gives $C_L=0.4211$, $C_{M,\text{LE}}=-0.2585$ at $9^\circ$ and $C_L=0.5326$, $C_{M,\text{LE}}=-0.3133$ at $11^\circ$, so $x_{\text{ac}}/c=0.0548/0.1115=0.491$.

---

## Q2. Prandtl-Glauert derivation and critical Mach number (16 marks)

> (i) Show how $\left(1-M_\infty^2\right)\dfrac{\partial^2\phi}{\partial x^2}+\dfrac{\partial^2\phi}{\partial y^2}=0$ ($M_\infty^2<1$) reduces to Laplace's equation and derive $C_p=\dfrac{C_{p0}}{\sqrt{1-M_\infty^2}}$. [8]
> (ii) A high-lift aerofoil (slat + flaps) has $C_{p0,\min}=-5.4$. Knowing $M_{\text{crit}}\in[0.3,0.4]$, find a better estimate. [8]

### (i) Derivation of the Prandtl–Glauert rule [8 marks]

The derivation follows [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#6. The Prandtl–Glauert transformation|W07b §6–7]]. For $M_\infty<1$ write $\beta=\sqrt{1-M_\infty^2}$, which is real and positive, so the potential equation is

$$
\beta^2\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0.
$$

Define the transformed variables

$$
\phi_0=\beta\phi,\qquad x_0=x,\qquad y_0=\beta y.
$$

Since $x_0=x$ and $\phi=\phi_0/\beta$,

$$
\frac{\partial^2\phi}{\partial x^2}=\frac{1}{\beta}\frac{\partial^2\phi_0}{\partial x_0^2}.
$$

Since $y_0=\beta y$, the chain rule gives

$$
\frac{\partial}{\partial y}=\frac{\mathrm{d}y_0}{\mathrm{d}y}\frac{\partial}{\partial y_0}=\beta\frac{\partial}{\partial y_0}.
$$

Applying it twice to $\phi=\phi_0/\beta$:

$$
\frac{\partial^2\phi}{\partial y^2}=\beta^2\frac{\partial^2}{\partial y_0^2}\left(\frac{\phi_0}{\beta}\right).
$$

$$
\frac{\partial^2\phi}{\partial y^2}=\beta\frac{\partial^2\phi_0}{\partial y_0^2}.
$$

Substitute both second derivatives into the potential equation:

$$
\beta^2\cdot\frac{1}{\beta}\frac{\partial^2\phi_0}{\partial x_0^2}+\beta\frac{\partial^2\phi_0}{\partial y_0^2}=0.
$$

$$
\beta\left(\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\partial^2\phi_0}{\partial y_0^2}\right)=0.
$$

For $M_\infty<1$, $\beta\neq0$, so

$$
\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\partial^2\phi_0}{\partial y_0^2}=0,
$$

which is Laplace's equation: $\phi_0$ is an incompressible potential flow in the $(x_0,y_0)$ plane.

The body is the same in both planes. The linearised tangency condition on $y=0$ for a surface $y=f(x)$ is $\partial\phi/\partial y=U_\infty f'(x)$. In the new variables

$$
\frac{\partial\phi}{\partial y}=\frac{\partial(\phi_0/\beta)}{\partial(y_0/\beta)}=\frac{\partial\phi_0}{\partial y_0},
$$

so the incompressible problem has $\partial\phi_0/\partial y_0=U_\infty f'(x_0)$ on $y_0=0$: the same slope distribution, hence the same aerofoil.

The incompressible pressure coefficient is $C_{p0}=-2u_0'/U_\infty=-(2/U_\infty)\,\partial\phi_0/\partial x_0$. The compressible one is

$$
C_p=-\frac{2u'}{U_\infty}=-\frac{2}{U_\infty}\frac{\partial\phi}{\partial x}.
$$

Substitute $\phi=\phi_0/\beta$ and $x=x_0$:

$$
C_p=-\frac{2}{U_\infty}\frac{\partial(\phi_0/\beta)}{\partial x_0}.
$$

$$
C_p=\frac{1}{\beta}\left(-\frac{2}{U_\infty}\frac{\partial\phi_0}{\partial x_0}\right).
$$

$$
\boxed{C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}}}
$$

### (ii) Critical Mach number [8 marks]

![[at_pp_202223_q2_mcrit.png|900]]

At $M_{\text{crit}}$ the minimum-pressure point is just sonic. The Prandtl–Glauert value of $C_p$ there must equal the sonic pressure coefficient ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#8. Estimating the critical Mach number|W07b §8]]), which for $\gamma=1.4$ is

$$
C_{p,cr}=\frac{2}{1.4M_\infty^2}\left[\left(\frac{1+0.2M_\infty^2}{1.2}\right)^{3.5}-1\right].
$$

At $M_\infty=0.32$, for example, the left-hand side is $-5.4/\sqrt{1-0.1024}=-5.4/0.9474=-5.6997$, and the right-hand side is $\dfrac{2}{0.14336}\left[(1.02048/1.2)^{3.5}-1\right]=13.951\times(0.56713-1)=-6.0389$. The other rows follow in the same way:

| $M_\infty$ | $-5.4/\sqrt{1-M_\infty^2}$ | $C_{p,cr}(M_\infty)$ | Difference |
|---:|---:|---:|---:|
| 0.30 | −5.6607 | −6.9473 | +1.2866 |
| 0.32 | −5.6997 | −6.0389 | +0.3392 |
| 0.33 | −5.7205 | −5.6453 | −0.0752 |
| 0.35 | −5.7646 | −4.9564 | −0.8082 |
| 0.40 | −5.8919 | −3.6620 | −2.2299 |

The difference changes sign between $0.32$ and $0.33$, and linear interpolation between them gives

$$
M_{\text{crit}}=0.32+0.01\times\frac{0.3392}{0.3392+0.0752}=0.32+0.01\times0.8185=\boxed{0.328}.
$$

> [!check] Exact root
> A root finder gives $M_{\text{crit}}=0.3281$, where both sides equal $-5.7165$.

---

## Q3. Minimum-length nozzle via Method of Characteristics (16 marks)

> A 2D symmetric C–D nozzle accelerates air from a sonic throat (`0`) to exit Mach number $M_e=1.9$ with characteristic lines `0-1-4` and `0-2-3-5` shown in Figure Q.3.
> (i) Define $R^+$ and $R^-$ and show that $\theta_{\max}=\nu(M_e)/2$. [6]
> (ii) Initial lines at `0` have flow angles $\theta_{\max}/2$ (`0-1`) and $\theta_{\max}$ (`0-2`). Find $\theta_2$ and $M_2$. [6]
> (iii) Find the angles of characteristic lines `2-4` and `3-5` (full grid calculation not required). [4]

![[at_pp_202223_q3_mln.png|900]]

### (i) Riemann invariants and the maximum wall angle [6 marks]

In steady, homentropic, irrotational planar supersonic flow the Riemann invariants are ([[SESA3029 W05a - Method of Characteristics|W05a]])

$$
R^+=\nu-\theta,\ \text{constant along a } C^+ \text{ characteristic, inclined at } \theta+\mu,
$$

$$
R^-=\nu+\theta,\ \text{constant along a } C^- \text{ characteristic, inclined at } \theta-\mu,
$$

where $\nu$ is the Prandtl–Meyer function, $\theta$ the flow angle and $\mu=\arcsin(1/M)$ the Mach angle.

The derivation follows [[SESA3029 W05b - Minimum-Length Nozzle Design#13. The minimum-length nozzle|W05b §13]]. The throat is sonic and parallel, so there

$$
M=1,\qquad \nu=0,\qquad \theta=0.
$$

The sharp corner at 0 expands the flow in a centred fan of $C^-$ waves. Every $C^+$ line crossing the fan comes from the uniform sonic flow, so it carries

$$
R^+=\nu-\theta=0-0=0.
$$

Hence on every ray of the fan

$$
\nu=\theta.
$$

The last ray, 0–2–3, leaves the corner at the wall angle $\theta_{\max}$, so on it $\nu=\theta_{\max}$ and

$$
R^-_{023}=\nu+\theta=\theta_{\max}+\theta_{\max}=2\theta_{\max}.
$$

This $C^-$ line reaches the centreline at point 3, the first point of the uniform exit flow, where symmetry gives $\theta_3=0$ and the design gives $\nu_3=\nu(M_e)$:

$$
R^-_3=\nu(M_e)+0=\nu(M_e).
$$

$R^-$ is constant along the line, so $R^-_3=R^-_{023}$:

$$
2\theta_{\max}=\nu(M_e).
$$

$$
\boxed{\theta_{\max}=\frac{\nu(M_e)}{2}}
$$

For $M_e=1.9$ the IFT row gives $\nu(1.9)=23.5861^\circ$, so

$$
\theta_{\max}=\frac{23.5861^\circ}{2}=11.7931^\circ.
$$

### (ii) Flow angle and Mach number at point 2 [6 marks]

Line 0–1 leaves the corner with $\theta=\theta_{\max}/2$, and in the fan $\nu=\theta$, so

$$
R^-_{01}=\frac{\theta_{\max}}{2}+\frac{\theta_{\max}}{2}=\theta_{\max}=11.7931^\circ.
$$

Point 1 is on the centreline, so $\theta_1=0$ and $\nu_1=R^-_{01}=11.7931^\circ$. The $C^+$ line 1–2–4 that leaves it carries

$$
R^+_{124}=\nu_1-\theta_1=11.7931^\circ-0=11.7931^\circ.
$$

Point 2 lies on this $C^+$ line and on the $C^-$ line 0–2–3, which carries $R^-_{023}=2\theta_{\max}=23.5861^\circ$ from (i). The unit process gives

$$
\nu_2=\frac{R^+_{124}+R^-_{023}}{2}=\frac{11.7931+23.5861}{2}=17.6896^\circ,
$$

$$
\theta_2=\frac{R^-_{023}-R^+_{124}}{2}=\frac{23.5861-11.7931}{2}=\boxed{5.90^\circ}.
$$

In terms of $\theta_{\max}$ these are $\nu_2=\tfrac32\theta_{\max}$ and $\theta_2=\tfrac12\theta_{\max}$. To invert $\nu_2$, the IFT rows $M=1.68$ ($\nu=17.2220^\circ$) and $M=1.70$ ($\nu=17.8099^\circ$) bracket it:

$$
f=\frac{17.6896-17.2220}{17.8099-17.2220}=\frac{0.4676}{0.5879}=0.7953,
$$

$$
M_2=1.68+0.02\times0.7953=\boxed{1.696}.
$$

The exact inverse of the Prandtl–Meyer function gives $M_2=1.6959$.

### (iii) Angles of characteristic lines 2-4 and 3-5 [4 marks]

The wall downstream of 0 is designed to be non-reflecting, so no $C^-$ wave crosses the $C^+$ line 2–4 between point 2 and the wall point 4. The state is therefore constant along 2–4: $\theta_4=\theta_2=5.90^\circ$ and $M_4=M_2=1.696$, and the line is straight. The Mach angle at 2 is

$$
\mu_2=\arcsin\frac{1}{1.6959}=36.13^\circ,
$$

and the averaged slope of the formula sheet reduces to the slope at either end:

$$
\alpha_{24}=\tfrac12\left[(\theta+\mu)_2+(\theta+\mu)_4\right]=\theta_2+\mu_2=5.90^\circ+36.13^\circ=\boxed{42.0^\circ}.
$$

Line 3–5 is the $C^+$ line bounding the uniform exit flow. At both ends $\theta=0$ and $M=M_e=1.9$, so

$$
\mu_e=\arcsin\frac{1}{1.9}=31.76^\circ,
$$

$$
\alpha_{35}=0^\circ+\mu_e=\boxed{31.8^\circ}.
$$

---

## Q4. 2D steady conduction on a symmetric square block (14 marks)

> [!warning] Not yet lectured
> Heat transfer (Weeks 9–12, not yet lectured). Check the notation against those lectures when they are written up.

> A monolithic square block of side $20\ \text{cm}\times20\ \text{cm}$ has constant boundary temperatures $300\ \text{K}$ on the left and right faces and $500\ \text{K}$ on the top and bottom faces. Using $\Delta x=\Delta y=5\ \text{cm}$ for $\dfrac{\partial^2 T}{\partial x^2}+\dfrac{\partial^2 T}{\partial y^2}=0$:
> (i) Exploit symmetries to derive the four algebraic stencil relations. [6]
> (ii) Solve the resulting $4\times4$ linear system. [8]

![[at_pp_202223_q4_fd_block.png|750]]

### (i) Symmetries and the four stencil relations [6 marks]

Central differences at an interior node P with east, west, north and south neighbours E, W, N, S give

$$
\frac{T_E-2T_P+T_W}{\Delta x^2}+\frac{T_N-2T_P+T_S}{\Delta y^2}=0.
$$

With $\Delta x=\Delta y$, multiply through by $\Delta x^2$:

$$
T_E+T_W+T_N+T_S-4T_P=0.
$$

The $20\ \text{cm}$ square with $5\ \text{cm}$ steps has $3\times3=9$ interior nodes $(i,j)$, $i,j\in\{1,2,3\}$, counted from the lower-left corner. The geometry and boundary temperatures are symmetric about the vertical centreline $x=10$ cm and the horizontal centreline $y=10$ cm, so only four temperatures differ. $T_1$ is shared by the four nodes next to the corners, $(1,1)$, $(3,1)$, $(1,3)$ and $(3,3)$. $T_2$ belongs to the nodes $(2,1)$ and $(2,3)$ on the vertical centreline, next to the $500$ K faces. $T_3$ belongs to the nodes $(1,2)$ and $(3,2)$ on the horizontal centreline, next to the $300$ K faces. $T_4$ is the centre node $(2,2)$.

Apply the stencil at one representative node of each kind, in the lower-left quadrant.

At $(1,1)$ the neighbours are W $=300$, S $=500$, E $=T_2$ and N $=T_3$:

$$
300+500+T_2+T_3-4T_1=0,
$$

$$
4T_1-T_2-T_3=800. \tag{1}
$$

At $(2,1)$ the neighbours are W $=T_1$, E $=T_1$ (by symmetry), S $=500$ and N $=T_4$:

$$
2T_1+500+T_4-4T_2=0,
$$

$$
-2T_1+4T_2-T_4=500. \tag{2}
$$

At $(1,2)$ the neighbours are S $=T_1$, N $=T_1$, W $=300$ and E $=T_4$:

$$
2T_1+300+T_4-4T_3=0,
$$

$$
-2T_1+4T_3-T_4=300. \tag{3}
$$

At $(2,2)$ the neighbours are W and E $=T_3$, S and N $=T_2$:

$$
2T_2+2T_3-4T_4=0,
$$

$$
-T_2-T_3+2T_4=0. \tag{4}
$$

### (ii) Solution of the 4×4 system [8 marks]

Add (2) and (3):

$$
-4T_1+4(T_2+T_3)-2T_4=800. \tag{5}
$$

From (4),

$$
T_2+T_3=2T_4.
$$

From (1),

$$
T_2+T_3=4T_1-800.
$$

Equate the two expressions for $T_2+T_3$:

$$
2T_4=4T_1-800. \tag{6}
$$

Put $T_2+T_3=2T_4$ into (5):

$$
-4T_1+8T_4-2T_4=800,
$$

$$
-4T_1+6T_4=800.
$$

From (6), $6T_4=3(4T_1-800)=12T_1-2400$:

$$
-4T_1+12T_1-2400=800,
$$

$$
8T_1=3200,
$$

$$
T_1=\boxed{400\ \text{K}}.
$$

Back-substitute into (6):

$$
T_4=\frac{4\times400-800}{2}=\boxed{400\ \text{K}}.
$$

From (2), $T_2=(500+2T_1+T_4)/4$:

$$
T_2=\frac{500+2\times400+400}{4}=\frac{1700}{4}=\boxed{425\ \text{K}}.
$$

From (3), $T_3=(300+2T_1+T_4)/4$:

$$
T_3=\frac{300+2\times400+400}{4}=\frac{1500}{4}=\boxed{375\ \text{K}}.
$$

> [!check] Residuals
> Equation (1): $1600-425-375=800$. Equation (2): $-800+1700-400=500$. Equation (3): $-800+1500-400=300$. Equation (4): $-425-375+800=0$. All four are satisfied. The centre value of $400$ K, the mean of the two boundary temperatures, also follows from superposition: rotating the block by $90^\circ$ swaps the two boundary temperatures, and the average of the two problems is a uniform $400$ K.

---

## Q5. Counterflow oil-water heat exchanger via LMTD (18 marks)

> [!warning] Not yet lectured
> Heat transfer (Weeks 9–12, not yet lectured). Check the notation against those lectures when they are written up.

> A counterflow shell-and-tube heat exchanger heats $\dot m_w=2.5\ \text{kg/s}$ of water from $15^\circ\text{C}$ to $85^\circ\text{C}$ using engine oil entering at $160^\circ\text{C}$ ($h_o=400\ \text{W/(m}^2\text{ K)}$). Ten thin-walled tubes of diameter $D=25\ \text{mm}$ carry the water, each making 8 passes through the shell. Properties: $c_{p,\text{oil}}=2350\ \text{J/(kg K)}$; water $c_p=4181\ \text{J/(kg K)}$, $\mu=5.48\times10^{-4}\ \text{N s/m}^2$, $k=0.643\ \text{W/(m K)}$, $\text{Pr}=3.56$.
> (i) If oil leaves at $100^\circ\text{C}$, find its mass flow rate $\dot m_{\text{oil}}$. [6]
> (ii) Find tube $Re_D$ and combined coefficient $h'$ ($U$). [6]
> (iii) Use the LMTD method to find total tube length $L$ and pass length $L_{\text{pass}}$. [6]

### (i) Oil mass flow rate [6 marks]

The heat taken up by the water is

$$
\dot Q=\dot m_wc_{p,w}\left(T_{w,\text{out}}-T_{w,\text{in}}\right)=2.5\times4181\times(85-15)=731\,675\ \text{W}.
$$

The oil gives up the same heat, $\dot Q=\dot m_{\text{oil}}c_{p,\text{oil}}\left(T_{o,\text{in}}-T_{o,\text{out}}\right)$, so

$$
\dot m_{\text{oil}}=\frac{\dot Q}{c_{p,\text{oil}}\left(T_{o,\text{in}}-T_{o,\text{out}}\right)}=\frac{731\,675}{2350\times(160-100)}=\frac{731\,675}{141\,000}=\boxed{5.19\ \text{kg/s}}.
$$

### (ii) Tube Reynolds number and combined heat transfer coefficient [6 marks]

The water divides equally between the ten tubes, so each carries $\dot m_{\text{tube}}=2.5/10=0.25$ kg/s. With $\dot m=\rho V\pi D^2/4$, the Reynolds number is

$$
Re_D=\frac{\rho VD}{\mu}=\frac{4\dot m_{\text{tube}}}{\pi D\mu}=\frac{4\times0.25}{\pi\times0.025\times5.48\times10^{-4}}=\boxed{2.32\times10^4}\ (23\,234).
$$

This is well above the transition value of about 2300 for pipe flow, so the flow is turbulent. The water is being heated, so the formula-sheet turbulent pipe correlation takes $n=0.4$:

$$
Nu_D=0.023\,Re_D^{4/5}\,\text{Pr}^{0.4}=0.023\times(23\,234)^{0.8}\times(3.56)^{0.4},
$$

$$
Nu_D=0.023\times3111.0\times1.6618=118.9.
$$

The tube-side coefficient is

$$
h_i=\frac{Nu_D\,k}{D}=\frac{118.9\times0.643}{0.025}=3058\ \text{W/(m}^2\text{ K)}.
$$

The tube walls are thin, so their conduction resistance is neglected and the two convective resistances add in series:

$$
\frac{1}{h'}=\frac{1}{h_i}+\frac{1}{h_o}=\frac{1}{3058}+\frac{1}{400}=3.270\times10^{-4}+2.500\times10^{-3}=2.827\times10^{-3}\ \text{m}^2\,\text{K/W},
$$

$$
h'=\boxed{353.7\ \text{W/(m}^2\text{ K)}}.
$$

The oil side, with the smaller coefficient, controls $h'$.

### (iii) Tube length and pass length by the LMTD method [6 marks]

In counterflow the hot inlet faces the cold outlet, so the end temperature differences are

$$
\Delta T_1=T_{o,\text{in}}-T_{w,\text{out}}=160-85=75\ \text{K},
$$

$$
\Delta T_2=T_{o,\text{out}}-T_{w,\text{in}}=100-15=85\ \text{K}.
$$

The log mean temperature difference is

$$
\Delta T_{\text{lm}}=\frac{\Delta T_1-\Delta T_2}{\ln(\Delta T_1/\Delta T_2)}=\frac{75-85}{\ln(75/85)}=\frac{-10}{-0.12516}=79.90\ \text{K}.
$$

The paper describes the exchanger as counterflow and supplies no correction-factor chart, so $F=1$. The required area is

$$
A=\frac{\dot Q}{h'\,\Delta T_{\text{lm}}}=\frac{731\,675}{353.7\times79.90}=25.89\ \text{m}^2.
$$

The area is that of ten tubes, each of length $L$ over all its eight passes, $A=N\pi DL$:

$$
L=\frac{A}{N\pi D}=\frac{25.89}{10\times\pi\times0.025}=\boxed{32.96\ \text{m}},
$$

$$
L_{\text{pass}}=\frac{L}{8}=\frac{32.96}{8}=\boxed{4.12\ \text{m}}.
$$

> [!check] Area and LMTD
> The total tube run is $10\times8\times4.12=329.6$ m, and $\pi\times0.025\times329.6=25.89\ \text{m}^2$. The end differences are close ($75/85=0.88$), so $\Delta T_{\text{lm}}=79.90$ K is just below the arithmetic mean of $80$ K.

---

## Paper slips and ambiguities

- Q5(iii), correction factor. The paper calls the exchanger "shell-and-tube counterflow" with eight tube passes, and no $F$-chart is attached, so the solution uses pure counterflow ($F=1$). For one shell pass with an even number of tube passes, $P=(85-15)/(160-15)=0.483$ and $R=(160-100)/(85-15)=0.857$ give $F=0.878$, which lengthens each pass to $4.12/0.878=4.69$ m. An earlier draft of these notes quoted $F\approx0.82$ and a pass length of about $5.0$ m; both were wrong.
- Q1(ii), table rows. The IFT rows used for the upper aft face are $\nu(2.44)=37.7077^\circ$ and $\nu(2.46)=38.1831^\circ$, and for Q3(ii) $\nu(1.68)=17.2220^\circ$; an earlier draft had $37.7115^\circ$, $38.1844^\circ$ and $17.2430^\circ$. The answers are unchanged.
- Q1(v). An earlier draft put the shock-expansion aerodynamic centre at $0.487c$; the finite difference over $9^\circ$–$11^\circ$ gives $0.491c$.
- Q2(ii). The left- and right-hand-side columns of the table were corrected in the third and fourth decimal places; the root, $0.328$, is unchanged.
