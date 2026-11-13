---
title: "SESA3043 Deep Dive - Joukowski and Kármán-Trefftz Aerofoils, Full Derivation"
module: "SESA3043 Advanced Aeronautics"
type: topic
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
order: 6.5
tags: [sesa3043, potential-flow, conformal-mapping, joukowski, karman-trefftz, kutta-condition, circle-theorem, derivation, deep-dive]
aliases: ["Joukowski deep dive", "Kármán–Trefftz deep dive", "KT aerofoil full derivation", "Kutta circulation derivation"]
date: 2026-11-12
status: lectured
coverage: "Every step from the lifting cylinder to the Joukowski and Kármán–Trefftz aerofoils (Ch2 slides 13–20, lectured 8–9 Oct): the circle theorem, the critical points and the trailing-edge angle, the far-field scaling, the Kutta circulation, the surface speed, Cp and CL, with every number checked against ktreff.py and the coursework aerofoil (ε = 0.07, β = 0.06, τ = 0.2)"
parent: ["[[SESA3043 Advanced Aeronautics Hub]]"]
prerequisites: ["[[SESA3043 2.1 - Complex Functions and Conformal Mapping]]", "[[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]", "[[Complex Velocity Potential]]"]
next_topics: ["[[SESA3043 2.3 - Panel Methods]]"]
key_concepts: ["[[Joukowski Transformation]]", "[[Kármán–Trefftz Transformation]]", "[[Conformal Mapping]]", "[[Kutta Condition]]", "[[Kutta-Joukowski Theorem]]"]
tutorial_sheets: ["03 - Exams & Past Papers/Ch2_Revision_Questions.pdf"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf", "02 - Sources/Lectures/Ch2_Notes_CW Code Explainer.pdf", "02 - Sources/Lectures/ktreff.py", "02 - Sources/Lectures/08 October 2026 at 13_50_19.txt", "02 - Sources/Lectures/09 October 2026 at 14_57_18.txt", "02 - Sources/Lectures/09 October 2026 at 14_17_51.txt"]
---

# SESA3043 Deep Dive - Joukowski and Kármán-Trefftz Aerofoils, Full Derivation

> [!abstract] Summary
> A lifting cylinder in the $\bar z$-plane is carried onto an aerofoil by the Joukowski map $z=\bar z+b^2/\bar z$ or the Kármán–Trefftz map, whose exponent $p=2-\tau/\pi$ turns the circle's smooth point $\bar z=b$ into a trailing edge of included angle $\tau$. The map's derivative vanishes there, so the circulation must put the rear stagnation point on $\bar z=b$: $\Gamma=4\pi a\bar U_\infty\sin(\alpha+\beta)$, with $\bar U_\infty=(2/p)U_\infty$. Kutta–Joukowski then gives $C_L=16\pi a\sin(\alpha+\beta)/(pc)$, which for the coursework aerofoil at $\alpha=3^\circ$ is $0.776024$, the exact value against which the panel method is tested.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the steps that turn flow over a cylinder into flow over an aerofoil, why the trailing edge is sharp, or where $\Gamma=4\pi aU_\infty\sin(\alpha+\beta)$ comes from; or when checking the coursework's exact $C_L$ and $C_p$. The exam asks for the logic, not the arithmetic (L-b).
> - **Assumptions:** 2-D, steady, incompressible, inviscid, irrotational; the map is analytic outside the circle with $\mathrm dz/\mathrm d\bar z\neq0$ except at $\bar z=b$; angles in radians; $\Gamma$ clockwise positive.
> - **Method:** 1. Lifting cylinder in $\bar z$: $\Phi=\bar U_\infty\left[\zeta e^{-i\alpha}+a^2e^{i\alpha}/\zeta\right]+\frac{i\Gamma}{2\pi}\ln\zeta$, $\zeta=\bar z-\bar z_0$. 2. Map with $z(\bar z)$; the circle through $\bar z=b$ gives the sharp TE. 3. Kutta: $\mathrm d\Phi/\mathrm d\bar z=0$ at $\zeta=ae^{-i\beta}$, so $\Gamma=4\pi a\bar U_\infty\sin(\alpha+\beta)$. 4. $u-iv=(\mathrm d\Phi/\mathrm d\bar z)/(\mathrm dz/\mathrm d\bar z)$ and $C_p=1-|u-iv|^2/U_\infty^2$. 5. $C_L=2\Gamma/(U_\infty c)$.
> - **Common mistakes:** using $U_\infty$ for the circle-plane stream with the KT map, which needs $\bar U_\infty=(2/p)U_\infty$ (otherwise $C_L$ is 3 % low here, more for larger $\tau$); expecting the KT trailing edge to have a finite speed like the Joukowski cusp, when it is a stagnation point.
> - **Practise:** [[#8. The coursework aerofoil, worked through|§8, the coursework aerofoil]] · [[SESA3043 2.1 - Complex Functions and Conformal Mapping#The flow and the Kutta condition|2.1, Kutta circulation]]

A conformal map moves a solved flow from one plane to another without changing the streamlines' identity: the value of $\psi$ on each streamline is carried across, and the speed is divided by the local stretch $|\mathrm dz/\mathrm d\bar z|$ ([[SESA3043 2.1 - Complex Functions and Conformal Mapping#Why an analytic map preserves angles (derivation)|2.1 §2]]). The cylinder is the one shape whose flow at any incidence and with any circulation is known in closed form, so every aerofoil in Chapter 2 starts as a circle in the $\bar z$-plane. The position of the circle relative to the two critical points of the map sets the shape: the circle passes through $\bar z=b$, which becomes the sharp trailing edge, and encloses $\bar z=-b$, so the leading edge stays round. Moving the centre left gives thickness, and moving it up gives camber.

At the critical point $\bar z=b$ the map folds the plane instead of stretching it. A finite velocity in the circle plane becomes an infinite one on the aerofoil, unless the circle-plane flow is stationary at that point. The circulation is the one free parameter of the cylinder flow, and it is chosen to make the rear stagnation point sit exactly on $\bar z=b$. That choice is the Kutta condition. It fixes the lift, and the Kutta–Joukowski theorem turns the circulation into $C_L$ without any pressure integration.

The Joukowski map folds the plane through a full $2\pi$ at $\bar z=b$, so its trailing edge is a cusp with zero included angle. The Kármán–Trefftz (KT) map folds it through a little less, $(2-\tau/\pi)\pi$, and leaves a wedge of angle $\tau$. The same exponent also rescales the far field by $2/p$, which is the one place the KT calculation differs from the Joukowski one in a way that changes the numbers.

## 1. Planes, notation and assumptions

The flow is two-dimensional, steady, incompressible and inviscid, and it starts irrotational and stays so, which is what makes a complex potential $\Phi=\phi+i\psi$ exist ([[Complex Velocity Potential]]). Each assumption is used at a definite step: irrotationality and incompressibility make $\phi$ and $\psi$ harmonic, so an analytic map carries the solution across; steadiness lets Bernoulli give $C_p$ from the speed alone; inviscid flow is why the Kutta condition has to be imposed by hand rather than arising from viscosity.

| Symbol | Meaning |
|---|---|
| $\bar z$, $z$ | the circle plane and the aerofoil (physical) plane. The bar marks the plane, not a complex conjugate; a conjugate is written with a star, $w^*$ |
| $b$ | the transfer constant; the critical points of both maps are $\bar z=\pm b$ |
| $a$ | the radius of the circle |
| $\varepsilon$, $\beta$ | the thickness factor (centre moved left by $\varepsilon b$) and the camber factor (centre moved up by $a\sin\beta$) |
| $\bar z_0$ | the centre of the circle, $\bar z_0=-\varepsilon b+ia\sin\beta$, with $a\cos\beta=b(1+\varepsilon)$ |
| $\zeta$, $\theta$ | position relative to the centre, $\zeta=\bar z-\bar z_0$; on the circle $\zeta=ae^{i\theta}$ |
| $\tau$, $p$ | the trailing-edge included angle in radians, and $p=2-\tau/\pi$ ($p=2$ is Joukowski) |
| $\alpha$ | incidence of the free stream to the $x$-axis |
| $\bar U_\infty$, $U_\infty$ | free-stream speed in the circle plane and in the aerofoil plane |
| $\Gamma$ | circulation, **clockwise positive**, so the vortex term is $+\frac{i\Gamma}{2\pi}\ln\zeta$ |

The clockwise convention matches Chapter 2 and the coursework code. [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#Lifting cylinder: uniform flow plus doublet plus point vortex|1.3]] counts counter-clockwise as positive and writes $-\frac{i\Gamma}{2\pi}\ln z$; the two differ only in the sign attached to the symbol $\Gamma$. With clockwise $\Gamma>0$ the lift is upwards.

The trailing-edge point has a simple position on the circle. Measured from the centre it is

$$
\zeta_{TE}=b-\bar z_0 .
$$

Substitute the centre:

$$
\zeta_{TE}=b+\varepsilon b-ia\sin\beta .
$$

Use $b(1+\varepsilon)=a\cos\beta$:

$$
\zeta_{TE}=a\cos\beta-ia\sin\beta=ae^{-i\beta} .
$$

So the trailing edge is at $\theta=-\beta$ on the circle, for any $\varepsilon$. The other critical point, $\bar z=-b$, lies inside the circle: its distance from the centre satisfies $|{-b}-\bar z_0|^2=b^2(1-\varepsilon)^2+a^2\sin^2\beta$, which is less than $a^2=a^2\cos^2\beta+a^2\sin^2\beta=b^2(1+\varepsilon)^2+a^2\sin^2\beta$ whenever $\varepsilon>0$. The map is therefore conformal at every point of the circle except the trailing edge, and the leading edge is round.

## 2. The lifting cylinder in the circle plane

### The circle theorem

The doublet term that turns a uniform stream into flow round a cylinder is an instance of a general result, the circle theorem (Milne-Thomson). Let $f(\zeta)$ be the complex potential of a flow whose singularities all lie outside the circle $|\zeta|=a$. Then

$$
\Phi(\zeta)=f(\zeta)+\left[f\!\left(\frac{a^2}{\zeta^*}\right)\right]^*
$$

has the same singularities outside the circle and makes $|\zeta|=a$ a streamline.

On the circle, $\zeta\zeta^*=|\zeta|^2=a^2$, so

$$
\frac{a^2}{\zeta^*}=\zeta\qquad\text{on }|\zeta|=a .
$$

The second term then becomes the conjugate of the first:

$$
\Phi=f(\zeta)+\left[f(\zeta)\right]^*=2\,\mathrm{Re}\,f(\zeta)\qquad\text{on }|\zeta|=a .
$$

$\Phi$ is real on the circle, so $\psi=\mathrm{Im}\,\Phi=0$ there: the circle is a streamline. If $f$ is singular at $\zeta_k$ with $|\zeta_k|>a$, the added term is singular where $a^2/\zeta^*=\zeta_k$, that is at $\zeta=a^2/\zeta_k^*$, whose modulus $a^2/|\zeta_k|$ is less than $a$. Every new singularity is inside the body, so the flow outside is unchanged in character. The added term is analytic: if $f(\zeta)=\sum_kc_k\zeta^k$, then $[f(a^2/\zeta^*)]^*=\sum_kc_k^*(a^2/\zeta)^k$, a function of $\zeta$ alone.

### Stream at incidence, doublet and vortex

A uniform stream of speed $\bar U_\infty$ at angle $\alpha$ has $u-iv=\bar U_\infty(\cos\alpha-i\sin\alpha)=\bar U_\infty e^{-i\alpha}$, so its potential is

$$
f(\zeta)=\bar U_\infty e^{-i\alpha}\zeta .
$$

Its only singularity is at infinity. Evaluate it at $a^2/\zeta^*$:

$$
f\!\left(\frac{a^2}{\zeta^*}\right)=\bar U_\infty e^{-i\alpha}\frac{a^2}{\zeta^*} .
$$

Conjugate, which flips the sign of $i$ and turns $\zeta^*$ back into $\zeta$:

$$
\left[f\!\left(\frac{a^2}{\zeta^*}\right)\right]^*=\bar U_\infty e^{i\alpha}\frac{a^2}{\zeta} .
$$

This is a doublet at the centre, aligned with the stream. The image of the singularity at infinity has landed at $\zeta=0$, as the theorem says. Adding a point vortex at the centre gives the lifting cylinder, with the shift to the offset centre written in:

$$
\boxed{\Phi=\bar U_\infty\left(\zeta e^{-i\alpha}+\frac{a^2e^{i\alpha}}{\zeta}\right)+\frac{i\Gamma}{2\pi}\ln\zeta,\qquad\zeta=\bar z-\bar z_0}
$$

The vortex keeps the circle a streamline. On $\zeta=ae^{i\theta}$, $\ln\zeta=\ln a+i\theta$, so

$$
\frac{i\Gamma}{2\pi}\ln\zeta=\frac{i\Gamma}{2\pi}\ln a-\frac{\Gamma\theta}{2\pi} ,
$$

whose imaginary part, $\Gamma\ln a/2\pi$, is the same at every $\theta$. The body streamline is $\psi=\Gamma\ln a/2\pi$ rather than $0$, which changes nothing physical. For any $\Gamma$ this is a valid flow round the cylinder; the cylinder alone gives no reason to prefer one value.

### Velocity on the circle and the stagnation points

$\zeta$ differs from $\bar z$ by a constant, so $\mathrm d\Phi/\mathrm d\bar z=\mathrm d\Phi/\mathrm d\zeta$. Differentiate term by term:

$$
\frac{\mathrm d\Phi}{\mathrm d\bar z}=\bar U_\infty e^{-i\alpha}-\frac{\bar U_\infty a^2e^{i\alpha}}{\zeta^2}+\frac{i\Gamma}{2\pi\zeta} .
$$

On the circle, put $\zeta=ae^{i\theta}$:

$$
\frac{\mathrm d\Phi}{\mathrm d\bar z}=\bar U_\infty e^{-i\alpha}-\bar U_\infty e^{i\alpha}e^{-2i\theta}+\frac{i\Gamma}{2\pi a}e^{-i\theta} .
$$

Take out the factor $e^{-i\theta}$:

$$
\frac{\mathrm d\Phi}{\mathrm d\bar z}=e^{-i\theta}\left[\bar U_\infty e^{i(\theta-\alpha)}-\bar U_\infty e^{-i(\theta-\alpha)}+\frac{i\Gamma}{2\pi a}\right] .
$$

Use $e^{i\chi}-e^{-i\chi}=2i\sin\chi$:

$$
\frac{\mathrm d\Phi}{\mathrm d\bar z}=e^{-i\theta}\left[2i\bar U_\infty\sin(\theta-\alpha)+\frac{i\Gamma}{2\pi a}\right] .
$$

Take out $i$:

$$
\boxed{\frac{\mathrm d\Phi}{\mathrm d\bar z}=ie^{-i\theta}\left[2\bar U_\infty\sin(\theta-\alpha)+\frac{\Gamma}{2\pi a}\right]\qquad\text{on }\zeta=ae^{i\theta}}
$$

The prefactor has modulus 1, so the circle-plane surface speed is the modulus of the bracket. Conjugating gives $u+iv=-ie^{i\theta}[\dots]$; $-ie^{i\theta}$ is the unit tangent pointing clockwise, so a positive bracket means clockwise flow round the circle. On top ($\theta=\pi/2$) with $\alpha=0$ the bracket is $2\bar U_\infty+\Gamma/2\pi a$: the free stream runs over the top in the $+x$ direction and a clockwise $\Gamma$ adds to it, which is the source of the lift.

The stagnation points are where the bracket vanishes:

$$
\sin(\theta_s-\alpha)=-\frac{\Gamma}{4\pi a\bar U_\infty} .
$$

For $|\Gamma|<4\pi a\bar U_\infty$ there are two of them on the circle. Changing $\Gamma$ slides them round the circle, and the Kutta condition picks the $\Gamma$ that puts one of them at $\theta=-\beta$.

## 3. The Joukowski map and its critical points

The Joukowski map and its derivative are

$$
z=\bar z+\frac{b^2}{\bar z},\qquad\frac{\mathrm dz}{\mathrm d\bar z}=1-\frac{b^2}{\bar z^2} .
$$

The derivative vanishes where $\bar z^2=b^2$, at the critical points $\bar z=\pm b$. Far from the origin $b^2/\bar z\to0$, so $z\to\bar z$ and $\mathrm dz/\mathrm d\bar z\to1$: the free stream is the same in both planes, and $\bar U_\infty=U_\infty$. The geometry of the circle and the chord, $b/c=(1+2\varepsilon)/[4(1+\varepsilon)^2]$, are derived in [[SESA3043 2.1 - Complex Functions and Conformal Mapping#Chord length (derivation)|2.1 §4]].

### Why the trailing edge is a cusp

Write a point near the trailing edge as $\bar z=b+s$ with $|s|\ll b$. The second term of the map is

$$
\frac{b^2}{b+s}=\frac{b}{1+s/b} .
$$

Expand the denominator as a geometric series:

$$
\frac{b}{1+s/b}=b\left(1-\frac sb+\frac{s^2}{b^2}-\frac{s^3}{b^3}+\dots\right) .
$$

Multiply in the $b$:

$$
\frac{b^2}{b+s}=b-s+\frac{s^2}{b}-\frac{s^3}{b^2}+\dots
$$

Add $\bar z=b+s$; the linear terms cancel:

$$
z=2b+\frac{s^2}{b}-\frac{s^3}{b^2}+\dots
$$

So, to leading order,

$$
z-2b\approx\frac{s^2}{b} .
$$

Write $s=|s|e^{i\varphi}$. Then $z-2b\approx(|s|^2/b)\,e^{2i\varphi}$: directions leaving the trailing edge have their angles doubled. Near $\bar z=b$ the circle is locally its tangent line, and the fluid outside it fills the half-plane of directions $\varphi$ from $-\beta-\pi/2$ to $-\beta+\pi/2$, centred on the outward radius at $-\beta$. Doubling turns that range of width $\pi$ into one of width $2\pi$, from $-2\beta-\pi$ to $-2\beta+\pi$. The fluid wraps all the way round the point, and the two edges of the range, which are the upper and lower surfaces, leave in the same direction, $\pi-2\beta$. The body there has zero included angle: a cusp. At the leading edge the circle stays clear of $\bar z=-b$, the map is conformal, and the round nose of the circle stays round.

## 4. The Kármán–Trefftz map

$$
z=2b\,\frac{(\bar z+b)^p+(\bar z-b)^p}{(\bar z+b)^p-(\bar z-b)^p},\qquad p=2-\frac\tau\pi .
$$

### The ratio form and the Joukowski limit

Divide the numerator and the denominator by $(\bar z+b)^p$ and write

$$
r=\left(\frac{\bar z-b}{\bar z+b}\right)^p .
$$

The map becomes

$$
z=2b\,\frac{1+r}{1-r} .
$$

This form shows where $z(\bar z)$ is single-valued. A non-integer power has a branch cut where its argument is negative and real. $(\bar z-b)/(\bar z+b)$ is negative and real only on the segment of the real axis between $-b$ and $b$, which lies inside the circle, so the ratio form is single-valued everywhere in the flow. The course's form agrees with it there: $(\bar z\pm b)^p$ each jump across the real axis to the left of $-b$, but by the same factor, which cancels between numerator and denominator (on the coursework aerofoil the two forms agree to $4\times10^{-16}$).

For $p=2$, expand both squares in the course's form:

$$
(\bar z+b)^2+(\bar z-b)^2=2\bar z^2+2b^2,\qquad(\bar z+b)^2-(\bar z-b)^2=4b\bar z .
$$

Substitute:

$$
z=2b\,\frac{2\bar z^2+2b^2}{4b\bar z}=\frac{\bar z^2+b^2}{\bar z}=\bar z+\frac{b^2}{\bar z} ,
$$

the Joukowski map.

### The derivative of the map

Write $A=(\bar z+b)^p$ and $B=(\bar z-b)^p$, so that $z=2b(A+B)/(A-B)$. Their derivatives are

$$
A'=\frac{pA}{\bar z+b},\qquad B'=\frac{pB}{\bar z-b} .
$$

The quotient rule gives

$$
\frac{\mathrm dz}{\mathrm d\bar z}=2b\,\frac{(A'+B')(A-B)-(A+B)(A'-B')}{(A-B)^2} .
$$

Multiply out the numerator:

$$
(A'+B')(A-B)-(A+B)(A'-B')=AA'-A'B+AB'-BB'-AA'+AB'-A'B+BB' .
$$

The $AA'$ and $BB'$ terms cancel:

$$
(A'+B')(A-B)-(A+B)(A'-B')=2(AB'-A'B) .
$$

Substitute $A'$ and $B'$:

$$
2(AB'-A'B)=2pAB\left(\frac{1}{\bar z-b}-\frac{1}{\bar z+b}\right) .
$$

Combine the fractions:

$$
\frac{1}{\bar z-b}-\frac{1}{\bar z+b}=\frac{2b}{\bar z^2-b^2} .
$$

So

$$
2(AB'-A'B)=\frac{4pbAB}{\bar z^2-b^2} .
$$

Put this back into the quotient:

$$
\boxed{\frac{\mathrm dz}{\mathrm d\bar z}=\frac{8b^2p\,AB}{(\bar z^2-b^2)(A-B)^2}}
$$

This is line 1 of the `dzdzbar` block of the Code Explainer and of `ktreff`, `dzdzbar=(8.0*b**2*p*(zp*zm))/((zbar**2-b**2)*(zp-zm)**2)`, with `zp` $=A$ and `zm` $=B$. It is zero at $\bar z=b$ (where $B=0$) for any $p>1$, so the trailing edge is a critical point for every KT aerofoil, not just the Joukowski one.

### The trailing-edge angle

Put $\bar z=b+s$ again. Then $B=s^p$ is small, and $A=(2b+s)^p\approx(2b)^p$. Write the map as

$$
z=2b\,\frac{1+B/A}{1-B/A} .
$$

For small $x=B/A$, $(1+x)/(1-x)=(1+x)(1+x+x^2+\dots)\approx1+2x$:

$$
z\approx2b\left(1+\frac{2B}{A}\right) .
$$

Subtract $2b$ and substitute $A$ and $B$:

$$
\boxed{z-2b\approx\frac{4b}{(2b)^p}\,s^p}
$$

The constant $4b/(2b)^p$ is real and positive, so it scales distances without rotating them, and every direction $\varphi$ leaving $\bar z=b$ is carried to the direction $p\varphi$. The fluid's half-plane of width $\pi$ becomes a sector of width $p\pi$. What is left for the body is

$$
2\pi-p\pi=(2-p)\pi .
$$

Substitute $p=2-\tau/\pi$:

$$
(2-p)\pi=\frac\tau\pi\,\pi=\tau .
$$

The trailing edge is a wedge of included angle $\tau$, which is how $p$ is chosen. The bisector of the fluid sector, the outward radius at $-\beta$, maps to $-p\beta$, so the wake leaves the trailing edge along the direction $-p\beta$ to the $x$-axis. For Joukowski ($p=2$) this reproduces the cusp of §3 and its direction $-2\beta$.

> [!check] The angle measured on the coursework aerofoil
> With $\varepsilon=0.07$, $\beta=0.06$, $\tau=0.2$: the chords from the trailing edge to the surface points at $\theta=-\beta\pm10^{-4}$ enclose $11.4599^\circ$, against $\tau=11.4592^\circ$, and their bisector points at $-6.657^\circ$, against $-p\beta=-6.656^\circ$. The ratio $(z-2b)/s^p$ tends to $3.8457$ as $|s|\to0$, which is $4b/(2b)^p$.

### The far field and the circle-plane stream

Far from the body put $t=b/\bar z$, which is small. Then

$$
\frac{\bar z-b}{\bar z+b}=\frac{1-t}{1+t} .
$$

Its logarithm is an odd function of $t$, so it has no $t^2$ term:

$$
\ln\frac{1-t}{1+t}=-2t-\tfrac23t^3-\dots
$$

Multiply by $p$ and exponentiate:

$$
r=e^{-2pt+O(t^3)}=1-2pt+2p^2t^2+O(t^3) .
$$

The two brackets of the ratio form follow:

$$
1+r=2-2pt+O(t^2),\qquad1-r=2pt\left(1-pt+O(t^2)\right) .
$$

Divide:

$$
\frac{1+r}{1-r}=\frac{2(1-pt)+O(t^2)}{2pt(1-pt)+O(t^3)}=\frac{1}{pt}+O(t) .
$$

Multiply by $2b$ and put back $t=b/\bar z$:

$$
\boxed{z=\frac2p\,\bar z+O\!\left(\frac1{\bar z}\right)}
$$

There is no constant term, so the far field is neither shifted nor rotated, only scaled by $2/p$. Differentiating, $\mathrm dz/\mathrm d\bar z\to2/p$, and far away

$$
u-iv=\frac{\mathrm d\Phi/\mathrm d\bar z}{\mathrm dz/\mathrm d\bar z}\to\bar U_\infty e^{-i\alpha}\cdot\frac p2 .
$$

The incidence is the same in both planes, and the speeds are related by

$$
\boxed{U_\infty=\frac p2\,\bar U_\infty,\qquad\bar U_\infty=\frac2p\,U_\infty}
$$

This is `Uinf=p/2.0` in `ktreff`, which works with $\bar U_\infty=1$. For the coursework aerofoil $2/p=1.032878$, and the computed $z/\bar z$ at $|\bar z|=10^4$ is $1.0328775$. Using $U_\infty$ in place of $\bar U_\infty$ would make $\Gamma$ and $C_L$ low by the factor $p/2$, 3.2 % here, and $1-C_p$ low by $(p/2)^2$, 6.2 %.

## 5. The Kutta condition and the circulation

The velocity on the aerofoil is the circle-plane velocity divided by the stretch:

$$
u-iv=\frac{\mathrm d\Phi/\mathrm d\bar z}{\mathrm dz/\mathrm d\bar z} .
$$

At the trailing edge the denominator is zero (§§3–4). If the numerator is not, the speed there is infinite: the flow whips round the sharp edge from the lower surface to the upper one, which a real fluid cannot do, because the boundary layer separates and sheds vorticity until the flow leaves the edge smoothly. The inviscid model reproduces that end state by requiring the numerator to vanish too. This is the **Kutta condition** ([[Kutta Condition]]): the trailing edge, $\theta=-\beta$, is a stagnation point of the circle-plane flow.

Set the bracket of §2 to zero at $\theta=-\beta$:

$$
2\bar U_\infty\sin(-\beta-\alpha)+\frac{\Gamma}{2\pi a}=0 .
$$

Use $\sin(-\chi)=-\sin\chi$:

$$
-2\bar U_\infty\sin(\alpha+\beta)+\frac{\Gamma}{2\pi a}=0 .
$$

Solve for $\Gamma$:

$$
\boxed{\Gamma=4\pi a\bar U_\infty\sin(\alpha+\beta)}
$$

In the aerofoil plane's free stream, with $\bar U_\infty=(2/p)U_\infty$,

$$
\Gamma=\frac{8\pi a}{p}\,U_\infty\sin(\alpha+\beta) .
$$

For Joukowski, $p=2$ and this is the Joukowski circulation $\Gamma=4\pi aU_\infty\sin(\alpha+\beta)$. The geometry enters only through $a$ and $\beta$, and $\beta$ appears added to $\alpha$: the zero-lift incidence is $\alpha=-\beta$, where the free stream in the circle plane points straight at the trailing edge along the radius at $-\beta$.

With this $\Gamma$, the bracket becomes $2\bar U_\infty[\sin(\theta-\alpha)+\sin(\alpha+\beta)]$. The sum-to-product identity $\sin X+\sin Y=2\sin\frac{X+Y}2\cos\frac{X-Y}2$ with $X=\theta-\alpha$ and $Y=\alpha+\beta$ gives

$$
\sin(\theta-\alpha)+\sin(\alpha+\beta)=2\sin\frac{\theta+\beta}{2}\,\cos\frac{\theta-2\alpha-\beta}{2} .
$$

The first factor vanishes at $\theta=-\beta$, the trailing edge. The second vanishes where $(\theta-2\alpha-\beta)/2=\pi/2$:

$$
\theta_f=\pi+2\alpha+\beta ,
$$

the front stagnation point, just below the nose for positive $\alpha+\beta$.

### Speed at the trailing edge

The Kutta condition makes the trailing-edge speed finite, but its value depends on $\tau$. Let $\delta=\theta+\beta$ be the small angle from the trailing edge. Near $\delta=0$ the first factor is $\sin(\delta/2)\approx\delta/2$ and the second is $\cos(\alpha+\beta)$, so the circle-plane speed is

$$
|\mathrm d\Phi/\mathrm d\bar z|\approx2\bar U_\infty\cdot2\cdot\frac\delta2\cos(\alpha+\beta)=2\bar U_\infty\,\delta\cos(\alpha+\beta) .
$$

The distance from the critical point is

$$
s=ae^{i\theta}-ae^{-i\beta}=ae^{-i\beta}\left(e^{i\delta}-1\right)\approx iae^{-i\beta}\delta ,
$$

so $|s|=a\delta$.

For Joukowski, $\mathrm dz/\mathrm d\bar z=(\bar z-b)(\bar z+b)/\bar z^2\approx s\cdot2b/b^2=2s/b$, so $|\mathrm dz/\mathrm d\bar z|\approx2a\delta/b$. Divide, and the $\delta$ cancels:

$$
q_{TE}=\frac{2\bar U_\infty\delta\cos(\alpha+\beta)}{2a\delta/b}=\bar U_\infty\frac ba\cos(\alpha+\beta) .
$$

With $\bar U_\infty=U_\infty$ and $b/a=\cos\beta/(1+\varepsilon)$:

$$
\frac{q_{TE}}{U_\infty}=\frac{\cos\beta\cos(\alpha+\beta)}{1+\varepsilon} .
$$

The cusped trailing edge has a finite, non-zero speed. For $\varepsilon=0.1$, $\beta=6^\circ$, $\alpha=5^\circ$ this is $0.8875$, so $C_{p,TE}=0.212$ (the computed surface speed at $\delta=10^{-5}$ is $0.88750$).

For KT, differentiating $z-2b\approx4b\,s^p/(2b)^p$ gives $|\mathrm dz/\mathrm d\bar z|\approx4bp\,(a\delta)^{p-1}/(2b)^p$. Divide:

$$
q\approx\frac{2\bar U_\infty\,\delta\cos(\alpha+\beta)\,(2b)^p}{4bp\,(a\delta)^{p-1}}=\frac{\bar U_\infty(2b)^p\cos(\alpha+\beta)}{2bp\,a^{p-1}}\,\delta^{2-p} .
$$

Since $2-p=\tau/\pi>0$, $q\to0$: a trailing edge with a finite angle is a stagnation point, $C_p=1$, on both surfaces. The approach is slow, $1-C_p\propto\delta^{2\tau/\pi}$, so the rise to $C_p=1$ is confined to a tiny region. This is why `dpan` sets the two trailing-edge nodes to $C_p=1$ ([[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)|2.3 §10]]), and why the raw map gives $0/0$ at the end point.

> [!check] The trailing-edge limit on the coursework aerofoil
> The coefficient is $0.9505$ (with $U_\infty=1$). At $\delta=10^{-2}$, $10^{-4}$ and $10^{-6}$ the exact surface speed is $0.7100$, $0.5288$ and $0.3944$, against $0.7090$, $0.5288$ and $0.3944$ from the power law, so $C_p=0.496$, $0.720$ and $0.844$. Even a millionth of a radian from the edge, $C_p$ is only $0.84$.

## 6. Velocity and pressure on the aerofoil

The speed on the aerofoil surface is the circle-plane speed divided by the stretch:

$$
q=\frac{|\mathrm d\Phi/\mathrm d\bar z|}{|\mathrm dz/\mathrm d\bar z|}=\frac{2\bar U_\infty\left|\sin(\theta-\alpha)+\sin(\alpha+\beta)\right|}{|\mathrm dz/\mathrm d\bar z|} .
$$

Bernoulli from the free stream, with the flow steady and irrotational so that one constant holds everywhere, gives

$$
C_p=1-\frac{q^2}{U_\infty^2} .
$$

Substitute $q$:

$$
C_p=1-\frac{4\bar U_\infty^2\left[\sin(\theta-\alpha)+\sin(\alpha+\beta)\right]^2}{U_\infty^2\,|\mathrm dz/\mathrm d\bar z|^2} .
$$

Use $\bar U_\infty/U_\infty=2/p$:

$$
\boxed{C_p=1-\frac{16\left[\sin(\theta-\alpha)+\sin(\alpha+\beta)\right]^2}{p^2\,|\mathrm dz/\mathrm d\bar z|^2}}
$$

with $\mathrm dz/\mathrm d\bar z$ from §4 evaluated at $\bar z=\bar z_0+ae^{i\theta}$. For Joukowski, $p=2$ and the numerator is $4[\dots]^2$. Only the modulus of $u-iv$ is needed, so $u$ and $v$ never have to be separated (L-b). `ktreff` computes the same quantity as `1-dphidz*conj(dphidz)/Uinf**2` with $\bar U_\infty=1$; on the coursework aerofoil the two agree to $3\times10^{-13}$ in $q$.

![[aa_deepdive_kt_mapping.png|900]]

Panel (a) is the circle plane, with the dividing streamline (orange) arriving at the front stagnation point and leaving from $\bar z=b$. Panel (b) is the same set of $\psi$ values after the KT map: every streamline keeps its value of $\psi$, and the dividing streamline leaves the trailing edge smoothly. Panel (c) magnifies the trailing edge, where the surfaces meet at $\tau=11.46^\circ$ and the dividing streamline leaves along the bisector at $-p\beta$. Panel (d) is the exact $C_p$: the suction peak just behind the nose, the front stagnation point at $\theta_f=\pi+2\alpha+\beta$, and the two surfaces closing towards $C_p=1$ at the trailing edge.

## 7. Lift

The circulation is the same in both planes. It is $\oint\mathrm d\Phi$ round a closed curve enclosing the body, and the integral of $\mathrm d\Phi$ does not depend on which plane the curve is drawn in, because the map takes a closed curve round the circle to a closed curve round the aerofoil ([[SESA3043 2.1 - Complex Functions and Conformal Mapping#What happens to streamlines and velocities|2.1 §2]]). The [[Kutta-Joukowski Theorem|Kutta–Joukowski theorem]] in the physical plane, where the free stream is $U_\infty$, then gives

$$
L'=\rho U_\infty\Gamma .
$$

Divide by $\tfrac12\rho U_\infty^2c$:

$$
C_L=\frac{\rho U_\infty\Gamma}{\tfrac12\rho U_\infty^2c}=\frac{2\Gamma}{U_\infty c} .
$$

Substitute $\Gamma=(8\pi a/p)U_\infty\sin(\alpha+\beta)$:

$$
\boxed{C_L=\frac{16\pi a}{pc}\sin(\alpha+\beta)}
$$

For Joukowski ($p=2$) this is the $C_L=8\pi(a/c)\sin(\alpha+\beta)$ of [[SESA3043 2.1 - Complex Functions and Conformal Mapping#The flow and the Kutta condition|2.1]]. With $c=1$ it is `ktreff`'s `Cl=8.0*pi*a*sin(alpha+beta)/Uinf` with `Uinf=p/2`. The lift-curve slope at small $\alpha+\beta$ is $16\pi a/(pc)$ per radian and the zero-lift angle is $-\beta$. Thickness raises the slope above $2\pi$ through $a/c$; the trailing-edge angle enters through both $p$ and $b/c$.

> [!check] Lift by pressure integration
> Integrating $-C_p\,\hat n$ round the exact coursework surface (200 000 segments) gives $C_L=0.7760237$ and a drag coefficient of $1\times10^{-10}$. The circulation route gives $0.7760237$, and the zero drag is d'Alembert's paradox, as it must be for steady inviscid flow round a closed body.

## 8. The coursework aerofoil, worked through

The coursework's Table 1 gives this aerofoil as $\varepsilon=0.07$, $\beta=0.06$, $\tau=0.2$ (radians), and Q2(a) runs the panel method at $\alpha=3^\circ$ against the conformal-mapping $C_L$ ([[SESA3043 Advanced Aeronautics Hub#Assessment and deadlines|hub]]). `ktreff` takes $c=1$ through its $b/c$ formula and $\bar U_\infty=1$. Every value below was computed in Python with the formulae above and checked against the Blackboard `ktreff.py`.

| Quantity | Working | Value |
|---|---|---|
| $p$ | $2-0.2/\pi$ | $1.936338$ |
| $b$ | $\tfrac14\left[(1.07)^p-0.07^p\right]/(1.07)^p$ | $0.248727$ |
| $a$ | $b(1+\varepsilon)/\cos\beta$ | $0.266618$ |
| $\bar z_0$ | $-\varepsilon b+ia\sin\beta$ | $-0.017411+0.015987i$ |
| $\bar U_\infty$ | $(2/p)U_\infty$, $U_\infty=1$ | $1.032878$ |
| $\alpha+\beta$ | $3^\circ+3.4377^\circ$ | $6.4377^\circ$, $\sin=0.112124$ |
| $\Gamma$ | $4\pi a\bar U_\infty\sin(\alpha+\beta)$ | $0.388012$ ($U_\infty c$ units) |
| $C_L$ | $2\Gamma/(U_\infty c)$ | $\mathbf{0.776024}$ |
| lift-curve slope | $16\pi a/(pc)$ | $6.9211$ per rad $=0.12080$ per degree ($1.102\times2\pi$) |
| zero-lift angle | $-\beta$ | $-3.438^\circ$ |
| front stagnation point | $\theta_f=\pi+2\alpha+\beta$ | $189.44^\circ$; $x/c=0.0031$, $y/c=-0.0071$ |
| suction peak | minimum of the boxed $C_p$ | $C_{p,\min}=-0.985$ at $x/c=0.031$ on the upper surface |

At other incidences the same formula gives $C_L=0.4150$ at $0^\circ$, $1.0156$ at $5^\circ$ and $1.6084$ at $10^\circ$, the inviscid line against which the XFOIL results of Q3 can be read. For a feel of the dimensional numbers, the same aerofoil with $c=0.25$ m in a 20 m/s stream at sea level carries $\Gamma=1.940$ m²/s and $L'=\rho U_\infty\Gamma=47.5$ N/m.

The same $\varepsilon$ and $\beta$ with a cusped trailing edge ($\tau=0$, Joukowski) give $C_L=0.7519$ at $3^\circ$ and a slope of $6.706$ per radian, so the $11.5^\circ$ trailing edge adds about 3 % to the lift. Thin-aerofoil theory with this aerofoil's maximum camber of $2.899$ % chord (coursework reference run), $C_L=2\pi(\alpha+2h/c)=0.693$, misses about 11 %. Its zero-lift angle, $-2h/c=-3.32^\circ$, is close to $-\beta=-3.44^\circ$, so almost all of the gap is in the slope, $2\pi$ against $6.921$ per radian: the effect of thickness and the trailing-edge angle.

### Checks against the code

Three details of `ktreff` matter when its $C_L$ is used as the reference. The chord is not exactly 1: the point farthest from the trailing edge, the leading edge in XFOIL's convention, is at $\theta=182.93^\circ$, at a distance $1.000019$, so $C_L$ based on the true chord is $0.776009$, a change in the fifth figure. That chord line lies at $-0.036^\circ$ to the $x$-axis, while `ktreff` measures $\alpha$ from the $x$-axis, so the incidence to the chord is $3.036^\circ$. And $C_L$ comes from the circulation, not from a pressure integral, so it does not depend on the number of points `n`.

The doublet panel method (`dpan`, with the vault's fixed copies) converges to this value from above at first:

| panels $n$ | 40 | 80 | 160 | 320 | 640 |
|---|---:|---:|---:|---:|---:|
| panel $C_L$ | 0.82808 | 0.78366 | 0.77645 | 0.77592 | 0.77598 |
| error | +6.71 % | +0.98 % | +0.055 % | −0.013 % | −0.006 % |

The error changes sign between 160 and 320 panels, so an order of accuracy computed from successive differences across that pair is meaningless; an order fit for Q2(a) has to use grids on one side of the crossing.

## 9. Common mistakes

Most errors in this material are about which plane a quantity lives in:

- using $U_\infty$ for the circle-plane stream with the KT map; the circle plane needs $\bar U_\infty=(2/p)U_\infty$, and only for Joukowski are they equal;
- forgetting the offset centre: every $\bar z$ in the cylinder potential must be $\bar z-\bar z_0$, which is why the trailing edge sits at $\theta=-\beta$ rather than $\theta=0$;
- evaluating $u-iv$ at the trailing edge without the Kutta circulation, or with it but expecting a finite non-zero speed on a KT aerofoil; with $\tau>0$ the trailing edge is a stagnation point;
- taking the KT trailing-edge angle as $p\pi$ or $\pi-\tau$; the fluid sector is $p\pi$ and the body angle is $2\pi-p\pi=\tau$;
- using the Joukowski chord $b/c=(1+2\varepsilon)/[4(1+\varepsilon)^2]$ for a KT aerofoil; with $p\neq2$ it is $[(1+\varepsilon)^p-\varepsilon^p]/[4(1+\varepsilon)^p]$;
- mixing the clockwise-positive $\Gamma$ of Chapter 2 with the counter-clockwise vortex potential of 1.3, which flips the sign of the lift;
- degrees in the code: `ktreff` and `dpan` take radians.

## Links

- Parent: [[SESA3043 Advanced Aeronautics Hub]]
- Lecture note: [[SESA3043 2.1 - Complex Functions and Conformal Mapping]] (the shapes, the chord, the demo sweep) · [[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)|2.3 §10]] (the coursework code and its traps) · [[SESA3043 2.3 - Panel Methods#7. Validation against exact solutions|2.3 §7]] (KT as the panel-method test case)
- Concepts: [[Joukowski Transformation]] · [[Kármán–Trefftz Transformation]] · [[Conformal Mapping]] · [[Complex Velocity Potential]] · [[Panel Method]]
- Earlier: [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#Lifting cylinder: uniform flow plus doublet plus point vortex|1.3, the lifting cylinder]] · [[Kutta Condition]] · [[Kutta-Joukowski Theorem]] · [[Flow Past a Cylinder]] · [[SESA2022 T4 - Thin Aerofoil Theory]]
- Formulae: [[SESA3043 Formula Sheet]]

## Sources

- `Ch2 Exact Solution and methods for potential flow.pdf`, slides 13–20 (Dr Zhiwei Hu): the plate and ellipse, the Joukowski geometry, the lifting-cylinder potential with $\bar U_\infty$ and $\Gamma$ (slide 17), the KT map (slide 19) and the coursework pointer (slide 20). Lectured Thu 8 and Fri 9 Oct.
- `09 October 2026 at 14_57_18.txt` (L-b), ll. 69–458: the build-up from plate to aerofoil, the transformation of the solution and the KT map; ll. 480–495, what is examinable. `08 October 2026 at 13_50_19.txt` (L-a) for conformal mapping and $\mathrm d\Phi/\mathrm dz=u-iv$; `09 October 2026 at 14_17_51.txt`, the demo recording.
- `Ch2_Notes_CW Code Explainer.pdf` (pp. 1–2) and `ktreff.py` (N.D. Sandham 2006, Python port): the code each derivation is matched against.
- The circle theorem: L. M. Milne-Thomson, *Theoretical Hydrodynamics*; Katz and Plotkin, *Low-Speed Aerodynamics*, Ch. 6, for the KT map.
- Checks: every number in §§4–8 was computed in Python from the formulae in this note and compared with `ktreff.py` (identical $C_L$; surface speed to $3\times10^{-13}$); the panel table uses copies of the fixed `dpan_fixed.py` and `ktreff_fixed.py`, and its $n=40$ and $80$ values match the coursework reference run. Figure: `generate_aa_deepdive_figures.py` (`fig_kt_mapping`).

## Self-study tasks

Two things were set on this material: understanding the logic of the cylinder-to-aerofoil steps, which is what the exam asks (L-b, ll. 490–495), and running the Blackboard code for the coursework (L-b, ll. 446–458; slide 20). Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(L-b, ll. 490–495)** Without numbers, explain each step from a cylinder to a KT aerofoil: why the circle passes through $\bar z=b$ and encloses $\bar z=-b$, what the shifts $\varepsilon b$ and $a\sin\beta$ do, and why a circulation has to be chosen. → [[#3. The Joukowski map and its critical points|§3]] · [[#5. The Kutta condition and the circulation|§5]]
- [ ] **(L-b, ll. 327–348)** Find $u-iv$ on the aerofoil by the chain rule and $C_p$ from the modulus alone, and reach the boxed $C_p$ of §6. → [[#6. Velocity and pressure on the aerofoil|§6]]
- [ ] **(L-b, ll. 446–458; slide 20)** Run `ktreff` for your own coursework parameters at $\alpha=3^\circ$ and reproduce $C_L=0.776024$ from $16\pi a\sin(\alpha+\beta)/p$ by hand. → [[#8. The coursework aerofoil, worked through|§8]]

### Further practice

- [ ] (suggested, not lecturer-set) Derive $\Gamma=4\pi a\bar U_\infty\sin(\alpha+\beta)$ from the factorised surface velocity, and find the front stagnation point $\theta_f=\pi+2\alpha+\beta$. → [[#5. The Kutta condition and the circulation|§5]]
- [ ] (suggested, not lecturer-set) Show that the KT trailing edge has included angle $\tau$ and that the far field is scaled by $2/p$, so that $U_\infty=(p/2)\bar U_\infty$. → [[#The trailing-edge angle|§4, angle]] · [[#The far field and the circle-plane stream|§4, far field]]
- [ ] (suggested, not lecturer-set) Show that the Joukowski trailing-edge speed is $U_\infty\cos\beta\cos(\alpha+\beta)/(1+\varepsilon)$ while the KT one is zero, and evaluate both. → [[#Speed at the trailing edge|§5, trailing-edge speed]]

## Transcript and slide slips

> [!note] Slide 17 and the `ktreff` comment
> Where: [[#5. The Kutta condition and the circulation]] and [[#Checks against the code]].
>
> Slide 17 writes the potential with the circle-plane stream $\bar U_\infty$ but the circulation as $\Gamma=4\pi aU_\infty\sin(\alpha+\beta)$. The Kutta condition gives $\Gamma=4\pi a\bar U_\infty\sin(\alpha+\beta)$; the two agree for Joukowski, where $\bar U_\infty=U_\infty$, but for a KT aerofoil $\bar U_\infty=(2/p)U_\infty$, which is the `Uinf=p/2` of the code. The slide's shift of the centre, dropped from the same potential, is flagged in [[SESA3043 2.1 - Complex Functions and Conformal Mapping#Transcript and slide slips|2.1]].
>
> `ktreff`'s comment *"shifted so that 0<x<1"* holds only approximately: with camber the point farthest from the trailing edge lands at $x=-1.9\times10^{-5}$ for the coursework aerofoil, and the chord is $1.000019$. The other `ktreff` and Code Explainer slips are in [[SESA3043 2.3 - Panel Methods#Coursework Code Explainer slips|2.3]].

### Transcript slips (L-b)

> [!warning] Slips in `09 October 2026 at 14_57_18.txt` not already listed in 2.1
> | Where | Said | Correct |
> |---|---|---|
> | L-b, l. 242 | the centre goes up *"by amount of angle theta"* | by the angle $\beta$ (said correctly at l. 261) |
> | L-b, l. 282 | *"you will get a formula for Z-bar"* | a formula for $z$, the aerofoil surface |
> | L-b, ll. 305–306 | *"e-thin plus e-thin plus beta, e-thin plus B, plus B"* | $a\cos\beta=b+\varepsilon b$ |
> | L-b, l. 321 | *"the code of your error for it is about four times the transform constant"* | the chord of the aerofoil is about $4b$ |
> | L-b, l. 401 | the KT map *"done by common trappers independently"* | Kármán and Trefftz published it jointly (1918) |
> | L-b, l. 409 | *"B is still the transform function"* | $b$ is still the transfer constant |
> | L-b, ll. 413, 417 | $\tau$ *"in radius"* | in radians |
