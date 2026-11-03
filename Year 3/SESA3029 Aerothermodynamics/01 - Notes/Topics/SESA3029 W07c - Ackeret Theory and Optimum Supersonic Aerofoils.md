---
title: "SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 4: High-speed aerodynamics"
order: 9
tags: [sesa3029, compressible-flow, supersonic, ackeret, linear-theory, wave-drag, diamond-aerofoil]
aliases: ["SESA3029 Lecture 4.5", "SESA3029 Lecture 4.6", "SESA3029 W07c"]
date: 2026-11-03
status: written-ahead
coverage: "Lectures 4.5–4.6 written ahead from the slides; not yet lectured (no transcript)"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W05a - Method of Characteristics]]"]
next_topics: []
key_concepts: ["[[Ackeret Theory]]", "[[Supersonic Wave Drag]]", "[[Linearised Compressible Potential Equation]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]", "[[SESA3029 Example Sheet 1 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture4-5.pdf", "02 - Sources/Lectures/Lecture4-6.pdf"]
---

# SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils

> [!abstract] Summary
> For $M_\infty>1$ the linearised potential equation is a wave equation. Its solutions are constant along Mach lines, which gives Ackeret's formula $C_p=2\theta/\sqrt{M_\infty^2-1}$ for a thin surface inclined at $\theta$ to the free stream. Integrated over a thin aerofoil this gives $C_l=4\alpha/\sqrt{M_\infty^2-1}$, whatever the camber or thickness, and a wave drag $C_d=\frac{4}{\sqrt{M_\infty^2-1}}\left[\alpha^2+\overline{(h')^2}+\overline{(y_c')^2}\right]$. Minimising the drag picks out a symmetric, faceted section with maximum thickness at mid-chord: the diamond aerofoil.

> [!summary]- Exam use: quick path
> - **Use it when:** a thin aerofoil or flat plate is in supersonic flow at small angles, and the question asks for Ackeret, linear or "first-order" theory (otherwise use the exact [[Shock-Expansion Theory|shock-expansion method]]).
> - **Assumptions:** inviscid, shock-free to first order (weak waves), thin, small angles **in radians**, $M_\infty$ about 1.2 to 5; $\theta$ measured from the free-stream direction, positive for compression.
> - **Method:** 1. $\lambda=\sqrt{M_\infty^2-1}$. 2. On each face, find $\theta$ relative to $\vec U_\infty$ (sign: compression +). 3. $C_p=2\theta/\lambda$, $p=p_\infty+q_\infty C_p$. 4. $C_l=4\alpha/\lambda$; $C_d=\frac4\lambda[\alpha^2+(t/c)^2]$ for a diamond. 5. Compare with shock-expansion if asked.
> - **Common mistakes:** using degrees for $\theta$ and $\alpha$ ("Remember #3"); getting the sign of $\theta$ on the lower surface wrong (it is positive when the lower surface turns the flow **downward** into itself).
> - **Practise:** [[#Worked example: flat plate at M = 2, α = 10° (4.5 slide 7, homework)|the flat-plate homework]] · [[SESA3029 Example Sheet 2 - Solutions#Q5. Diamond aerofoil by Ackeret theory|ES2 Q5]]

> [!info] Written ahead of the lecture
> This note is written from the 4.5 deck (8 slides) and the 4.6 deck (11 slides) before they have been lectured. The steps the slides skip, the lower surface and the slide 10 question are filled in, and every number is checked in Python. When the transcripts arrive, the note will be reconciled with them and its status changed to `lectured`.

In [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]] the sign of $1-M_\infty^2$ decided the character of the linear potential equation. Below $M_\infty=1$ it is elliptic: a disturbance is felt everywhere, and a stretch of the $y$-axis turns it into Laplace's equation. Above $M_\infty=1$ the sign flips and the equation becomes the wave equation. A disturbance can then only travel along Mach lines, downstream, which is the zone of influence of the MoC ([[SESA3029 W05a - Method of Characteristics|W05a]]). That makes the supersonic problem easier, not harder: the pressure at a point on the surface depends only on the local surface slope.

Ackeret theory is the small-angle limit of the exact shock-expansion method of [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]. It gives up a few per cent of accuracy in exchange for closed-form lift and drag, and those formulas answer a design question the exact method cannot answer directly: what shape of aerofoil has the least wave drag?

## 1. The wave equation and its solution (4.5 slides 2–3)

Start from the potential equation with $M_\infty>1$ (slide 2) and move the $x$-term across:

$$
(1-M_\infty^2)\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0
\quad\Rightarrow\quad
(M_\infty^2-1)\frac{\partial^2\phi}{\partial x^2}=\frac{\partial^2\phi}{\partial y^2}.
$$

Define

$$
\lambda=\sqrt{M_\infty^2-1}
\quad\Rightarrow\quad
\lambda^2\frac{\partial^2\phi}{\partial x^2}=\frac{\partial^2\phi}{\partial y^2}.
$$

This is a wave equation, with $x$ playing the part of time. Look for solutions that are constant along particular lines (slide 2):

$$
\phi=f(\eta),\qquad \eta=x-\lambda y .
$$

**Check it.** Since $\partial\eta/\partial x=1$,

$$
u'=\frac{\partial\phi}{\partial x}=\frac{\mathrm df}{\mathrm d\eta}\frac{\partial\eta}{\partial x}=\frac{\mathrm df}{\mathrm d\eta},
$$

$$
\frac{\partial^2\phi}{\partial x^2}=\frac{\partial}{\partial x}\left(\frac{\mathrm df}{\mathrm d\eta}\right)=\frac{\mathrm d}{\mathrm d\eta}\left(\frac{\mathrm df}{\mathrm d\eta}\right)\frac{\partial\eta}{\partial x}=\frac{\mathrm d^2f}{\mathrm d\eta^2}.
$$

Since $\partial\eta/\partial y=-\lambda$ (slide 3),

$$
v'=\frac{\partial\phi}{\partial y}=\frac{\mathrm df}{\mathrm d\eta}\frac{\partial\eta}{\partial y}=-\lambda\frac{\mathrm df}{\mathrm d\eta},
$$

$$
\frac{\partial^2\phi}{\partial y^2}=\frac{\partial}{\partial y}\left(-\lambda\frac{\mathrm df}{\mathrm d\eta}\right)=\frac{\mathrm d}{\mathrm d\eta}\left(-\lambda\frac{\mathrm df}{\mathrm d\eta}\right)\frac{\partial\eta}{\partial y}=\lambda^2\frac{\mathrm d^2f}{\mathrm d\eta^2}.
$$

So $\text{LHS}=\lambda^2\phi_{xx}=\lambda^2f''$ and $\text{RHS}=\phi_{yy}=\lambda^2f''$, and the equation is satisfied for **any** function $f$.

> [!warning] Two slips on 4.5 slide 3
> Slide 3 writes *"since $\partial\eta/\partial x=-\lambda$"* next to $v'$; it should be $\partial\eta/\partial y=-\lambda$ ($\partial\eta/\partial x=1$, as on slide 2). In the $\partial^2\phi/\partial y^2$ line, the middle step is printed as $\partial/\partial x(-\lambda\,\mathrm df/\mathrm d\eta)$ instead of $\partial/\partial y$. The final $\lambda^2f''$ is right.

## 2. Mach lines and the key result u′ = −v′/λ (4.5 slides 3–4)

$f(\eta)$ is constant wherever $\eta$ is constant (slide 3):

$$
\eta=x-\lambda y=C'
\quad\Rightarrow\quad
y=\frac1\lambda x+C .
$$

From the Mach-angle triangle (hypotenuse $M_\infty$, opposite side 1, adjacent side $\sqrt{M_\infty^2-1}$; [[Mach Waves and Mach Angle]]),

$$
\tan\mu=\frac{1}{\sqrt{M_\infty^2-1}}=\frac1\lambda
\quad\Rightarrow\quad
y=(\tan\mu)\,x+C .
$$

The lines of constant $\phi$ are the free-stream Mach lines, inclined at $\mu$ to the flow (slide 4): *"the solutions are constant along the Mach lines!"* Each line carries the disturbance made where it leaves the surface, unchanged, out to infinity.

Because $u'$ and $v'$ are both multiples of the same $\mathrm df/\mathrm d\eta$, they are linked everywhere, and in particular along each Mach line (slide 4):

$$
u'=\frac{\mathrm df}{\mathrm d\eta},\quad v'=-\lambda\frac{\mathrm df}{\mathrm d\eta}
\quad\Rightarrow\quad
\boxed{u'=-\frac{v'}{\lambda}=-\frac{v'}{\sqrt{M_\infty^2-1}}}
$$

This holds above the aerofoil, where the Mach lines run up and downstream. Below it the disturbances run down and downstream, along $\eta=x+\lambda y$. The slides do only the upper side; the lower side is the same calculation with $\partial\eta/\partial y=+\lambda$, which gives $u'=+v'/\lambda$ (and the wave equation is again satisfied, checked symbolically).

![[at_ackeret_mach_lines.png|900]]

## 3. Ackeret's formula (4.5 slide 5)

Consider an aerofoil whose surface slope is $\theta$ (slide 5). There is no reflected wave and no shock, so in MoC terms the flow above the surface is a simple flow region. On the surface the flow is tangent to it, so for small slopes

$$
\tan\theta\simeq\theta=\frac{v'}{U_\infty}.
$$

On the upper surface $u'=-v'/\lambda$, so

$$
\frac{u'}{U_\infty}=-\frac{1}{\lambda}\frac{v'}{U_\infty}=-\frac{\theta}{\sqrt{M_\infty^2-1}}.
$$

The linearised pressure coefficient from 4.3 is $C_p=-2u'/U_\infty$, so

$$
\boxed{C_p=\frac{2\theta}{\sqrt{M_\infty^2-1}}}\qquad\text{(Ackeret formula)}
$$

On the lower surface the signs of both $u'=+v'/\lambda$ and the outward slope flip together, and the formula is the same once $\theta$ is defined by the course's rules (slide 6):

- *Remember #1:* $\theta$ is measured from the free-stream vector $\vec U_\infty$, not from the chord.
- *Remember #2:* $\theta$ is positive if the surface compresses the flow (turns it into itself) and negative if it expands it.

So a surface element facing forwards into the flow, on either side, has $C_p>0$, and one facing backwards has $C_p<0$.

> [!tip] The same result from the method of characteristics
> Above the aerofoil every $C^-$ characteristic comes from the uniform free stream, so the Riemann invariant $R^-=\nu+\theta$ is the same everywhere: $\nu+\theta=\nu_\infty$ ([[SESA3029 W05a - Method of Characteristics|W05a]]). A surface turning the flow by $\theta$ (upward, compression) therefore has $\nu=\nu_\infty-\theta$. For small changes $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm dU/U$ (W03 §5), so $-\theta=\lambda\,u'/U_\infty$: the same $u'/U_\infty=-\theta/\lambda$. Ackeret theory is the MoC in the limit of weak waves, which is why slide 5 calls the flow *"a simple flow in MoC terminology"*.

![[at_ackeret_vs_exact.png|900]]

The left panel shows how good the linear formula is at $M_\infty=2$. For a compression the exact oblique-shock $C_p$ rises faster than $2\theta/\lambda$; for an expansion the exact Prandtl–Meyer $C_p$ falls more slowly. At $\theta=2^\circ$ the error is about 4.5 %; at $10^\circ$ it is 25 % on each surface. Both exact curves lie above the linear ones, so in the difference $C_{p,l}-C_{p,u}$ the two errors have opposite signs and largely cancel. That is why the plate's $C_l$ is only 1 % out.

## 4. The flat plate at incidence (4.5 slides 6–7)

A thin flat plate at incidence $\alpha$ in a supersonic stream (slide 6). The upper surface turns the flow away from itself, $\theta=-\alpha$; the lower surface turns it into itself, $\theta=+\alpha$:

$$
C_{p_u}=\frac{-2\alpha}{\sqrt{M_\infty^2-1}},\qquad C_{p_l}=\frac{2\alpha}{\sqrt{M_\infty^2-1}}.
$$

Both pressures are uniform along the chord. The net force per unit span acts normal to the plate:

$$
N'=(p_l-p_u)\,c=\tfrac12\rho_\infty U_\infty^2\,c\,(C_{p_l}-C_{p_u}),
$$

$$
C_n=\frac{N'}{\tfrac12\rho_\infty U_\infty^2c}=C_{p_l}-C_{p_u}=\frac{4\alpha}{\sqrt{M_\infty^2-1}}.
$$

Resolve perpendicular and parallel to the free stream (slide 7). For small incidence $\cos\alpha\simeq1$ and $\sin\alpha\simeq\alpha$:

$$
C_l=C_n\cos\alpha\simeq\frac{4\alpha}{\sqrt{M_\infty^2-1}},\qquad
C_d=C_n\sin\alpha\simeq\frac{4\alpha^2}{\sqrt{M_\infty^2-1}}.
$$

*Remember #3: you must use the radian values of $\theta$ and $\alpha$ here* (slide 7). The drag is pure **wave drag**: it exists in inviscid flow, with no boundary layer, because the plate's force is normal to it and there is no leading-edge suction at supersonic speed ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]). Note that $C_d=\alpha\,C_l$, and the uniform $\Delta C_p$ puts the centre of pressure at mid-chord, which is the $c/4\to c/2$ shift of W03.

### Worked example: flat plate at M = 2, α = 10° (4.5 slide 7, homework)

*For $M_\infty=2$ and $\alpha=10^\circ$, calculate $C_l$ and $C_d$ using 1) the Ackeret theory and 2) the shock-expansion method, and compare the results (homework).*

**Ackeret.** $\lambda=\sqrt{4-1}=1.7321$ and $\alpha=10^\circ=0.17453$ rad:

$$
C_l=\frac{4(0.17453)}{1.7321}=0.4031,\qquad C_d=\frac{4(0.17453)^2}{1.7321}=0.0703 .
$$

These are the slide's numbers. Keeping the $\cos\alpha$ and $\sin\alpha$ instead gives $0.3969$ and $0.0700$; the slide uses the small-angle forms.

**Shock-expansion.** This is the [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#Flat plate at incidence, step by step (slides 7–13): M₁ = 2, α = 10°, p₁ = 30 kPa, c = 1 m|W03 §6 flat plate]], the same case.

- Lower surface, an oblique shock with $\theta=10^\circ$ at $M=2$: $\beta=39.31^\circ$, $M_{n1}=2\sin39.31^\circ=1.267$, $p_l/p_\infty=1.7066$.
- Upper surface, a Prandtl–Meyer expansion: $\nu(2)=26.38^\circ\to36.38^\circ$, so $M_u=2.385$ and $p_u/p_\infty=0.5480$.
- With $q_\infty/p_\infty=\tfrac12\gamma M_\infty^2=2.8$: $C_n=(1.7066-0.5480)/2.8=0.4138$.

$$
C_l=C_n\cos\alpha=0.4075,\qquad C_d=C_n\sin\alpha=0.0719 .
$$

Slide 7 gives $0.4075$ and $0.0719$ ✓.

**Comparison.** Ackeret is 1.1 % low on lift and 2.2 % low on drag at $10^\circ$. On each surface separately the errors are much larger (the exact $C_{p_l}=0.252$ and $C_{p_u}=-0.161$, against Ackeret's $\pm0.202$), but in $C_{p_l}-C_{p_u}$ they almost cancel.

## 5. Summary: the two linear theories together (4.5 slide 8; 4.6 slide 2)

For incompressible flow a symmetric thin aerofoil has $C_{l0}=2\pi\alpha$ ([[SESA2022 T4 - Thin Aerofoil Theory#4. Symmetric aerofoil (flat plate)|SESA2022 T4 §4]]). The two compressible theories give

$$
\text{Prandtl–Glauert }(M_\infty<1):\ C_l=\frac{2\pi\alpha}{\sqrt{1-M_\infty^2}},\qquad
\text{Ackeret }(M_\infty>1):\ C_l=\frac{4\alpha}{\sqrt{M_\infty^2-1}} .
$$

The ratio $C_l/C_{l0}$ climbs to infinity as $M_\infty\to1$ from below and comes down from infinity above it, falling to $2/(\pi\lambda)=0.37$ at $M_\infty=2$ (see the right panel of the [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#7. The Prandtl–Glauert rule for Cp, Cl and Cm (4.4 slides 4–6)|W07b §7 figure]]). Neither theory holds near $M_\infty=1$, where the real lift, from the 4.2 CFD, peaks at a finite value.

## 6. A general thin aerofoil (4.6 slides 3–4)

Split a general thin aerofoil into three parts (slide 3): a symmetric thickness distribution $h(x)$, a camber line $y_c(x)$, and incidence $\alpha$, with the chord line tilted down by $\alpha x$:

$$
y_u(x)=h(x)+y_c(x)-\alpha x
\quad\Rightarrow\quad
\frac{\mathrm dy_u}{\mathrm dx}=\frac{\mathrm dh}{\mathrm dx}+\frac{\mathrm dy_c}{\mathrm dx}-\alpha ,
$$

$$
y_l(x)=-h(x)+y_c(x)-\alpha x
\quad\Rightarrow\quad
\frac{\mathrm dy_l}{\mathrm dx}=-\frac{\mathrm dh}{\mathrm dx}+\frac{\mathrm dy_c}{\mathrm dx}-\alpha .
$$

Small perturbation means $\tan\theta_u\simeq\theta_u$ and $\tan\alpha\simeq\alpha$. The camber line is defined so that $y_c=0$ at the leading and trailing edges, and $h=0$ there too.

![[at_aerofoil_decomposition.png|900]]

**Signs** (slide 4). A wall with positive slope compresses flow above it and expands flow below it. So, with *Remember #2*,

$$
\theta_u\simeq\frac{\mathrm dy_u}{\mathrm dx},\qquad \theta_l\simeq-\frac{\mathrm dy_l}{\mathrm dx}.
$$

With this convention,

$$
\theta_u=\frac{\mathrm dh}{\mathrm dx}+\frac{\mathrm dy_c}{\mathrm dx}-\alpha,\qquad
\theta_l=\frac{\mathrm dh}{\mathrm dx}-\frac{\mathrm dy_c}{\mathrm dx}+\alpha ,
$$

and Ackeret gives

$$
C_{p_u}=\frac{2}{\sqrt{M_\infty^2-1}}\left(\frac{\mathrm dh}{\mathrm dx}+\frac{\mathrm dy_c}{\mathrm dx}-\alpha\right),\qquad
C_{p_l}=\frac{2}{\sqrt{M_\infty^2-1}}\left(\frac{\mathrm dh}{\mathrm dx}-\frac{\mathrm dy_c}{\mathrm dx}+\alpha\right).
$$

## 7. Lift coefficient (4.6 slide 5)

The free stream is horizontal, and to first order each surface element's pressure acts vertically over its length $\mathrm dx$:

$$
L'=\int_0^c(p_l-p_u)\,\mathrm dx
\quad\Rightarrow\quad
C_l=\frac{1}{\tfrac12\rho_\infty U_\infty^2c}\int_0^c(p_l-p_u)\,\mathrm dx=\frac1c\int_0^c(C_{p_l}-C_{p_u})\,\mathrm dx .
$$

Substitute the two $C_p$:

$$
C_l=\frac{2}{c\sqrt{M_\infty^2-1}}\int_0^c\left[\left(h'-y_c'+\alpha\right)-\left(h'+y_c'-\alpha\right)\right]\mathrm dx .
$$

The thickness slopes cancel:

$$
C_l=\frac{4}{c\sqrt{M_\infty^2-1}}\int_0^c\left(\alpha-\frac{\mathrm dy_c}{\mathrm dx}\right)\mathrm dx .
$$

Integrate. The camber term is $[y_c]_0^c=y_c(c)-y_c(0)=0$:

$$
C_l=\frac{4}{c\sqrt{M_\infty^2-1}}\left(\alpha c-0\right)
\quad\Rightarrow\quad
\boxed{C_l=\frac{4\alpha}{\sqrt{M_\infty^2-1}}}
$$

This is the flat-plate result (slide 5). In inviscid linear supersonic theory **neither camber nor thickness affects the lift**, only the incidence of the chord line. This differs from subsonic thin-aerofoil theory, where camber shifts the zero-lift angle. Here camber changes the local loading, but its integral is zero.

## 8. Drag coefficient (4.6 slide 6)

Each surface element of length $\mathrm dx$ carries a pressure force normal to it. Its streamwise component is $p\sin\theta\,\mathrm ds\simeq p\,\theta\,\mathrm dx$, rearwards when the element faces forwards ($\theta>0$):

$$
D'=\int_0^c\left(p_l\sin\theta_l+p_u\sin\theta_u\right)\mathrm dx\simeq\int_0^c\left(p_l\theta_l+p_u\theta_u\right)\mathrm dx .
$$

> [!warning] Slide 6 writes $\cos\theta$
> 4.6 slide 6 prints $D'=\int(p_l\cos\theta_l+p_u\cos\theta_u)\,\mathrm dx\simeq\int(p_l\theta_l+p_u\theta_u)\,\mathrm dx$. The horizontal component of a force normal to a surface at slope $\theta$ is $p\sin\theta$, not $p\cos\theta$; the approximation $\simeq p\theta$ that follows is the $\sin$ version.

Next, replace $p$ by $p-p_\infty$. This is allowed because a uniform pressure on a closed body gives no force:

$$
\int_0^c(\theta_l+\theta_u)\,\mathrm dx=\int_0^c2\frac{\mathrm dh}{\mathrm dx}\,\mathrm dx=2\left[h\right]_0^c=0 .
$$

So the slide's next line, with $C_p$ in place of $p$, follows:

$$
C_d=\frac1c\int_0^c\left(C_{p_l}\theta_l+C_{p_u}\theta_u\right)\mathrm dx .
$$

With $C_p=2\theta/\lambda$ on each surface:

$$
C_d=\frac{2}{c\sqrt{M_\infty^2-1}}\int_0^c\left(\theta_l^2+\theta_u^2\right)\mathrm dx
=\frac{2}{c\sqrt{M_\infty^2-1}}\int_0^c\left[\left(h'-y_c'+\alpha\right)^2+\left(h'+y_c'-\alpha\right)^2\right]\mathrm dx .
$$

Expand the two squares. Writing $s=y_c'-\alpha$, they are $(h'-s)^2+(h'+s)^2=2h'^2+2s^2$, and

$$
2s^2=2\left(y_c'-\alpha\right)^2=2y_c'^2-4\alpha y_c'+2\alpha^2 .
$$

The cross term integrates to zero, $\int_0^c-4\alpha y_c'\,\mathrm dx=-4\alpha[y_c]_0^c=0$. Hence (slide 6)

$$
\boxed{C_d=\frac{4}{c\sqrt{M_\infty^2-1}}\int_0^c\left[\alpha^2+\left(\frac{\mathrm dh}{\mathrm dx}\right)^2+\left(\frac{\mathrm dy_c}{\mathrm dx}\right)^2\right]\mathrm dx}
$$

All three components contribute to the wave drag, and each one adds a positive square: drag due to lift ($\alpha^2$), drag due to thickness, and drag due to camber. Camber adds drag without adding lift, so remove it: *"We favour thin symmetric aerofoils for low drag in supersonic flight"* (slide 6). See [[Supersonic Wave Drag]].

> [!check] How much does a little camber cost? (suggested)
> A parabolic camber line $y_c=4\varepsilon x(c-x)/c^2$ with $\varepsilon=0.02c$ has $y_c'=4\varepsilon(1-2x/c)/c$ and $\frac1c\int_0^c y_c'^2\,\mathrm dx=\frac{16}{3}(\varepsilon/c)^2=0.00213$. On a 5 % diamond at $\alpha=2.86^\circ$, $M_\infty=2$ ($\alpha^2+(t/c)^2=0.0050$), this raises $C_d$ from $0.01155$ to $0.01647$, an extra 43 %, for no change in $C_l$.

## 9. Thickness drag and the optimum section (4.6 slides 7–10)

For a symmetric aerofoil ($y_c=0$) the drag is (slide 7)

$$
C_d=\frac{4}{\sqrt{M_\infty^2-1}}\left[\alpha^2+\frac1c\int_0^c\left(\frac{\mathrm dh}{\mathrm dx}\right)^2\mathrm dx\right].
$$

Which $h(x)$, for a given thickness $t$, makes the integral smallest? Let the half-thickness peak at $t/2$ at $x=k$, and write $h$ as a straight-line segment plus arbitrary functions $f$ and $g$ that are zero at their end points (slide 7):

$$
x\le k:\quad h=\frac{tx}{2k}+f(x),\qquad f(0)=f(k)=0
\quad\Rightarrow\quad
\frac{\mathrm dh}{\mathrm dx}=\frac{t}{2k}+\frac{\mathrm df}{\mathrm dx},
$$

$$
x\ge k:\quad h=\frac{t(c-x)}{2(c-k)}+g(x),\qquad g(k)=g(c)=0
\quad\Rightarrow\quad
\frac{\mathrm dh}{\mathrm dx}=-\frac{t}{2(c-k)}+\frac{\mathrm dg}{\mathrm dx}.
$$

Square and integrate each part (slide 8):

$$
\int_0^c h'^2\,\mathrm dx=\int_0^k\left[\frac{t^2}{4k^2}+\frac tk\frac{\mathrm df}{\mathrm dx}+\left(\frac{\mathrm df}{\mathrm dx}\right)^2\right]\mathrm dx+\int_k^c\left[\frac{t^2}{4(c-k)^2}-\frac{t}{c-k}\frac{\mathrm dg}{\mathrm dx}+\left(\frac{\mathrm dg}{\mathrm dx}\right)^2\right]\mathrm dx .
$$

The constant terms integrate to $t^2/(4k)$ and $t^2/[4(c-k)]$. The cross terms vanish by the end conditions: $\int_0^k f'\,\mathrm dx=f(k)-f(0)=0$ and $\int_k^c g'\,\mathrm dx=0$. So

$$
\int_0^c h'^2\,\mathrm dx=\frac{t^2}{4}\left(\frac1k+\frac{1}{c-k}\right)+\int_0^k\left(\frac{\mathrm df}{\mathrm dx}\right)^2\mathrm dx+\int_k^c\left(\frac{\mathrm dg}{\mathrm dx}\right)^2\mathrm dx .
$$

The last two integrals are squares, so any non-zero $f$ or $g$ only adds drag. For least drag $f=g=0$: the faces should be straight. *Faceted aerofoils are favoured in supersonic flight* (slide 8).

**Optimum $k$** (slide 9). With straight faces the integral is

$$
F(k)=\frac{t^2}{4}\left(\frac1k+\frac1{c-k}\right).
$$

Seek a minimum:

$$
\frac{\mathrm dF}{\mathrm dk}=\frac{t^2}{4}\left[-\frac{1}{k^2}-\frac{1}{(c-k)^2}(-1)\right]=0
\quad\Rightarrow\quad
k^2=(c-k)^2
\quad\Rightarrow\quad
\boxed{k=\frac c2}
$$

(the other branch, $k=-(c-k)$, would need $c=0$). The second derivative, $\frac{t^2}{2}\left[\frac1{k^3}+\frac1{(c-k)^3}\right]>0$, confirms a minimum. At $k=c/2$,

$$
\int_0^c\left(\frac{\mathrm dh}{\mathrm dx}\right)^2\mathrm dx=\frac{t^2}{4}\left(\frac2c+\frac2c\right)=\frac{t^2}{c}.
$$

The maximum thickness should be at half chord, and the section is a **diamond** (slide 10). Its lift and minimised drag are

$$
C_l=\frac{4\alpha}{\sqrt{M_\infty^2-1}},\qquad C_d=\frac{4}{\sqrt{M_\infty^2-1}}\left[\alpha^2+\left(\frac tc\right)^2\right].
$$

![[at_thickness_drag.png|900]]

The figure puts numbers on it. Moving the peak to $k=0.3c$ costs 19 % more thickness drag. A biconvex section (two parabolic arcs, $h=2t\,x(c-x)/c^2$) has $\int h'^2\,\mathrm dx=4t^2/(3c)$, a third more than the diamond, which is the price of the smooth surface.

Slide 10 lists the three findings: symmetric (uncambered) aerofoils are better, faceted ones are better still, and the symmetric faceted aerofoil with its thickest point at half chord is best.

## 10. The best angle of attack (4.6 slide 10 question)

*"At what angle of attack can you achieve the highest lift-to-drag ratio?"* (slide 10). Write $\tau=t/c$. The $4/\lambda$ cancels in the ratio:

$$
\frac LD=\frac{C_l}{C_d}=\frac{\alpha}{\alpha^2+\tau^2}.
$$

Differentiate with respect to $\alpha$:

$$
\frac{\mathrm d}{\mathrm d\alpha}\left(\frac LD\right)=\frac{(\alpha^2+\tau^2)-\alpha(2\alpha)}{(\alpha^2+\tau^2)^2}=\frac{\tau^2-\alpha^2}{(\alpha^2+\tau^2)^2}.
$$

It is zero when

$$
\boxed{\alpha=\frac tc}\qquad\Rightarrow\qquad\left(\frac LD\right)_{max}=\frac{\tau}{2\tau^2}=\frac{1}{2\,(t/c)} .
$$

At the optimum, drag due to lift equals drag due to thickness. The result does not depend on $M_\infty$ (within Ackeret theory). Geometrically, $\alpha=t/c$ is the angle at which the diamond's upper front face lies along the free stream, since its half-angle is $(t/2)/(c/2)=t/c$. So there is no wave at all from the upper leading edge, which is the $\alpha=2.86^\circ$ case of [[SESA3029 Example Sheet 1 - Solutions#Q7. Wave patterns at α = 5°, 2.86° and −2.86°|Example Sheet 1 Q7]].

![[at_diamond_lift_to_drag.png|900]]

> [!check] A 5 % diamond at $M_\infty=2$
> $\alpha=t/c=0.05$ rad $=2.86^\circ$, $\lambda=1.7321$: $C_l=4(0.05)/1.7321=0.1155$, $C_d=\frac{4}{1.7321}(0.0025+0.0025)=0.01155$, so $L/D=10.0=1/(2\times0.05)$ ✓. The [[SESA3029 Example Sheet 2 - Solutions#Q5. Diamond aerofoil by Ackeret theory|ES2 Q5]] diamond (same $t/c$, $\alpha=2^\circ$) gets $L/D=9.39$, so it flies slightly below its best angle. Viscous skin friction, which Ackeret leaves out, lowers the real $L/D$ and moves the best angle up.

Real supersonic wings use thin, nearly symmetric sections close to this ideal but with rounded noses for low-speed flight (slide 11). The X-1 used NACA 65-110 and 65-108 sections, and the X-1E a NACA 64A004. The F-22 uses NACA 64A005.92 at the root and 64A004.29 at the tip. Overlaid on a diamond on slide 11, the F-22 root section is almost indistinguishable from it.

## Problem-solving workflow

1. Check that the question wants linear (Ackeret) theory, and that the angles are small and $M_\infty$ is well above 1.
2. Compute $\lambda=\sqrt{M_\infty^2-1}$ and convert every angle to radians.
3. For each face, find $\theta$ from the free-stream direction (compression +) and $C_p=2\theta/\lambda$; get $p$ if pressures are asked for.
4. For lift and drag, use the integrated results ($C_l=4\alpha/\lambda$; $C_d$ from §8), or sum face by face for an odd shape.
5. For the moment, $\Delta C_p$ is uniform on a flat plate, so the load acts at $c/2$.
6. If asked to compare, redo the faces with oblique-shock and Prandtl–Meyer relations ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]).

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| Ackeret theory; Ackeret formula | linearised supersonic (thin-aerofoil) theory; first-order supersonic theory | 4.5 slides 1–8 | |
| $\lambda=\sqrt{M_\infty^2-1}$ | $\beta$ (Anderson and many textbooks; also ES2 Q4–Q5) | 4.5 slides 2–4 | The course keeps $\beta=\sqrt{1-M_\infty^2}$ for Prandtl–Glauert |
| Mach lines (characteristic lines) | Mach waves; characteristics | 4.5 slides 2–4 | |
| diamond shaped aerofoil | double-wedge aerofoil; rhombic aerofoil | 4.6 slides 9–10 | |
| faceted aerofoils | polygonal aerofoils; wedge sections | 4.6 slide 8 | |
| drag (from thickness, camber, incidence) | wave drag due to thickness / due to lift | 4.6 slides 6–8 | |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]
- New concepts: [[Ackeret Theory]] · [[Supersonic Wave Drag]]
- Earlier this module: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]] (the exact method) · [[SESA3029 W05a - Method of Characteristics|W05a]] (Riemann invariants, simple flow region) · [[Mach Waves and Mach Angle]] · [[Shock-Expansion Theory]]
- Earlier years: [[SESA2022 T4 - Thin Aerofoil Theory]] (subsonic thin-aerofoil decomposition, $C_{l0}=2\pi\alpha$)
- Worked sheets: [[SESA3029 Example Sheet 2 - Solutions#Q4. Flat plate by Ackeret theory|ES2 Q4]] · [[SESA3029 Example Sheet 2 - Solutions#Q5. Diamond aerofoil by Ackeret theory|ES2 Q5]] · exact versions in [[SESA3029 Example Sheet 1 - Solutions#Q4. Flat plate by shock-expansion theory|ES1 Q4]] and [[SESA3029 Example Sheet 1 - Solutions#Q6. Diamond aerofoil by shock-expansion theory|ES1 Q6]]
- Formulae: [[SESA3029 Formula Sheet#Euler equations and compressible aerofoils (Lectures 4.1–4.6)|Formula sheet: Chapter 4]]

## Sources

- `Lecture4-5.pdf`: 4.5 Ackeret Theory (Supersonic Aerofoil Theory for $M_\infty>1.2$), 8 slides. Not yet lectured.
- `Lecture4-6.pdf`: 4.6 Optimum Supersonic Aerofoils, 11 slides. Not yet lectured.
- Figures: `generate_aerothermo_w07_figures.py` (`at_ackeret_mach_lines.png`, `at_ackeret_vs_exact.png`, `at_aerofoil_decomposition.png`, `at_thickness_drag.png`, `at_diamond_lift_to_drag.png`). The shock-expansion curves use the exact θ–β–M and Prandtl–Meyer relations and reproduce the slide 7 numbers.
- Anderson, *Modern Compressible Flow*, §§4.15 and 9.7–9.9 (linearised supersonic flow); *Fundamentals of Aerodynamics*, §12.3.

## Self-study tasks

These decks have not been lectured; the slide 7 homework and the slide 10 question are set on the slides themselves. The rest are *suggested, not lecturer-set*.

### Core

- [ ] **(4.5 slide 7, homework)** $M_\infty=2$, $\alpha=10^\circ$: $C_l$ and $C_d$ by Ackeret and by shock-expansion. Answers 0.4031, 0.0703 and 0.4075, 0.0719. → [[#Worked example: flat plate at M = 2, α = 10° (4.5 slide 7, homework)|§4]]
- [ ] Derive $u'=-v'/\lambda$ and the Ackeret formula, including the check that $f(x-\lambda y)$ solves the wave equation. → [[#1. The wave equation and its solution (4.5 slides 2–3)|§§1–3]]
- [ ] Derive $C_l=4\alpha/\lambda$ and the three-term $C_d$ for a general thin aerofoil. → [[#7. Lift coefficient (4.6 slide 5)|§§7–8]]
- [ ] Show that the optimum symmetric section is the diamond ($f=g=0$, $k=c/2$). → [[#9. Thickness drag and the optimum section (4.6 slides 7–10)|§9]]
- [ ] **(4.6 slide 10 question)** Find the angle of attack for maximum $L/D$ of a diamond. Answer $\alpha=t/c$, $(L/D)_{max}=c/(2t)$. → [[#10. The best angle of attack (4.6 slide 10 question)|§10]]

### Further practice

- [ ] Redo [[SESA3029 Example Sheet 2 - Solutions#Q4. Flat plate by Ackeret theory|ES2 Q4]] and [[SESA3029 Example Sheet 2 - Solutions#Q5. Diamond aerofoil by Ackeret theory|Q5]] in the course's notation ($\lambda$ for $\sqrt{M^2-1}$).
- [ ] Derive $u'=+v'/\lambda$ for the lower surface and confirm that $C_p=2\theta/\lambda$ still holds with the course's sign rule. → [[#2. Mach lines and the key result u′ = −v′/λ (4.5 slides 3–4)|§2]]
- [ ] Get the Ackeret formula from the Riemann invariant $R^-=\nu+\theta$. → [[#3. Ackeret's formula (4.5 slide 5)|§3, the tip]]
- [ ] Show that a biconvex section has $4/3$ of the diamond's thickness drag. → [[#9. Thickness drag and the optimum section (4.6 slides 7–10)|§9]]
- [ ] Explain why the slide 6 drag integral can use $C_p$ instead of $p$. → [[#8. Drag coefficient (4.6 slide 6)|§8]]
