---
title: "SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 4: High-speed aerodynamics"
order: 8
tags: [sesa3029, compressible-flow, potential-flow, linearisation, prandtl-glauert, karman-tsien, critical-mach-number]
aliases: ["SESA3029 Lecture 4.3", "SESA3029 Lecture 4.4", "SESA3029 W07b"]
date: 2026-11-03
status: written-ahead
coverage: "Lectures 4.3–4.4 written ahead from the slides; not yet lectured (no transcript)"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[Streamfunction and Velocity Potential]]"]
next_topics: ["[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
key_concepts: ["[[Linearised Compressible Potential Equation]]", "[[Prandtl-Glauert Transformation]]", "[[Critical Mach Number]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture4-3.pdf", "02 - Sources/Lectures/Lecture4-4.pdf"]
---

# SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation

> [!abstract] Summary
> Lecture 4.3 reduces the steady Euler equations, for small disturbances to a uniform stream, to one linear equation for a perturbation potential, $(1-M_\infty^2)\phi_{xx}+\phi_{yy}=0$, with the linearised pressure coefficient $C_p=-2u'/U_\infty$. Lecture 4.4 stretches the $y$-coordinate by $\beta=\sqrt{1-M_\infty^2}$ to turn this into Laplace's equation. The result is the Prandtl–Glauert rule: any incompressible thin-aerofoil $C_p$, $C_l$ or $C_m$ is divided by $\sqrt{1-M_\infty^2}$. Matching the corrected suction peak to the isentropic sonic $C_p$ then gives the critical Mach number, with the Kármán–Tsien rule as a better correction.

> [!summary]- Exam use: quick path
> - **Use it when:** you are given an incompressible $C_p$, $C_l$ or $C_m$ (thin-aerofoil theory, a low-speed test) and need its value at a subsonic $M_\infty$, or you need $M_{crit}$ from $C_{p0,min}$.
> - **Assumptions:** inviscid, irrotational, isentropic (shock-free); thin body, so $u',v'\ll U_\infty$; subsonic, and not near $M_\infty=1$ (the course says $M_\infty<0.8$ on the 4.4 title slide).
> - **Method:** 1. Get the incompressible value $C_{p0}$ (or $C_{l0}=2\pi\alpha$ for a flat plate). 2. Divide by $\beta=\sqrt{1-M_\infty^2}$. 3. For $M_{crit}$: write $C_{p0,min}/\sqrt{1-M^2}$ and $C_{p,cr}(M)$. 4. Find where they cross, by trial values or a plot. 5. Check $M_{crit}$ lies in the subsonic range where the rule is valid.
> - **Common mistakes:** multiplying by $\beta$ instead of dividing; using $C_{p,cr}$ with the local $M$ instead of $M=1$, or with $M_\infty$ in the wrong place.
> - **Practise:** [[#Worked example: Cp0,min = −0.4 (4.4 slides 8–9 and 11)|$M_{crit}$ for $C_{p0,min}=-0.4$]] · [[SESA3029 Example Sheet 2 - Solutions#Q6. Critical Mach number via Prandtl–Glauert|ES2 Q6]]

> [!info] Written ahead of the lecture
> This note is written from the 4.3 deck (8 slides) and the 4.4 deck (11 slides) before they have been lectured. The steps the slides skip are filled in, and the numbers are checked in Python. When the transcripts arrive, the note will be reconciled with what was actually said, and its status will change to `lectured`.

The CFD of [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils|4.2]] showed that at moderate subsonic Mach numbers the flow round an aerofoil looks like the incompressible flow, only stronger: the same smooth $C_p$ curve, with bigger peaks. That suggests the incompressible solution, which we can already compute (thin-aerofoil theory, panel methods, conformal mapping), might be corrected rather than thrown away. Lecture 4.3 makes this precise. A thin aerofoil disturbs the free stream only slightly, so the nonlinear Euler equations can be linearised about the uniform flow. Lecture 4.4 then shows that the linear compressible equation is Laplace's equation in disguise.

Two assumptions carry the whole chapter. The disturbances $u'$ and $v'$ are small compared with $U_\infty$, so products of them can be dropped. And the flow is isentropic and irrotational: no shocks, and therefore no entropy jumps or vorticity behind them. These are the same conditions as for the [[Homentropic Flow|homentropic flow]] of the MoC, and they fail exactly where the 4.2 CFD showed shocks.

## 1. Steady Euler equations in non-conservative form (4.3 slides 2–3)

Drop the time derivatives from the vector Euler equations of 4.1 (slide 2). The $x$-momentum equation is

$$
\frac{\partial(\rho u^2+p)}{\partial x}+\frac{\partial(\rho uv)}{\partial y}=0 .
$$

Write $\rho u^2=(\rho u)u$ and $\rho uv=(\rho v)u$, and use the product rule on each:

$$
\rho u\frac{\partial u}{\partial x}+u\frac{\partial(\rho u)}{\partial x}+\rho v\frac{\partial u}{\partial y}+u\frac{\partial(\rho v)}{\partial y}+\frac{\partial p}{\partial x}=0 .
$$

Group the two terms multiplied by $u$:

$$
\rho u\frac{\partial u}{\partial x}+\rho v\frac{\partial u}{\partial y}+u\left[\frac{\partial(\rho u)}{\partial x}+\frac{\partial(\rho v)}{\partial y}\right]+\frac{\partial p}{\partial x}=0 .
$$

The $y$-momentum equation, $\partial(\rho uv)/\partial x+\partial(\rho v^2+p)/\partial y=0$, expands the same way with $v$ outside the bracket:

$$
\rho u\frac{\partial v}{\partial x}+\rho v\frac{\partial v}{\partial y}+v\left[\frac{\partial(\rho u)}{\partial x}+\frac{\partial(\rho v)}{\partial y}\right]+\frac{\partial p}{\partial y}=0 .
$$

> [!warning] Slide 2 has $u$ outside the bracket in the $y$-momentum equation
> 4.3 slide 2 writes "$+u[\dots]$" in the $y$-momentum line. Expanding $\partial(\rho uv)/\partial x+\partial(\rho v^2)/\partial y$ gives $v[\partial(\rho u)/\partial x+\partial(\rho v)/\partial y]$ (checked symbolically). The bracket is zero anyway (next step), so the slip does not change the result.

Steady mass conservation is (slide 3)

$$
\frac{\partial(\rho u)}{\partial x}+\frac{\partial(\rho v)}{\partial y}=0
\quad\Longleftrightarrow\quad
u\frac{\partial\rho}{\partial x}+v\frac{\partial\rho}{\partial y}=-\rho\left(\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}\right).
$$

The left form makes both square brackets vanish, so

$$
\rho u\frac{\partial u}{\partial x}+\rho v\frac{\partial u}{\partial y}+\frac{\partial p}{\partial x}=0 \qquad (1)
$$

$$
\rho u\frac{\partial v}{\partial x}+\rho v\frac{\partial v}{\partial y}+\frac{\partial p}{\partial y}=0 \qquad (2)
$$

## 2. One equation for the velocity field (4.3 slides 3–4)

Take $u\times(1)+v\times(2)$ (slide 3):

$$
\rho u^2\frac{\partial u}{\partial x}+\rho uv\frac{\partial u}{\partial y}+\rho uv\frac{\partial v}{\partial x}+\rho v^2\frac{\partial v}{\partial y}=-u\frac{\partial p}{\partial x}-v\frac{\partial p}{\partial y}.
$$

Now use isentropic flow. Pressure and density are linked by $p=C\rho^\gamma$ everywhere, so any pressure gradient is $a^2$ times the density gradient, $\partial p/\partial x=a^2\,\partial\rho/\partial x$ with $a^2=(\partial p/\partial\rho)_s$:

$$
-u\frac{\partial p}{\partial x}-v\frac{\partial p}{\partial y}=-a^2\left(u\frac{\partial\rho}{\partial x}+v\frac{\partial\rho}{\partial y}\right).
$$

The right form of mass conservation replaces the bracket:

$$
-a^2\left(u\frac{\partial\rho}{\partial x}+v\frac{\partial\rho}{\partial y}\right)=a^2\rho\left(\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}\right).
$$

