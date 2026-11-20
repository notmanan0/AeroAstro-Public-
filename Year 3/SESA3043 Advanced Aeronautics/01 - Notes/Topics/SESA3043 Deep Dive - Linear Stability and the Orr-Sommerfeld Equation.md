---
title: "SESA3043 Deep Dive - Linear Stability and the Orr-Sommerfeld Equation"
module: "SESA3043 Advanced Aeronautics"
type: topic
stream: "Chapter 3: Methods for Boundary Layers"
order: 12.5
tags: [sesa3043, boundary-layer, transition, stability, orr-sommerfeld, tollmien-schlichting, en-method, derivation, deep-dive]
aliases: ["Orr-Sommerfeld derivation", "Orr-Sommerfeld deep dive", "Linear stability deep dive", "Blasius neutral curve"]
date: 2026-11-12
status: lectured
coverage: "Every step from the decomposition of CH3-4 slides 22–23 to the Orr–Sommerfeld equation of slide 24 (the derivation the course leaves to White Ch. 5.2), the parallel-flow approximation by order of magnitude, temporal and spatial growth (slides 25–29), and a numerical solution for the Blasius layer that reproduces the neutral curve, Re_crit ≈ 519 and the eⁿ envelope of slides 30–43"
parent: ["[[SESA3043 Advanced Aeronautics Hub]]"]
prerequisites: ["[[SESA3043 3.4 - Transition to Turbulence]]", "[[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]", "[[SESA3043 1.2 - Conservation Laws and Governing Equations]]"]
next_topics: ["[[SESA3043 3.5 - Momentum Integral Equation]]", "[[SESA3043 3.6 - Viscous-Inviscid Interaction]]"]
key_concepts: ["[[Linear Stability and Transition Prediction]]", "[[Incompressible Navier-Stokes Equations]]", "[[Blasius and Falkner-Skan Similarity Solutions]]"]
tutorial_sheets: ["03 - Exams & Past Papers/Ch3_Revision_Questions.pdf"]
sources: ["02 - Sources/Lectures/CH3-4 Transition to Turbulence(1).pdf", "02 - Sources/Lectures/06 November 2026 at 14_52_55.txt", "02 - Sources/Lectures/06 November 2026 at 15_54_41.txt"]
---

# SESA3043 Deep Dive - Linear Stability and the Orr-Sommerfeld Equation

