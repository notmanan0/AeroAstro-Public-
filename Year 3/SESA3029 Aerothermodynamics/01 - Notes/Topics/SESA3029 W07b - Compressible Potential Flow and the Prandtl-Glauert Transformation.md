---
title: "SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 4: High-speed aerodynamics"
order: 8
tags: [sesa3029, compressible-flow, potential-flow, linearisation, prandtl-glauert, karman-tsien, critical-mach-number]
aliases: ["SESA3029 Lecture 4.3", "SESA3029 Lecture 4.4", "SESA3029 W07b"]
date: 2026-11-03
status: lectured
coverage: "Lecture 4.3 (§§1–5, Fri 6 Nov) and Lecture 4.4 (§§6–9, Mon 9 Nov), both lectured and checked against their transcripts; every slide covered"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[Streamfunction and Velocity Potential]]"]
next_topics: ["[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
key_concepts: ["[[Linearised Compressible Potential Equation]]", "[[Prandtl-Glauert Transformation]]", "[[Critical Mach Number]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture4-3.pdf", "02 - Sources/Lectures/Lecture4-4.pdf", "02 - Sources/Lectures/06 November 2026 at 16_57_37.txt", "02 - Sources/Lectures/Lecture 4-4.txt"]
---

# SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation

> [!abstract] Summary
> For small disturbances to a uniform stream, the steady Euler equations reduce to one linear equation for a perturbation potential, $(1-M_\infty^2)\phi_{xx}+\phi_{yy}=0$, with the linearised pressure coefficient $C_p=-2u'/U_\infty$. For $M_\infty<1$ the change of variables $\phi_0=\beta\phi$, $y_0=\beta y$, with $\beta=\sqrt{1-M_\infty^2}$, turns it into Laplace's equation, so an incompressible thin-aerofoil $C_p$, $C_l$ or $C_m$ becomes the compressible one on division by $\beta$: the Prandtl–Glauert rule, which does not apply to drag. Matching the corrected suction peak to the isentropic sonic $C_p$ gives the critical Mach number, 0.747 for $C_{p0,min}=-0.4$, or 0.733 with the Kármán–Tsien correction.

> [!summary]- Exam use: quick path
> - **Use it when:** you are given an incompressible $C_p$, $C_l$ or $C_m$ (thin-aerofoil theory, a panel method, a low-speed test) and need its value at a subsonic $M_\infty$, or you need $M_{crit}$ from $C_{p0,min}$.
> - **Assumptions:** inviscid, irrotational, isentropic (shock-free, so below $M_{crit}$ for the real flow); thin body, so $u',v'\ll U_\infty$; $M_\infty<0.8$ (4.4 title slide); $\gamma=1.4$ for air in $C_{p,cr}$.
> - **Method:** 1. Get the incompressible value $C_{p0}$ (or $C_{l0}=2\pi\alpha$ for a flat plate, $\alpha$ in radians). 2. Divide by $\beta=\sqrt{1-M_\infty^2}$. 3. For $M_{crit}$: write LHS $=C_{p0,min}/\sqrt{1-M^2}$ and RHS $=C_{p,cr}(M)$. 4. Evaluate both at two or three trial Mach numbers, find where LHS − RHS changes sign and interpolate linearly. 5. Check $M_{crit}$ lies below about 0.8.
> - **Common mistakes:** multiplying by $\beta$ instead of dividing, or dividing $C_d$ by $\beta$ too; putting the local Mach number into $C_{p,cr}$ where $M=1$ belongs (the free-stream Mach number in $C_{p,cr}$ is the unknown $M_{crit}$).
> - **Practise:** [[#Worked example: Cp0,min = −0.4 (4.4 slides 8–9 and 11)|$M_{crit}$ for $C_{p0,min}=-0.4$]] · [[SESA3029 Example Sheet 2 - Solutions#Q6. Critical Mach number via Prandtl–Glauert|ES2 Q6]]

Euler CFD of an aerofoil at moderate subsonic Mach numbers ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils|4.2]]) gives a $C_p$ curve that looks like the incompressible one, only stronger: the same smooth shape, with bigger peaks. The incompressible solution, which thin-aerofoil theory, panel methods and conformal mapping already provide, can therefore be corrected instead of solving the compressible problem from scratch. A thin aerofoil disturbs the free stream only slightly, so the nonlinear Euler equations can be linearised about the uniform flow (§§1–5). For subsonic flow the resulting linear equation is Laplace's equation in a rescaled coordinate system (§6), every incompressible pressure, lift and moment coefficient carries over by one division (§7), and the same pieces give an estimate of the critical Mach number without any CFD (§§8–9).

Two assumptions carry the whole chapter. The disturbances $u'$ and $v'$ are small compared with $U_\infty$, so products of them can be dropped. And the flow is isentropic and irrotational: no shocks, and therefore no entropy jumps or vorticity behind them. These are the same conditions as for the [[Homentropic Flow|homentropic flow]] of the MoC, and they fail where shocks appear in the 4.2 CFD.

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

The flow is isentropic, so pressure and density are linked by $p=C\rho^\gamma$ everywhere (L4-3, ll. 104–116). Differentiate:

$$
\mathrm dp=\gamma C\rho^{\gamma-1}\,\mathrm d\rho=\gamma\,\frac{C\rho^\gamma}{\rho}\,\mathrm d\rho=\gamma\frac{p}{\rho}\,\mathrm d\rho .
$$

With $p=\rho RT$, $\gamma p/\rho=\gamma RT=a^2$, so $\mathrm dp=a^2\,\mathrm d\rho$. Any pressure gradient is therefore $a^2$ times the density gradient, $\partial p/\partial x=a^2\,\partial\rho/\partial x$, and (1) can equally be written $\rho u\,\partial u/\partial x+\rho v\,\partial u/\partial y=-a^2\,\partial\rho/\partial x$. Multiplying out the right-hand side of the combined equation:

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

This is still exact for steady, isentropic, inviscid 2D flow. Continuity and the two momentum equations have been combined into one (L4-3, ll. 145–147). Density has disappeared; only velocities and the local speed of sound remain.

## 3. Linearising about the free stream (4.3 slides 4–5)