Divide by $\rho$ (slide 4):

$$
u^2\frac{\partial u}{\partial x}+uv\left(\frac{\partial u}{\partial y}+\frac{\partial v}{\partial x}\right)+v^2\frac{\partial v}{\partial y}=a^2\left(\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}\right).
$$

This is still exact for steady, isentropic, inviscid 2D flow. Density has disappeared; only velocities and the local speed of sound remain.

## 3. Linearising about the free stream (4.3 slides 4–5)

Let $u=U_\infty+u'$ and $v=v'$ with $u',v'\ll U_\infty$ (slide 4). $U_\infty$ is constant, so $\partial u/\partial x=\partial u'/\partial x$ and so on:

$$
(U_\infty+u')^2\frac{\partial u'}{\partial x}+(U_\infty+u')v'\left(\frac{\partial u'}{\partial y}+\frac{\partial v'}{\partial x}\right)+v'^2\frac{\partial v'}{\partial y}=a^2\left(\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}\right).
$$

On the left, expand $(U_\infty+u')^2=U_\infty^2+2U_\infty u'+u'^2$. Every term except $U_\infty^2\,\partial u'/\partial x$ is a product of at least two small quantities ($u'\,\partial u'/\partial x$, $v'\,\partial u'/\partial y$, $v'^2\,\partial v'/\partial y$, …). Drop them:

$$
U_\infty^2\frac{\partial u'}{\partial x}=a^2\left(\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}\right).
$$

The local $a^2$ still depends on the flow. The energy equation for steady adiabatic flow, $h+\tfrac12V^2=\text{const}$ with $h=c_pT=a^2/(\gamma-1)$, multiplied by $(\gamma-1)$, gives (slide 5)

$$
a_\infty^2+\frac{\gamma-1}{2}U_\infty^2=a^2+\frac{\gamma-1}{2}\left(u^2+v^2\right)=a^2+\frac{\gamma-1}{2}\left[(U_\infty+u')^2+v'^2\right].
$$

Expand the bracket:

$$
a_\infty^2+\frac{\gamma-1}{2}U_\infty^2=a^2+\frac{\gamma-1}{2}\left(U_\infty^2+2u'U_\infty+u'^2+v'^2\right).
$$

Cancel $\tfrac{\gamma-1}{2}U_\infty^2$ and drop $u'^2$ and $v'^2$:

$$
a^2=a_\infty^2-(\gamma-1)u'U_\infty .
$$

Substitute into the linearised equation:

$$
U_\infty^2\frac{\partial u'}{\partial x}=\left[a_\infty^2-(\gamma-1)u'U_\infty\right]\left(\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}\right).
$$

The $(\gamma-1)u'U_\infty$ term multiplies derivatives of small quantities, so it is second order. Drop it, divide by $a_\infty^2$ and use $M_\infty=U_\infty/a_\infty$:

$$
M_\infty^2\frac{\partial u'}{\partial x}=\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}.
$$

Rearrange:

$$
\boxed{(1-M_\infty^2)\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}=0}
$$

This is the linearised Euler equation of slide 5. From four nonlinear equations we have one linear one: *"Substantially reduced!"* (slide 4).

## 4. The velocity potential equation (4.3 slides 6–7)

Assume the flow is irrotational (slide 6). For homentropic flow this is consistent: shock-free flow from a uniform stream carries no vorticity.

$$
\omega=\frac{\partial v}{\partial x}-\frac{\partial u}{\partial y}=0
\quad\Rightarrow\quad
\frac{\partial v'}{\partial x}-\frac{\partial u'}{\partial y}=0 .
$$

Define a perturbation velocity potential $\phi$ with

$$
\frac{\partial\phi}{\partial x}=u',\qquad \frac{\partial\phi}{\partial y}=v'.
$$

Irrotationality is then automatic, because mixed partial derivatives commute:

$$
\frac{\partial v'}{\partial x}-\frac{\partial u'}{\partial y}=\frac{\partial^2\phi}{\partial x\,\partial y}-\frac{\partial^2\phi}{\partial y\,\partial x}=0 .
$$

Substituting $u'=\phi_x$ and $v'=\phi_y$ into the boxed equation gives the **linearised compressible potential equation** (see [[Linearised Compressible Potential Equation]]):

$$
\boxed{(1-M_\infty^2)\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0}
$$

Here $\phi$ is the potential of the **perturbation** velocity only; the full potential is $U_\infty x+\phi$.

Slide 7 lists what this equation can and cannot do.

- As $M_\infty\to0$ it reduces to Laplace's equation, the incompressible potential flow of [[Streamfunction and Velocity Potential]] and [[SESA3043 1.2b - Potential-Flow Review|SESA3043 1.2b]].
- It is not valid near $M_\infty=1$: *"we would have needed to carry around the next order of terms"*. The reason is visible in §3. The term we kept is $(1-M_\infty^2)\,\partial u'/\partial x$, and near $M_\infty=1$ its coefficient goes to zero, so it becomes no larger than the second-order terms we dropped. Keeping the largest of them gives what textbooks call the transonic small-disturbance equation, $[1-M_\infty^2-(\gamma+1)M_\infty^2u'/U_\infty]\,\partial u'/\partial x+\partial v'/\partial y=0$ (checked by expanding to second order). The course does not go this far.
- It is not applicable to hypersonic flow ($M_\infty>5$). There $M_\infty^2u'/U_\infty$ is no longer small even when $u'/U_\infty$ is.

The sign of $1-M_\infty^2$ decides the type of equation, and with it the solution method (slide 7):

| Regime on slide 7 | Type | Method |
|---|---|---|
| $M_\infty<0.9$ ("transonic" on the slide) | elliptic | Prandtl–Glauert transformation (§§6–8) |
| $M_\infty>1.1$ (supersonic) | hyperbolic | Ackeret theory ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils\|W07c]]) |