> [!abstract] Summary
> Splitting the 2-D incompressible Navier–Stokes equations into a steady laminar base flow plus a small wave $\hat v(y)e^{i(\alpha x-\omega t)}$, dropping products of the disturbance and treating the base flow as parallel leaves three linear ODEs in $y$. Eliminating $\hat u$ with continuity and $\hat p$ by cross-differentiating the two momentum equations gives the fourth-order Orr–Sommerfeld equation, an eigenvalue problem for $\alpha$ once $\bar u(y)$, $Re$ and $\omega$ are fixed. Solved numerically for the Blasius profile, it gives the thumb-shaped neutral curve with its tip at $Re_{\delta^*,crit}=519$ ($Re_x=9.1\times10^4$), and integrating the spatial growth rates gives the $e^n$ envelope, which reaches $n=9$ at $Re_x=3.2\times10^6$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks where the Orr–Sommerfeld equation comes from, what each assumption does, how to read the thumb plot, or why $Re_{crit}$ is not the transition point.
> - **Assumptions:** 2-D, incompressible, Newtonian; steady laminar base flow, locally parallel ($\bar u=\bar u(y)$, $\bar v$ and $\partial\bar u/\partial x$ neglected); small disturbances (products of primes dropped); normal modes $e^{i(\alpha x-\omega t)}$.
> - **Method:** 1. $u=\bar u+u'$ etc. into continuity and both momentum equations. 2. Subtract the base flow and drop products of primes. 3. Drop $\bar v$ and $\partial\bar u/\partial x$ (parallel flow, error $O(1/Re_{\delta^*})$). 4. Normal modes: $\partial_x\to i\alpha$, $\partial_t\to-i\omega$. 5. $\hat u=(i/\alpha)\hat v'$, solve $x$-momentum for $\hat p$, differentiate, substitute into $y$-momentum.
> - **Common mistakes:** the sign of growth (with $e^{i(\alpha x-\omega t)}$ the amplitude is $e^{-\alpha_ix}$, so $\alpha_i<0$ grows); calling the tip of the thumb the transition Reynolds number.
> - **Practise:** [[#5. Eliminating the pressure - the Orr–Sommerfeld equation|§5, the derivation]] · [[#10. From growth rates to transition - the eⁿ envelope|§10, transition on a flat plate]]

A laminar boundary layer is a steady solution of the Navier–Stokes equations, but a solution can be steady without being stable. Small disturbances are always present: sound, free-stream turbulence, vibration and roughness are converted into waves inside the layer by receptivity ([[SESA3043 3.4 - Transition to Turbulence#2. The roadmap to transition|3.4 §2]]). Linear stability theory asks whether such a wave, once inside, grows or decays. While its amplitude is small, the wave hardly changes the base flow, its own self-interaction is negligible, and the equations it obeys are linear with coefficients that depend on the base profile $\bar u(y)$.

Linear equations with coefficients independent of $x$ and $t$ have solutions that are exponentials in $x$ and $t$, so the disturbance can be taken as a single travelling wave of wavenumber $\alpha$ and frequency $\omega$ with an unknown shape across the layer. Substituting it turns three PDEs into one ODE in $y$, the Orr–Sommerfeld equation. Its non-zero solutions exist only for particular combinations of $\alpha$, $\omega$ and $Re$; the combinations with zero growth trace out the neutral curve, and the curve has a lowest Reynolds number below which every wave decays.

The wave grows by drawing energy from the base-flow shear. The coupling term is $v'\,\mathrm d\bar u/\mathrm dy$ in the $x$-momentum equation: a wall-normal velocity fluctuation carries fluid from one layer of the shear flow to another with a different streamwise speed. Whether the energy gained outweighs viscous dissipation depends on the phase relation between $u'$ and $v'$, which viscosity itself sets near the wall. That is why the Blasius layer is stable at low $Re$, unstable in a band of frequencies above $Re_{crit}$, and why the band narrows again at high $Re$.

## 1. Assumptions and notation

The analysis uses the unsteady 2-D incompressible Navier–Stokes equations for a general flow, not the boundary-layer equations. Each assumption enters at a definite step:

- **incompressible and Newtonian**, with $\rho$ and $\nu$ constant, so the equations are [[Incompressible Navier-Stokes Equations|incompressible Navier–Stokes]] with $\nu\nabla^2$ viscous terms (§2);
- **two-dimensional**: no $z$-dependence and no $w$, so the disturbance is a spanwise-uniform wave, a TS wave (§2);
- **steady laminar base flow** that satisfies the equations on its own, so its terms cancel after substitution (§2);
- **small disturbances**: products of primed quantities are dropped, which linearises the equations (§2);
- **locally parallel base flow**: $\bar v$ and $\partial\bar u/\partial x$ are neglected in the disturbance equations, so the coefficients depend on $y$ only (§3);
- **normal modes**: the disturbance is a single wave $e^{i(\alpha x-\omega t)}$ (§4).

| Symbol | Meaning |
|---|---|
| $\bar u(y)$, $\bar v$, $\bar p$ | laminar base flow (Blasius in the numerical sections) |
| $u'$, $v'$, $p'$ | disturbance (perturbation) |
| $\hat u(y)$, $\hat v(y)$, $\hat p(y)$ | shape functions; $\hat v$ is the eigenvector of the Orr–Sommerfeld problem |
| $\alpha=\alpha_r+i\alpha_i$ | wavenumber, $\alpha_r=2\pi/\lambda$ |
| $\omega$ | angular frequency, $2\pi/T$ |
| $c_{ph}=\omega/\alpha$ | phase speed |
| $\mathrm D$, primes on $\bar u$ | $\mathrm d/\mathrm dy$; $\bar u'=\mathrm d\bar u/\mathrm dy$, $\bar u''=\mathrm d^2\bar u/\mathrm dy^2$ |
| $Re_{\delta^*}$, $F$ | $U_e\delta^*/\nu$ and $\omega\nu/U_e^2$, the axes of the thumb plot |

A prime on a flow variable ($u'$) marks the disturbance, while a prime on $\bar u$ is a $y$-derivative of the base profile. The two never appear on the same symbol.

## 2. Decomposition and linearisation

Every variable is the base flow plus a perturbation:

$$
u=\bar u+u',\qquad v=\bar v+v',\qquad p=\bar p+p' .
$$

Substitute into continuity:

$$
\frac{\partial(\bar u+u')}{\partial x}+\frac{\partial(\bar v+v')}{\partial y}=0 .
$$

Split each derivative:

$$
\left(\frac{\partial\bar u}{\partial x}+\frac{\partial\bar v}{\partial y}\right)+\left(\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}\right)=0 .
$$

The base flow satisfies continuity on its own, so the first bracket is zero:

$$
\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}=0 .\qquad\text{(L1)}
$$

Continuity is linear, so nothing is dropped. The $x$-momentum equation is

$$
\frac{\partial(\bar u+u')}{\partial t}+(\bar u+u')\frac{\partial(\bar u+u')}{\partial x}+(\bar v+v')\frac{\partial(\bar u+u')}{\partial y}=-\frac1\rho\frac{\partial(\bar p+p')}{\partial x}+\nu\nabla^2(\bar u+u') .
$$

The base flow is steady, so $\partial\bar u/\partial t=0$ and the time derivative is $\partial u'/\partial t$. Multiply out the first convective term:

$$
(\bar u+u')\frac{\partial(\bar u+u')}{\partial x}=\bar u\frac{\partial\bar u}{\partial x}+\bar u\frac{\partial u'}{\partial x}+u'\frac{\partial\bar u}{\partial x}+u'\frac{\partial u'}{\partial x} .
$$

Multiply out the second:

$$
(\bar v+v')\frac{\partial(\bar u+u')}{\partial y}=\bar v\frac{\partial\bar u}{\partial y}+\bar v\frac{\partial u'}{\partial y}+v'\frac{\partial\bar u}{\partial y}+v'\frac{\partial u'}{\partial y} .
$$

The pressure and viscous terms are linear and split directly. Collect the terms that contain only base-flow quantities:

$$
\bar u\frac{\partial\bar u}{\partial x}+\bar v\frac{\partial\bar u}{\partial y}+\frac1\rho\frac{\partial\bar p}{\partial x}-\nu\nabla^2\bar u=0 .
$$

This is the steady $x$-momentum equation for the base flow, which it satisfies, so the whole group cancels. What remains is exact:

$$
\frac{\partial u'}{\partial t}+\bar u\frac{\partial u'}{\partial x}+u'\frac{\partial\bar u}{\partial x}+\bar v\frac{\partial u'}{\partial y}+v'\frac{\partial\bar u}{\partial y}+\underbrace{u'\frac{\partial u'}{\partial x}+v'\frac{\partial u'}{\partial y}}_{\text{quadratic}}=-\frac1\rho\frac{\partial p'}{\partial x}+\nu\nabla^2u' .
$$

The last two terms on the left are products of two small quantities. If the disturbance amplitude is $\varepsilon U_e$ with $\varepsilon\ll1$, they are $O(\varepsilon^2)$ while every other disturbance term is $O(\varepsilon)$. Dropping them is the linearisation:

$$
\frac{\partial u'}{\partial t}+\bar u\frac{\partial u'}{\partial x}+u'\frac{\partial\bar u}{\partial x}+\bar v\frac{\partial u'}{\partial y}+v'\frac{\partial\bar u}{\partial y}=-\frac1\rho\frac{\partial p'}{\partial x}+\nu\nabla^2u' .
$$

The $y$-momentum equation goes the same way. After the base-flow terms cancel and the products $u'\,\partial v'/\partial x$ and $v'\,\partial v'/\partial y$ are dropped:

$$
\frac{\partial v'}{\partial t}+\bar u\frac{\partial v'}{\partial x}+u'\frac{\partial\bar v}{\partial x}+\bar v\frac{\partial v'}{\partial y}+v'\frac{\partial\bar v}{\partial y}=-\frac1\rho\frac{\partial p'}{\partial y}+\nu\nabla^2v' .
$$

Linearisation is what makes a single wave a valid solution: in a linear equation, waves of different $\alpha$ and $\omega$ do not interact, so each can be studied alone. It also limits the theory to the early, slow stage of transition. Once the TS waves are large enough for the dropped products to matter, the Λ-vortices and breakdown of [[SESA3043 3.4 - Transition to Turbulence#2. The roadmap to transition|3.4 §2]] follow, and those are outside linear theory.

## 3. The parallel-flow approximation by order of magnitude

The disturbance equations above still contain $\partial\bar u/\partial x$, $\bar v$ and $\partial\bar v/\partial x$, which make the coefficients depend on $x$. A boundary layer grows slowly compared with the wavelength of a TS wave, so these terms are small. The sizes follow from the Blasius solution ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions|3.2]]).

