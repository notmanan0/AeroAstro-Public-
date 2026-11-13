---
title: "SESA3043 Deep Dive - Momentum Integral Equation and Pohlhausen Method"
module: "SESA3043 Advanced Aeronautics"
type: topic
stream: "Chapter 3: Methods for Boundary Layers"
order: 13.5
tags: [sesa3043, boundary-layer, momentum-integral, von-karman, pohlhausen, separation, thwaites, derivation, deep-dive]
aliases: ["Kármán–Pohlhausen method deep dive", "MIE and Pohlhausen deep dive", "Momentum integral equation derivation in full"]
date: 2026-11-12
status: lectured
coverage: "Every step of the von Kármán momentum integral equation (CH3-5 slides 5–38, BL6) and of the Pohlhausen quartic (CH3-3 slides 8–27, BL3–BL4), the integral properties as functions of λ worked by hand, and the coupling of the two into the Kármán–Pohlhausen growth equation (an extension), checked against Blasius, Falkner–Skan, Howarth's retarded flow and the circular cylinder"
parent: ["[[SESA3043 Advanced Aeronautics Hub]]"]
prerequisites: ["[[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]]", "[[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]]", "[[SESA3043 3.5 - Momentum Integral Equation]]"]
next_topics: ["[[SESA3043 3.6 - Viscous-Inviscid Interaction]]"]
key_concepts: ["[[Momentum Integral Equation]]", "[[Pohlhausen Method]]", "[[Boundary Layer Separation]]", "[[Displacement and Momentum Thickness]]"]
tutorial_sheets: ["03 - Exams & Past Papers/Ch3_Revision_Questions.pdf"]
sources: ["02 - Sources/Lectures/CH3-5 Momentum Integral Eqn(1).pdf", "02 - Sources/Lectures/Ch3_Notes_Momentum Integral Eq.pdf", "02 - Sources/Lectures/CH3-3 Pohlhausen.pdf", "02 - Sources/Lectures/Ch3_Notes_Pohlhausen.pdf", "02 - Sources/Lectures/05 November 2026 at 13_59_07.txt", "02 - Sources/Lectures/06 November 2026 at 14_52_55.txt", "02 - Sources/Lectures/12 November 2026 at 13_50_20.txt"]
---

# SESA3043 Deep Dive - Momentum Integral Equation and Pohlhausen Method

> [!abstract] Summary
> Integrating the boundary-layer momentum equation across the layer gives von Kármán's momentum integral equation, $\mathrm d\theta/\mathrm dx+(2+H)(\theta/U_e)\,\mathrm dU_e/\mathrm dx=C_f/2$: one ODE in $x$, valid for any profile, but with three unknowns. Pohlhausen's quartic supplies the missing two, $H$ and $C_f$, as functions of $\lambda=(\delta^2/\nu)\,\mathrm dU_e/\mathrm dx$. Substituted into the momentum integral, the pair become a single first-order ODE for $Z=\theta^2/\nu$, $U_e\,\mathrm dZ/\mathrm dx=F(K)$, which is marched from the leading edge until $\lambda=-12$ marks separation. On Howarth's linearly retarded flow this predicts separation at $x/L=0.157$ against the exact $0.120$: the method gets the growth of the layer within a few per cent and the separation point late.