Let $u=U_\infty+u'$ and $v=v'$ with $u',v'\ll U_\infty$ (slide 4). $U_\infty$ is constant, so $\partial u/\partial x=\partial u'/\partial x$ and so on:

$$
(U_\infty+u')^2\frac{\partial u'}{\partial x}+(U_\infty+u')v'\left(\frac{\partial u'}{\partial y}+\frac{\partial v'}{\partial x}\right)+v'^2\frac{\partial v'}{\partial y}=a^2\left(\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}\right).
$$

On the left, expand $(U_\infty+u')^2=U_\infty^2+2U_\infty u'+u'^2$. Every term except $U_\infty^2\,\partial u'/\partial x$ is a product of at least two small quantities ($u'\,\partial u'/\partial x$, $v'\,\partial u'/\partial y$, $v'^2\,\partial v'/\partial y$, …). Drop them:

$$
U_\infty^2\frac{\partial u'}{\partial x}=a^2\left(\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}\right).
$$

Collected on one side, this is $(a^2-U_\infty^2)\,\partial u'/\partial x+a^2\,\partial v'/\partial y=0$ (L4-3, ll. 211–216). It already looks linear, since no products of $u'$ and $v'$ are left, but the local $a^2$ still depends on the flow. The energy equation for steady adiabatic flow, $h+\tfrac12V^2=\text{const}$ with $h=c_pT=a^2/(\gamma-1)$, multiplied by $(\gamma-1)$, gives (slide 5)

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

The $(\gamma-1)u'U_\infty$ term multiplies derivatives of small quantities, so it is second order. Drop it, divide by $a_\infty^2$ and use $M_\infty=U_\infty/a_\infty$.

In the expression for $a^2$ itself, $(\gamma-1)u'U_\infty$ is first order and is kept. It only becomes negligible here, where it multiplies $\partial u'/\partial x+\partial v'/\partial y$. Dropping it from $a^2$ earlier would not change this equation, but the first-order $a^2$ is needed again for the pressure coefficient in §5 (L4-3, ll. 268–286). Then:

$$
M_\infty^2\frac{\partial u'}{\partial x}=\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}.
$$

Rearrange:

$$
\boxed{(1-M_\infty^2)\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}=0}
$$

This is the linearised Euler equation (slide 5): four nonlinear equations have become one linear one. The dropped second- and third-order terms are one reason the aerofoil theories built on this equation (4.4–4.6) are approximate; keeping the second-order terms gives better theories (L4-3, ll. 289–299), including the transonic small-disturbance equation of §4 near $M_\infty=1$.

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

Here $\phi$ is the potential of the **perturbation** velocity only; the full potential is $U_\infty x+\phi$. The linearised Euler equation was one equation in two unknowns, $u'$ and $v'$, so on its own it was not a determinate system. The potential turns it into one equation in one unknown (L4-3, ll. 320–327).

The equation has three limits (slide 7).

- As $M_\infty\to0$ it reduces to Laplace's equation, the incompressible potential flow of [[Streamfunction and Velocity Potential]] and [[SESA3043 1.2b - Potential-Flow Review|SESA3043 1.2b]].
- It is not valid near $M_\infty=1$, where the next order of terms would be needed. The reason is visible in §3. The term kept is $(1-M_\infty^2)\,\partial u'/\partial x$, and near $M_\infty=1$ its coefficient goes to zero, so it becomes no larger than the second-order terms that were dropped. Keeping the largest of them gives the transonic small-disturbance equation (the textbook name; not lectured), $[1-M_\infty^2-(\gamma+1)M_\infty^2u'/U_\infty]\,\partial u'/\partial x+\partial v'/\partial y=0$ (checked by expanding to second order).
- It is not applicable to hypersonic flow ($M_\infty>5$). There $M_\infty^2u'/U_\infty$ is no longer small even when $u'/U_\infty$ is.

The sign of $1-M_\infty^2$ decides the type of equation, and with it the solution method (slide 7):

| Regime on slide 7 | Type | Method |
|---|---|---|
| $M_\infty<0.9$ ("transonic" on the slide) | elliptic | Prandtl–Glauert transformation (§§6–8) |
| $M_\infty>1.1$ (supersonic) | hyperbolic | Ackeret theory ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils\|W07c]]) |

In the hyperbolic case a quantity is constant along the Mach lines, the same structure as in the [[SESA3029 W05a - Method of Characteristics|method of characteristics]] (L4-3, ll. 380–383).

> [!note] The word *transonic* in this chapter
> The Prandtl–Glauert range is labelled *transonic* (4.3 slide 7, and the 4.4 title, *Transonic Aerofoil Theory for $M_\infty<0.8$*). Most textbooks call this range subsonic compressible and keep *transonic* for mixed flow, roughly $0.8<M_\infty<1.2$, where shocks appear and linear theory fails. The quoted limits also vary: $M_\infty<0.9$ and $M_\infty>1.1$ on 4.3 slide 7; 0.8 and 1.2 on the 4.4 and 4.5 title slides and in L4-3 (ll. 368–378). For Prandtl–Glauert the working limit is about 0.8, which can be pushed to 0.85–0.9 with quickly falling accuracy (L4-4, ll. 25–27). In the exam, use the slides' word and quote 0.8 and 1.2 as the safe range.

## 5. The linearised pressure coefficient (4.3 slide 8)

$C_p$ is what lift and drag are built from, so the linearised theory needs it (L4-3, ll. 339–351). Start from the definition and take $p_\infty$ outside the bracket:

$$
C_p=\frac{p-p_\infty}{\tfrac12\rho_\infty U_\infty^2}=\frac{p_\infty}{\tfrac12\rho_\infty U_\infty^2}\left(\frac{p}{p_\infty}-1\right).
$$

Write $p_\infty=\rho_\infty RT_\infty$; the densities cancel and the 2 moves up:

$$
\frac{p_\infty}{\tfrac12\rho_\infty U_\infty^2}=\frac{2RT_\infty}{U_\infty^2}.
$$

Multiply top and bottom by $\gamma$ and use $a_\infty^2=\gamma RT_\infty$:

