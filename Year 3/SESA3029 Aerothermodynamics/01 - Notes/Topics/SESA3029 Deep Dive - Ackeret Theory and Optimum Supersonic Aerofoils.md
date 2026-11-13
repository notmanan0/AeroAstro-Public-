---
title: "SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 4: High-speed aerodynamics"
order: 9.5
tags: [sesa3029, compressible-flow, supersonic, ackeret, wave-equation, wave-drag, diamond-aerofoil, derivation, deep-dive]
aliases: ["Ackeret theory derivation", "Ackeret deep dive", "Supersonic wave drag derivation", "Optimum supersonic aerofoil proof"]
date: 2026-11-12
status: lectured
coverage: "§§1–3 and the flat-plate results follow Lecture 4.5 (lectured Thu 12 Nov, checked against the transcript): the general solution of the wave equation by characteristic coordinates, the choice of family above and below, the flow field and C_p on both surfaces. §§4–7 follow Lecture 4.6 (lectured Fri 13 Nov, checked against the transcript): lift of a general thin aerofoil, the three parts of the wave drag, the optimum thickness distribution and the diamond's best L/D. §8 checks every result against exact shock-expansion numbers."
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]", "[[SESA3029 Deep Dive - From the Euler Equations to Prandtl-Glauert]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]"]
next_topics: []
key_concepts: ["[[Ackeret Theory]]", "[[Supersonic Wave Drag]]", "[[Linearised Compressible Potential Equation]]", "[[Shock-Expansion Theory]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]", "[[SESA3029 Example Sheet 1 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture4-5.pdf", "02 - Sources/Lectures/Lecture 4-5.txt", "02 - Sources/Lectures/Lecture4-6.pdf", "02 - Sources/Lectures/Lecture 4-6.txt"]
---

# SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils

> [!abstract] Summary
> For $M_\infty>1$ the linear potential equation is the wave equation, whose general solution is $f(x-\lambda y)+g(x+\lambda y)$; above a thin aerofoil only $f$ survives and below it only $g$, so each surface slope is carried unchanged along a Mach line and $C_p=2\theta/\sqrt{M_\infty^2-1}$ on both surfaces with one sign rule. Integrating gives $C_l=4\alpha/\lambda$ independent of camber and thickness, and a wave drag $C_d=\tfrac4\lambda[\alpha^2+\overline{h'^2}+\overline{y_c'^2}]$ that is a sum of squares. Completing the square shows that straight faces meeting at mid-chord, the diamond, minimise the thickness drag, and the drag polar gives the best $L/D=c/(2t)$ at $\alpha=t/c$.