> [!note] What the course calls "transonic"
> The course calls the Prandtl–Glauert range "transonic", here and in the 4.4 title (*"Transonic Aerofoil Theory for $M_\infty<0.8$"*). Most textbooks call this range "subsonic compressible" and keep "transonic" for mixed flow, roughly $0.8<M_\infty<1.2$, where shocks appear and linear theory fails. The limits also differ between slides: $M_\infty<0.9$ and $M_\infty>1.1$ on 4.3 slide 7, but $M_\infty<0.8$ and $M_\infty>1.2$ on the 4.4 and 4.5 title slides. In the exam, use the course's words and quote the 4.4/4.5 limits as the safe range.

## 5. The linearised pressure coefficient (4.3 slide 8)

The pressure coefficient, with the dynamic pressure written in terms of $M_\infty$ ($\tfrac12\rho_\infty U_\infty^2=\tfrac12\gamma p_\infty M_\infty^2$, using $a_\infty^2=\gamma p_\infty/\rho_\infty$), is

$$
C_p=\frac{p-p_\infty}{\tfrac12\rho_\infty U_\infty^2}=\frac{2}{\gamma M_\infty^2}\left(\frac{p}{p_\infty}-1\right).
$$

Write the pressure ratio with the perfect-gas law and $a^2=\gamma RT$:

$$
\frac{p}{p_\infty}=\frac{\rho RT}{\rho_\infty RT_\infty}=\frac{\rho}{\rho_\infty}\,\frac{a^2}{a_\infty^2}.
$$

Isentropic flow has $p=C\rho^\gamma$, so $p/p_\infty=(\rho/\rho_\infty)^\gamma$. Dividing the two expressions gives $(\rho/\rho_\infty)^{\gamma-1}=a^2/a_\infty^2$, and so

$$
\frac{p}{p_\infty}=\left(\frac{a^2}{a_\infty^2}\right)^{\gamma/(\gamma-1)}.
$$

Use $a^2=a_\infty^2-(\gamma-1)u'U_\infty$ from §3, divided by $a_\infty^2$:

$$
\frac{p}{p_\infty}=\left[1-(\gamma-1)M_\infty^2\frac{u'}{U_\infty}\right]^{\gamma/(\gamma-1)}.
$$

The bracket is $1+x$ with $x$ small. The binomial expansion $(1+x)^n\approx1+nx$, with $n=\gamma/(\gamma-1)$:

$$
\frac{p}{p_\infty}\approx1-\gamma M_\infty^2\frac{u'}{U_\infty}.
$$

Substitute into $C_p$:

$$
C_p=\frac{2}{\gamma M_\infty^2}\left(-\gamma M_\infty^2\frac{u'}{U_\infty}\right)
\quad\Rightarrow\quad
\boxed{C_p=-\frac{2u'}{U_\infty}}
$$

$M_\infty$ has cancelled. The linearised $C_p$ looks exactly like the incompressible thin-aerofoil one of [[SESA2022 T4 - Thin Aerofoil Theory#Linearised pressure coefficient|SESA2022 T4]], but $u'$ now comes from the compressible equation.

## 6. The Prandtl–Glauert transformation (4.4 slides 2–3)

For $M_\infty<1$ write $\beta=\sqrt{1-M_\infty^2}$, so the potential equation is

$$
\beta^2\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0 .
$$

Define new variables (slide 2):

$$
\phi_0=\beta\phi,\qquad x_0=x,\qquad y_0=\beta y .
$$

Change variables one derivative at a time. Since $x_0=x$,

$$
\frac{\partial^2\phi}{\partial x^2}=\frac{1}{\beta}\frac{\partial^2\phi_0}{\partial x_0^2}.
$$

Since $y_0=\beta y$, the chain rule gives $\partial/\partial y=(\mathrm dy_0/\mathrm dy)\,\partial/\partial y_0=\beta\,\partial/\partial y_0$. Applying it twice:

$$
\frac{\partial^2\phi}{\partial y^2}=\beta^2\frac{\partial^2}{\partial y_0^2}\left(\frac{\phi_0}{\beta}\right)=\beta\frac{\partial^2\phi_0}{\partial y_0^2}.
$$

Substitute both:

$$
\beta^2\cdot\frac1\beta\frac{\partial^2\phi_0}{\partial x_0^2}+\beta\frac{\partial^2\phi_0}{\partial y_0^2}=0
\quad\Rightarrow\quad
\beta\left(\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\partial^2\phi_0}{\partial y_0^2}\right)=0 .
$$

For $M_\infty<1$, $\beta\neq0$, so

$$
\boxed{\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\partial^2\phi_0}{\partial y_0^2}=0}
$$

*"A simple transform takes us back to Laplace's equation"* (slide 2). The slide does this in one line by writing $\beta^2\phi_{xx}+\phi_{yy}$ as $\partial^2(\beta\phi)/\partial x^2+\partial^2(\beta\phi)/\partial(\beta y)^2$ after multiplying through by $\beta$.

What it means (slide 3): $\phi_0$ is an incompressible flow ($M_\infty\to0$) in the $(x_0,y_0)$ plane. Solve that problem, then transform back with $\phi=\phi_0/\beta$, $x=x_0$, $y=y_0/\beta$ to get the compressible solution in $(x,y)$.

> [!tip] Is it the same aerofoil? (not on the slides)
> Stretching $y$ looks as if it should make the incompressible aerofoil thinner. It does not, because thin-aerofoil theory applies the flow-tangency condition on the axis, $y=0$, not on the actual surface. For an aerofoil $y=f(x)$ the condition is $v'(x,0)=U_\infty f'(x)$, i.e. $\partial\phi/\partial y=U_\infty f'(x)$ at $y=0$. In the new variables
> $$\frac{\partial\phi}{\partial y}=\frac{\partial(\phi_0/\beta)}{\partial(y_0/\beta)}=\frac{\partial\phi_0}{\partial y_0},$$
> so the incompressible problem has $\partial\phi_0/\partial y_0=U_\infty f'(x_0)$ at $y_0=0$: the **same** slope distribution, so the same aerofoil. The Prandtl–Glauert rule therefore compares one aerofoil at two Mach numbers.

![[at_pg_wavy_wall.png|900]]

The figure shows the physical meaning on a wavy wall, for which the linear equation has an exact solution. Compressibility does two things: the pressure disturbance at the wall is $1/\beta$ times larger, and it reaches $1/\beta$ times further from the wall. At $M_\infty=0.8$ both factors are $1.67$.

## 7. The Prandtl–Glauert rule for Cp, Cl and Cm (4.4 slides 4–6)

For incompressible flow, Bernoulli gives (slide 4)

$$
p+\tfrac12\rho_\infty U^2=p_\infty+\tfrac12\rho_\infty U_\infty^2
\quad\Rightarrow\quad
C_p=1-\left(\frac{U}{U_\infty}\right)^2 .
$$

On a thin aerofoil $U\approx U_\infty+u_0'$ (the $v'^2$ contribution is second order):

$$
C_p=1-\left(\frac{U_\infty+u_0'}{U_\infty}\right)^2=1-1-\frac{2u_0'}{U_\infty}-\left(\frac{u_0'}{U_\infty}\right)^2 .
$$

Neglect the square:

$$
C_{p0}=-\frac{2u_0'}{U_\infty}=-\frac{2}{U_\infty}\frac{\partial\phi_0}{\partial x_0}.
$$

This has the same form as the compressible $C_p$ of §5. Now write the compressible $C_p$ in the transformed variables (slide 5):

$$
C_p=-\frac{2u'}{U_\infty}=-\frac{2}{U_\infty}\frac{\partial\phi}{\partial x}=-\frac{2}{U_\infty}\frac{\partial(\beta^{-1}\phi_0)}{\partial x_0}=-\frac{2}{\beta U_\infty}\frac{\partial\phi_0}{\partial x_0}.
$$

Compare with $C_{p0}$:

$$
\boxed{C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}}}
$$

Lift and moment coefficients are chordwise integrals of $C_p$, so the same factor comes straight through (slide 5):

$$
C_l=\frac{C_{l0}}{\sqrt{1-M_\infty^2}},\qquad C_m=\frac{C_{m0}}{\sqrt{1-M_\infty^2}} .
$$

Once an incompressible pressure coefficient is known, for example from thin-aerofoil theory, the compressible one is found *"simply by dividing it by $\sqrt{1-M_\infty^2}$"* (slide 5). Since $C_l$ and $C_m$ scale by the same factor, $x_{cp}=-C_m/C_l$ and the aerodynamic centre do not move: a thin aerofoil keeps its $c/4$ aerodynamic centre throughout the Prandtl–Glauert range. Compare this with the jump to $c/2$ at supersonic speed ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]).

![[at_compressibility_corrections.png|900]]

> [!check] A flat plate at $\alpha=4^\circ$, $M_\infty=0.7$ (suggested)
> $C_{l0}=2\pi\alpha=2\pi(0.06981)=0.4386$. Then $\beta=\sqrt{1-0.49}=0.7141$, and $C_l=0.4386/0.7141=0.6142$, a 40 % increase. The factor $1/\beta$ is $1.048$ at $M_\infty=0.3$, $1.155$ at $0.5$, $1.25$ at $0.6$ and $1.667$ at $0.8$.

Slide 6 plots $C_l/C_{l0}$ against $M_\infty$. It climbs slowly at first and steeply above 0.7, and it goes to infinity at $M_\infty=1$, which is not physical: the linear theory has broken down there (§4). In reality the lift rises a little more than this once a supersonic region develops, as seen in the 4.2 CFD (slide 6, citing 4.2).

## 8. Estimating the critical Mach number (4.4 slides 7–9)

Recall from [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#7. Flow regimes and the critical Mach number (4.2 slides 5–12)|4.2]] that $M_{crit}$ is the free-stream Mach number at which the local Mach number first reaches 1 somewhere on the surface. We need two relations between $C_p$ and Mach number.

**What $C_p$ corresponds to a local Mach number $M$?** The flow is isentropic from the free stream to the surface, so $p_0$ is the same at both. Write $p/p_\infty$ as a ratio of two isentropic stagnation ratios (slide 7):

$$
\frac{p}{p_\infty}=\frac{p_0/p_\infty}{p_0/p}=\left(\frac{1+\frac{\gamma-1}{2}M_\infty^2}{1+\frac{\gamma-1}{2}M^2}\right)^{\gamma/(\gamma-1)} .
$$

Substitute into $C_p=\frac{2}{\gamma M_\infty^2}\left(\frac{p}{p_\infty}-1\right)$. At $M_\infty=M_{crit}$ the local Mach number at the critical point is $M=1$, so $1+\frac{\gamma-1}{2}M^2=\frac{\gamma+1}{2}$:

$$
C_{p,cr}=\frac{2}{\gamma M_{crit}^2}\left[\left(\frac{1+\frac{\gamma-1}{2}M_{crit}^2}{1+\frac{\gamma-1}{2}}\right)^{\gamma/(\gamma-1)}-1\right].
$$

This exact isentropic relation depends only on the free-stream Mach number (and $\gamma$), not on the aerofoil.

**Where does the aerofoil reach it?** The point where $M=1$ is reached first is reasonably taken as the point of minimum $C_{p0}$, *"since the flow (incompressible) is fastest at this point"* (slide 8). Prandtl–Glauert gives the compressible $C_p$ there as $C_{p0,min}/\sqrt{1-M_\infty^2}$.

Setting the two equal gives one equation for $M_{crit}$ (slide 8):

$$
\boxed{\frac{C_{p0,min}}{\sqrt{1-M_{crit}^2}}=\frac{2}{\gamma M_{crit}^2}\left[\left(\frac{1+\frac{\gamma-1}{2}M_{crit}^2}{1+\frac{\gamma-1}{2}}\right)^{\gamma/(\gamma-1)}-1\right]}
$$

It has no closed-form solution. The lecturer's approach is to plot the left-hand side (LHS) and the right-hand side (RHS) against $M_\infty$ and read off the crossing (slide 9). In an exam, tabulate a few values and interpolate.

### Worked example: Cp0,min = −0.4 (4.4 slides 8–9 and 11)

*If $C_{p0,min}=-0.4$ in incompressible flow of air, estimate $M_{crit}$* (slide 8). Air, so $\gamma=1.4$ and $\gamma/(\gamma-1)=3.5$:

| $M_\infty$ | LHS: $-0.4/\sqrt{1-M_\infty^2}$ | RHS: $C_{p,cr}$ | LHS − RHS |
|---:|---:|---:|---:|
| 0.60 | −0.5000 | −1.2943 | +0.794 |
| 0.70 | −0.5601 | −0.7791 | +0.219 |
| 0.74 | −0.5947 | −0.6260 | +0.031 |
| 0.75 | −0.6047 | −0.5912 | −0.014 |

The sign changes between 0.74 and 0.75. Linear interpolation on LHS − RHS gives $0.74+0.01\times0.031/0.045=0.7469$, and the exact root is

$$
M_{crit}=0.747\qquad(\text{Prandtl–Glauert; slide 8}),
$$

with $C_p=-0.602$ at the critical point. Above this free-stream Mach number a supersonic region forms on the aerofoil.

![[at_critical_mach_number.png|900]]

> [!tip] Reading the plot
> $C_{p,cr}$ falls steeply in magnitude as $M_\infty$ rises: at high free-stream Mach number only a small speed-up is needed to reach $M=1$. Meanwhile the corrected suction peak grows. A more negative $C_{p0,min}$ (a thicker or more highly loaded aerofoil) meets the $C_{p,cr}$ curve earlier: $C_{p0,min}=-1.0$ gives $M_{crit}=0.606$. That is why thin aerofoils, and the flat-rooftop supercritical sections of 4.2, are used for high subsonic flight.

## 9. Improved correction: Kármán–Tsien (4.4 slides 10–11)

Prandtl–Glauert underestimates the compressible suction at higher subsonic Mach numbers. Slide 10 compares it with experiment and two refinements, the Kármán–Tsien (1939) and Laitone rules; only Kármán–Tsien is given as a formula:

$$
C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}+\dfrac{M_\infty^2}{1+\sqrt{1-M_\infty^2}}\,\dfrac{C_{p0}}{2}} .
$$

For a suction peak $C_{p0}<0$ the extra term makes the denominator smaller, so $|C_p|$ is larger than Prandtl–Glauert's. The experimental points on slide 10 sit between the two. Kármán–Tsien reduces to Prandtl–Glauert as $C_{p0}\to0$.

Repeating the critical-Mach calculation with Kármán–Tsien on the left-hand side (slide 11):

$$
M_{crit}=0.733\qquad(\text{Kármán–Tsien, }C_{p0,min}=-0.4),
$$

compared with $0.747$ from Prandtl–Glauert. The stronger suction is predicted to reach sonic conditions earlier. Check: at $M_\infty=0.733$, Kármán–Tsien gives $-0.649$ and $C_{p,cr}=-0.651$. For $C_{p0,min}=-1.0$ the two rules give 0.606 and 0.585.

## Problem-solving workflow

1. Identify the incompressible input: $C_{p0}$ at a point, $C_{p0,min}$, or $C_{l0}$ (e.g. $2\pi\alpha$ from thin-aerofoil theory).
2. Check validity: thin body, attached and shock-free, $M_\infty$ below about 0.8 (and below $M_{crit}$ for the rule to describe the real flow).
3. Scale by $1/\sqrt{1-M_\infty^2}$, or use Kármán–Tsien if asked.
4. For $M_{crit}$, tabulate LHS and RHS at three or four Mach numbers, find the sign change, and interpolate.
5. State the answer with the rule used, and $\gamma=1.4$.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| velocity potential equation; compressible potential equation | linearised small-perturbation potential equation; Prandtl–Glauert equation | 4.3 slides 6–7; 4.5 slide 2 | $\phi$ is the perturbation potential |
| linearised Euler equation | small-disturbance equation; linearised (small-perturbation) theory | 4.3 slide 5 | |
| transonic aerofoil theory ($M_\infty<0.8$) | subsonic compressible (linearised) theory | 4.4 title; 4.3 slide 7 ("Transonic ($M_\infty<0.9$)") | Textbooks keep "transonic" for mixed sub/supersonic flow (§4 note) |
| Prandtl–Glauert transformation | Prandtl–Glauert rule; Göthert's rule (3D); compressibility correction | 4.4 slides 1–5 | |
| Karman–Tsien (1939) | Kármán–Tsien rule; von Kármán–Tsien correction | 4.4 slides 10–11 | The slides drop the accent |
| $C_{p0}$ (incompressible) | $C_{p,0}$; $C_{p,inc}$ | 4.4 slides 4–8 | |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]] · Next: [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]
- New concepts: [[Linearised Compressible Potential Equation]] · [[Prandtl-Glauert Transformation]] · [[Critical Mach Number]]
- Earlier this module: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#4. Stagnation properties|W01 §4]] (isentropic ratios used for $C_{p,cr}$) · [[Homentropic Flow]] (the same assumption as the MoC)
- Earlier years and other modules: [[SESA2022 T4 - Thin Aerofoil Theory]] (the incompressible $C_{p0}$ and $C_{l0}=2\pi\alpha$) · [[Streamfunction and Velocity Potential]] · [[Laplace's Equation]] · [[SESA3043 1.2b - Potential-Flow Review|SESA3043 1.2b]] · [[SESA3043 2.3 - Panel Methods|SESA3043 2.3]] (panel-method $C_{p0}$ to correct)
- Worked sheet: [[SESA3029 Example Sheet 2 - Solutions#Q6. Critical Mach number via Prandtl–Glauert|ES2 Q6]] ($C_{p0,min}=-2.5$, $M_{crit}=0.448$)
- Formulae: [[SESA3029 Formula Sheet#Euler equations and compressible aerofoils (Lectures 4.1–4.6)|Formula sheet: Chapter 4]]

## Sources

- `Lecture4-3.pdf`: 4.3 Compressible Potential Flow Equations, 8 slides. Not yet lectured.
- `Lecture4-4.pdf`: 4.4 Prandtl-Glauert Transformation (Transonic Aerofoil Theory for $M_\infty<0.8$), 11 slides. Not yet lectured.
- Figures: `generate_aerothermo_w07_figures.py` (`at_pg_wavy_wall.png`, `at_compressibility_corrections.png`, `at_critical_mach_number.png`). Every number is computed in the script; the $M_{crit}$ roots match slides 9 and 11 (0.747, 0.733).
- Anderson, *Modern Compressible Flow*, Ch. 9 (linearised flow) and §11.4–11.6; *Fundamentals of Aerodynamics*, §§11.3–11.6.

## Self-study tasks

These decks have not been lectured, so every task is *suggested, not lecturer-set*. Tasks set in the lectures will be added when the transcripts arrive.

### Core

- [ ] Derive $(1-M_\infty^2)\phi_{xx}+\phi_{yy}=0$ from the steady Euler equations, stating where each assumption enters. → [[#1. Steady Euler equations in non-conservative form (4.3 slides 2–3)|§§1–4]]
- [ ] Derive $C_p=-2u'/U_\infty$, including the binomial step. → [[#5. The linearised pressure coefficient (4.3 slide 8)|§5]]
- [ ] Show that the Prandtl–Glauert transformation gives Laplace's equation and $C_p=C_{p0}/\sqrt{1-M_\infty^2}$. → [[#6. The Prandtl–Glauert transformation (4.4 slides 2–3)|§6]] and [[#7. The Prandtl–Glauert rule for Cp, Cl and Cm (4.4 slides 4–6)|§7]]
- [ ] Find $M_{crit}$ for $C_{p0,min}=-0.4$ by a table of LHS and RHS. Answer 0.747. → [[#Worked example: Cp0,min = −0.4 (4.4 slides 8–9 and 11)|§8]]
- [ ] Solve [[SESA3029 Example Sheet 2 - Solutions#Q6. Critical Mach number via Prandtl–Glauert|ES2 Q6]] ($C_{p0,min}=-2.5$). Answer 0.448.

### Further practice

- [ ] Redo the $C_{p0,min}=-0.4$ example with Kármán–Tsien. Answer 0.733. → [[#9. Improved correction: Kármán–Tsien (4.4 slides 10–11)|§9]]
- [ ] Explain why the linear equation fails near $M_\infty=1$ and for $M_\infty>5$. → [[#4. The velocity potential equation (4.3 slides 6–7)|§4]]
- [ ] Show that the boundary condition makes the transformed problem the same aerofoil. → [[#6. The Prandtl–Glauert transformation (4.4 slides 2–3)|§6, the tip]]
- [ ] Find the slide 2 slip in the $y$-momentum line and check that it does not change the result. → [[#1. Steady Euler equations in non-conservative form (4.3 slides 2–3)|§1]]
- [ ] $M_{crit}$ for $C_{p0,min}=-1.0$: 0.606 (P–G) and 0.585 (K–T). → [[#8. Estimating the critical Mach number (4.4 slides 7–9)|§8]]