$$
\frac{2\gamma RT_\infty}{\gamma U_\infty^2}=\frac{2a_\infty^2}{\gamma U_\infty^2}=\frac{2}{\gamma M_\infty^2},
\qquad\text{so}\qquad
C_p=\frac{2}{\gamma M_\infty^2}\left(\frac{p}{p_\infty}-1\right).
$$

This rewriting was a question on the 2025–26 exam paper (L4-3, ll. 391–417).

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

$M_\infty$ has cancelled. The linearised $C_p$ looks exactly like the incompressible thin-aerofoil one of [[SESA2022 T4 - Thin Aerofoil Theory#Linearised pressure coefficient|SESA2022 T4]], but $u'$ now comes from the compressible equation. Starting from Bernoulli and applying the same small-perturbation argument gives the identical expression ([[#7. The Prandtl–Glauert rule for Cp, Cl and Cm (4.4 slides 4–6)|§7]] does this), so there is no break between low-speed and high-speed $C_p$ at this order (L4-3, ll. 476–479). This is the $C_p$ used for the surface pressure, lift and drag in 4.4–4.6.

## 6. The Prandtl–Glauert transformation (4.4 slides 2–3)

For $M_\infty<1$ write $\beta=\sqrt{1-M_\infty^2}$, which is real and positive, so the potential equation is

$$
\beta^2\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0 .
$$

Define new variables (slide 2):

$$
\phi_0=\beta\phi,\qquad x_0=x,\qquad y_0=\beta y .
$$

The streamwise coordinate is unchanged, and the normal coordinate is shrunk by the factor $\beta<1$. Change variables one derivative at a time. Since $x_0=x$,

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

A shorter route gives the one-line form on slide 2. Divide $\beta^2\phi_{xx}+\phi_{yy}=0$ by $\beta$:

$$
\beta\frac{\partial^2\phi}{\partial x^2}+\frac{1}{\beta}\frac{\partial^2\phi}{\partial y^2}=0 .
$$

$\beta$ is a constant, so it can go inside the derivatives. In the first term $\beta\,\phi_{xx}=\partial^2(\beta\phi)/\partial x^2$. In the second, $\partial/\partial(\beta y)=\beta^{-1}\,\partial/\partial y$, so $\partial^2(\beta\phi)/\partial(\beta y)^2=\beta\cdot\beta^{-2}\phi_{yy}=\beta^{-1}\phi_{yy}$. Hence

$$
\frac{\partial^2(\beta\phi)}{\partial x^2}+\frac{\partial^2(\beta\phi)}{\partial(\beta y)^2}=0 ,
$$

which is Laplace's equation for $\phi_0=\beta\phi$ in $x_0=x$, $y_0=\beta y$.

A solution of Laplace's equation is an incompressible potential flow ($M_\infty\to0$), so $\phi_0$ is an incompressible flow in the $(x_0,y_0)$ plane (slide 3). It is the equation thin-aerofoil theory is built on ([[SESA2022 T4 - Thin Aerofoil Theory]]). Solve that problem, or take an existing solution, then transform back with $\phi=\phi_0/\beta$, $x=x_0$, $y=y_0/\beta$ to get the compressible solution in $(x,y)$. The compressible problem never has to be solved separately: one incompressible solution covers every subsonic Mach number up to about 0.8, and the conversion is a single division by $\beta$ with no further dependence on $\alpha$ or the aerofoil shape.

> [!tip] The transformed problem is the same aerofoil
> Shrinking the normal coordinate ($y_0=\beta y$) looks as if it should make the incompressible aerofoil thinner. It does not, because thin-aerofoil theory applies the flow-tangency condition on the axis, $y=0$, not on the actual surface. For an aerofoil $y=f(x)$ the condition is $v'(x,0)=U_\infty f'(x)$, i.e. $\partial\phi/\partial y=U_\infty f'(x)$ at $y=0$. In the new variables
> $$\frac{\partial\phi}{\partial y}=\frac{\partial(\phi_0/\beta)}{\partial(y_0/\beta)}=\frac{\partial\phi_0}{\partial y_0},$$
> so the incompressible problem has $\partial\phi_0/\partial y_0=U_\infty f'(x_0)$ at $y_0=0$: the **same** slope distribution, so the same aerofoil. The Prandtl–Glauert rule therefore compares one aerofoil at two Mach numbers.

![[at_pg_wavy_wall.png|900]]

On a wavy wall, for which the linear equation has an exact solution, compressibility does two things: the pressure disturbance at the wall is $1/\beta$ times larger, and it reaches $1/\beta$ times further from the wall. At $M_\infty=0.8$ both factors are $1.67$.

## 7. The Prandtl–Glauert rule for Cp, Cl and Cm (4.4 slides 4–6)

For incompressible flow, Bernoulli gives (slide 4)

$$
p+\tfrac12\rho_\infty U^2=p_\infty+\tfrac12\rho_\infty U_\infty^2 ,
$$

with the same density $\rho_\infty$ on both sides, since it is constant everywhere. Move $p_\infty$ to the left and divide by $\tfrac12\rho_\infty U_\infty^2$:

$$
C_p=\frac{p-p_\infty}{\tfrac12\rho_\infty U_\infty^2}=1-\left(\frac{U}{U_\infty}\right)^2 .
$$

On a thin aerofoil $U\approx U_\infty+u_0'$ (the $v'^2$ contribution is second order):

$$
C_p=1-\left(\frac{U_\infty+u_0'}{U_\infty}\right)^2=1-1-\frac{2u_0'}{U_\infty}-\left(\frac{u_0'}{U_\infty}\right)^2 .
$$

Neglect the square:

$$
C_{p0}=-\frac{2u_0'}{U_\infty}=-\frac{2}{U_\infty}\frac{\partial\phi_0}{\partial x_0}.
$$

This has the same form as the compressible $C_p$ of §5.

> [!warning] The subscript 0 means incompressible
> In $C_{p0}$, $u_0'$, $\phi_0$, $C_{l0}$ and $C_{m0}$ the subscript 0 marks the incompressible solution ($M_\infty\to0$), not stagnation conditions (L4-4, ll. 126–128). §8 uses $p_0$ for the stagnation pressure in the same working as $C_{p0,min}$, so both meanings appear side by side there.

The compressible $C_p$ of §5, written in the transformed variables with $\phi=\phi_0/\beta$ and $x=x_0$ (slide 5), is

$$
C_p=-\frac{2u'}{U_\infty}=-\frac{2}{U_\infty}\frac{\partial\phi}{\partial x}=-\frac{2}{U_\infty}\frac{\partial(\beta^{-1}\phi_0)}{\partial x_0}=-\frac{2}{\beta U_\infty}\frac{\partial\phi_0}{\partial x_0}.
$$

Compare with $C_{p0}$:

$$
\boxed{C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}}}
$$

Once an incompressible pressure coefficient is known, for example from thin-aerofoil theory or a panel method, the compressible one at the same point follows by dividing by $\sqrt{1-M_\infty^2}$ (slide 5).

### Lift and moment coefficients (4.4 slide 5)

The $C_p$ rule holds point by point. $C_l$ and $C_m$ follow only after integrating over the chord, and that step needs the definitions of the force coefficients.

Put $x$ along the chord from the leading edge ($x=0$) to the trailing edge ($x=c$), with the free stream at angle $\alpha$ to it. Per unit span, the pressure on the upper surface pushes down and the pressure on the lower surface pushes up. A surface element whose projection on the chord is $\mathrm dx$ carries a force normal to the chord of $p\,\mathrm dx$, so the force normal to the chord is

$$
N'=\int_0^c\left(p_l-p_u\right)\mathrm dx .
$$

This is the **normal force**, perpendicular to the chord, not the lift, which is perpendicular to the free stream (L4-4, ll. 150–156). With the chordwise force $F_t'$ of [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#2. Aerodynamic review and the low-speed baseline|W01 §2]],

$$
L'=N'\cos\alpha-F_t'\sin\alpha .
$$

For small $\alpha$, $\cos\alpha\approx1$, and $F_t'\sin\alpha$ is second order because $F_t'$ is itself at most of order $N'\alpha$. So to first order $L'\approx N'$. Subtract $p_\infty$ from both pressures; it cancels:

$$
L'\approx\int_0^c\left[(p_l-p_\infty)-(p_u-p_\infty)\right]\mathrm dx .
$$

Divide by $\tfrac12\rho_\infty U_\infty^2c$:

$$
C_l=\frac{L'}{\tfrac12\rho_\infty U_\infty^2c}\approx\frac1c\int_0^c\left(C_{p,l}-C_{p,u}\right)\mathrm dx .
$$

Insert the Prandtl–Glauert rule at each $x$, $C_{p,l}=C_{p0,l}/\beta$ and $C_{p,u}=C_{p0,u}/\beta$. $\beta$ does not vary along the chord, so it comes out of the integral:

$$
C_l=\frac1\beta\cdot\frac1c\int_0^c\left(C_{p0,l}-C_{p0,u}\right)\mathrm dx=\frac{C_{l0}}{\beta}.
$$

The step works because $x_0=x$: the chordwise variable and its limits, 0 to $c$, are the same in both problems.

The moment about the leading edge (nose-up positive, as in W01 §2) follows the same way. The upward force $(p_l-p_u)\,\mathrm dx$ at a distance $x$ aft of the leading edge gives a nose-down moment:

$$
M_{LE}'=-\int_0^c\left(p_l-p_u\right)x\,\mathrm dx .
$$

The chordwise force acts along the chord line of a thin aerofoil, so to first order it has no moment about the leading edge. Subtract $p_\infty$ and divide by $\tfrac12\rho_\infty U_\infty^2c^2$:

$$
C_{m,LE}=-\frac{1}{c^2}\int_0^c\left(C_{p,l}-C_{p,u}\right)x\,\mathrm dx=\frac{C_{m0,LE}}{\beta}.
$$

So (slide 5)

$$
\boxed{C_l=\frac{C_{l0}}{\sqrt{1-M_\infty^2}},\qquad C_m=\frac{C_{m0}}{\sqrt{1-M_\infty^2}}}
$$

Since $C_{m,x}=C_{m,LE}+(x/c)C_n$ (W01 §2), the moment about any point on the chord scales by the same factor. The ratios $x_{CP}/c=-C_{m,LE}/C_n$ and $x_{AC}/c=-\mathrm dC_{m,LE}/\mathrm dC_n$ are therefore unchanged: a thin aerofoil keeps its $c/4$ aerodynamic centre ([[SESA2022 T4 - Thin Aerofoil Theory#6. Moments, aerodynamic centre, centre of pressure|SESA2022 T4 §6]]) throughout the Prandtl–Glauert range. Compare this with the jump to $c/2$ at supersonic speed ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]).

> [!check] A flat plate at $\alpha=4^\circ$, $M_\infty=0.7$
> Thin-aerofoil theory gives $\mathrm dC_l/\mathrm d\alpha=2\pi$ for a symmetric section ([[SESA2022 T4 - Thin Aerofoil Theory#4. Symmetric aerofoil (flat plate)|SESA2022 T4 §4]]), so $C_{l0}=2\pi\alpha=2\pi(0.06981)=0.4386$, with $\alpha$ in radians. Then $\beta=\sqrt{1-0.49}=0.7141$, and $C_l=2\pi\alpha/\sqrt{1-M_\infty^2}=0.4386/0.7141=0.6142$, a 40 % increase. The factor $1/\beta$ is $1.048$ at $M_\infty=0.3$, $1.155$ at $0.5$, $1.25$ at $0.6$, $1.400$ at $0.7$ and $1.667$ at $0.8$.

### Lift against Mach number (4.4 slide 6)

![[at_compressibility_corrections.png|900]]

The ratio $C_l/C_{l0}=1/\sqrt{1-M_\infty^2}$ is 1 at $M_\infty=0$, climbs slowly at first and steeply above 0.7, and reaches 1.67 at $M_\infty=0.8$ (slide 6; right panel above). It goes to infinity at $M_\infty=1$, which is not physical: the linear theory has broken down there (§4).

The Euler CFD lift curve of 4.2 ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#8. Lift, drag and the mechanism of drag divergence (4.2 slides 13–15)|W07a §8]]) follows this curve through the subsonic range, up to a critical Mach number of roughly 0.75–0.8 for that aerofoil. A trend that would otherwise take a series of CFD runs or wind-tunnel tests comes from one formula (L4-4, ll. 207–227).

Once a supersonic region forms on the upper surface, the lift rises further than Prandtl–Glauert predicts (slide 6). Behind the sonic point the flow keeps accelerating, as supersonic flow does in the diverging part of a converging–diverging nozzle (W07a §8), so the pressure on the upper surface falls further and pulls the aerofoil up harder. The same low pressure acts on the rearward-facing part of the surface and is ended by a shock, so the drag rises too, and faster than the lift: $C_l/C_d$ is lower in the transonic range than at subsonic speed (L4-4, ll. 195–206).

### Drag does not follow the rule

There is no rule $C_d=C_{d0}/\sqrt{1-M_\infty^2}$ (L4-4, ll. 180–186). Drag is the force along the free stream. For a thin aerofoil it comes from the pressure acting on the forward- and rearward-facing parts of the surface, and from skin friction. The pressure part needs the surface slopes, not only the chordwise positions, so it is an integral over $y$ ($\oint p\,\mathrm dy$ around the surface) rather than over $x$.

Take $x$ along the free stream and the surfaces $y_u(x)$ and $y_l(x)$. On the upper surface the pressure on an element pushes rearward with $p\,\mathrm dy_u=p\,(\mathrm dy_u/\mathrm dx)\,\mathrm dx$ where the surface faces forward; on the lower surface the rearward push is $-p\,\mathrm dy_l$. So

$$
D_p'=\int_0^c\left(p_u\frac{\mathrm dy_u}{\mathrm dx}-p_l\frac{\mathrm dy_l}{\mathrm dx}\right)\mathrm dx .
$$

A uniform pressure exerts no net force on a closed body. The thickness $y_u-y_l$ is zero at both edges, so

$$
\int_0^c p_\infty\left(\frac{\mathrm dy_u}{\mathrm dx}-\frac{\mathrm dy_l}{\mathrm dx}\right)\mathrm dx=p_\infty\Big[y_u-y_l\Big]_0^c=0 .
$$

Subtract it and divide by $\tfrac12\rho_\infty U_\infty^2c$:

$$
C_{d,p}=\frac1c\int_0^c\left(C_{p,u}\frac{\mathrm dy_u}{\mathrm dx}-C_{p,l}\frac{\mathrm dy_l}{\mathrm dx}\right)\mathrm dx .
$$

In the linear theory the slopes are the same in both problems ([[#6. The Prandtl–Glauert transformation (4.4 slides 2–3)|§6]], the tip), so formally this integral also picks up $1/\beta$. What it scales is zero. Inviscid, shock-free flow round a closed 2D aerofoil has no drag (d'Alembert's paradox; on a flat plate the leading-edge suction of W01 §2 cancels the rearward tilt of the normal force). The subcritical compressible flow is a transformed incompressible one, so its inviscid drag is zero as well.

The drag of a real aerofoil below $M_{crit}$ is skin friction and the pressure drag of the boundary layer and wake, which the inviscid transformation does not describe. The drag coefficient stays nearly constant as $M_\infty$ rises towards $M_{crit}$ and then rises steeply (drag divergence, W07a §8). The Prandtl–Glauert rule therefore covers $C_p$, $C_l$ and $C_m$ only.

## 8. Estimating the critical Mach number (4.4 slides 7–9)

$M_{crit}$ is the free-stream Mach number at which the local Mach number first reaches 1 somewhere on the surface ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#7. Flow regimes and the critical Mach number (4.2 slides 5–12)|W07a §7]]). Finding it by CFD or in a wind tunnel takes a sequence of runs, raising or lowering $M_\infty$ until the peak surface Mach number is just 1. Two relations between $C_p$ and Mach number give an estimate directly.

The first is the $C_p$ at which the local flow is sonic. The flow is isentropic from the free stream to the surface, so $p_0$, the stagnation pressure, is the same at both. Write $p/p_\infty$ as a ratio of two isentropic stagnation ratios ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#4. Stagnation properties|W01 §4]]; slide 7):

$$
\frac{p}{p_\infty}=\frac{p_0/p_\infty}{p_0/p}=\left(\frac{1+\frac{\gamma-1}{2}M_\infty^2}{1+\frac{\gamma-1}{2}M^2}\right)^{\gamma/(\gamma-1)} .
$$

The numerator uses the free-stream Mach number and the denominator the local one. Substitute into $C_p=\frac{2}{\gamma M_\infty^2}\left(\frac{p}{p_\infty}-1\right)$. At $M_\infty=M_{crit}$ the local Mach number at the critical point is $M=1$, so $1+\frac{\gamma-1}{2}M^2=\frac{\gamma+1}{2}$:

$$
C_{p,cr}=\frac{2}{\gamma M_{crit}^2}\left[\left(\frac{1+\frac{\gamma-1}{2}M_{crit}^2}{1+\frac{\gamma-1}{2}}\right)^{\gamma/(\gamma-1)}-1\right].
$$

This exact isentropic relation depends only on the free-stream Mach number (and $\gamma$), not on the aerofoil.

The second is the aerofoil's own $C_p$ at that point. The point where $M=1$ is reached first is taken as the point of minimum $C_{p0}$, where the incompressible flow is fastest (slide 8). Prandtl–Glauert gives the compressible $C_p$ there as $C_{p0,min}/\sqrt{1-M_\infty^2}$.

Setting the two equal gives one equation for $M_{crit}$ (slide 8):

$$
\boxed{\frac{C_{p0,min}}{\sqrt{1-M_{crit}^2}}=\frac{2}{\gamma M_{crit}^2}\left[\left(\frac{1+\frac{\gamma-1}{2}M_{crit}^2}{1+\frac{\gamma-1}{2}}\right)^{\gamma/(\gamma-1)}-1\right]}
$$

It has no closed-form solution. Plot the left-hand side (LHS) and the right-hand side (RHS) against $M_\infty$ and read off the crossing (slide 9), or use a root-finding method: by hand, evaluate both sides at two trial Mach numbers either side of the root and interpolate linearly (L4-4, ll. 263–265).

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

Prandtl–Glauert underestimates the compressible suction at higher subsonic Mach numbers. The Kármán–Tsien rule (1939), about a decade after Prandtl–Glauert (1928), adds a term to the denominator (slide 10):

$$
C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}+\dfrac{M_\infty^2}{1+\sqrt{1-M_\infty^2}}\,\dfrac{C_{p0}}{2}} .
$$

For a suction peak, $C_{p0}<0$, the extra term is negative, so the denominator is smaller and $|C_p|$ is larger than Prandtl–Glauert's. As $C_{p0}\to0$ the extra term vanishes and Kármán–Tsien reduces to Prandtl–Glauert, so the two differ most at strong suction peaks and high $M_\infty$. Measured $C_p$ (slide 10) lies above the Prandtl–Glauert curve, close to Kármán–Tsien, and at the highest Mach numbers between Kármán–Tsien and a third, more complicated correction, Laitone's, which is not lectured.

With Kármán–Tsien on the left-hand side (slide 11), $C_{p0,min}=-0.4$, $\gamma=1.4$:

| $M_\infty$ | LHS: Kármán–Tsien | RHS: $C_{p,cr}$ | LHS − RHS |
|---:|---:|---:|---:|
| 0.70 | −0.6089 | −0.7791 | +0.170 |
| 0.72 | −0.6321 | −0.6996 | +0.067 |
| 0.73 | −0.6450 | −0.6621 | +0.017 |
| 0.74 | −0.6588 | −0.6260 | −0.033 |

Interpolating between 0.73 and 0.74 gives $0.73+0.01\times0.017/0.050=0.7334$:

$$
M_{crit}=0.733\qquad(\text{Kármán–Tsien, }C_{p0,min}=-0.4),
$$

compared with $0.747$ from Prandtl–Glauert. The stronger suction reaches sonic conditions at a lower free-stream Mach number; the change is small, 0.014. Check: at $M_\infty=0.733$, Kármán–Tsien gives $-0.649$ and $C_{p,cr}=-0.651$. For $C_{p0,min}=-1.0$ the two rules give 0.606 and 0.585.

## Problem-solving workflow

1. Identify the incompressible input: $C_{p0}$ at a point, $C_{p0,min}$, or $C_{l0}$ (e.g. $2\pi\alpha$ from thin-aerofoil theory, $\alpha$ in radians).
2. Check validity: thin body, attached and shock-free, $M_\infty$ below about 0.8 (and below $M_{crit}$ for the rule to describe the real flow).
3. Scale $C_p$, $C_l$ or $C_m$ by $1/\sqrt{1-M_\infty^2}$, or use Kármán–Tsien for $C_p$ if asked. Leave $C_d$ alone.
4. For $C_l$ or $C_m$ from a pressure distribution, integrate $C_{p,l}-C_{p,u}$ along the chord and divide the result by $\beta$; scaling the pressures first gives the same answer.
5. For $M_{crit}$, tabulate LHS and RHS at two to four Mach numbers, find the sign change, interpolate, and state the rule used and $\gamma=1.4$.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| velocity potential equation; compressible potential equation | linearised small-perturbation potential equation; Prandtl–Glauert equation | 4.3 slides 6–7; 4.4 slide 2 ("potential flow equation"); 4.5 slide 2 | $\phi$ is the perturbation potential |
| linearised Euler equation | small-disturbance equation; linearised (small-perturbation) theory | 4.3 slide 5 | |
| transonic aerofoil theory ($M_\infty<0.8$) | subsonic compressible (linearised) theory | 4.4 title; 4.3 slide 7 ("Transonic ($M_\infty<0.9$)"); L4-4, l. 25 ("transonic region", spoken) | Textbooks keep *transonic* for mixed sub/supersonic flow (§4 note) |
| Prandtl–Glauert transformation; P-G transformation | Prandtl–Glauert rule; Göthert's rule (3D); compressibility correction | 4.4 slides 1–5, 7 | |
| Karman–Tsien (1939) | Kármán–Tsien rule; von Kármán–Tsien correction | 4.4 slides 10–11 | The slides drop the accent |
| $C_{p0}$, $C_{l0}$, $C_{m0}$ (incompressible) | $C_{p,0}$; $C_{p,inc}$; $C_{p,i}$ | 4.4 slides 4–8 | 0 = incompressible, not stagnation (L4-4, ll. 126–128) |
| normal force $N'$ | $F_n'$ (W01 §2); normal-force coefficient $C_n$ | L4-4, ll. 151–156 (spoken) | $L'\approx N'$ for small $\alpha$ |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]] · Next: [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]
- New concepts: [[Linearised Compressible Potential Equation]] · [[Prandtl-Glauert Transformation]] · [[Critical Mach Number]]
- Earlier: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#2. Aerodynamic review and the low-speed baseline|W01 §2]] (normal and chordwise force, $C_{m,LE}$, leading-edge suction) · [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#4. Stagnation properties|W01 §4]] (isentropic ratios used for $C_{p,cr}$) · [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#8. Lift, drag and the mechanism of drag divergence (4.2 slides 13–15)|W07a §8]] (CFD lift against Prandtl–Glauert; drag divergence) · [[Drag Divergence]] · [[Homentropic Flow]] (the same assumption as the MoC)
- Earlier years and other modules: [[SESA2022 T4 - Thin Aerofoil Theory]] (the incompressible $C_{p0}$ and $C_{l0}=2\pi\alpha$) · [[Streamfunction and Velocity Potential]] · [[Laplace's Equation]] · [[SESA3043 1.2b - Potential-Flow Review|SESA3043 1.2b]] · [[SESA3043 2.3 - Panel Methods|SESA3043 2.3]] (panel-method $C_{p0}$ to correct)
- Worked sheet: [[SESA3029 Example Sheet 2 - Solutions#Q6. Critical Mach number via Prandtl–Glauert|ES2 Q6]] ($C_{p0,min}=-2.5$, $M_{crit}=0.448$)
- Formulae: [[SESA3029 Formula Sheet#Euler equations and compressible aerofoils (Lectures 4.1–4.6)|Formula sheet: Chapter 4]]

## Sources

- `Lecture4-3.pdf`: 4.3 Compressible Potential Flow Equations, 8 slides. Lectured Fri 6 Nov.
- `06 November 2026 at 16_57_37.txt` (L4-3): the Fri 6 Nov recording (492 lines). Ll. 1–36 answer the 4.2 trailing-edge question ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#Why there are oblique shocks at the trailing edge|W07a]]); ll. 37–480 are Lecture 4.3, covered to the last slide; ll. 486–492 are empty end-of-recording lines.
- `Lecture4-4.pdf`: 4.4 Prandtl-Glauert Transformation (Transonic Aerofoil Theory for $M_\infty<0.8$), 11 slides. Lectured Mon 9 Nov.
- `Lecture 4-4.txt` (L4-4): the Mon 9 Nov recording (299 lines), covering all 11 slides. Ll. 1–27 recap the 4.3 equation and its range; ll. 28–85 the transformation (slides 2–3); ll. 99–138 work the L4-3 Bernoulli homework and $C_p=C_{p0}/\beta$ (slides 4–5); ll. 139–186 derive $C_l$ and $C_m$ from the chordwise integrals and set the drag reading; ll. 187–222 cover slide 6 and return to 4.2 slides 13–15 (CFD lift against Prandtl–Glauert, drag rise); ll. 223–293 the critical Mach number and Kármán–Tsien (slides 7–11). Ll. 297–298 put supersonic (Ackeret) theory next, on Thu 12 Nov ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]]).
- Figures: `generate_aerothermo_w07_figures.py` (`at_pg_wavy_wall.png`, `at_compressibility_corrections.png`, `at_critical_mach_number.png`). Every number is computed in the script; the $M_{crit}$ roots match slides 9 and 11 (0.747, 0.733).
- Anderson, *Modern Compressible Flow*, Ch. 9 (linearised flow) and §§11.4–11.6; *Fundamentals of Aerodynamics*, §§11.3–11.7 (§11.7, drag divergence, for the drag reading).

## Self-study tasks

Tasks citing L4-3 or L4-4 were set or posed in those lectures (Fri 6 and Mon 9 Nov). The last three are suggested, not lecturer-set.

### Core

- [ ] **(L4-3, ll. 391–417; 2025–26 exam paper)** Show that $C_p=\dfrac{2}{\gamma M_\infty^2}\left(\dfrac{p}{p_\infty}-1\right)$, then derive $C_p=-2u'/U_\infty$, including the binomial step. → [[#5. The linearised pressure coefficient (4.3 slide 8)|§5]]
- [ ] **(L4-3, ll. 55–327)** Derive $(1-M_\infty^2)\phi_{xx}+\phi_{yy}=0$ from the steady Euler equations, stating where each assumption enters. → [[#1. Steady Euler equations in non-conservative form (4.3 slides 2–3)|§§1–4]]
- [ ] **(L4-3, ll. 476–479; worked in L4-4, ll. 99–138)** Start from incompressible Bernoulli, apply $U=U_\infty+u_0'$, and show that $C_{p0}=-2u_0'/U_\infty$; then use $\phi=\phi_0/\beta$ to show $C_p=C_{p0}/\sqrt{1-M_\infty^2}$. → [[#7. The Prandtl–Glauert rule for Cp, Cl and Cm (4.4 slides 4–6)|§7]]
- [ ] **(L4-4, ll. 141–179)** Show that $\int_0^c(p_l-p_u)\,\mathrm dx$ is the normal force, not the lift, say when $L'\approx N'$, and derive $C_l=C_{l0}/\sqrt{1-M_\infty^2}$ and $C_m=C_{m0}/\sqrt{1-M_\infty^2}$ from the chordwise integrals. → [[#Lift and moment coefficients (4.4 slide 5)|§7, lift and moment]]
- [ ] **(L4-4, ll. 261–277; slide 8)** Find $M_{crit}$ for $C_{p0,min}=-0.4$ by evaluating LHS and RHS at trial Mach numbers and interpolating. Answer 0.747. → [[#Worked example: Cp0,min = −0.4 (4.4 slides 8–9 and 11)|§8]]

### Further practice

- [ ] **(L4-4, ll. 180–186; reading)** Read how drag relates between the incompressible and compressible solutions (Anderson, *Fundamentals of Aerodynamics*, §§11.4 and 11.7), and explain why there is no $C_d=C_{d0}/\sqrt{1-M_\infty^2}$ rule. → [[#Drag does not follow the rule|§7, drag]]
- [ ] **(L4-4, ll. 283–293; slide 11)** Redo the $C_{p0,min}=-0.4$ example with Kármán–Tsien. Answer 0.733. → [[#9. Improved correction: Kármán–Tsien (4.4 slides 10–11)|§9]]
- [ ] **(L4-4, ll. 66–89)** From $\mathrm dC_l/\mathrm d\alpha=2\pi$ get $C_{l0}$ for a flat plate, write its compressible $C_l$, and evaluate it at $\alpha=4^\circ$, $M_\infty=0.7$. Answer 0.614. → [[#Lift and moment coefficients (4.4 slide 5)|§7, the check]]
- [ ] **(L4-3, l. 123)** Expand the $y$-momentum equation yourself to get equation (2), $\rho u\,\partial v/\partial x+\rho v\,\partial v/\partial y=-a^2\,\partial\rho/\partial y$. → [[#1. Steady Euler equations in non-conservative form (4.3 slides 2–3)|§1]]
- [ ] **(Example Sheet 2, Q6)** Solve [[SESA3029 Example Sheet 2 - Solutions#Q6. Critical Mach number via Prandtl–Glauert|ES2 Q6]] ($C_{p0,min}=-2.5$). Answer 0.448.
- [ ] **(L4-3, ll. 268–286)** Explain why the $(\gamma-1)u'U_\infty$ term is kept in $a^2$ but dropped from the linearised Euler equation. → [[#3. Linearising about the free stream (4.3 slides 4–5)|§3]]
- [ ] **(L4-3, ll. 355–378; L4-4, ll. 12–27)** Explain why the linear equation fails near $M_\infty=1$ and for $M_\infty>5$. → [[#4. The velocity potential equation (4.3 slides 6–7)|§4]]
- [ ] (suggested, not lecturer-set) Show that the boundary condition makes the transformed problem the same aerofoil. → [[#6. The Prandtl–Glauert transformation (4.4 slides 2–3)|§6, the tip]]
- [ ] (suggested, not lecturer-set) $M_{crit}$ for $C_{p0,min}=-1.0$: 0.606 (P–G) and 0.585 (K–T). → [[#8. Estimating the critical Mach number (4.4 slides 7–9)|§8]]
- [ ] (suggested, not lecturer-set) Find the slide 2 slip in the $y$-momentum line and check that it does not change the result. → [[#1. Steady Euler equations in non-conservative form (4.3 slides 2–3)|§1]]

## Transcript and slide slips

> [!warning] Slide 2 has $u$ outside the bracket in the $y$-momentum equation
> Where: [[#1. Steady Euler equations in non-conservative form (4.3 slides 2–3)]].
>
> 4.3 slide 2 writes "$+u[\dots]$" in the $y$-momentum line. Expanding $\partial(\rho uv)/\partial x+\partial(\rho v^2)/\partial y$ gives $v[\partial(\rho u)/\partial x+\partial(\rho v)/\partial y]$ (checked symbolically). The bracket is zero anyway (next step), so the slip does not change the result.

### Transcript slips (L4-3)

Whisper writes aerofoil as *"air force"*/*"aerophore"*, Kutta as *"cutter"*, expansion fan as *"expansion fat"*, Prandtl–Glauert as *"plantar-glarus"*, Ackeret as *"accurate"* and isentropic as *"isentery"*. These are not listed below.

> [!warning] Slips in `06 November 2026 at 16_57_37.txt` (L4-3, Fri 6 Nov)
> | Where | Said | Correct |
> |---|---|---|
> | l. 66 | the $x$-momentum line read as *"That's the y-momentum equation"* | $x$-momentum (the next line, l. 68, is $y$-momentum) |
> | ll. 86–96 | the product-rule grouping changed twice | the grouping of §1: $\rho v\,\partial u/\partial y+u\,\partial(\rho v)/\partial y$ |
> | ll. 100–101 | unintelligible | the bracket $u[\partial(\rho u)/\partial x+\partial(\rho v)/\partial y]$, zero by mass conservation (l. 102) |
> | l. 129 | *"minus a squared u times rho partial rho by partial x"* | $-a^2(u\,\partial\rho/\partial x+v\,\partial\rho/\partial y)$, no extra $\rho$ |
> | ll. 163–165 | $\partial u'/\partial x$ and $\partial v'/\partial x$ in the cross term, then *"this one is y"* | the cross term is $(U_\infty+u')v'(\partial u'/\partial y+\partial v'/\partial x)$ |
> | l. 171 | *"order of one is five order of two and order of three"* | first-, second- and third-order terms (garbled) |
> | l. 246 | *"gamma minus over 2 times 2 times U prime U infinity"* | $\frac{\gamma-1}{2}\cdot2u'U_\infty$ |
> | l. 265 | *"partial U prime by partial S"* | $\partial u'/\partial x$ |
> | ll. 368, 378 | *"up to Mach number of 0.8"*, *"1.2 and above"* | slide 7 prints 0.9 and 1.1; the 4.4/4.5 titles use 0.8 and 1.2 (§4 note) |
> | l. 419 | *"rho R T over rho infinity R T infinity squared T infinity"* | $p/p_\infty=\rho RT/(\rho_\infty RT_\infty)$ |
> | l. 462 | *"times U U prime over U infinity"* | $a^2/a_\infty^2=1-(\gamma-1)M_\infty^2\,u'/U_\infty$ |
> | l. 468 | *"one plus N is gamma over gamma minus one"* | $n=\gamma/(\gamma-1)$, so $nx=-\gamma M_\infty^2u'/U_\infty$ |

### Transcript slips (L4-4)

Whisper writes Prandtl as *"Pronto"*/*"Planter"*, Glauert as *"Glaurot"*/*"Gelauert"*/*"glower"*, Kármán–Tsien as *"Karmann"*/*"Kahn-Mansion"*/*"common Zn"*, Mach number as *"mark number"*, aerofoil as *"error-for"*/*"air flow"*, transonic as *"transfer"*/*"transferring"*, Bernoulli as *"Brunner"*, and $\phi$ as *"v"* or *"P"* in *"partial v by partial x"* (ll. 103–105). These are not listed below.

> [!warning] Slips in `Lecture 4-4.txt` (L4-4, Mon 9 Nov)
> | Where | Said | Correct |
> |---|---|---|
> | l. 6 | Glauert described as one of Prandtl's PhD students | Glauert worked at the Royal Aircraft Establishment and published the rule in 1928 (slide 11); he was not Prandtl's doctoral student. Kármán (l. 284) was Prandtl's doctoral student |
> | ll. 19–23 | at high $M_\infty$ the large negative $1-M_\infty^2$ leaves the $\phi_{yy}$ term contributing very little, so the equation fails | in any solution the two terms balance; the hypersonic failure comes from the dropped terms, which grow like $M_\infty^2u'/U_\infty$ (§4) |
> | l. 78 | one solution covers *"Mach 0 to Mach 0.9"* | slide 1: $M_\infty<0.8$; up to 0.85–0.9 only with quickly falling accuracy (ll. 25–27) |
> | l. 88 | *"2 pi alpha divided by 1 minus square root of 1 minus m squared"* | $C_l=2\pi\alpha/\sqrt{1-M_\infty^2}$ |
> | ll. 173, 178, 181 | $\beta$, and the divisor of $C_l$, $C_m$ and $C_D$, given as *"1 minus M infinity squared"* | $\beta=\sqrt{1-M_\infty^2}$ (corrected aloud at l. 180) |
> | ll. 180–184 | drag differs because it is integrated in $y$ and the vertical coordinates of the two problems are not the same | in thin-aerofoil theory the surface slopes are the same in both problems (§6, the tip), so the pressure-drag integral would scale by $1/\beta$ like the others; the rule fails for drag because inviscid subcritical drag is zero in both problems and real drag is viscous ([[#Drag does not follow the rule|§7, drag]]) |
> | l. 194 | *"1.6 at Mach number about 1.8"* | $C_l/C_{l0}=1.6$ at $M_\infty\approx0.78$ and 1.67 at 0.8; the slide 6 axis ends at 1.8, reached near $M_\infty=0.83$ |