> [!summary]- Exam use: quick path
> - **Use it when:** a thin aerofoil is in supersonic flow at small angles and a question asks for Ackeret's $C_p$, $C_l$ or $C_d$, for the drag split into incidence, thickness and camber, or for the optimum section and best incidence.
> - **Assumptions:** steady, inviscid, shock-free to first order; thin, small slopes **in radians**; $1.2\lesssim M_\infty\lesssim3$–4; $\theta$ measured from $\vec U_\infty$, positive for compression.
> - **Method:** 1. $\lambda=\sqrt{M_\infty^2-1}$. 2. Write $y_u$ and $y_l$; $\theta_u=y_u'$, $\theta_l=-y_l'$. 3. $C_p=2\theta/\lambda$ on each surface. 4. $C_l=\tfrac1c\int(C_{p_l}-C_{p_u})\,\mathrm dx$, $C_d=\tfrac1c\int(C_{p_u}\theta_u+C_{p_l}\theta_l)\,\mathrm dx$. 5. For the optimum, complete the square in $\int h'^2\,\mathrm dx$, then minimise over the crest position $k$.
> - **Common mistakes:** using degrees for $\theta$ or $\alpha$; giving the lower surface the same sign rule as the upper ($\theta_l=-y_l'$, because a rising wall expands the flow below it).
> - **Practise:** [[#8. Checks against shock-expansion theory|§8 checks]] · [[SESA3029 Example Sheet 2 - Solutions#Q5. Diamond aerofoil by Ackeret theory|ES2 Q5]]

Below $M_\infty=1$ a thin aerofoil makes itself felt everywhere, so the pressure at one point depends on the shape of the whole section, and an incompressible solution has to be found and then corrected ([[SESA3029 Deep Dive - From the Euler Equations to Prandtl-Glauert|Prandtl–Glauert]]). Above $M_\infty=1$ a disturbance can only travel along the two Mach lines through its source and only downstream. Above the aerofoil that leaves one family of lines, each starting on the surface, each carrying outwards the disturbance made where it started. The pressure at a surface point then depends on the slope at that point alone, and the field problem disappears.

That locality makes the optimum section easy to find. Lift is set by the incidence, and the wave drag is an integral of squared slopes, which can be minimised by elementary means. The optimum, a symmetric section with straight faces meeting at mid-chord, follows exactly from the linear theory, and its wave drag at zero incidence is within 0.5 % of the exact shock-expansion value for thickness ratios up to 10 % at $M_\infty=2$.

## 1. Assumptions and the wave equation

The theory rests on the linear potential equation of 4.3, whose derivation and range are set out in [[SESA3029 Deep Dive - From the Euler Equations to Prandtl-Glauert#6. Order of magnitude: which terms survive|the Euler-to-Prandtl–Glauert deep dive, §6]]. The assumptions are:

- **steady, inviscid, shock-free**: weak shocks are allowed, because their entropy jump is of third order in the deflection ([[SESA3029 Deep Dive - Theta-Beta-Mach Relation, Full Derivation#Leaving the Mach line: the weak-shock limit|θ–β–M deep dive §6]]), so to first order the flow is homentropic and irrotational;
- **thin aerofoil**: surface slopes are small and in radians, so $\tan\theta\approx\sin\theta\approx\theta$, and the boundary condition can be applied on $y=0$;
- **supersonic, not hypersonic**: $(\gamma+1)M_\infty^4\tau\ll(M_\infty^2-1)^{3/2}$ for thickness ratio $\tau$, which is why the range is about $1.2<M_\infty<3$–4;
- **free stream along $x$**: the incidence $\alpha$ is carried by the aerofoil geometry (§3), and $\theta$ is measured from $\vec U_\infty$ (Remember #1).

With $M_\infty>1$, move the $x$ term of the potential equation across and define $\lambda=\sqrt{M_\infty^2-1}$:

$$
(1-M_\infty^2)\phi_{xx}+\phi_{yy}=0
\quad\Rightarrow\quad
\lambda^2\phi_{xx}=\phi_{yy} .
$$

This is the wave equation, with $x$ in the role of time and $1/\lambda$ in the role of wave speed.

## 2. General solution by characteristic coordinates

$\phi=f(x-\lambda y)$ satisfies the equation, and a change of variables shows that every solution has this form plus one other. Define the two characteristic coordinates

$$
\eta=x-\lambda y,\qquad\zeta=x+\lambda y ,
$$

where $\eta$ is the course's variable. Their derivatives are $\eta_x=1$, $\eta_y=-\lambda$, $\zeta_x=1$, $\zeta_y=\lambda$. By the chain rule

$$
\phi_x=\phi_\eta\eta_x+\phi_\zeta\zeta_x=\phi_\eta+\phi_\zeta,\qquad
\phi_y=\phi_\eta\eta_y+\phi_\zeta\zeta_y=-\lambda\phi_\eta+\lambda\phi_\zeta .
$$

Apply the same rule again:

$$
\phi_{xx}=\phi_{\eta\eta}+2\phi_{\eta\zeta}+\phi_{\zeta\zeta},
$$

$$
\phi_{yy}=\lambda^2\phi_{\eta\eta}-2\lambda^2\phi_{\eta\zeta}+\lambda^2\phi_{\zeta\zeta} .
$$

Substitute into $\lambda^2\phi_{xx}-\phi_{yy}=0$. The $\phi_{\eta\eta}$ and $\phi_{\zeta\zeta}$ terms cancel:

$$
\lambda^2\left(2\phi_{\eta\zeta}+2\phi_{\eta\zeta}\right)=4\lambda^2\phi_{\eta\zeta}=0
\quad\Rightarrow\quad
\phi_{\eta\zeta}=0 .
$$

Integrate with respect to $\zeta$: $\phi_\eta$ does not depend on $\zeta$, so it is some function of $\eta$ alone. Integrate that with respect to $\eta$, adding a function of $\zeta$ as the constant of integration:

$$
\boxed{\phi=f(x-\lambda y)+g(x+\lambda y)}
$$

for any two functions $f$ and $g$ (checked symbolically). On a line $x-\lambda y=\text{const}$, $f$ is constant; such a line has slope $\mathrm dy/\mathrm dx=1/\lambda=\tan\mu$, a left-running Mach line. On $x+\lambda y=\text{const}$, $g$ is constant, along a right-running Mach line of slope $-\tan\mu$.

### Which family exists above and below

Take a point P at height $y_P>0$ above the aerofoil. The line $x+\lambda y=x_P+\lambda y_P$ through P meets the axis at $x=x_P+\lambda y_P$, downstream of P. A $g$-disturbance at P would therefore have to come from a part of the aerofoil downstream of P, against the direction in which supersonic disturbances travel, or from infinity, where the flow is uniform. Neither supplies one, so above the aerofoil $g$ is constant and can be set to zero:

$$
\phi=f(x-\lambda y)\quad(y>0),
$$

whose line through P meets the axis at $x_P-\lambda y_P$, upstream of P, as it must. Below the aerofoil the same argument with $y_P<0$ leaves

$$
\phi=g(x+\lambda y)\quad(y<0).
$$

## 3. The flow field and the surface pressure

Let the upper and lower surfaces be $y=y_u(x)$ and $y=y_l(x)$, with the free stream along $x$. Above the aerofoil, from $\phi=f(\eta)$,

$$
u'=\phi_x=f'(\eta),\qquad v'=\phi_y=-\lambda f'(\eta) .
$$

So $u'=-v'/\lambda$ everywhere above the aerofoil. The thin-aerofoil boundary condition, applied on $y=0^+$, is

$$
v'(x,0^+)=U_\infty\,y_u'(x) .
$$

At $y=0$, $\eta=x$, so this fixes $f'$ along the whole axis:

$$
-\lambda f'(x)=U_\infty y_u'(x)
\quad\Rightarrow\quad
f'(x)=-\frac{U_\infty}{\lambda}y_u'(x) .
$$

Since $f'$ is a function of one variable, the same formula holds with $x$ replaced by $\eta$ anywhere above the aerofoil:

$$
u'(x,y)=-\frac{U_\infty}{\lambda}\,y_u'(x-\lambda y) .
$$

The disturbance at height $y$ is the surface slope at the point $x-\lambda y$, where the Mach line through $(x,y)$ leaves the surface, carried out unchanged and undiminished. With the linearised $C_p=-2u'/U_\infty$,

$$
C_p(x,y)=\frac{2}{\lambda}\,y_u'(x-\lambda y)
\quad\Rightarrow\quad
C_{p_u}(x)=\frac{2y_u'(x)}{\lambda}\ \text{on the surface}.
$$

![[at_ackeret_mach_lines.png|900]]

Below the aerofoil, from $\phi=g(\zeta)$,

$$
u'=g'(\zeta),\qquad v'=\lambda g'(\zeta) .
$$

The boundary condition on $y=0^-$ is $v'(x,0^-)=U_\infty y_l'(x)$, and at $y=0$, $\zeta=x$:

$$
\lambda g'(x)=U_\infty y_l'(x)
\quad\Rightarrow\quad
u'(x,0^-)=\frac{U_\infty}{\lambda}y_l'(x)
\quad\Rightarrow\quad
C_{p_l}(x)=-\frac{2y_l'(x)}{\lambda} .
$$

Both surfaces obey one formula,

$$
\boxed{C_p=\frac{2\theta}{\sqrt{M_\infty^2-1}},\qquad\theta_u=\frac{\mathrm dy_u}{\mathrm dx},\quad\theta_l=-\frac{\mathrm dy_l}{\mathrm dx}}
$$

which is the course's sign convention, here derived instead of chosen. A positive $\theta$ is a surface that turns into the flow on its own side, which compresses it, and a negative $\theta$ expands it (Remember #2). A rising wall ($y'>0$) compresses the flow above it and expands the flow below it.

For a flat plate at incidence $\alpha$, $y_u=y_l=-\alpha x$, so $\theta_u=-\alpha$ and $\theta_l=+\alpha$: the upper surface expands and the lower surface compresses, as the duct test of [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#4. The flat plate at incidence|W07c §4]] gives. The same formula also follows from the Riemann invariant $\nu+\theta=\nu_\infty$ in the limit of weak waves ([[SESA3029 Deep Dive - Riemann Invariants, Full Derivation#A simple flow region and the Ackeret limit|Riemann deep dive §8]]) and from the weak oblique shock ([[SESA3029 Deep Dive - Theta-Beta-Mach Relation, Full Derivation#Leaving the Mach line: the weak-shock limit|θ–β–M deep dive §6]]).

## 4. Lift of a general thin aerofoil

A general thin aerofoil is a thickness distribution $h(x)$, a camber line $y_c(x)$ and the incidence, with the chord tilted down by $\alpha x$:

$$
y_u=h+y_c-\alpha x,\qquad y_l=-h+y_c-\alpha x,\qquad h=y_c=0\ \text{at}\ x=0\ \text{and}\ x=c .
$$

The surface angles of §3 are

$$
\theta_u=y_u'=h'+y_c'-\alpha,\qquad\theta_l=-y_l'=h'-y_c'+\alpha .
$$

To first order each surface element's pressure force is vertical, and the free stream is horizontal, so the lift per unit span is the pressure difference integrated along $x$:

$$
C_l=\frac1c\int_0^c\left(C_{p_l}-C_{p_u}\right)\mathrm dx .
$$

With $C_p=2\theta/\lambda$, the integrand depends only on $\theta_l-\theta_u$:

$$
\theta_l-\theta_u=\left(h'-y_c'+\alpha\right)-\left(h'+y_c'-\alpha\right)=2\left(\alpha-y_c'\right).
$$

The thickness has cancelled: a symmetric thickness distribution adds the same pressure to both surfaces. Substitute:

$$
C_l=\frac{4}{\lambda c}\int_0^c\left(\alpha-y_c'\right)\mathrm dx .
$$

Integrate. The camber term is $[y_c]_0^c=0$:

$$
C_l=\frac{4}{\lambda c}\left(\alpha c-0\right)
\quad\Rightarrow\quad
\boxed{C_l=\frac{4\alpha}{\sqrt{M_\infty^2-1}}}
$$

Camber changes where along the chord the load sits, but not its total. This differs from subsonic thin-aerofoil theory, where camber shifts the zero-lift angle, because there the pressure at each point depends on the whole camber line through the elliptic equation, while here it depends only on the local slope.

## 5. Wave drag and its three parts

On the upper surface the outward normal is proportional to $(-y_u',1)$, and the pressure pushes along the inward normal. Per unit length $\mathrm dx$ of chord its $x$-component is $p_u\,y_u'$, rearwards where the surface faces forwards. On the lower surface the outward normal is proportional to $(y_l',-1)$ and the $x$-component is $-p_l\,y_l'$. The drag per unit span is therefore exactly

$$
D'=\int_0^c\left(p_u\,y_u'-p_l\,y_l'\right)\mathrm dx=\int_0^c\left(p_u\theta_u+p_l\theta_l\right)\mathrm dx .
$$

(Written with the inclination angle, $p\sin\theta\,\mathrm ds=p\tan\theta\,\mathrm dx$, which is $p\,\theta\,\mathrm dx$ to first order.) A uniform pressure on a closed body gives no force:

$$
\int_0^c\left(\theta_u+\theta_l\right)\mathrm dx=\int_0^c2h'\,\mathrm dx=2\left[h\right]_0^c=0 .
$$

Subtract $p_\infty$ times this zero from $D'$ and divide by $\tfrac12\rho_\infty U_\infty^2c$:

$$
C_d=\frac1c\int_0^c\left(C_{p_u}\theta_u+C_{p_l}\theta_l\right)\mathrm dx .
$$

Substitute $C_p=2\theta/\lambda$ on each surface:

$$
C_d=\frac{2}{\lambda c}\int_0^c\left(\theta_u^2+\theta_l^2\right)\mathrm dx .
$$

The drag is a sum of squares, so it is never negative and every slope adds to it. Write $s=y_c'-\alpha$, so that $\theta_u=h'+s$ and $\theta_l=h'-s$. Then

$$
\theta_u^2+\theta_l^2=\left(h'^2+2h's+s^2\right)+\left(h'^2-2h's+s^2\right)=2h'^2+2s^2 .
$$

Expand $s^2$:

$$
s^2=y_c'^2-2\alpha y_c'+\alpha^2 .
$$

The cross term integrates to zero, $\int_0^c-2\alpha y_c'\,\mathrm dx=-2\alpha[y_c]_0^c=0$. So

$$
C_d=\frac{4}{\lambda c}\int_0^c\left(\alpha^2+h'^2+y_c'^2\right)\mathrm dx .
$$

With overbars for chordwise means, $\overline{q}=\tfrac1c\int_0^cq\,\mathrm dx$:

$$
\boxed{C_d=\frac{4}{\sqrt{M_\infty^2-1}}\left[\alpha^2+\overline{\left(\frac{\mathrm dh}{\mathrm dx}\right)^2}+\overline{\left(\frac{\mathrm dy_c}{\mathrm dx}\right)^2}\right]}
$$

The three parts are the drag due to lift (incidence), the drag due to thickness and the drag due to camber, and they add without interaction. Camber costs drag and buys no lift (§4), so supersonic sections are uncambered. Eliminating $\alpha=\lambda C_l/4$ turns the first part into a lift-dependent drag and gives the drag polar:

$$
\frac{4\alpha^2}{\lambda}=\frac{4}{\lambda}\cdot\frac{\lambda^2C_l^2}{16}=\frac{\lambda C_l^2}{4}
\quad\Rightarrow\quad
C_d=\frac{\lambda}{4}C_l^2+\frac{4}{\lambda}\left[\overline{h'^2}+\overline{y_c'^2}\right].
$$

For a fixed $C_l$ the lift-dependent part grows with $M_\infty$ (as $\lambda$), while the thickness and camber parts fall (as $1/\lambda$).

> [!check] Camber drag for a parabolic camber line
> $y_c=4\varepsilon x(c-x)/c^2$ has $y_c'=4\varepsilon(c-2x)/c^2$, and $\tfrac1c\int_0^cy_c'^2\,\mathrm dx=\tfrac{16}{3}(\varepsilon/c)^2$ (computed symbolically). With $\varepsilon/c=0.02$ that is $0.00213$, which on a 5 % diamond at $\alpha=t/c$, $M_\infty=2$ raises $C_d$ from $0.01155$ to $0.01647$ for the same $C_l$ ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#8. Drag coefficient|W07c §8]]).

## 6. The optimum thickness distribution

For a symmetric section the only shape-dependent part of the drag is $\int_0^ch'^2\,\mathrm dx$, to be minimised over shapes $h(x)$ with maximum half-thickness $t/2$. Let the crest be at $x=k$. On the front part, $h$ rises from $h(0)=0$ to $h(k)=t/2$, so its slope has a fixed mean:

$$
\int_0^kh'\,\mathrm dx=h(k)-h(0)=\frac t2
\quad\Rightarrow\quad
m\equiv\frac{t}{2k}\ \text{is the mean slope}.
$$

### Completing the square

The integral of a square is never negative:

$$
\int_0^k\left(h'-m\right)^2\mathrm dx\ge0 .
$$

Expand the square:

$$
\int_0^kh'^2\,\mathrm dx-2m\int_0^kh'\,\mathrm dx+m^2k\ge0 .
$$

Substitute $\int_0^kh'\,\mathrm dx=t/2$ and $m=t/(2k)$:

$$
\int_0^kh'^2\,\mathrm dx-\frac{t}{k}\cdot\frac t2+\frac{t^2}{4k^2}\,k\ge0 .
$$

Simplify:

$$
\int_0^kh'^2\,\mathrm dx\ge\frac{t^2}{2k}-\frac{t^2}{4k}=\frac{t^2}{4k} .
$$

Equality holds only if $(h'-m)^2=0$ everywhere, i.e. $h'=m$: a straight face. The rear part, falling from $t/2$ at $k$ to 0 at $c$, gives in the same way $\int_k^ch'^2\,\mathrm dx\ge t^2/[4(c-k)]$, with equality for a straight face. This is the course's result in another form: writing $h$ as the straight face plus a function $f$ (or $g$) that vanishes at both ends gives

$$
\int_0^ch'^2\,\mathrm dx=\frac{t^2}{4}\left(\frac1k+\frac1{c-k}\right)+\int_0^kf'^2\,\mathrm dx+\int_k^cg'^2\,\mathrm dx ,
$$

where $f'=h'-m$ on the front, so the extra integrals are exactly the squares above. Any curvature of the faces only adds drag: faceted sections are favoured.

### The best crest position

With straight faces the drag integral depends only on $k$:

$$
F(k)=\frac{t^2}{4}\left(\frac1k+\frac1{c-k}\right).
$$

Differentiate:

$$
\frac{\mathrm dF}{\mathrm dk}=\frac{t^2}{4}\left[-\frac1{k^2}+\frac1{(c-k)^2}\right].
$$

Set it to zero:

$$
\frac1{k^2}=\frac1{(c-k)^2}
\quad\Rightarrow\quad
k=c-k
\quad\Rightarrow\quad
\boxed{k=\frac c2}
$$

taking the positive root, since $k=-(c-k)$ would need $c=0$. The second derivative, $\tfrac{t^2}{2}\left[k^{-3}+(c-k)^{-3}\right]$, is positive, so this is a minimum. At $k=c/2$:

$$
F\!\left(\frac c2\right)=\frac{t^2}{4}\left(\frac2c+\frac2c\right)=\frac{t^2}{c},\qquad\overline{h'^2}=\frac{F}{c}=\left(\frac tc\right)^2 .
$$

The optimum symmetric section is the **diamond**, with its thickest point at mid-chord, and its drag is

$$
C_d=\frac{4}{\sqrt{M_\infty^2-1}}\left[\alpha^2+\left(\frac tc\right)^2\right].
$$

Moving the crest to $k=0.3c$ gives $F=\tfrac{t^2}{4c}\left(\tfrac1{0.3}+\tfrac1{0.7}\right)=\tfrac{25}{21}\,\tfrac{t^2}{c}=1.190\,\tfrac{t^2}{c}$, 19 % more thickness drag. A biconvex section with the same $t$, $h=2tx(c-x)/c^2$, has $\int_0^ch'^2\,\mathrm dx=4t^2/(3c)$, a third more than the diamond (both computed symbolically).

![[at_thickness_drag.png|900]]

## 7. The diamond: best lift-to-drag ratio

The same expressions give the incidence for the highest lift-to-drag ratio. Write $\tau=t/c$. The factor $4/\lambda$ cancels in the ratio:

$$
\frac LD=\frac{C_l}{C_d}=\frac{\alpha}{\alpha^2+\tau^2} .
$$

Differentiate by the quotient rule:

$$
\frac{\mathrm d}{\mathrm d\alpha}\left(\frac LD\right)=\frac{\left(\alpha^2+\tau^2\right)-\alpha\cdot2\alpha}{\left(\alpha^2+\tau^2\right)^2}=\frac{\tau^2-\alpha^2}{\left(\alpha^2+\tau^2\right)^2} .
$$

It is zero at $\alpha=\tau$, positive below and negative above, so

$$
\boxed{\alpha_{opt}=\frac tc,\qquad\left(\frac LD\right)_{max}=\frac{\tau}{2\tau^2}=\frac{c}{2t}}
$$

independent of $M_\infty$. In the drag polar of §5 the same point is where a line from the origin touches the parabola $C_d=\lambda C_l^2/4+4\tau^2/\lambda$. Minimising $C_d/C_l=\lambda C_l/4+4\tau^2/(\lambda C_l)$, a sum of two positive terms with a constant product, puts the minimum where they are equal:

$$
\frac{\lambda C_l}{4}=\frac{4\tau^2}{\lambda C_l}
\quad\Rightarrow\quad
C_l=\frac{4\tau}{\lambda}
\quad\Rightarrow\quad
\alpha=\tau .
$$

At the best incidence the lift-dependent drag equals the thickness drag. Geometrically, the diamond's half-angle is $(t/2)/(c/2)=t/c$, so at $\alpha=t/c$ its upper front face lies along the free stream and sends out no wave ([[SESA3029 Example Sheet 1 - Solutions#Q7. Wave patterns at α = 5°, 2.86° and −2.86°|ES1 Q7]]).

![[at_ackeret_drag_polar.png|900]]

## 8. Checks against shock-expansion theory

All numbers use $\gamma=1.4$. The exact values come from the shock-expansion method ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]): an oblique shock or Prandtl–Meyer fan at each leading face, a fan at each crest, and the face pressures integrated in body axes, all computed in Python.

> [!check] Three cases against the course and example-sheet numbers
> - **Flat plate, $M_\infty=2$, $\alpha=10^\circ$ (homework).** Ackeret: $C_l=4(0.17453)/1.7321=0.4031$ and $C_d=4(0.17453)^2/1.7321=0.0703$. Shock-expansion: $0.4075$ and $0.0719$. Both match the course values; Ackeret is 1.1 % low on lift and 2.1 % low on drag.
> - **Diamond, $M_\infty=1.8$, $t/c=0.05$, $\alpha=2^\circ$ (ES1 Q6 and ES2 Q5).** Ackeret: $C_l=4(0.03491)/1.4967=0.09329$ and $C_d=\tfrac{4}{1.4967}(0.001218+0.0025)=0.009938$, i.e. $L'=10.58$ and $D'=1.127$ kN/m at $q_\infty=113.4$ kPa. Shock-expansion: $C_l=0.09381$, $C_d=0.009991$, i.e. $10.64$ and $1.133$ kN/m, the [[SESA3029 Example Sheet 1 - Solutions#Q6. Diamond aerofoil by shock-expansion theory|ES1 Q6]] answers. The ratio $L/D$ is 9.387 by Ackeret and 9.389 exactly.
> - **Best incidence of a 5 % diamond at $M_\infty=2$.** Ackeret: $\alpha=0.05$ rad $=2.865^\circ$, $C_l=0.11547$, $C_d=0.011547$, $L/D=10.000$. Shock-expansion at the same $\alpha$: $C_l=0.11609$, $C_d=0.011631$, $L/D=9.981$; scanning $\alpha$ puts the exact optimum at $2.85^\circ$ with the same $L/D$ to four figures.

The thickness drag alone ($\alpha=0$) is closer still:

| $t/c$ | $M_\infty=1.5$ | $M_\infty=2$ | $M_\infty=3$ |
|---:|---:|---:|---:|
| 0.05 | 1.0036 | 1.0011 | 1.0029 |
| 0.10 | 1.0157 | 1.0044 | 1.0108 |
| 0.15 | 1.0433 | 1.0098 | 1.0229 |

*(Ratio of the shock-expansion $C_d$ to Ackeret's $4\tau^2/\lambda$, diamond at zero incidence.)*

![[at_ackeret_wave_drag_exact.png|900]]

The local pressures are much less accurate than the drag: on the 5 % diamond at $M_\infty=2$ the exact $C_p$ on a front face is $0.0615$ against Ackeret's $0.0577$, 6.6 % higher. The errors cancel in the drag because of where the faces point. On a front face the flow is compressed, and the exact compression $C_p$ lies above $2\theta/\lambda$ ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#3. Ackeret's formula|W07c §3]]), which adds drag. On a rear face the flow is expanded, and the exact expansion $C_p$ also lies above the linear value, so there is less suction on a rearward-facing surface, which removes drag. If each face pressure is written as $C_1\theta+C_2\theta^2$ with the same $C_2$ on both faces (second-order or Busemann theory, not lectured), the front faces ($\theta=+\varepsilon$) add $C_2\varepsilon^3$ to the drag integrand and the rear faces ($\theta=-\varepsilon$) add $-C_2\varepsilon^3$, so the second-order corrections cancel and the remaining error in $C_d$ is of higher order in the slope. The cancellation is best near $M_\infty=2$, where the linear theory is most accurate overall ([[SESA3029 Deep Dive - From the Euler Equations to Prandtl-Glauert#Supersonic: the three terms combine|Euler-to-Prandtl–Glauert deep dive §6]]).

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Lecture note: [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]] (the lectured route, the flat plate, the sign rules, Remembers #1–#3, the real wing sections of 4.6 slide 11)
- Related deep dives: [[SESA3029 Deep Dive - From the Euler Equations to Prandtl-Glauert]] (where the wave equation comes from and when it holds) · [[SESA3029 Deep Dive - Theta-Beta-Mach Relation, Full Derivation]] (Ackeret's $C_p$ as the weak-shock limit) · [[SESA3029 Deep Dive - Riemann Invariants, Full Derivation]] (Ackeret as the weak-wave limit of the MoC)
- Exact method: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]] · [[Shock-Expansion Theory]]
- Concepts: [[Ackeret Theory]] · [[Supersonic Wave Drag]] · [[Linearised Compressible Potential Equation]] · [[Mach Waves and Mach Angle]]
- Worked sheets: [[SESA3029 Example Sheet 2 - Solutions#Q4. Flat plate by Ackeret theory|ES2 Q4]] · [[SESA3029 Example Sheet 2 - Solutions#Q5. Diamond aerofoil by Ackeret theory|ES2 Q5]] · [[SESA3029 Example Sheet 1 - Solutions#Q6. Diamond aerofoil by shock-expansion theory|ES1 Q6]]
- Earlier years: [[SESA2022 T4 - Thin Aerofoil Theory]] (the subsonic decomposition into thickness, camber and incidence)
- Formulae: [[SESA3029 Formula Sheet#Euler equations and compressible aerofoils|Formula sheet: Chapter 4]]

## Sources

- `Lecture4-5.pdf` (4.5 Ackeret Theory), slides 2–8: the wave equation, its solution along Mach lines, $u'=-v'/\lambda$, the Ackeret formula, the flat plate and the slide 7 example. Lectured Thu 12 Nov; recording `Lecture 4-5.txt` (L4-5).
- `Lecture4-6.pdf` (4.6 Optimum Supersonic Aerofoils), slides 3–10: the decomposition, the sign convention, $C_l$, $C_d$, the $f$–$g$ argument, the optimum $k$ and the diamond question. Lectured Fri 13 Nov (`Lecture 4-6.txt`, L4-6), following the slides; §§4–7 were checked against it.
- Anderson, *Modern Compressible Flow*, §§9.7–9.9 (linearised supersonic flow); Liepmann & Roshko, *Elements of Gasdynamics*, §§8.4–8.6 (wave drag and the optimum section).
- Checks: the general solution, the biconvex and camber integrals and $F(c/2)$ were verified symbolically (sympy); the shock-expansion numbers and every other number were computed in Python. Figures `at_ackeret_drag_polar.png` and `at_ackeret_wave_drag_exact.png` from `generate_aerothermo_deepdive_figures.py`; `at_ackeret_mach_lines.png` and `at_thickness_drag.png` from `generate_aerothermo_w07_figures.py`.

## Self-study tasks

Tasks citing L4-5 come from the Thu 12 Nov lecture and tasks citing 4.6 slides from the deck lectured on Fri 13 Nov (the same tasks, with L4-6 line references, appear in [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#Self-study tasks|W07c]]). Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(L4-5, ll. 23–160; slides 2–4)** Show that $\phi=f(x-\lambda y)$ solves $\lambda^2\phi_{xx}=\phi_{yy}$, that it is constant along Mach lines, and that $u'=-v'/\lambda$. → [[#2. General solution by characteristic coordinates|§2]] · [[#3. The flow field and the surface pressure|§3]]
- [ ] **(L4-5, ll. 170–216; slide 5)** Derive $C_p=2\theta/\sqrt{M_\infty^2-1}$ from flow tangency. → [[#3. The flow field and the surface pressure|§3]]
- [ ] **(4.5 slide 7, homework; L4-5, ll. 325–343)** $M_\infty=2$, $\alpha=10^\circ$ flat plate by Ackeret and by shock-expansion. Answers 0.4031, 0.0703 and 0.4075, 0.0719. → [[#8. Checks against shock-expansion theory|§8]]
- [ ] **(4.6 slides 5–6)** Derive $C_l=4\alpha/\lambda$ and the three-part $C_d$ for a general thin aerofoil. → [[#4. Lift of a general thin aerofoil|§4]] · [[#5. Wave drag and its three parts|§5]]
- [ ] **(4.6 slide 10 question)** Find the incidence for maximum $L/D$ of a diamond. Answer $\alpha=t/c$, $(L/D)_{max}=c/(2t)$. → [[#7. The diamond: best lift-to-drag ratio|§7]]

### Further practice

- [ ] **(4.6 slides 7–9)** Show that straight faces and $k=c/2$ minimise the thickness drag. → [[#6. The optimum thickness distribution|§6]]
- [ ] (suggested, not lecturer-set) Derive the general solution $f(x-\lambda y)+g(x+\lambda y)$ with characteristic coordinates and explain why only $f$ appears above the aerofoil. → [[#Which family exists above and below|§2]]
- [ ] (suggested, not lecturer-set) Prove the straight-face result by completing the square, and show that a biconvex section has $4/3$ of the diamond's thickness drag. → [[#Completing the square|§6]]
- [ ] (suggested, not lecturer-set) Derive the drag polar $C_d=\lambda C_l^2/4+4\tau^2/\lambda$ and find the best $L/D$ from it. → [[#7. The diamond: best lift-to-drag ratio|§7]]

## Transcript and slide slips

> [!warning] Slips on 4.5 slide 3 and 4.6 slide 6
> Where: [[#2. General solution by characteristic coordinates]] and [[#5. Wave drag and its three parts]].
>
> - 4.5 slide 3 writes *"since $\partial\eta/\partial x=-\lambda$"* next to $v'$; it is $\partial\eta/\partial y=-\lambda$. The middle step of $\phi_{yy}$ is printed with $\partial/\partial x$ for $\partial/\partial y$. The final $\lambda^2f''$ is right.
> - 4.6 slide 6 writes $D'=\int(p_l\cos\theta_l+p_u\cos\theta_u)\,\mathrm dx$. The streamwise component of a pressure force on a surface inclined at $\theta$ is $p\sin\theta\,\mathrm ds=p\tan\theta\,\mathrm dx$, which is $p\theta\,\mathrm dx$ to first order; the slide's next step, $\simeq\int(p_l\theta_l+p_u\theta_u)\,\mathrm dx$, is the $\sin$ version.

### Transcript slips (L4-5)

> [!warning] Slips in `Lecture 4-5.txt`
> | Where | Said | Correct |
> |---|---|---|
> | L4-5, l. 52 | *"theta by dx is minus lambda"* | $\partial\eta/\partial y=-\lambda$ (the slide 3 slip read aloud) |
> | L4-5, ll. 262–263 | positive $\theta$ for the upper surface of the plate | negative: $\theta_u=-\alpha$, an expansion (corrected aloud at l. 268) |
> | L4-5, l. 311 | $C_l$ *"four alpha divided by square root of m minus one"* | $4\alpha/\sqrt{M_\infty^2-1}$ |
> | L4-5, l. 313 | $C_d$ *"four alpha squared divided by m squared minus one"* | $4\alpha^2/\sqrt{M_\infty^2-1}$ |