The base flow changes over a streamwise distance of order $x$, the distance from the leading edge. The wave changes over $1/\alpha_r$. With $\delta^*/x=1.7208/\sqrt{Re_x}$ and $Re_{\delta^*}=1.7208\sqrt{Re_x}$,

$$
\frac{\delta^*}{x}=\frac{1.7208}{\sqrt{Re_x}}=\frac{1.7208^2}{Re_{\delta^*}}=\frac{2.961}{Re_{\delta^*}} .
$$

Compare $u'\,\partial\bar u/\partial x$, of size $u'U_e/x$, with the term it sits beside, $\bar u\,\partial u'/\partial x$, of size $U_e\alpha_ru'$:

$$
\frac{u'\,\partial\bar u/\partial x}{\bar u\,\partial u'/\partial x}\sim\frac{1}{\alpha_rx}=\frac{1}{\alpha_r\delta^*}\,\frac{\delta^*}{x}=\frac{2.961}{(\alpha_r\delta^*)\,Re_{\delta^*}} .
$$

The wall-normal base velocity follows from the course's Blasius variables. With $v=-\partial\psi/\partial x$ and $\psi_x=(U_e\xi/2x)(f-\eta f')$ from [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#3. Deriving the Blasius equation|3.2 §3]],

$$
\bar v=\frac{U_e\xi}{2x}\left(\eta f'-f\right) .
$$

Far from the wall $f'\to1$ and $f\to\eta-\eta^*$, so the bracket tends to $\eta^*$:

$$
\bar v_e=\frac{U_e\,\xi\eta^*}{2x}=\frac{U_e\delta^*}{2x} .
$$

This is the largest value of $\bar v$ anywhere in the layer, and with $\delta^*/x=2.961/Re_{\delta^*}$,

$$
\frac{\bar v_e}{U_e}=\frac{1.481}{Re_{\delta^*}} .
$$

Both neglected effects are therefore $O(1/Re_{\delta^*})$ relative to the terms kept. The viscous terms are nominally of the same order, $\nu\nabla^2u'$ against $U_e\alpha_ru'$ being $1/(\alpha_r\delta^*Re_{\delta^*})$, but they are kept for two reasons: near the wall the disturbance varies over a thin viscous sublayer, where its $y$-derivatives are large and the viscous term is $O(1)$, and the viscous term carries the highest derivative, without which the no-slip condition cannot be imposed. The non-parallel terms have no such amplification anywhere.

> [!check] Sizes at the tip of the thumb (Python)
> At $Re_{\delta^*}=519$ with $\alpha_r\delta^*=0.304$ (§9): $\delta^*/x=0.00570$, so $x=175\,\delta^*$; the wavelength is $2\pi/0.304=20.7\,\delta^*$, over which $\delta^*\propto\sqrt x$ grows by $\tfrac12(20.7/175)=5.9\%$. The ratio $1/(\alpha_rx)=0.019$ and $\bar v_e/U_e=0.0029$. Both shrink as $Re_{\delta^*}$ rises, so the approximation is weakest near $Re_{crit}$ and near the leading edge.

With $\partial\bar u/\partial x$, $\bar v$ and $\partial\bar v/\partial x$ set to zero, $\bar u=\bar u(y)$ and the linearised equations are

$$
\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}=0,\qquad\text{(L1)}
$$

$$
\frac{\partial u'}{\partial t}+\bar u\frac{\partial u'}{\partial x}+v'\,\bar u'=-\frac1\rho\frac{\partial p'}{\partial x}+\nu\nabla^2u',\qquad\text{(L2)}
$$

$$
\frac{\partial v'}{\partial t}+\bar u\frac{\partial v'}{\partial x}=-\frac1\rho\frac{\partial p'}{\partial y}+\nu\nabla^2v'.\qquad\text{(L3)}
$$

Here $\bar u'=\mathrm d\bar u/\mathrm dy$. The only coupling to the base-flow shear is $v'\bar u'$ in (L2), the energy-transfer term of the introduction.

## 4. Normal modes

The coefficients of (L1)–(L3) depend on $y$ alone, so the equations are unchanged by a shift in $x$ or $t$. Their solutions can therefore be built from exponentials in $x$ and $t$:

$$
u'=\hat u(y)\,e^{i(\alpha x-\omega t)},\qquad v'=\hat v(y)\,e^{i(\alpha x-\omega t)},\qquad p'=\hat p(y)\,e^{i(\alpha x-\omega t)} .
$$

The physical disturbance is the real part. Write $E=e^{i(\alpha x-\omega t)}$. Each derivative of $E$ brings down a constant factor:

$$
\frac{\partial E}{\partial x}=i\alpha E,\qquad\frac{\partial E}{\partial t}=-i\omega E .
$$

So for any disturbance quantity $q'=\hat q(y)E$:

$$
\frac{\partial q'}{\partial x}=i\alpha\,\hat q\,E,\qquad\frac{\partial q'}{\partial t}=-i\omega\,\hat q\,E,\qquad\frac{\partial q'}{\partial y}=\mathrm D\hat q\,E .
$$

The Laplacian follows from two $x$-derivatives and two $y$-derivatives:

$$
\nabla^2q'=\left[(i\alpha)^2\hat q+\mathrm D^2\hat q\right]E=\left(\mathrm D^2-\alpha^2\right)\hat q\,E .
$$

Substitute into (L1) and cancel the common factor $E$:

$$
i\alpha\hat u+\mathrm D\hat v=0 .\qquad\text{(a)}
$$

Substitute into (L2):

$$
-i\omega\hat u+i\alpha\bar u\,\hat u+\bar u'\hat v=-\frac{i\alpha}{\rho}\hat p+\nu\left(\mathrm D^2-\alpha^2\right)\hat u .
$$

Combine the first two terms:

$$
i\left(\alpha\bar u-\omega\right)\hat u+\bar u'\hat v=-\frac{i\alpha}{\rho}\hat p+\nu\left(\mathrm D^2-\alpha^2\right)\hat u .\qquad\text{(b)}
$$

Substitute into (L3) and combine in the same way:

$$
i\left(\alpha\bar u-\omega\right)\hat v=-\frac1\rho\mathrm D\hat p+\nu\left(\mathrm D^2-\alpha^2\right)\hat v .\qquad\text{(c)}
$$

The phase speed $c_{ph}=\omega/\alpha$ tidies the bracket:

$$
\alpha\bar u-\omega=\alpha\left(\bar u-c_{ph}\right) .
$$

The three PDEs are now three ODEs in $y$ for three shapes. White & Majdalani (Ch. 5.2) use a disturbance stream function instead, $\psi'=\phi(y)E$ with $u'=\partial\psi'/\partial y$ and $v'=-\partial\psi'/\partial x$. Then $\hat v=-i\alpha\phi$, a constant multiple, so the final equation is the same with $\phi$ in place of $\hat v$.

## 5. Eliminating the pressure - the Orr–Sommerfeld equation

Continuity (a) gives $\hat u$ in terms of $\hat v$:

$$
i\alpha\hat u=-\mathrm D\hat v .
$$

Divide by $i\alpha$, using $-1/i=i$:

$$
\hat u=\frac{i}{\alpha}\mathrm D\hat v .
$$

Substitute into (b). The first term becomes

$$
i\alpha\left(\bar u-c_{ph}\right)\frac{i}{\alpha}\mathrm D\hat v=-\left(\bar u-c_{ph}\right)\mathrm D\hat v ,
$$

and the viscous term becomes

$$
\nu\left(\mathrm D^2-\alpha^2\right)\frac{i}{\alpha}\mathrm D\hat v=\frac{i\nu}{\alpha}\left(\mathrm D^3-\alpha^2\mathrm D\right)\hat v .
$$

So (b) reads

$$
-\left(\bar u-c_{ph}\right)\mathrm D\hat v+\bar u'\hat v=-\frac{i\alpha}{\rho}\hat p+\frac{i\nu}{\alpha}\left(\mathrm D^3-\alpha^2\mathrm D\right)\hat v .
$$

Move the pressure to the left and everything else to the right:

$$
\frac{i\alpha}{\rho}\hat p=\left(\bar u-c_{ph}\right)\mathrm D\hat v-\bar u'\hat v+\frac{i\nu}{\alpha}\left(\mathrm D^3-\alpha^2\mathrm D\right)\hat v .
$$

Multiply by $1/(i\alpha)=-i/\alpha$:

$$
\frac{\hat p}{\rho}=\frac{i}{\alpha}\left[-\left(\bar u-c_{ph}\right)\mathrm D\hat v+\bar u'\hat v\right]+\frac{\nu}{\alpha^2}\left(\mathrm D^3-\alpha^2\mathrm D\right)\hat v .
$$

The factor on the last term is $(-i/\alpha)(i\nu/\alpha)=\nu/\alpha^2$. Differentiate in $y$. In the square bracket, the product rule gives

$$
\mathrm D\left[-\left(\bar u-c_{ph}\right)\mathrm D\hat v+\bar u'\hat v\right]=-\bar u'\mathrm D\hat v-\left(\bar u-c_{ph}\right)\mathrm D^2\hat v+\bar u''\hat v+\bar u'\mathrm D\hat v .
$$

The two $\bar u'\mathrm D\hat v$ terms cancel:

$$
\mathrm D\left[-\left(\bar u-c_{ph}\right)\mathrm D\hat v+\bar u'\hat v\right]=-\left(\bar u-c_{ph}\right)\mathrm D^2\hat v+\bar u''\hat v .
$$

So

$$
\frac{\mathrm D\hat p}{\rho}=\frac{i}{\alpha}\left[-\left(\bar u-c_{ph}\right)\mathrm D^2\hat v+\bar u''\hat v\right]+\frac{\nu}{\alpha^2}\left(\mathrm D^4-\alpha^2\mathrm D^2\right)\hat v .
$$

This is the cross-differentiation: the pressure appears in (b) undifferentiated and in (c) differentiated once in $y$, so differentiating the $\hat p$ from (b) and putting it into (c) removes it. Write (c) with the phase speed:

$$
i\alpha\left(\bar u-c_{ph}\right)\hat v=-\frac{\mathrm D\hat p}{\rho}+\nu\left(\mathrm D^2-\alpha^2\right)\hat v .
$$

Substitute $\mathrm D\hat p/\rho$:

$$
i\alpha\left(\bar u-c_{ph}\right)\hat v=\frac{i}{\alpha}\left(\bar u-c_{ph}\right)\mathrm D^2\hat v-\frac{i}{\alpha}\bar u''\hat v-\frac{\nu}{\alpha^2}\left(\mathrm D^4-\alpha^2\mathrm D^2\right)\hat v+\nu\left(\mathrm D^2-\alpha^2\right)\hat v .
$$

Multiply every term by $\alpha/i=-i\alpha$. Term by term: $i\alpha\cdot(-i\alpha)=\alpha^2$ on the left; $(i/\alpha)(-i\alpha)=1$ for the next two; $(-\nu/\alpha^2)(-i\alpha)=i\nu/\alpha$; and $\nu(-i\alpha)=-i\alpha\nu$:

$$
\alpha^2\left(\bar u-c_{ph}\right)\hat v=\left(\bar u-c_{ph}\right)\mathrm D^2\hat v-\bar u''\hat v+\frac{i\nu}{\alpha}\left(\mathrm D^4-\alpha^2\mathrm D^2\right)\hat v-i\alpha\nu\left(\mathrm D^2-\alpha^2\right)\hat v .
$$

Write the last term with the same prefactor, $-i\alpha\nu=(i\nu/\alpha)(-\alpha^2)$:

$$
-i\alpha\nu\left(\mathrm D^2-\alpha^2\right)\hat v=\frac{i\nu}{\alpha}\left(-\alpha^2\mathrm D^2+\alpha^4\right)\hat v .
$$

Combine the two viscous terms:

$$
\frac{i\nu}{\alpha}\left(\mathrm D^4-\alpha^2\mathrm D^2-\alpha^2\mathrm D^2+\alpha^4\right)\hat v=\frac{i\nu}{\alpha}\left(\mathrm D^4-2\alpha^2\mathrm D^2+\alpha^4\right)\hat v .
$$

Move the left-hand side across and group the inviscid terms:

$$
0=\left(\bar u-c_{ph}\right)\left(\mathrm D^2-\alpha^2\right)\hat v-\bar u''\hat v+\frac{i\nu}{\alpha}\left(\mathrm D^4-2\alpha^2\mathrm D^2+\alpha^4\right)\hat v .
$$

Move the viscous group to the right. This is the Orr–Sommerfeld equation in the course's form:

$$
\boxed{\left(\bar u-c_{ph}\right)\left(\frac{\mathrm d^2\hat v}{\mathrm dy^2}-\alpha^2\hat v\right)-\hat v\frac{\mathrm d^2\bar u}{\mathrm dy^2}=-\frac{i\nu}{\alpha}\left(\alpha^4\hat v-2\alpha^2\frac{\mathrm d^2\hat v}{\mathrm dy^2}+\frac{\mathrm d^4\hat v}{\mathrm dy^4}\right),\qquad c_{ph}=\frac{\omega}{\alpha}}
$$

The viscous bracket is $(\mathrm D^2-\alpha^2)^2\hat v$, the disturbance Laplacian applied twice, which is why the equation is fourth order. The left-hand side holds the inertia of the wave relative to the local flow ($\bar u-c_{ph}$) and the curvature of the base profile, $\bar u''$; the base flow enters only through $\bar u$ and $\bar u''$, so the same equation serves any parallel profile, Blasius, Falkner–Skan or Pohlhausen.

> [!check] Symbolic check (sympy)
> With $\hat u=(i/\alpha)\hat v'$, the $\hat p/\rho$ and $\mathrm D\hat p/\rho$ expressions above were checked symbolically against (b), and $i\alpha$ times the left side minus the right side of (c) equals the Orr–Sommerfeld residual identically. No step depends on the form of $\bar u(y)$.

## 6. Boundary conditions, scaling and the eigenvalue problem

Four conditions are needed for a fourth-order equation. At the wall the disturbance cannot pass through the surface, $\hat v(0)=0$, and it cannot slip, $\hat u(0)=0$, which through $\hat u=(i/\alpha)\mathrm D\hat v$ is $\mathrm D\hat v(0)=0$. Far from the wall the disturbance dies out, $\hat v\to0$ and $\mathrm D\hat v\to0$ as $y\to\infty$:

$$
\hat v(0)=\mathrm D\hat v(0)=0,\qquad\hat v,\ \mathrm D\hat v\to0\ \text{as}\ y\to\infty .
$$

Every term of the equation and every condition is proportional to $\hat v$, so $\hat v=0$ always satisfies them. A non-zero shape exists only when $\alpha$, $\omega$ and $\nu$ take special combinations: this is an eigenvalue problem, and the special values are eigenvalues with $\hat v$ the eigenvector. The amplitude of $\hat v$ is left undetermined, which is why linear theory gives growth rates but never the absolute size of a wave.

The equation becomes dimensionless with $\delta^*$ for length and $U_e$ for speed. Put $y=\delta^*\tilde y$, $\alpha=\tilde\alpha/\delta^*$, $\bar u=U_e\tilde u$ and $c_{ph}=U_e\tilde c$. Each $y$-derivative brings $1/\delta^*$, so the left side scales as $U_e/\delta^{*2}$ and the right side as $\nu/(\tilde\alpha\,\delta^{*3})$. Divide through by $U_e/\delta^{*2}$:

$$
\left(\tilde u-\tilde c\right)\left(\tilde{\mathrm D}^2-\tilde\alpha^2\right)\hat v-\tilde u''\hat v=-\frac{i}{\tilde\alpha\,Re_{\delta^*}}\left(\tilde{\mathrm D}^2-\tilde\alpha^2\right)^2\hat v,\qquad Re_{\delta^*}=\frac{U_e\delta^*}{\nu} .
$$

The only parameter is $Re_{\delta^*}$, so a given profile shape has one stability diagram drawn against $Re_{\delta^*}$. The frequency on the thumb plot is $F=\omega\nu/U_e^2$. With $\omega=\tilde\omega U_e/\delta^*$,

$$
F=\frac{\tilde\omega U_e}{\delta^*}\,\frac{\nu}{U_e^2}=\frac{\tilde\omega\,\nu}{U_e\delta^*}=\frac{\tilde\omega}{Re_{\delta^*}} .
$$

$F$ contains no length, so it stays constant as a wave of fixed physical frequency travels downstream along a layer at constant $U_e$, while $Re_{\delta^*}$ rises. That is why a fixed-frequency disturbance moves along a horizontal line on the thumb plot.

## 7. Temporal and spatial growth

The eigenvalue relation links $\alpha$, $\omega$ and $Re$. One of $\alpha$, $\omega$ is chosen real and the other is solved for. With real $\alpha$ and complex $\omega=\omega_r+i\omega_i$ (temporal growth),

$$
v'=\hat v\,e^{i(\alpha x-\omega_rt)}\,e^{\omega_it},
$$

so the wave grows in time everywhere at once when $\omega_i>0$. With real $\omega$ and complex $\alpha=\alpha_r+i\alpha_i$ (spatial growth),

$$
v'=\hat v\,e^{i[(\alpha_r+i\alpha_i)x-\omega t]}=\hat v\,e^{i(\alpha_rx-\omega t)}\,e^{-\alpha_ix},
$$

because $i\cdot i\alpha_ix=-\alpha_ix$. The three factors are the shape, the wave and the growth; the growth rate is $-\alpha_i$, so $\alpha_i<0$ is spatially unstable and $\alpha_i>0$ spatially stable.

A boundary layer is convectively unstable: a disturbance grows as it is carried downstream and the flow at a fixed point recovers once it has passed. A source such as a vibrating ribbon or engine noise fixes the frequency, so the spatial form is the one that matches experiment and the one used for the thumb plot and the $e^n$ method. The two forms share one neutral curve. On it the wave neither grows nor decays, so both $\alpha$ and $\omega$ are real at once, $\omega_i=0$ and $\alpha_i=0$ together. The neutral curve can therefore be found from the cheaper temporal problem and the spatial growth rates filled in afterwards, which is how §8 does it.

## 8. Solving the equation numerically for the Blasius layer

The Orr–Sommerfeld equation has no closed-form solution for the Blasius profile, so it is solved numerically. The base profile comes from the course's Blasius equation $f'''+ff''=0$ with $f''(0)=0.46960$ ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#4. Solving it: guess-and-shooting method|3.2 §4]]). Since $\delta^*=\eta^*\xi$ with $\eta^*=1.21678$, a height $\tilde y=y/\delta^*$ sits at $\eta=\eta^*\tilde y$, so

$$
\tilde u(\tilde y)=f'(\eta^*\tilde y),\qquad\tilde u''(\tilde y)=\eta^{*2}f'''(\eta^*\tilde y)=-\eta^{*2}\,f f''\big|_{\eta^*\tilde y} .
$$

The profile is concave everywhere, $\tilde u''\le0$, with $\tilde u''=0$ only at the wall, where $f(0)=0$. The equation is discretised by Chebyshev collocation: $\hat v$ is represented by its values at $N+1$ Chebyshev points mapped algebraically onto $0\le\tilde y\le40$, with half the points below $\tilde y=4$ so that the wall region and the critical layer are well resolved, and derivatives become matrices. The two equations nearest each end are replaced by the four boundary conditions.

For the temporal problem (real $\tilde\alpha$), multiply the dimensionless equation by $\tilde\alpha$ and collect the terms in $\tilde\omega=\tilde\alpha\tilde c$:

$$
\left[\tilde\alpha\tilde u\left(\tilde{\mathrm D}^2-\tilde\alpha^2\right)-\tilde\alpha\tilde u''+\frac{i}{Re_{\delta^*}}\left(\tilde{\mathrm D}^2-\tilde\alpha^2\right)^2\right]\hat v=\tilde\omega\left(\tilde{\mathrm D}^2-\tilde\alpha^2\right)\hat v ,
$$

a generalised matrix eigenvalue problem $\mathbf A\hat{\mathbf v}=\tilde\omega\mathbf B\hat{\mathbf v}$. For the spatial problem (real $\tilde\omega$) the same equation is a quartic in $\tilde\alpha$,

$$
\left[\frac{i}{Re_{\delta^*}}\tilde\alpha^4-\tilde u\,\tilde\alpha^3+\left(\tilde\omega-\frac{2i}{Re_{\delta^*}}\tilde{\mathrm D}^2\right)\tilde\alpha^2+\left(\tilde u\tilde{\mathrm D}^2-\tilde u''\right)\tilde\alpha+\left(\frac{i}{Re_{\delta^*}}\tilde{\mathrm D}^4-\tilde\omega\tilde{\mathrm D}^2\right)\right]\hat v=0 ,
$$

which is solved as a linear eigenvalue problem four times the size by stacking $[\hat v,\tilde\alpha\hat v,\tilde\alpha^2\hat v,\tilde\alpha^3\hat v]$. Of the many eigenvalues, the TS mode is the least stable one with a phase speed between about $0.15U_e$ and $0.7U_e$; the others belong to the damped spectrum.

> [!check] Convergence and a benchmark (Python)
> The standard test case $Re_{\delta^*}=998$, $\tilde\alpha=0.308$ gives $\tilde c=0.364121+0.007962i$ for $N=60$, 80 and 100, the published value for this case to the digits printed ($0.36412+0.00796i$). The minimum Reynolds number on the neutral curve (§9) is $519.0609$, $519.0599$, $519.0598$ and $519.0592$ for $N=50$, 60, 80 and 100, and $519.060$ with the outer boundary moved to $30\delta^*$ or $60\delta^*$. The spatial solve at $Re_{\delta^*}=998$ and the real frequency $\tilde\omega=0.308\times0.36412$ gives $\tilde\alpha=0.308457-0.005720i$; the temporal growth converted with the group velocity, $-\omega_i/c_g=-0.002452/0.4286=-0.005722$, agrees to 0.04 %.

## 9. The neutral curve and the critical Reynolds number

![[aa_deepdive_neutral_curve.png|900]]

At each $Re_{\delta^*}$, the temporal growth $\omega_i$ of the TS mode changes sign at two real wavenumbers, a lower-branch and an upper-branch value; between them the wave grows. Converting each neutral pair $(\tilde\alpha,\tilde\omega)$ to $F=\tilde\omega/Re_{\delta^*}$ (§6) and repeating for each $Re_{\delta^*}$ draws the neutral curve in the $(Re_{\delta^*},F)$ axes of the thumb plot. The shading inside is the spatial $\alpha_i\delta^*$ from the quartic solve at each $(Re_{\delta^*},F)$: negative everywhere inside the curve, so every frequency in the band grows, and most negative, about $-0.012$, along the middle of the band at high $Re_{\delta^*}$. This is the thumb plot computed rather than sketched, and the growth-rate hump at a single $Re$ is a vertical cut through it.

The curve has a lowest point, the small critical Reynolds number. Below it, $\max_\alpha\omega_i<0$ and every disturbance decays. Root-finding on $\max_\alpha\omega_i(Re_{\delta^*})=0$ gives

$$
Re_{\delta^*,crit}=519.06,\qquad\tilde\alpha_{crit}=\alpha_r\delta^*=0.3038,\qquad\tilde\omega_{crit}=0.1205,
$$

so the first wave to grow travels at $c_{ph}=\tilde\omega/\tilde\alpha=0.397\,U_e$ and has $F_{crit}=0.1205/519.06=2.32\times10^{-4}$. White & Majdalani quote $Re_{\delta^*,crit}\approx520$, the value used in [[SESA3043 3.4 - Transition to Turbulence#6. The instability diagram and the "thumb" plot|3.4 §6]]. The wavelength is $2\pi/0.3038=20.7\,\delta^*$, about seven boundary-layer thicknesses ($\delta_{99}=\eta_{99}\xi=2.85\,\delta^*$), so a TS wave is long compared with the layer it lives in.

On a Blasius plate, $Re_{\delta^*}=1.7208\sqrt{Re_x}$, so

$$
Re_{x,crit}=\left(\frac{519.06}{1.7208}\right)^2=9.10\times10^4 .
$$

Two features of the computed curve match the sketched thumb plot. The band of unstable $F$ narrows and moves to lower frequency as $Re_{\delta^*}$ rises, because both branches fall roughly as a power of $Re_{\delta^*}$. And the upper branch closes towards the lower one at high $Re$: the Blasius profile is stable to every wave in the limit $Re\to\infty$, so its instability is viscous in origin and needs a finite Reynolds number, which is also why an adverse pressure gradient changes the picture so much.

> [!check] The tip of the thumb in metres (Python)
> At $U_e=50$ m/s and $\nu=1.5\times10^{-5}$ m²/s, the unit Reynolds number is $U_e/\nu=3.333\times10^6$ m⁻¹, so $x_{crit}=9.10\times10^4/(3.333\times10^6)=27.3$ mm. There $\delta^*=519.06\nu/U_e=0.156$ mm, the critical wavelength is $20.7\delta^*=3.22$ mm and the critical frequency is $\omega=\tilde\omega U_e/\delta^*=3.87\times10^4$ rad/s, or $f=6.16$ kHz. The first unstable waves are short, high-pitched ripples a few centimetres from the leading edge, yet the layer stays laminar for most of a metre (§10).

## 10. From growth rates to transition - the eⁿ envelope

![[aa_deepdive_en_envelope.png|900]]

A wave of fixed $F$ enters the thumb on the lower branch at $x_0$ and grows by $n=\ln(A/A_0)=-\int_{x_0}^x\alpha_i\,\mathrm dx$ until it leaves through the upper branch ([[SESA3043 3.4 - Transition to Turbulence#The n factor|3.4 §7]]). The thumb plot is in $Re_{\delta^*}$ and $\alpha_i\delta^*$, so the integral is converted. On a Blasius plate,

$$
Re_x=\left(\frac{Re_{\delta^*}}{1.7208}\right)^2 .
$$

Differentiate:

$$
\mathrm dRe_x=\frac{2Re_{\delta^*}}{1.7208^2}\,\mathrm dRe_{\delta^*} .
$$

With $x=\nu Re_x/U_e$ and $\delta^*=\nu Re_{\delta^*}/U_e$, divide the first by the second:

$$
\frac{\mathrm dx}{\delta^*}=\frac{\mathrm dRe_x}{Re_{\delta^*}}=\frac{2}{1.7208^2}\,\mathrm dRe_{\delta^*}=0.6754\,\mathrm dRe_{\delta^*} .
$$

Write $\alpha_i\,\mathrm dx=(\alpha_i\delta^*)(\mathrm dx/\delta^*)$:

$$
n=-\int_{x_0}^x\alpha_i\,\mathrm dx=-0.6754\int_{Re_{\delta^*,0}}^{Re_{\delta^*}}\left(\alpha_i\delta^*\right)\mathrm dRe_{\delta^*} .
$$

The integral is a property of the Blasius profile alone; $U_e$ and $\nu$ enter only when $Re_{\delta^*}$ is turned back into a distance. Integrating along each row of constant $F$ gives the constant-frequency amplification curves. Each rises from zero at its lower-branch crossing, peaks where it leaves the thumb and then falls. Low frequencies enter late but stay inside for a long range of $Re_{\delta^*}$ and so reach large $n$; high frequencies enter early but leave quickly. The envelope, the maximum over all frequencies at each station, is what the $e^n$ method compares with $n_{crit}$.

Computed with $\Delta Re_{\delta^*}=20$ and frequencies every $2\times10^{-6}$ in $F$, the envelope crosses the three values of $n_{crit}$ that matter for this module at:

| $n_{crit}$ | $A/A_0=e^{n_{crit}}$ | $Re_{\delta^*,tr}$ | $Re_{x,tr}$ | $x_{tr}$ at 50 m/s (m) | $Re_{x,tr}/Re_{x,crit}$ |
|---:|---:|---:|---:|---:|---:|
| 9 | 8103 | 3083 | $3.21\times10^6$ | 0.963 | 35.3 |
| 7 | 1097 | 2581 | $2.25\times10^6$ | 0.675 | 24.7 |
| 5 | 148 | 2074 | $1.45\times10^6$ | 0.436 | 16.0 |

The value $n_{crit}=9$ is the clean-environment calibration of Smith & Gamberoni and van Ingen and the XFOIL and XFLR5 default. On a flat plate it puts transition at $Re_x=3.2\times10^6$, the classical figure for natural transition in quiet flow, and 35 times the critical $Re_x$: instability starts long before transition. The illustrative growth-rate tables of [[SESA3043 3.4 - Transition to Turbulence#9. Worked example: locating transition on a flat plate (suggested)|3.4 §9]] gave $x_{tr}=0.958$ m at the same speed, within 1 % of the computed 0.963 m. The frequency whose curve touches the envelope at $n=9$ is $F\approx26\times10^{-6}$, which at 50 m/s is $f=F U_e^2/(2\pi\nu)\approx690$ Hz, a factor of nine below the first unstable frequency.

Coursework Q4 runs XFOIL with $n_{crit}=7$ and 5 to mimic a rougher or noisier environment ([[SESA3043 Advanced Aeronautics Hub#Assessment and deadlines|hub, coursework]]). On a flat plate those values move transition to 70 % and 45 % of the clean-flow distance. The coursework Reynolds number $Re_c=10^5$ is below even the $n_{crit}=5$ value of $Re_{x,tr}=1.45\times10^6$, so a zero-pressure-gradient layer at that Reynolds number would stay laminar over the whole chord. Any transition XFOIL predicts there is driven by the adverse pressure gradient behind the suction peak, which enlarges the thumb and steepens the amplification curves, and the effect of changing $n_{crit}$ shows up through that region.

> [!warning] What the envelope does and does not give
> The table assumes a Blasius layer at every station, a quiet environment and growth from linear theory alone. The $e^n$ method has no receptivity model, so $n_{crit}$ is calibrated rather than derived; it ignores the nonlinear stages and treats the layer as parallel. The numbers are a check on the method, not a prediction for a real plate with a pressure gradient or roughness.

## 11. Common mistakes

Most errors on this topic are about signs, names and which Reynolds number is meant, rather than about the algebra:

- taking $\alpha_i>0$ as growth: with $e^{i(\alpha x-\omega t)}$ the amplitude is $e^{-\alpha_ix}$, so growth needs $\alpha_i<0$ (spatial) or $\omega_i>0$ (temporal);
- calling $Re_{\delta^*,crit}=519$ the transition Reynolds number: it is the first point at which any wave can grow, and on a Blasius plate transition comes 35 times further along in $Re_x$;
- converting $Re_{\delta^*}$ to $Re_x$ with a factor instead of a square: $Re_x=(Re_{\delta^*}/1.7208)^2$, and only at zero pressure gradient;
- forgetting that $\hat u=(i/\alpha)\mathrm D\hat v$ turns the no-slip condition into $\mathrm D\hat v(0)=0$, so four conditions are imposed, two at each end;
- reading the prime on $\bar u'$ as a disturbance: on $\bar u$ it is a $y$-derivative;
- dropping the viscous term because it is $O(1/Re)$: it is large inside the thin wall layer and is needed for no slip, whereas the non-parallel terms are uniformly $O(1/Re_{\delta^*})$.

## Links

- Parent: [[SESA3043 Advanced Aeronautics Hub]]
- Lecture note: [[SESA3043 3.4 - Transition to Turbulence]] (the roadmap, the thumb plot, the $e^n$ method and its limitations, and the worked transition example)
- Base flow: [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]] · [[Blasius and Falkner-Skan Similarity Solutions]] · [[Shooting Method and the Blasius Solution]] (SESA2029)
- Concepts: [[Linear Stability and Transition Prediction]] · [[Incompressible Navier-Stokes Equations]] · [[Order-of-Magnitude Analysis]] · [[Prandtl Boundary-Layer Equations]]
- Where it is used: [[SESA3043 3.6 - Viscous-Inviscid Interaction]] (XFOIL's $N_{crit}$) · [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]] (adverse-gradient profiles)
- Earlier years: [[Eigenvalues and Eigenvectors]] (MATH1054) · [[Von Neumann Stability Analysis]] (the same normal-mode idea applied to a numerical scheme)
- Formulae: [[SESA3043 Formula Sheet]]

## Sources

- `CH3-4 Transition to Turbulence(1).pdf`, slides 19–24 (decomposition, normal modes, linearisation and the Orr–Sommerfeld equation), 25–29 (temporal and spatial growth), 30–34 (instability diagram and thumb plot), 37–43 (the $n$ factor and the $e^n$ method), 44 (limitations), 46 (pressure gradients) and 47 (key formulae).
- `06 November 2026 at 14_52_55.txt` (BL4, Fri 6 Nov), ll. 1680–1986: the decomposition, normal modes, the route to the Orr–Sommerfeld equation and the choice of spatial growth.
- `06 November 2026 at 15_54_41.txt` (BL5, Fri 6 Nov), ll. 1–110 and 113–237: shape, wave and growth, the thumb plot and the $e^n$ method.
- F. M. White & J. Majdalani, *Viscous Fluid Flow*, 4th ed. (2022), Ch. 5.2 (the further reading of slide 24, with the stream-function form and $Re_{\delta^*,crit}\approx520$).
- A. M. O. Smith & N. Gamberoni (1956) and J. L. van Ingen (1956), the $e^9$ calibration (slide 43).
- Checks: the elimination of $\hat u$ and $\hat p$ was verified with sympy. The eigenvalue solver (Chebyshev collocation, $N=50$, algebraic mapping to $40\delta^*$) was checked against the $Re_{\delta^*}=998$ benchmark and for convergence in $N$ and domain height; every number in §§3 and 8–10 was computed in Python.
- Figures: `generate_aa_deepdive_figures.py` (`fig_neutral_curve`, which writes `aa_deepdive_neutral_curve.png` and `aa_deepdive_en_envelope.png`). The amplification curves in the figure use a coarser grid than the table, so the figure labels are rounded to the nearest 100.

## Self-study tasks

No homework was set for 3.4, and the full derivation is optional reading (BL4, ll. 1943–1962). Sheet-set tasks are the Chapter 3 revision questions on §3.4, cited to the transcript lines that cover them; tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **Sheet-set Q3 (BL4, ll. 1680–1986; BL5, ll. 19–34)** Write the decomposition and the normal-mode form, linearise the $x$-momentum equation term by term, and say which assumption removes each dropped term. → [[#2. Decomposition and linearisation|§2]] · [[#4. Normal modes|§4]]
- [ ] **Optional reading (BL4, ll. 1943–1962; slide 24)** Eliminate $\hat u$ and $\hat p$ from (a)–(c) and arrive at the Orr–Sommerfeld equation of slide 24, then state its four boundary conditions. → [[#5. Eliminating the pressure - the Orr–Sommerfeld equation|§5]] · [[#6. Boundary conditions, scaling and the eigenvalue problem|§6]]
- [ ] **Sheet-set Q4 (BL5, ll. 46–107)** On the computed thumb plot, read off the unstable frequency band at $Re_{\delta^*}=1000$ (answer $55\times10^{-6}<F<131\times10^{-6}$) and say why the tip at $Re_{\delta^*}=519$ is not the transition point. → [[#9. The neutral curve and the critical Reynolds number|§9]]
- [ ] **Sheet-set Q5 (BL5, ll. 113–237)** Convert $n=-\int\alpha_i\,\mathrm dx$ to an integral in $Re_{\delta^*}$ for a Blasius plate, and use the envelope to find $x_{tr}$ for $n_{crit}=9$ at 50 m/s. Answer 0.963 m. → [[#10. From growth rates to transition - the eⁿ envelope|§10]]

### Further practice

- [ ] (suggested, not lecturer-set) Show that $\bar v_e=U_e\delta^*/(2x)$ for the Blasius layer, and hence that the non-parallel terms are $O(1/Re_{\delta^*})$. → [[#3. The parallel-flow approximation by order of magnitude|§3]]
- [ ] (suggested, not lecturer-set) For coursework Q4, find $Re_{x,tr}$ on a flat plate for $n_{crit}=7$ and 5 and explain why a layer at $Re_c=10^5$ needs an adverse pressure gradient to transition. → [[#10. From growth rates to transition - the eⁿ envelope|§10]]
- [ ] (suggested, not lecturer-set) Write a Chebyshev-collocation solver for the temporal problem and reproduce $\tilde c=0.36412+0.00796i$ at $Re_{\delta^*}=998$, $\tilde\alpha=0.308$, then find $Re_{\delta^*,crit}=519$. → [[#8. Solving the equation numerically for the Blasius layer|§8]]

## Transcript and slide slips

> [!warning] Slips in the parts of BL4 and BL5 this note uses
> Where: [[#2. Decomposition and linearisation]] and [[#7. Temporal and spatial growth]].
>
> | Where | Said | Correct |
> |---|---|---|
> | BL4, ll. 1871–1872 | the $p'$ shape *"again the shape V hat"* | $\hat p(y)$ |
> | BL4, ll. 1889–1910 | *"steady"* Navier–Stokes, then corrected | unsteady 2-D incompressible Navier–Stokes; the $\partial/\partial t$ terms give the $-i\omega$ factors |
> | BL4, l. 1928 | $x$-momentum read with only *"partial square U, partial Y square"* | $\nu\left(\partial^2u/\partial x^2+\partial^2u/\partial y^2\right)$; the $\partial^2/\partial x^2$ part gives the $-\alpha^2$ terms |
> | BL4, l. 1936 | *"U, V, and T"* | $u$, $v$ and $p$ |
> | BL4, ll. 1964–1968 | *"phi hat"* for the $v$ shape | $\hat v$, as on slide 24 ($\phi$ is White's stream-function shape, $\hat v=-i\alpha\phi$) |
> | BL4, l. 1974; BL5, l. 6 | *"eigenfactors"* | eigenvectors $\hat v$ |
> | BL5, ll. 23–27 | the spatial-growth disturbance written as *"phi prime is equal to phi hat"* | $v'=\hat v(y)e^{i(\alpha_rx-\omega t)}e^{-\alpha_ix}$ (slide 29) |
> | BL5, l. 69 | *"has negative alpha, sorry, positive alpha i"* | outside the neutral curve $\alpha_i>0$, as corrected |