> [!summary]- Exam use: quick path
> - **Use it when:** a laminar layer grows under a given $U_e(x)$ that is not a power law, and you need $\theta(x)$, $C_f(x)$ or an estimate of where it separates; or when a question asks you to derive the MIE or the Pohlhausen coefficients.
> - **Assumptions:** 2-D, steady, incompressible, laminar (for the closure; the MIE itself is profile-free); $U_e(x)$ known from potential flow; quartic profile valid for $-12\le\lambda\le12$.
> - **Method:** 1. MIE: $\frac{\mathrm d\theta}{\mathrm dx}+(2+H)\frac{\theta}{U_e}\frac{\mathrm dU_e}{\mathrm dx}=\frac{C_f}{2}$. 2. Quartic: $\theta/\delta=\frac{37}{315}-\frac{\lambda}{945}-\frac{\lambda^2}{9072}$, $\delta^*/\delta=\frac3{10}-\frac\lambda{120}$, $\tau_w\delta/\mu U_e=2+\frac\lambda6$. 3. With $K=\theta^2U_e'/\nu=(\theta/\delta)^2\lambda$, march $U_e\,\mathrm d(\theta^2/\nu)/\mathrm dx=F(K)$. 4. Recover $\lambda$ from $K$, then $\delta$, $\delta^*$, $C_f$. 5. Separation where $\lambda=-12$ ($K=-0.157$).
> - **Common mistakes:** treating $\lambda=-12$ as an accurate separation point (it is late; Thwaites' $K=-0.09$ is closer); integrating for $\delta$ directly and losing the $\mathrm d^2U_e/\mathrm dx^2$ term.
> - **Practise:** [[#8. Worked case: separation in a linearly retarded flow]] · [[SESA3043 Ch3 Revision Questions - Worked Solutions#3.3 Pohlhausen and pressure gradient|Ch3 revision 3.3]]

The two methods answer different halves of one question. The momentum integral equation (MIE) is an exact consequence of the boundary-layer equations: it says how fast the momentum deficit of the layer, measured by $\theta$, grows under wall friction and the pressure gradient. It knows nothing about the shape of the profile, which is why it holds for laminar and turbulent layers alike, and also why it cannot be solved on its own: the shape enters through $H=\delta^*/\theta$ and the friction through $C_f$, and neither is fixed by the equation.

The Pohlhausen quartic is a shape. It fixes the profile from conditions at the wall and the edge and leaves one free parameter, $\lambda$, set by the local pressure gradient and the local thickness. Given $\lambda$, the quartic delivers $H$ and $C_f$, which is exactly what the MIE lacks. The MIE in turn says how $\theta$, and hence $\delta$ and $\lambda$, change with $x$. Each method closes the other, and together they predict the whole development of a laminar layer from the edge velocity alone.

The weakness is in the shape. Every station is forced onto the same one-parameter family of quartics, so the profile near separation, which in reality is strongly emptied near the wall, is represented only roughly. The growth of $\theta$ comes out within a few per cent of exact solutions, but the moment at which the wall shear reaches zero is reached too late.

## 1. Assumptions and notation

The MIE derivation uses the 2-D boundary-layer equations, so it inherits their assumptions: steady flow, incompressible ($\rho$ and $\nu$ constant), two-dimensional, high Reynolds number so that $\partial p/\partial y=0$ across the layer and the pressure gradient is $-\rho U_e\,\mathrm dU_e/\mathrm dx$ from Bernoulli at the edge ([[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#1. Pressure gradient terminology|3.3 §1]]). No assumption about the profile is made. For a turbulent layer $u$ and $\tau_w$ are time means. The Pohlhausen closure adds a laminar quartic profile, which is a modelling assumption rather than a consequence of the equations.

| Symbol | Meaning |
|---|---|
| $U_e(x)$, $U_e'$ | edge velocity from potential flow and its gradient $\mathrm dU_e/\mathrm dx$ |
| $\delta^*=\int_0^\infty(1-u/U_e)\,\mathrm dy$ | displacement thickness |
| $\theta=\int_0^\infty(u/U_e)(1-u/U_e)\,\mathrm dy$ | momentum thickness |
| $H=\delta^*/\theta$, $C_f=\tau_w/(\tfrac12\rho U_e^2)$ | shape factor and local skin-friction coefficient |
| $\delta$, $\eta=y/\delta$ | edge of the quartic (where $u=U_e$ exactly) and the Pohlhausen coordinate, $0\le\eta\le1$ |
| $\lambda=\dfrac{\delta^2}{\nu}U_e'$ | the course's non-dimensional pressure-gradient parameter |
| $Z=\theta^2/\nu$, $K=\dfrac{\theta^2}{\nu}U_e'$ | the growth variable and the momentum-thickness form of the pressure-gradient parameter (§6) |
| $g(\lambda)=\theta/\delta$, $h(\lambda)=\delta^*/\delta$, $a_1(\lambda)=\tau_w\delta/(\mu U_e)$ | the three profile integrals of the quartic (§5) |

The $\eta$ here runs from 0 to 1. It is not the Blasius and Falkner–Skan $\eta=y/\xi$ of [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions|3.2]], which runs to infinity. Schlichting and White write the course's $\lambda$ as $\Lambda$; Thwaites writes $K$ as $\lambda_\theta$ (or $m=-\lambda_\theta$), and Holstein and Bohlen, who introduced it, write $K$.

## 2. The momentum integral equation, line by line

### Continuity times the velocity defect

The two equations are continuity and $x$-momentum, with the pressure gradient written through the edge velocity:

$$
\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=0,\qquad(1)
$$

$$
u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}=U_eU_e'+\nu\frac{\partial^2u}{\partial y^2}.\qquad(2)
$$

Multiply (1) by $(u-U_e)$. The right-hand side is still zero:

$$
(u-U_e)\frac{\partial u}{\partial x}+(u-U_e)\frac{\partial v}{\partial y}=0.\qquad(3)
$$

Add (3) to the left of (2); adding zero changes nothing:

$$
u\frac{\partial u}{\partial x}+(u-U_e)\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}+(u-U_e)\frac{\partial v}{\partial y}=U_eU_e'+\nu\frac{\partial^2u}{\partial y^2}.\qquad(4)
$$

The multiplier $(u-U_e)$ is chosen because it vanishes at the edge of the layer. Every integrand built from it will then die away outside the layer, which keeps the integrals to $y=\infty$ finite.

### Rewriting two terms with the product rule

$U_e$ depends on $x$ only. Differentiating the defect in $x$:

$$
\frac{\partial}{\partial x}(u-U_e)=\frac{\partial u}{\partial x}-U_e' .
$$

Multiply by $u$:

$$
u\frac{\partial}{\partial x}(u-U_e)=u\frac{\partial u}{\partial x}-uU_e' .
$$

Rearrange for the first term of (4):

$$
u\frac{\partial u}{\partial x}=u\frac{\partial}{\partial x}(u-U_e)+uU_e' .
$$

Differentiating the defect in $y$, $\partial U_e/\partial y=0$:

$$
\frac{\partial}{\partial y}(u-U_e)=\frac{\partial u}{\partial y}.
$$

Multiply by $v$:

$$
v\frac{\partial u}{\partial y}=v\frac{\partial}{\partial y}(u-U_e).
$$

Substitute both into (4) and label the seven terms:

$$
\underbrace{u\frac{\partial(u-U_e)}{\partial x}}_{①}+\underbrace{uU_e'}_{②}+\underbrace{(u-U_e)\frac{\partial u}{\partial x}}_{③}+\underbrace{v\frac{\partial(u-U_e)}{\partial y}}_{④}+\underbrace{(u-U_e)\frac{\partial v}{\partial y}}_{⑤}=\underbrace{U_eU_e'}_{⑥}+\underbrace{\nu\frac{\partial^2u}{\partial y^2}}_{⑦}.
$$

### Grouping into exact derivatives

The product rule for the two factors $u$ and $(u-U_e)$ puts the derivative once on each:

$$
\frac{\partial}{\partial x}\left[u(u-U_e)\right]=u\frac{\partial(u-U_e)}{\partial x}+(u-U_e)\frac{\partial u}{\partial x}.
$$

The right-hand side is ① + ③ exactly. This is why the first term of (4) was rewritten: in its original form, $u\,\partial u/\partial x$, it would have paired with ③ only after an extra $uU_e'$ was split off, and that extra piece is term ②. Terms ② and ⑥ both carry $U_e'$; move ⑥ to the left and combine:

$$
uU_e'-U_eU_e'=(u-U_e)U_e' .
$$

Terms ④ and ⑤ are the product rule in $y$:

$$
v\frac{\partial(u-U_e)}{\partial y}+(u-U_e)\frac{\partial v}{\partial y}=\frac{\partial}{\partial y}\left[v(u-U_e)\right].
$$

Seven terms have become four:

$$
\frac{\partial}{\partial x}\left[u(u-U_e)\right]+(u-U_e)U_e'+\frac{\partial}{\partial y}\left[v(u-U_e)\right]=\nu\frac{\partial^2u}{\partial y^2}.
$$

### Dimensionless integrands

The integral thicknesses are defined with $u/U_e$, so write the first two terms in that form. Multiply and divide the first by $U_e^2$:

$$
u(u-U_e)=U_e^2\,\frac{u}{U_e}\left(\frac{u}{U_e}-1\right).
$$

Multiply and divide the second by $U_e$:

$$
(u-U_e)U_e'=\left(\frac{u}{U_e}-1\right)U_eU_e' .
$$

The equation to be integrated is

$$
\frac{\partial}{\partial x}\left[U_e^2\frac{u}{U_e}\left(\frac{u}{U_e}-1\right)\right]+\left(\frac{u}{U_e}-1\right)U_eU_e'+\frac{\partial}{\partial y}\left[v(u-U_e)\right]=\nu\frac{\partial^2u}{\partial y^2}.\qquad(5)
$$

### Integrating across the layer

Integrate every term of (5) over $0\le y<\infty$, calling the four integrals I, II, III and IV.

**Term I.** The limits $0$ and $\infty$ do not depend on $x$, and the integrand vanishes outside the layer because $u/U_e-1\to0$ there, so the integral converges and the $x$-derivative can be taken outside (Leibniz's rule with fixed limits):

$$
\text{I}=\int_0^\infty\frac{\partial}{\partial x}\left[U_e^2\frac{u}{U_e}\left(\frac{u}{U_e}-1\right)\right]\mathrm dy=\frac{\mathrm d}{\mathrm dx}\int_0^\infty U_e^2\frac{u}{U_e}\left(\frac{u}{U_e}-1\right)\mathrm dy .
$$

$U_e^2$ does not depend on $y$, so it leaves the integral:

$$
\text{I}=\frac{\mathrm d}{\mathrm dx}\left[U_e^2\int_0^\infty\frac{u}{U_e}\left(\frac{u}{U_e}-1\right)\mathrm dy\right].
$$

The integrand is minus the momentum-thickness integrand, $\frac{u}{U_e}(\frac{u}{U_e}-1)=-\frac{u}{U_e}(1-\frac{u}{U_e})$:

$$
\text{I}=-\frac{\mathrm d}{\mathrm dx}\left(U_e^2\theta\right).
$$

**Term II.** $U_eU_e'$ is a function of $x$ alone:

$$
\text{II}=U_eU_e'\int_0^\infty\left(\frac{u}{U_e}-1\right)\mathrm dy .
$$

The integrand is minus the displacement-thickness integrand:

$$
\text{II}=-U_eU_e'\,\delta^* .
$$

**Term III.** The integrand is an exact $y$-derivative, so the integral is the bracket evaluated at the limits:

$$
\text{III}=\big[v(u-U_e)\big]_{y=0}^{y\to\infty}.
$$

At the wall $v=0$. Far from the wall $u-U_e\to0$, but $v$ does not vanish there: continuity gives $v_e\ne0$ wherever the layer grows. The product still vanishes, because $u-U_e$ decays faster than any power of $y$ while $v$ grows at most linearly. So

$$
\text{III}=v_e(U_e-U_e)-0\cdot(0-U_e)=0 .
$$

**Term IV.** $\nu$ is constant (incompressible flow), so it leaves the integral, and the integral of a derivative is the bracket:

$$
\text{IV}=\nu\int_0^\infty\frac{\partial^2u}{\partial y^2}\,\mathrm dy=\nu\left[\frac{\partial u}{\partial y}\right]_{y=0}^{y\to\infty}.
$$

Outside the layer $u=U_e$ and the gradient is zero; at the wall $\nu\,\partial u/\partial y=\tau_w/\rho$ with $\tau_w=\mu\,\partial u/\partial y|_0$:

$$
\text{IV}=\nu\left(0-\left.\frac{\partial u}{\partial y}\right|_0\right)=-\frac{\tau_w}{\rho}.
$$

### Assembling the equation

Put I + II + III = IV:

$$
-\frac{\mathrm d}{\mathrm dx}\left(U_e^2\theta\right)-U_eU_e'\delta^*+0=-\frac{\tau_w}{\rho}.
$$

Change every sign:

$$
\frac{\mathrm d}{\mathrm dx}\left(U_e^2\theta\right)+U_eU_e'\delta^*=\frac{\tau_w}{\rho}.\qquad(6)
$$

Expand the first term by the product rule:

$$
U_e^2\frac{\mathrm d\theta}{\mathrm dx}+2U_eU_e'\theta+U_eU_e'\delta^*=\frac{\tau_w}{\rho}.
$$

Divide by $U_e^2$:

$$
\frac{\mathrm d\theta}{\mathrm dx}+\frac{2\theta+\delta^*}{U_e}U_e'=\frac{\tau_w}{\rho U_e^2}.
$$

Write $\delta^*=H\theta$ and take $\theta$ out of the bracket:

$$
\frac{\mathrm d\theta}{\mathrm dx}+(2+H)\frac{\theta}{U_e}U_e'=\frac{\tau_w}{\rho U_e^2}.
$$

Finally $\tau_w/(\rho U_e^2)=\tfrac12\,\tau_w/(\tfrac12\rho U_e^2)=C_f/2$:

$$
\boxed{\frac{\mathrm d\theta}{\mathrm dx}+(2+H)\frac{\theta}{U_e}\frac{\mathrm dU_e}{\mathrm dx}=\frac{C_f}{2}}
$$

Form (6) reads directly as a momentum balance per unit span on a slice of layer of length $\mathrm dx$. $\rho U_e^2\theta$ is the momentum deficit flux, the momentum the layer lacks compared with inviscid flow. It grows through wall friction, $\tau_w$, and through the pressure gradient acting on the displaced fluid, $-U_eU_e'\delta^*\rho=\delta^*\,\mathrm dp_e/\mathrm dx$. In an adverse gradient ($U_e'<0$) the second term adds to the growth; in a favourable one it can make $\theta$ shrink. The factor 2 in $(2+H)$ comes from differentiating $U_e^2$, the $H$ from the pressure force on $\delta^*$.

## 3. The flat-plate form and the drag

With zero pressure gradient, $U_e'=0$ and the middle term drops out:

$$
\frac{\mathrm d\theta}{\mathrm dx}=\frac{C_f}{2}.
$$

Integrated from the leading edge ($\theta=0$) to $x=L$, with $\tau_w=\rho U_e^2\,\mathrm d\theta/\mathrm dx$, the drag per unit span is

$$
D'=\int_0^L\tau_w\,\mathrm dx=\rho U_e^2\int_0^L\frac{\mathrm d\theta}{\mathrm dx}\,\mathrm dx=\rho U_e^2\,\theta(L),
$$

the control-volume result of [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures|3.1]]. The flat-plate form needs zero pressure gradient, not a flat surface; [[SESA3043 3.5 - Momentum Integral Equation#2. What it means|3.5 §2]] checks it against Blasius and uses it for the ship-fouling estimate.

The MIE has one equation and, with $U_e$ known, three unknowns: $\theta$, $H$ and $C_f$. The closure can be an assumed profile or an empirical correlation. Sections 4–5 build the assumed profile, and §6 couples it to the MIE.

## 4. The quartic and its five conditions

The profile is a fourth-order polynomial in $\eta=y/\delta$:

$$
\frac{u}{U_e}=a_0+a_1\eta+a_2\eta^2+a_3\eta^3+a_4\eta^4,\qquad0\le\eta\le1,
$$

with $u=U_e$ for $\eta>1$. Its first two derivatives are

$$
\frac{\mathrm d}{\mathrm d\eta}\left(\frac{u}{U_e}\right)=a_1+2a_2\eta+3a_3\eta^2+4a_4\eta^3,
$$

$$
\frac{\mathrm d^2}{\mathrm d\eta^2}\left(\frac{u}{U_e}\right)=2a_2+6a_3\eta+12a_4\eta^2 .
$$

Five coefficients need five conditions. Four are kinematic:

$$
\eta=0:\ a_0=0\qquad\text{(no slip)}
$$

$$
\eta=1:\ a_1+a_2+a_3+a_4=1\qquad\text{(matched edge velocity)}
$$

$$
\eta=1:\ a_1+2a_2+3a_3+4a_4=0\qquad\text{(zero slope at the edge)}
$$

$$
\eta=1:\ 2a_2+6a_3+12a_4=0\qquad\text{(zero curvature at the edge)}
$$

The fifth is the momentum equation itself, evaluated at the wall, and it is the only place the pressure gradient enters. At $y=0$, $u=v=0$, so both convective terms of (2) vanish:

$$
0=U_eU_e'+\nu\left.\frac{\partial^2u}{\partial y^2}\right|_{y=0}.
$$

With $u=U_e\cdot(u/U_e)$ and $y=\delta\eta$, each $y$-derivative brings $1/\delta$, and $U_e$ and $\delta$ do not depend on $y$:

$$
\frac{\partial^2u}{\partial y^2}=\frac{U_e}{\delta^2}\frac{\mathrm d^2}{\mathrm d\eta^2}\left(\frac{u}{U_e}\right).
$$

Substitute:

$$
0=U_eU_e'+\frac{\nu U_e}{\delta^2}\left.\frac{\mathrm d^2}{\mathrm d\eta^2}\left(\frac{u}{U_e}\right)\right|_{\eta=0}.
$$

Divide by $\nu U_e/\delta^2$:

$$
0=\frac{\delta^2}{\nu}U_e'+\left.\frac{\mathrm d^2}{\mathrm d\eta^2}\left(\frac{u}{U_e}\right)\right|_{\eta=0}.
$$

The first term is the definition of $\lambda$; the second, at $\eta=0$, is $2a_2$ (the $6a_3\eta$ and $12a_4\eta^2$ terms vanish):

$$
\lambda=-2a_2\quad\Rightarrow\quad a_2=-\frac\lambda2\qquad\text{(Eqs. 6–7)}
$$

Now eliminate. Subtract the edge-velocity condition from the edge-slope condition:

$$
(a_1+2a_2+3a_3+4a_4)-(a_1+a_2+a_3+a_4)=0-1
\quad\Rightarrow\quad a_2+2a_3+3a_4=-1 .\qquad(8)
$$

Halve the curvature condition:

$$
a_2+3a_3+6a_4=0 .\qquad(9)
$$

Subtract (8) from (9):

$$
a_3+3a_4=1 .\qquad(10)
$$

Put $3a_4=1-a_3$ from (10) into (8):

$$
a_2+2a_3+1-a_3=-1\quad\Rightarrow\quad a_2+a_3=-2 .\qquad(11)
$$

With $a_2=-\lambda/2$:

$$
a_3=-2+\frac\lambda2 .
$$

From (10):

$$
a_4=\frac{1-a_3}{3}=\frac{3-\lambda/2}{3}=1-\frac\lambda6 .\qquad(12)
$$

From the edge-velocity condition:

$$
a_1=1-a_2-a_3-a_4=1+\frac\lambda2+2-\frac\lambda2-1+\frac\lambda6=2+\frac\lambda6 .\qquad(13)
$$

Assemble the profile:

$$
\frac{u}{U_e}=\left(2+\frac\lambda6\right)\eta-\frac\lambda2\eta^2+\left(\frac\lambda2-2\right)\eta^3+\left(1-\frac\lambda6\right)\eta^4 .
$$

Collect the terms without $\lambda$ and the terms with $\lambda$:

$$
\frac{u}{U_e}=\left(2\eta-2\eta^3+\eta^4\right)+\frac\lambda6\left(\eta-3\eta^2+3\eta^3-\eta^4\right).
$$

The second bracket is $\eta(1-3\eta+3\eta^2-\eta^3)=\eta(1-\eta)^3$, so

$$
\boxed{\frac{u}{U_e}=F(\eta)+\lambda G(\eta),\qquad F=2\eta-2\eta^3+\eta^4,\qquad G=\frac{\eta}{6}(1-\eta)^3}
$$

$F$ is the zero-pressure-gradient profile and $\lambda G$ the correction for the pressure gradient. The wall slope is $a_1=2+\lambda/6$, which reaches zero at $\lambda=-12$: the quartic's separation profile. At the other end, $u/U_e-1=(1-\eta)^3[\lambda\eta/6-(1+\eta)]$ becomes positive near $\eta=1$ once $\lambda>12$, an overshoot above $U_e$, so the family is used for $-12\le\lambda\le12$ ([[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#Limits of the method|3.3, limits of the method]]).

## 5. Integral thicknesses, wall shear and shape factor as functions of λ

The results match [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#3. Integral properties as functions of λ|3.3 §3]], which lists them without the working. With $\mathrm dy=\delta\,\mathrm d\eta$ and $u=U_e$ beyond $\eta=1$, every integral stops at $\eta=1$. Five elementary integrals are needed. The ones containing $(1-\eta)^3$ use the beta-function result

$$
\int_0^1\eta^a(1-\eta)^3\,\mathrm d\eta=\frac{a!\,3!}{(a+4)!}=\frac{6}{(a+1)(a+2)(a+3)(a+4)} .
$$

$$
\int_0^1F\,\mathrm d\eta=\left[\eta^2-\frac{\eta^4}{2}+\frac{\eta^5}{5}\right]_0^1=1-\frac12+\frac15=\frac{7}{10}
$$

$$
\int_0^1G\,\mathrm d\eta=\frac16\cdot\frac{6}{2\cdot3\cdot4\cdot5}=\frac{1}{120}
$$

$F^2$ expands to six terms:

$$
F^2=4\eta^2-8\eta^4+4\eta^5+4\eta^6-4\eta^7+\eta^8 .
$$

Integrate term by term:

$$
\int_0^1F^2\,\mathrm d\eta=\frac43-\frac85+\frac46+\frac47-\frac48+\frac19=\frac{367}{630}.
$$

Write $FG=\frac16\left(2\eta^2-2\eta^4+\eta^5\right)(1-\eta)^3$ and use the beta result with $a=2$, 4 and 5:

$$
\int_0^1FG\,\mathrm d\eta=\frac16\left[2\cdot\frac{6}{3\cdot4\cdot5\cdot6}-2\cdot\frac{6}{5\cdot6\cdot7\cdot8}+\frac{6}{6\cdot7\cdot8\cdot9}\right]=\frac16\left[\frac{1}{30}-\frac{1}{140}+\frac{1}{504}\right]=\frac{71}{15120}.
$$

$G^2=\frac{1}{36}\eta^2(1-\eta)^6$, a beta integral with exponents 2 and 6:

$$
\int_0^1G^2\,\mathrm d\eta=\frac{1}{36}\cdot\frac{2!\,6!}{9!}=\frac{1}{36}\cdot\frac{1}{252}=\frac{1}{9072}.
$$

**Displacement thickness.**

$$
\frac{\delta^*}{\delta}=\int_0^1\left(1-F-\lambda G\right)\mathrm d\eta=1-\frac{7}{10}-\frac{\lambda}{120}
$$

$$
\boxed{h(\lambda)\equiv\frac{\delta^*}{\delta}=\frac{3}{10}-\frac{\lambda}{120}}
$$

**Momentum thickness.** Expand $\frac{u}{U_e}(1-\frac{u}{U_e})=(F+\lambda G)-(F+\lambda G)^2$:

$$
\frac\theta\delta=\int_0^1F\,\mathrm d\eta+\lambda\int_0^1G\,\mathrm d\eta-\int_0^1F^2\,\mathrm d\eta-2\lambda\int_0^1FG\,\mathrm d\eta-\lambda^2\int_0^1G^2\,\mathrm d\eta .
$$

Substitute the five integrals:

$$
\frac\theta\delta=\frac{7}{10}+\frac{\lambda}{120}-\frac{367}{630}-\frac{142\lambda}{15120}-\frac{\lambda^2}{9072}.
$$

Collect: $\frac{7}{10}-\frac{367}{630}=\frac{441-367}{630}=\frac{74}{630}=\frac{37}{315}$, and $\frac{1}{120}-\frac{142}{15120}=\frac{126-142}{15120}=-\frac{1}{945}$:

$$
\boxed{g(\lambda)\equiv\frac\theta\delta=\frac{37}{315}-\frac{\lambda}{945}-\frac{\lambda^2}{9072}}
$$

**Wall shear and skin friction.** $\tau_w=\mu\,\partial u/\partial y|_0=(\mu U_e/\delta)\,\mathrm d(u/U_e)/\mathrm d\eta|_0=(\mu U_e/\delta)\,a_1$:

$$
\boxed{a_1(\lambda)\equiv\frac{\tau_w\delta}{\mu U_e}=2+\frac\lambda6},\qquad C_f=\frac{\tau_w}{\tfrac12\rho U_e^2}=\frac{2\nu}{U_e\delta}\left(2+\frac\lambda6\right)=\frac{4+\lambda/3}{Re_\delta}.
$$

**Shape factor.**

$$
H(\lambda)=\frac{h}{g}=\frac{3/10-\lambda/120}{37/315-\lambda/945-\lambda^2/9072}.
$$

At $\lambda=0$, $H=\frac{3}{10}\cdot\frac{315}{37}=\frac{189}{74}=2.554$; at $\lambda=-12$, $h=0.4$, $g=0.11429$ and $H=3.500$. The exact flat-plate value is 2.59 and the exact Falkner–Skan separation value 4.03 ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#The table, recomputed|3.2]]), so the quartic is close on a flat plate and well short at separation: its separation profile is not empty enough near the wall. Panel (a) of the figure in §6 shows this directly.

## 6. Coupling λ to the momentum integral equation

3.5 stops at the closure problem and 3.3 at the quartic and $\lambda$. Joining them is the Kármán–Pohlhausen method, which goes beyond both; it is step 5 of the quick path in [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients|3.3]], the way to get $\delta(x)$.

### Why δ is the wrong variable to march

$\lambda$ contains $\delta$, so the obvious unknown is $\delta(x)$, or $Z_\delta=\delta^2/\nu$ so that $\lambda=Z_\delta U_e'$. Start from the MIE in dimensional form (the line before dividing by $U_e^2$ in §2), with $\tau_w/\rho=\nu U_ea_1/\delta$:

$$
U_e^2\frac{\mathrm d\theta}{\mathrm dx}+(2\theta+\delta^*)U_eU_e'=\frac{\nu U_ea_1}{\delta}.
$$

Multiply by $\delta/(\nu U_e)$, and use $\theta=g\delta$, $\delta^*=h\delta$:

$$
\frac{U_e\delta}{\nu}\frac{\mathrm d\theta}{\mathrm dx}+(2g+h)\frac{\delta^2U_e'}{\nu}=a_1 .
$$

The second term is $(2g+h)\lambda$. In the first, $\theta=\delta g(\lambda)$ depends on $x$ through both $\delta$ and $\lambda$:

$$
\frac{\mathrm d\theta}{\mathrm dx}=g\frac{\mathrm d\delta}{\mathrm dx}+\delta\,g'(\lambda)\frac{\mathrm d\lambda}{\mathrm dx}.
$$

Multiply by $U_e\delta/\nu$ and use $\delta\,\mathrm d\delta/\mathrm dx=\tfrac12\nu\,\mathrm dZ_\delta/\mathrm dx$ and $\delta^2/\nu=Z_\delta$:

$$
\frac{U_e\delta}{\nu}\frac{\mathrm d\theta}{\mathrm dx}=U_e\left[\frac g2\frac{\mathrm dZ_\delta}{\mathrm dx}+Z_\delta\,g'\frac{\mathrm d\lambda}{\mathrm dx}\right].
$$

$\lambda=Z_\delta U_e'$ is a product of two functions of $x$:

$$
\frac{\mathrm d\lambda}{\mathrm dx}=U_e'\frac{\mathrm dZ_\delta}{\mathrm dx}+Z_\delta U_e'' .
$$

Substitute, and use $Z_\delta U_e'=\lambda$:

$$
U_e\frac{\mathrm dZ_\delta}{\mathrm dx}\left[\frac g2+\lambda g'\right]+U_eZ_\delta^2U_e''g'+(2g+h)\lambda=a_1 .
$$

This is Pohlhausen's original form. It contains $U_e''$, the second derivative of a velocity distribution that usually comes from a measured or computed pressure distribution, which is noisy to differentiate twice. Marching the momentum thickness instead removes it.

### The momentum-thickness form

Start from the MIE:

$$
\frac{\mathrm d\theta}{\mathrm dx}+(2+H)\frac{\theta}{U_e}U_e'=\frac{C_f}{2}.
$$

Multiply every term by $U_e\theta/\nu$:

$$
\frac{U_e\theta}{\nu}\frac{\mathrm d\theta}{\mathrm dx}+(2+H)\frac{\theta^2U_e'}{\nu}=\frac{C_f}{2}\frac{U_e\theta}{\nu}.
$$

In the first term, $\theta\,\mathrm d\theta/\mathrm dx=\tfrac12\,\mathrm d(\theta^2)/\mathrm dx$; with $Z=\theta^2/\nu$:

$$
\frac{U_e\theta}{\nu}\frac{\mathrm d\theta}{\mathrm dx}=\frac{U_e}{2}\frac{\mathrm dZ}{\mathrm dx}.
$$

In the second term, define

$$
K\equiv\frac{\theta^2}{\nu}\frac{\mathrm dU_e}{\mathrm dx}=ZU_e' .
$$

On the right, $C_f/2=\tau_w/(\rho U_e^2)=\nu a_1/(U_e\delta)$ from §5, so

$$
\frac{C_f}{2}\frac{U_e\theta}{\nu}=a_1\frac{\theta}{\delta}=a_1g\equiv T .
$$

$T=\tau_w\theta/(\mu U_e)$ is the shear correlation of the closure. The MIE has become

$$
\frac{U_e}{2}\frac{\mathrm dZ}{\mathrm dx}+(2+H)K=T .
$$

Multiply by 2 and isolate the derivative:

$$
\boxed{U_e\frac{\mathrm dZ}{\mathrm dx}=F(K)\equiv2\left[T-(2+H)K\right]}
$$

Nothing in this equation is specific to Pohlhausen: any one-parameter closure that gives $H$ and $T$ as functions of $K$ produces the same equation. For the quartic, $\theta=g\delta$ links $K$ to $\lambda$:

$$
K=\frac{\theta^2}{\delta^2}\cdot\frac{\delta^2}{\nu}U_e'=g(\lambda)^2\lambda .
$$

Substitute $H=h/g$, $T=a_1g$ and $K=g^2\lambda$ into $F$:

$$
(2+H)K=\left(2+\frac hg\right)g^2\lambda=g(2g+h)\lambda,
$$

$$
\boxed{F=2g\left[a_1-(2g+h)\lambda\right]}
$$

with $g$, $h$ and $a_1$ the three polynomials of §5. Expanded, $F$ is a quintic in $\lambda$ (checked symbolically):

$$
F=\frac{148}{315}-\frac{9004}{99225}\lambda+\frac{1663}{595350}\lambda^2+\frac{11}{99225}\lambda^3-\frac{19}{6858432}\lambda^4-\frac{\lambda^5}{20575296}.
$$

$K(\lambda)=g^2\lambda$ increases monotonically over $-12\le\lambda\le12$, from $-0.1567$ to $0.0948$, so each $K$ in that range has one $\lambda$, and the march can carry $K$ and recover $\lambda$ by a one-dimensional root-find.

| $\lambda$ | $K$ | $H$ | $F(K)$ | $0.45-6K$ (Thwaites) | state |
|---:|---:|---:|---:|---:|---|
| −12 | −0.1567 | 3.500 | 1.724 | 1.390 | separation (quartic) |
| −6 | −0.0862 | 2.921 | 1.088 | 0.967 | adverse |
| 0 | 0 | 2.554 | 0.4698 | 0.450 | flat plate |
| 6 | 0.0689 | 2.333 | 0.0459 | 0.037 | favourable |
| 7.052 | 0.0770 | 2.308 | 0 | −0.012 | stagnation point |
| 12 | 0.0948 | 2.250 | −0.0948 | −0.119 | upper limit |

![[aa_deepdive_pohlhausen_family.png|900]]

Panel (b) is the whole method on one graph. Every exact similarity solution sits on it as a point: for Falkner–Skan flows $K=\beta\theta^{*2}$ and, from the similarity form of the MIE, $f''(0)=(1+\beta)\theta^*+\beta\eta^*$ ([[SESA3043 Deep Dive - Falkner-Skan Similarity, Full Derivation]]), $F=2\theta^{*2}(1-\beta)$. The exact points lie almost on a straight line, and Thwaites' correlation is that line, $F\approx0.45-6K$. The quartic's curve agrees with them on the favourable side and over-predicts $F$ increasingly in adverse gradients: the quartic thickens a decelerating layer too fast, yet its separation threshold, $K=-0.157$, lies far beyond the exact $K\approx-0.068$ to $-0.09$. Panel (a) shows why: matched at the same $\theta$, the quartic is close to Blasius and to Hiemenz stagnation flow but much fuller near the wall than the exact Falkner–Skan separation profile.

### Starting conditions

The growth equation is first order, so it needs one starting value.

- **Sharp leading edge with finite $U_e$** (a flat plate, or Howarth's flow of §8): $\theta=0$ at $x=0$, so $Z(0)=0$ and $K(0)=0$.
- **Stagnation point** ($U_e\to0$ as $x\to0$, as on a cylinder or an aerofoil nose): $\mathrm dZ/\mathrm dx=F(K)/U_e$ stays finite only if $F(K)\to0$ there, so the march starts at $F(K_0)=0$, which gives $\lambda_0=7.052$ and $K_0=0.0770$, with $Z(0)=K_0/U_e'(0)$.

The upper limit $\lambda=12$ is never reached in practice, because the stagnation start, the most favourable case, is at $\lambda=7.05$.

### Thwaites' closed form as the straight-line closure

Thwaites' integral ([[SESA3043 3.5 - Momentum Integral Equation#Thwaites' method (extension)|3.5 §3]]) follows from the boxed equation once $F$ is taken as linear in $K$. Set $F=0.45-6K$:

$$
U_e\frac{\mathrm dZ}{\mathrm dx}=0.45-6ZU_e' .
$$

Move the $Z$ term to the left:

$$
U_e\frac{\mathrm dZ}{\mathrm dx}+6U_e'Z=0.45 .
$$

Multiply by $U_e^5$:

$$
U_e^6\frac{\mathrm dZ}{\mathrm dx}+6U_e^5U_e'Z=0.45\,U_e^5 .
$$

The left side is the derivative of a product:

$$
\frac{\mathrm d}{\mathrm dx}\left(U_e^6Z\right)=0.45\,U_e^5 .
$$

Integrate from a point where $U_e^6Z=0$ (a sharp leading edge or a stagnation point):

$$
Z=\frac{\theta^2}{\nu}=\frac{0.45}{U_e^6}\int_0^xU_e^5\,\mathrm dx .
$$

The Pohlhausen $F$ is a quintic in $\lambda$, and $\lambda$ is itself a root of a cubic in $K$, so no integrating factor exists and the equation has to be marched numerically.

## 7. Two checks against exact solutions

### Flat plate

With $U_e'=0$, $K=0$, $\lambda=0$ and $F=148/315=0.46984$ for all $x$:

$$
U_e\frac{\mathrm dZ}{\mathrm dx}=\frac{148}{315}.
$$

Integrate from $Z(0)=0$:

$$
\frac{\theta^2}{\nu}=\frac{148}{315}\frac{x}{U_e}.
$$

Divide by $x^2$ and take the square root, with $Re_x=U_ex/\nu$:

$$
\frac\theta x=\sqrt{\frac{148}{315}}\,\frac{1}{\sqrt{Re_x}}=\frac{0.6854}{\sqrt{Re_x}}.
$$

Then $\delta=\theta/g(0)=\frac{315}{37}\theta$ and $\delta^*=\frac{3}{10}\delta$:

$$
\frac\delta x=\frac{5.836}{\sqrt{Re_x}},\qquad\frac{\delta^*}{x}=\frac{1.751}{\sqrt{Re_x}}.
$$

The friction is $C_f=4\nu/(U_e\delta)=4/(5.836\sqrt{Re_x})$:

$$
C_f=\frac{0.6854}{\sqrt{Re_x}},
$$

equal to $\theta/x$, as $\mathrm d\theta/\mathrm dx=C_f/2$ with $\theta\propto\sqrt x$ requires. Against Blasius ($\theta/x=C_f=0.664/\sqrt{Re_x}$, $\delta^*/x=1.721/\sqrt{Re_x}$, $H=2.59$), the quartic is 3.2 % high on $\theta$ and $C_f$, 1.7 % high on $\delta^*$ and 1.4 % low on $H$. The $\delta/x=5.84/\sqrt{Re_x}$ is the edge of the polynomial, not a 99 % thickness, so it is not comparable with Blasius' $4.91$.

### Stagnation point (the 3.2 cylinder problem)

For $U_e=cx$, $U_e'=c$ and $K=Zc$ is the same at every $x$ if $Z$ is constant. The starting condition $F(K_0)=0$ then holds everywhere, and

$$
\theta=\sqrt{\frac{K_0\nu}{c}}=\sqrt{0.07704}\,\sqrt{\frac\nu c}=0.2776\sqrt{\frac\nu c}.
$$

Falkner–Skan with $\beta=1$ gives $\xi=\sqrt{\nu/c}$ and $\theta=\theta^*\xi=0.2923\sqrt{\nu/c}$, so the quartic is 5.1 % low. The displacement thickness is closer: $\delta=\sqrt{\lambda_0\nu/c}=2.656\sqrt{\nu/c}$ and $\delta^*=h(7.052)\,\delta=0.6406\sqrt{\nu/c}$, against the exact $0.6479\sqrt{\nu/c}$ ($-1.1$ %). The wall shear, written as an equivalent $f''(0)=a_1/\sqrt{\lambda_0}=1.196$, is 3.0 % below the exact 1.2326.

> [!check] The 3.2 worked problem through Pohlhausen
> The cylinder of the 3.2 worked problem, $U_\infty=30$ m/s, $R=0.1$ m, $\nu=1.46\times10^{-5}$ m²/s, has $c=2U_\infty/R=600$ s⁻¹ and $\sqrt{\nu/c}=1.560\times10^{-4}$ m ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#7.1 δ99 near the front stagnation point of a cylinder|3.2 §7.1]]). Pohlhausen gives $\theta=0.0433$ mm and $\delta^*=0.0999$ mm; Falkner–Skan gives 0.0456 mm and 0.1011 mm. The polynomial edge sits at $\delta=0.414$ mm, outside the exact $\delta_{99}=0.371$ mm, as an edge where $u=U_e$ exactly must. *(Computed.)*

## 8. Worked case: separation in a linearly retarded flow

Howarth's flow (1938) is the standard test of a separation prediction: a flat plate whose edge velocity falls linearly from the leading edge,

$$
U_e=U_0\left(1-\frac xL\right),\qquad U_e'=-\frac{U_0}{L}.
$$

It is not a power law, so no similarity solution exists, and its exact separation point is known from numerical solutions of the boundary-layer equations: $x_s/L=0.1198$.

### Making the march universal

Use $\bar x=x/L$ and the dimensionless growth variable $\zeta=ZU_0/L=\theta^2U_0/(\nu L)=(\theta/L)^2Re_L$. Then

$$
\frac{\mathrm dZ}{\mathrm dx}=\frac{L}{U_0}\frac{\mathrm d\zeta}{\mathrm dx}=\frac{L}{U_0}\cdot\frac1L\frac{\mathrm d\zeta}{\mathrm d\bar x}=\frac{1}{U_0}\frac{\mathrm d\zeta}{\mathrm d\bar x}.
$$

Substitute into $U_e\,\mathrm dZ/\mathrm dx=F$ with $U_e=U_0(1-\bar x)$:

$$
U_0(1-\bar x)\cdot\frac{1}{U_0}\frac{\mathrm d\zeta}{\mathrm d\bar x}=F(K)
\quad\Rightarrow\quad
\frac{\mathrm d\zeta}{\mathrm d\bar x}=\frac{F(K)}{1-\bar x}.
$$

The pressure-gradient parameter is

$$
K=ZU_e'=\frac{L\zeta}{U_0}\cdot\left(-\frac{U_0}{L}\right)=-\zeta .
$$

The march is $\mathrm d\zeta/\mathrm d\bar x=F(-\zeta)/(1-\bar x)$ from $\zeta(0)=0$, and separation is at $\zeta=0.1567$. Neither $U_0$, $L$ nor $\nu$ appears: the separation point $x_s/L$ is the same at every Reynolds number, as [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#4. What λ means|3.3 §4]] argued for any geometrically similar laminar flow. Reynolds number sets only the size, $\theta/L=\sqrt{\zeta/Re_L}$.

### The march

Integrating numerically (RK45, tolerance $10^{-11}$, with $\lambda$ recovered from $K$ by Brent's method at each evaluation) gives the table below. The exact column is a finite-difference march of the full boundary-layer equations (implicit, 300 points across the layer), which reproduces the Blasius $0.332$ at the leading edge; Thwaites uses the closed form, $\zeta=0.075\left[(1-\bar x)^{-6}-1\right]$.

| $x/L$ | $\zeta$ | $K$ | $\lambda$ | $H$ | $\theta\sqrt{Re_L}/L$ Pohlhausen | Thwaites | exact |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 0.02 | 0.01016 | −0.0102 | −0.73 | 2.590 | 0.1008 | 0.0983 | 0.0971 |
| 0.04 | 0.02204 | −0.0220 | −1.56 | 2.634 | 0.1485 | 0.1443 | 0.1424 |
| 0.06 | 0.03604 | −0.0360 | −2.53 | 2.688 | 0.1899 | 0.1836 | 0.1812 |
| 0.08 | 0.05266 | −0.0527 | −3.67 | 2.758 | 0.2295 | 0.2207 | 0.2179 |
| 0.10 | 0.07257 | −0.0726 | −5.04 | 2.850 | 0.2694 | 0.2571 | 0.2543 |
| 0.12 | 0.09669 | −0.0967 | −6.76 | 2.980 | 0.3109 | 0.2941 | separated |
| 0.14 | 0.12639 | −0.1264 | −9.08 | 3.184 | 0.3555 | separated | separated |
| 0.1565 | 0.15673 | −0.1567 | −12.00 | 3.500 | 0.3959 | separated | separated |

The first row can be checked by hand. Near the leading edge $K\approx0$, so $F\approx0.4698$ and the march integrates directly:

$$
\zeta\approx0.4698\int_0^{\bar x}\frac{\mathrm ds}{1-s}=-0.4698\ln(1-\bar x)=-0.4698\ln0.98=0.0095 .
$$

The marched value, 0.0102, is 7 % higher because $F$ grows as $K$ turns negative.

Pohlhausen separates at

$$
\frac{x_s}{L}=0.1565,
$$

30 % downstream of the exact 0.1198. Thwaites, with $K=-0.09$ at separation, gives $(1-\bar x)^{-6}=1+0.09/0.075=2.2$, so $x_s/L=1-2.2^{-1/6}=0.1231$, 3 % late. The finite-difference march loses convergence at $x/L=0.1191$, where the wall shear collapses as $\sqrt{x_s-x}$ (Goldstein's singularity), and extrapolating $\tau_w^2$ to zero puts separation at 0.1194.

Two different errors are at work. The growth is good: at $x/L=0.10$ the Pohlhausen $\theta$ is 6 % above the exact value and Thwaites' 1 %. The separation criterion is bad: at the exact separation point the quartic still has $\lambda=-6.8$ and $H=2.98$, halfway to its own threshold. The layer is the right size but the wrong shape.

![[aa_deepdive_pohlhausen_separation.png|900]]

### In numbers

Take $U_0=10$ m/s, $L=0.5$ m and air with $\nu=1.5\times10^{-5}$ m²/s, so $U_0/L=20$ s⁻¹ and

$$
Re_L=\frac{10\times0.5}{1.5\times10^{-5}}=3.33\times10^5 ,
$$

low enough for the layer to stay laminar. The scale is $L/\sqrt{Re_L}=0.5/577.4=0.866$ mm. At the predicted separation point:

$$
x_s=0.1565\times0.5\ \text{m}=78.3\ \text{mm},
$$

$$
\theta_s=\sqrt{0.15673}\times0.866\ \text{mm}=0.343\ \text{mm},
$$

$$
\delta_s=\frac{\theta_s}{g(-12)}=\frac{0.343}{0.11429}=3.00\ \text{mm},\qquad\delta^*_s=0.4\,\delta_s=1.20\ \text{mm}.
$$

Check $\lambda$ from its definition:

$$
\lambda=\frac{\delta_s^2}{\nu}U_e'=\frac{(3.00\times10^{-3})^2}{1.5\times10^{-5}}\times(-20)=-12.0 .
$$

A flat plate at the same $x$ would have $\theta=0.235$ mm and $\delta=2.00$ mm: the adverse gradient has thickened the layer by half in under 8 cm while slowing the edge flow by only 16 %. The exact separation is at 59.9 mm and Thwaites predicts 61.6 mm.

### The cylinder in the same way

For the potential-flow cylinder, $U_e=2U_\infty\sin\phi$ with $x=R\phi$. With $\zeta=ZU_\infty/R$, the same steps give

$$
\frac{\mathrm d\zeta}{\mathrm d\phi}=\frac{F(K)}{2\sin\phi},\qquad K=2\zeta\cos\phi,
$$

started at the stagnation point with $K_0=0.0770$, $\zeta(0)=K_0/2$. Pohlhausen separates at $\phi=107.4^\circ$, Thwaites at $103.1^\circ$, and the exact solution for this $U_e$ at $104.5^\circ$ (Terrill, 1960; the finite-difference march here gives $104.3^\circ$). The real laminar separation on a cylinder is near $80^\circ$ ([[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#5. Laminar vs turbulent separation|3.3 §5]]), because the separated wake changes the pressure distribution over the rear of the cylinder, so the potential-flow $U_e$ fed to every method here is wrong where separation is decided. That error belongs to the input, not to the closure, and it is the reason for the viscous–inviscid coupling of [[SESA3043 3.6 - Viscous-Inviscid Interaction|3.6]].

> [!check] Numbers (computed)
> Flat plate: $F(0)=148/315=0.46984$, $\theta\sqrt{Re_x}/x=0.6854$, $\delta\sqrt{Re_x}/x=5.836$, $\delta^*\sqrt{Re_x}/x=1.751$. Stagnation: $\lambda_0=7.0523$, $K_0=0.07704$. Separation: $K(-12)=-0.15673$. Howarth: $x_s/L=0.15651$ (Pohlhausen), $0.12314$ (Thwaites), $0.1194$ (finite-difference march; accepted $0.1198$). Cylinder: $107.37^\circ$, $103.11^\circ$, $104.30^\circ$. Falkner–Skan points by shooting: $K=-0.0681$, $0$, $0.0446$, $0.0855$ and $F=0.8217$, $0.4410$, $0.2083$, $0$ for $\beta=-0.19884$, 0, 0.3, 1; $f''(0)=(1+\beta)\theta^*+\beta\eta^*$ holds to five decimals for each.

## 9. Where the method stands

The coupled method is a one-parameter closure: every profile it uses is one of a single family, so the shape at a station depends only on the local $\lambda$, not on the history of the layer. Real layers in a changing pressure gradient carry some memory, and near separation the true profile empties much faster than any quartic can. That is why $\theta$ comes out well and the separation point late. The quartic's separation shape factor, 3.5, is far below the exact 4.0, and its separation threshold $K=-0.157$ is more than twice the Falkner–Skan value, $-0.068$.

The method is also laminar only. The MIE holds for turbulent layers, but the quartic and $\lambda=-12$ do not; a turbulent layer needs its own closure, such as the log-law profile behind the ship-fouling chart of [[SESA3043 3.5 - Momentum Integral Equation#The method behind the chart|3.5 §4]]. Finally, the march takes $U_e(x)$ from potential flow and never feeds back the displacement effect. Near separation the boundary-layer solution becomes singular for a prescribed $U_e$, and the remedy is interaction with the outer flow ([[SESA3043 3.6 - Viscous-Inviscid Interaction|3.6]]), which is what XFOIL does for the coursework, with a Thwaites-type laminar closure.

Common mistakes:

- reading $\lambda=-12$ as an accurate separation point rather than a late estimate;
- forgetting the stagnation-point starting value: starting a nose region from $\theta=0$ makes $\mathrm dZ/\mathrm dx=F(0)/U_e$ infinite at $U_e=0$;
- marching $\delta$ and dropping the $U_e''$ term of Pohlhausen's original form;
- using the MIE's $(2+H)$ with the flat-plate $H=2.55$ throughout instead of $H(\lambda)$ at each station;
- confusing $\lambda=(\delta^2/\nu)U_e'$ with $K=(\theta^2/\nu)U_e'$: at separation they are $-12$ and $-0.157$.

## Links

- Parent: [[SESA3043 Advanced Aeronautics Hub]]
- Lecture notes: [[SESA3043 3.5 - Momentum Integral Equation]] (the MIE, the closure problem, Thwaites and the ship chart) · [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]] (the quartic, $\lambda$ and separation physics)
- Related deep dive: [[SESA3043 Deep Dive - Falkner-Skan Similarity, Full Derivation]] (the similarity form of the MIE and the exact profiles used as benchmarks)
- Used next: [[SESA3043 3.6 - Viscous-Inviscid Interaction]] (integral boundary-layer methods coupled to a panel method)
- Concepts: [[Momentum Integral Equation]] · [[Pohlhausen Method]] · [[Boundary Layer Separation]] · [[Displacement and Momentum Thickness]] · [[Blasius and Falkner-Skan Similarity Solutions]] · [[Prandtl Boundary-Layer Equations]]
- Year 2: [[SESA2022 T2 - Boundary Layers]]
- Formulae: [[SESA3043 Formula Sheet]] · Worked: [[SESA3043 Ch3 Revision Questions - Worked Solutions]]

## Sources

- `CH3-5 Momentum Integral Eqn(1).pdf`, slides 5–39 (the derivation and the closure problem) and slide 46 (key formula); `Ch3_Notes_Momentum Integral Eq.pdf`, Eqs. (1)–(8).
- `CH3-3 Pohlhausen.pdf`, slides 8–27 and 38; `Ch3_Notes_Pohlhausen.pdf`, Eqs. (1)–(14).
- `12 November 2026 at 13_50_20.txt` (BL6): the MIE, ll. 104–296; flat plate, ll. 298–304; closure and Thwaites, ll. 335–351.
- `05 November 2026 at 13_59_07.txt` (BL3): the quartic and $\lambda$, ll. 219–310; separation at $\lambda=-12$ set as homework, ll. 340–345. `06 November 2026 at 14_52_55.txt` (BL4): the recap and the same homework, ll. 100–107.
- Extensions not in the course material: the coupling of §6 (Pohlhausen 1921; the $\theta$ form is Holstein and Bohlen's, 1940), Thwaites (1949), Howarth's retarded flow (1938) and Terrill's cylinder solution (1960), as presented in F. M. White & J. Majdalani, *Viscous Fluid Flow*, 4th ed. (2022), and H. Schlichting & K. Gersten, *Boundary-Layer Theory*.
- Checks: the coefficients, the five integrals, $g$, $h$, $F(\lambda)$ and $K(\lambda)$ were verified symbolically (sympy); the Falkner–Skan points by shooting; the marches with `scipy.integrate.solve_ivp`; the exact Howarth and cylinder separation points with an implicit finite-difference march of the boundary-layer equations.
- Figures: `generate_aa_deepdive_figures.py` (`fig_pohlhausen_family`, `fig_pohlhausen_separation`).

## Self-study tasks

The derivations were set in the lectures; the marches are suggested, not lecturer-set.

### Core

- [ ] **(BL6, ll. 75–78; revision 3.5 Q1–Q3)** Follow the MIE derivation term by term, saying why Term III vanishes although $v_e\ne0$. SESA6087 students derive it unaided. → [[#2. The momentum integral equation, line by line]]
- [ ] **(BL3, ll. 301–310)** Solve the five conditions for $a_0,\dots,a_4$ and assemble $F+\lambda G$. → [[#4. The quartic and its five conditions]]
- [ ] **(BL3, ll. 340–345; BL4, ll. 100–107; revision 3.3 Q5)** Show that the quartic separates at $\lambda=-12$. → [[#4. The quartic and its five conditions]]
- [ ] (suggested, not lecturer-set) Derive $\theta/\delta=\frac{37}{315}-\frac{\lambda}{945}-\frac{\lambda^2}{9072}$ by hand from the five elementary integrals. → [[#5. Integral thicknesses, wall shear and shape factor as functions of λ]]

### Further practice

- [ ] (suggested, not lecturer-set) Derive $U_e\,\mathrm dZ/\mathrm dx=2[T-(2+H)K]$ from the MIE, then $F=2g[a_1-(2g+h)\lambda]$, and recover the flat-plate $\theta/x=0.685/\sqrt{Re_x}$ and the stagnation start $\lambda_0=7.05$. → [[#6. Coupling λ to the momentum integral equation]] · [[#7. Two checks against exact solutions]]
- [ ] (suggested, not lecturer-set) Show that a linear $F=0.45-6K$ integrates to Thwaites' formula, and use it to find $x_s/L=0.123$ for $U_e=U_0(1-x/L)$. → [[#Thwaites' closed form as the straight-line closure]] · [[#8. Worked case: separation in a linearly retarded flow]]

## Transcript and slide slips

> [!warning] Slips that touch this derivation
> Where: [[#4. The quartic and its five conditions]] and [[#2. The momentum integral equation, line by line]].
>
> | Source | As given | Correct |
> |---|---|---|
> | `Ch3_Notes_Pohlhausen.pdf`, p. 2 | the $\lambda$ bracket expanded as $\eta(1-3\eta+3\eta^2+\eta^3)$ | $\eta(1-3\eta+3\eta^2-\eta^3)=\eta(1-\eta)^3$; the boxed $G$ is right |
> | BL3, l. 300 | *"lambda is equal to minus a2"* | $\lambda=-2a_2$ (said correctly at l. 307) |
> | BL6, ll. 288, 290 | *"the shear factor"* | the shape factor $H=\delta^*/\theta$ |
> | BL6, l. 275 | *"is equal to power, wall shear stress over density"* | $\tau_w/\rho$ |
>
> All four are also listed in [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#Transcript and slide slips|3.3]] and [[SESA3043 3.5 - Momentum Integral Equation#Transcript and slide slips|3.5]]. None changes a result.
