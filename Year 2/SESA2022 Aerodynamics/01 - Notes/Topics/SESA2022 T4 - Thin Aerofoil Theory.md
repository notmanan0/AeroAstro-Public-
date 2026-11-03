---
title: "SESA2022 T4 - Thin Aerofoil Theory"
module: "SESA2022 Aerodynamics"
type: topic
stream: "Topic 4: Thin Aerofoil Theory"
order: 4
tags:
  - sesa2022
  - thin-aerofoil-theory
  - aerofoils
aliases: ["Thin Aerofoil Theory", "TAT"]
date: 2026-09-23
status: lectured
coverage: "Lectures 28 Oct – 5 Nov 2025 (six lectures)"
parent: ["[[SESA2022 Aerodynamics Hub]]"]
prerequisites: ["[[SESA2022 T3 - Potential Flow]]", "[[Kutta-Joukowski Theorem]]"]
next_topics: ["[[SESA2022 T5 - Finite Wing Theory]]"]
key_concepts: ["[[Vortex Sheet]]", "[[Kutta Condition]]", "[[Glauert Integrals]]", "[[Aerodynamic Centre and Centre of Pressure]]", "[[Kelvin's Circulation Theorem]]", "[[Aerofoil Stall]]", "[[Trailing-Edge Flap in Thin Aerofoil Theory]]"]
tutorial_sheets: ["[[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-10-28.txt … 2025-11-05.txt", "02 - Sources/Airfoils and Wings/TAT.txt (earlier-year recording)"]
---

# SESA2022 T4 - Thin Aerofoil Theory

> [!abstract] Summary
> Thin aerofoil theory replaces a thin, lightly cambered aerofoil at small $\alpha$ by a vortex sheet $\gamma(\xi)$ on its chord line, then enforces flow tangency to the camber line and the Kutta condition $\gamma(TE)=0$. Writing $\gamma$ as a Fourier series in $\theta$ gives closed-form results, $c_l = 2\pi(\alpha-\alpha_{L=0}) = \pi(2A_0+A_1)$ and $c_{m,c/4} = \frac\pi4(A_2-A_1)$. Within its assumptions the lift slope is $2\pi$ per radian, the quarter chord is the aerodynamic centre, and camber only shifts $\alpha_{L=0}$ and adds a constant pitching moment (nose-down for positive camber).

> [!summary]- Exam use: quick path
> - **Use it when:** you are given a camber line $z(x)$ (typically $\propto x(1-x)$) or a trailing-edge flap and asked for $c_l$, $\alpha_{L=0}$, $c_{m,c/4}$, $c_{m,le}$, $x_{cp}$, ideal $\alpha$ or the loading $\Delta C_p$. These are the two question types in the past papers (28 Oct–5 Nov lectures: 31 Oct, ll. 1–2, 405–412).
> - **Assumptions:** inviscid, incompressible, irrotational; thin aerofoil with small camber; small $\alpha$ in radians; unit chord unless stated; $\eta$ (flap) positive trailing edge down.
> - **Method:** 1. Write $dz/dx$ and transform with $x = \tfrac c2(1-\cos\theta_0)$. 2. $A_0 = \alpha-\frac1\pi\int_0^\pi\frac{dz}{dx}d\theta_0$, $A_n = \frac2\pi\int_0^\pi\frac{dz}{dx}\cos n\theta_0\,d\theta_0$. 3. $c_l = \pi(2A_0+A_1)$; check $dc_l/d\alpha = 2\pi$. 4. $c_{m,c/4} = \frac\pi4(A_2-A_1)$, $c_{m,le} = -\frac{c_l}{4}+c_{m,c/4}$. 5. $x_{cp}/c = \frac14-c_{m,c/4}/c_l$, $\alpha_{L=0}$ from $c_l = 0$.
> - **Common mistakes:** working in degrees inside $2\pi\alpha$; mixing up $\cos\theta_0 = 1-2x/c$ (LE at $\theta_0 = 0$) when finding the hinge angle $\theta_h$.
> - **Exam format:** you need not reproduce the whole theory (28 Oct, ll. 43–48); the Glauert integrals are given (29 Oct, ll. 489–493). The full NACA 4-digit camber line is too long for a sit-down exam (31 Oct, ll. 61–66).
> - Revision-lecture advice (7 Jan revision, ll. 124–284): you will have to evaluate Fourier coefficients. Only two question types appear, a simple differentiable camber line or a trailing-edge flap; there are no quartic or NACA camber lines in an exam. The orthogonality integrals are on the formula sheet. *"The only place you're likely to go wrong is in converting from degrees to radians"* (l. 175). $c_m$ is usually small and negative for positive camber; reflex sections differ. Worked example: [[SESA2022 Exam 2024-25 Solutions|2024-25]] Q3 ($\epsilon = 0.0894$ in the lecture, $0.0893$ unrounded).
> - **Practise:** [[#Worked example 1: NACA 6500 (lecture, 31 Oct and 4 Nov)]] · [[#Worked example 2: 20% flap effectiveness (lecture, 31 Oct)]] · [[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]]

[[SESA2022 T3 - Potential Flow]] showed that lift needs circulation, $L' = \rho V_\infty\Gamma$, but left $\Gamma$ undetermined. Thin aerofoil theory finds it.

Air goes faster over the top of a lifting aerofoil than under it. A sheet of tiny vortices laid along the chord does exactly that: each clockwise vortex speeds the flow above it and slows the flow below it, so the jump in speed across the sheet is its strength $\gamma$, and through Bernoulli the pressure jump is $\rho V_\infty\gamma$. The question becomes: how much vorticity, and where?

Two rules fix it. First, the aerofoil is solid: at every point the sheet must turn the oncoming flow so that it slides along the camber line, no faster and no slower (tangency). Second, real air cannot whip round a sharp trailing edge, so the flow leaves the trailing edge smoothly and the speed jump there is zero (Kutta). With those two rules the vortex distribution, and so the lift, is unique. Out of the algebra drop three surprises the Wright brothers could not have guessed (4 Nov, ll. 285–295): every thin aerofoil has the same lift slope, $2\pi$ per radian; camber only shifts the lift curve sideways; and there is one point, the quarter chord, about which the pitching moment does not change with $\alpha$.

---

## 1. Aerofoil basics

Nomenclature (28 Oct lecture):
- Leading and trailing edge; the chord line joins them, with length $c$.
- **Camber line**: the locus of points midway between the upper and lower surfaces. Camber is its maximum distance from the chord line.
- **Thickness**: measured normal to the chord line.
- Angle of attack $\alpha$: the angle between the relative wind and the chord line.
- Notation: lower-case $c_l$, $c_m$ for 2D sections, capitals for 3D wings (28 Oct, ll. 126–130). Past papers write the camber line as capital $Z$; Anderson uses lower-case $z$ (29 Oct, ll. 63–66).

**NACA 4-digit (e.g. 2412)**: max camber $m = 0.02c$ at $p = 0.4c$, thickness $0.12c$. The 28 Oct lecture shows a NACA 6502: 6% camber at mid-chord, 2% thick.

**NACA 5-digit (e.g. 23012)**: design $C_l = 2\times3/20 = 0.3$; max camber at $30/2 = 15\%c$; 12% thickness.

**NACA 6-series (e.g. 65-218)**: series 6; minimum pressure at $0.5c$ for the symmetric section; design $C_l=0.2$; 18% thickness.

$$
c_l = \frac{L'}{q_\infty c},\quad q_\infty = \tfrac12\rho_\infty V_\infty^2,\quad Re = \frac{\rho V_\infty c}{\mu},\quad M=\frac{V_\infty}{a_\infty},\quad a_0 = \frac{dc_l}{d\alpha}
$$

Pressure plots usually show $-C_p$ upwards to highlight the suction peak.

### NACA 4-digit camber line with p = 0.5

The NACA 4-digit camber line forward of the maximum is $z/c = \frac{m}{p^2}\left[2p\frac xc-\left(\frac xc\right)^2\right]$. With $p = 0.5$ the aft formula is identical, and $m/p^2 = 4m$:

$$
\frac zc = 4m\left[\frac xc-\left(\frac xc\right)^2\right] = 4m\,\frac xc\left(1-\frac xc\right).
$$

For NACA 6500 ($m = 0.06$): $z = 0.24x(1-x)$ (unit chord). *"I found at least three past exam questions that started with that's the camber line"* (31 Oct, ll. 55–62).

## 2. Three key concepts (28 Oct lecture)

### Linearised pressure coefficient

Assumptions: small perturbation $v\ll V_\infty$ along the freestream.

Bernoulli between the freestream and a point where the speed is $V_\infty+v$:

$$
p+\tfrac12\rho(V_\infty+v)^2 = p_\infty+\tfrac12\rho V_\infty^2.
$$

Expand:

$$
p-p_\infty = -\rho V_\infty v-\tfrac12\rho v^2.
$$

Drop the second-order term and divide by $\tfrac12\rho V_\infty^2$:

$$
\boxed{C_p \approx -\frac{2v}{V_\infty}}
$$

(28 Oct, l. 284.)

### Vortex sheet and loading

A vortex sheet of strength $\gamma(s)$ per unit length induces a tangential velocity $+\gamma/2$ just above it and $-\gamma/2$ just below it (for clockwise $\gamma>0$), so

$$
\gamma(s) = V_{upper}-V_{lower},\qquad \Gamma = \int_{LE}^{TE}\gamma\,ds,\qquad dV_\theta = -\frac{\gamma\,ds}{2\pi r}.
$$

With $v_u = +\gamma/2$ and $v_l = -\gamma/2$ in the linearised $C_p$:

$$
\Delta C_p = C_{p,l}-C_{p,u} = -\frac{2v_l}{V_\infty}+\frac{2v_u}{V_\infty} = \frac{2\gamma}{V_\infty}.
$$

Integrating the loading along the chord ($ds\approx dx$):

$$
c_l = \frac1c\int_0^c\Delta C_p\,dx = \frac{2}{cV_\infty}\int_0^c\gamma\,dx
$$

$$
c_{m,le} = -\frac{1}{c^2}\int_0^c x\Delta C_p\,dx = -\frac{2}{c^2V_\infty}\int_0^c x\gamma\,dx
$$

The minus sign makes nose-up positive: upward loading at $x>0$ gives a nose-down moment about the leading edge. The first result is Kutta–Joukowski in coefficient form: $L' = \rho V_\infty\int\gamma\,dx = \rho V_\infty\Gamma$. See [[Vortex Sheet]].

### Kutta condition

Two cases for the flow at a sharp trailing edge (28 Oct, ll. 338–380). Potential flow alone allows the flow to go round the edge from below, with infinite speed there; real (viscous) flow does not. Instead it leaves smoothly. At a finite-angle trailing edge both surface velocities must then vanish (a stagnation point); at a cusped edge they are equal. Either way, Bernoulli with the same pressure $p_a$ on both sides of the edge gives $V_1 = V_2$, so

$$
\boxed{\gamma(TE) = V_1-V_2 = 0}
$$

Why the flow cannot go round the edge: a real boundary layer would have to climb from the very low pressure at the sharp edge into a steep adverse pressure gradient, and it separates instead (28 Oct, ll. 342–350). Too little circulation puts the rear stagnation point on the upper surface, too much puts it on the lower surface; only one value is "just right" (ll. 351–358).

This is how viscosity is accounted for without modelling it: it fixes the circulation and hence the lift. With curved trailing edges (some turbine blades) it is not obvious how to apply it, and CFD is needed (28 Oct, ll. 454–457). See [[Kutta Condition]].

> [!warning] Bogus explanations of lift (28 Oct, ll. 413–452)
> Equal transit time ("the air over the top must arrive at the trailing edge at the same time") is completely wrong: experiments show the upper flow arrives first. "It is just Newton's law" is true but useless: Newton's law only says the pressure below exceeds the pressure above, not by how much. Bernoulli is correct, provided you do not apply it across the rotational boundary layer, but it does not tell you the velocities. A real theory needs the Kutta condition to fix $\Gamma$.
>
> The module introduction gave a streamline-curvature picture instead: curved streamlines need a pressure gradient towards their centre of curvature, $\partial p/\partial n = \rho V^2/R$, so the flow curving over the upper surface sits at low pressure (L1, ll. 330–365; L4, ll. 330–400). That is correct physics, but it was introduced as *"not discovered until 2022"* (L1, l. 326); the curvature explanation is long established (e.g. Babinsky, *Physics Education*, 2003). It is also descriptive: like the others, it does not give the value of the lift.

## 3. The fundamental equation (29 Oct lecture)

![[tat_vortex_sheet_model.png|900]]

### Linearised boundary condition

The flow must be tangent to the camber line $z(x)$. The total velocity is the freestream $(V_\infty\cos\alpha, V_\infty\sin\alpha)$ plus the induced velocity $w'$ from the sheet. Tangency:

$$
\frac{dz}{dx} = \frac{V_\infty\sin\alpha+w'}{V_\infty\cos\alpha+u'}.
$$

For small $\alpha$, small camber and $u', w'\ll V_\infty$: $\sin\alpha\approx\alpha$, $\cos\alpha\approx1$, $u'$ negligible:

$$
\frac{dz}{dx} = \alpha+\frac{w'}{V_\infty}\quad\Rightarrow\quad w'(x) = V_\infty\left(\frac{dz}{dx}-\alpha\right).
$$

Because the camber is small, the sheet can be placed on the chord and the condition applied there (thin-aerofoil approximation).

### Induced velocity from the sheet

An element $\gamma(\xi)\,d\xi$ at $\xi$ is a point vortex. At $x$ on the chord, distance $x-\xi$ away, it induces a purely vertical velocity. With clockwise $\gamma>0$, a point downstream ($x>\xi$) sees downward velocity:

$$
dw(x) = -\frac{\gamma(\xi)\,d\xi}{2\pi(x-\xi)}.
$$

Integrate along the chord:

$$
w'(x) = -\frac{1}{2\pi}\int_0^c\frac{\gamma(\xi)\,d\xi}{x-\xi}.
$$

Equate with the boundary condition and multiply by $-1$:

$$
\boxed{\frac{1}{2\pi}\int_0^c\frac{\gamma(\xi)\,d\xi}{x-\xi} = V_\infty\left(\alpha-\frac{dz}{dx}\right)}
$$

This is the fundamental equation of thin aerofoil theory: an integral equation for $\gamma$, subject to $\gamma(c) = 0$.

### Transformation to θ

![[tat_theta_transform.png|640]]

$$
\xi = \frac c2(1-\cos\theta),\qquad x = \frac c2(1-\cos\theta_0),\qquad d\xi = \frac c2\sin\theta\,d\theta
$$

The LE is at $\theta = 0$ and the TE at $\theta=\pi$. The denominator becomes $x-\xi = \frac c2(\cos\theta-\cos\theta_0)$, so the $c/2$ factors cancel:

$$
\frac{1}{2\pi}\int_0^\pi\frac{\gamma(\theta)\sin\theta\,d\theta}{\cos\theta-\cos\theta_0} = V_\infty\left(\alpha-\frac{dz}{dx}\right)
$$

The force integrals transform the same way. With $dx = \frac c2\sin\theta\,d\theta$ and $x = \frac c2(1-\cos\theta)$:

$$
c_l = \frac{2}{cV_\infty}\int_0^\pi\gamma\,\frac c2\sin\theta\,d\theta = \frac{1}{V_\infty}\int_0^\pi\gamma\sin\theta\,d\theta
$$

$$
c_{m,le} = -\frac{2}{c^2V_\infty}\int_0^\pi\frac c2(1-\cos\theta)\,\gamma\,\frac c2\sin\theta\,d\theta = -\frac{1}{2V_\infty}\int_0^\pi\gamma\sin\theta(1-\cos\theta)\,d\theta
$$

### Improper integrals (lecture example)

The integrand blows up at $\theta = \theta_0$, so the integrals are principal values: cut out a symmetric gap $\pm\epsilon$ round the singularity and let $\epsilon\to0$ (29 Oct, ll. 375–457). The lecture's warm-up, for $0<x_0<1$:

$$
I = \lim_{\epsilon\to0}\left[-\int_0^{x_0-\epsilon}\frac{dx}{x_0-x}+\int_{x_0+\epsilon}^1\frac{dx}{x-x_0}\right]
$$

Integrate each part:

$$
I = \lim_{\epsilon\to0}\Big[\ln(x_0-x)\Big]_0^{x_0-\epsilon}+\Big[\ln(x-x_0)\Big]_{x_0+\epsilon}^1 = \lim_{\epsilon\to0}\left[\ln\epsilon-\ln x_0+\ln(1-x_0)-\ln\epsilon\right]
$$

The $\ln\epsilon$ terms cancel, leaving a finite answer:

$$
I = \ln\frac{1-x_0}{x_0}.
$$

*"Don't panic when you see an improper integral"* (29 Oct, ll. 624–626).

### Glauert integrals

These are singular at $\theta=\theta_0$ and taken as principal values. You will be given them in an exam (29 Oct, ll. 485–493):

$$
\text{(G1)}\;\int_0^\pi\frac{\cos n\theta\,d\theta}{\cos\theta-\cos\theta_0} = \frac{\pi\sin n\theta_0}{\sin\theta_0},\qquad \text{(G2)}\;\int_0^\pi\frac{\sin n\theta\sin\theta\,d\theta}{\cos\theta-\cos\theta_0} = -\pi\cos n\theta_0
$$

> [!note]- Derivation of the Glauert integrals (not lectured; for completeness)
> Write $I_n = \mathrm{PV}\!\int_0^\pi\frac{\cos n\theta}{\cos\theta-\cos\theta_0}d\theta$ and $c_0 = \cos\theta_0$.
>
> **$I_0 = 0$.** Substitute $t = \tan(\theta/2)$: $d\theta = \frac{2\,dt}{1+t^2}$, $\cos\theta = \frac{1-t^2}{1+t^2}$, so
>
> $$\cos\theta-c_0 = \frac{(1-c_0)-(1+c_0)t^2}{1+t^2},\qquad I_0 = \frac{2}{1+c_0}\,\mathrm{PV}\!\int_0^\infty\frac{dt}{k^2-t^2},\quad k = \tan\frac{\theta_0}{2}.$$
>
> The antiderivative is $\frac{1}{2k}\ln\left|\frac{k+t}{k-t}\right|$, which equals $0$ at $t=0$ and tends to $0$ as $t\to\infty$, so $I_0 = 0$.
>
> **$I_1 = \pi$.** Write $\cos\theta = (\cos\theta-c_0)+c_0$:
>
> $$I_1 = \int_0^\pi d\theta+c_0I_0 = \pi.$$
>
> **Recursion.** $\cos(n+1)\theta+\cos(n-1)\theta = 2\cos\theta\cos n\theta = 2(\cos\theta-c_0)\cos n\theta+2c_0\cos n\theta$. Integrate and divide:
>
> $$I_{n+1}+I_{n-1} = 2\int_0^\pi\cos n\theta\,d\theta+2c_0I_n = 2c_0I_n\quad(n\ge1).$$
>
> $I_n = \pi\sin n\theta_0/\sin\theta_0$ satisfies $I_0 = 0$, $I_1 = \pi$ and the same recursion, because $\sin(n+1)\theta_0+\sin(n-1)\theta_0 = 2\cos\theta_0\sin n\theta_0$. That is G1.
>
> **G2.** $\sin n\theta\sin\theta = \tfrac12[\cos(n-1)\theta-\cos(n+1)\theta]$, so
>
> $$\text{G2} = \tfrac12(I_{n-1}-I_{n+1}) = \frac{\pi}{2\sin\theta_0}\left[\sin(n-1)\theta_0-\sin(n+1)\theta_0\right] = \frac{\pi}{2\sin\theta_0}(-2\cos n\theta_0\sin\theta_0) = -\pi\cos n\theta_0.$$

## 4. Symmetric aerofoil (flat plate)

With $dz/dx=0$ the equation is $\frac{1}{2\pi}\int_0^\pi\frac{\gamma\sin\theta\,d\theta}{\cos\theta-\cos\theta_0} = V_\infty\alpha$. Integral equations like this are solved by proposing a solution and checking it, not by a procedure (29 Oct, ll. 510–527). The proposal:

$$
\boxed{\gamma(\theta) = 2V_\infty\alpha\frac{1+\cos\theta}{\sin\theta}}
$$

**Check with G1.** $\gamma\sin\theta = 2V_\infty\alpha(1+\cos\theta)$, so the left-hand side is

$$
\frac{2V_\infty\alpha}{2\pi}\left[\int_0^\pi\frac{d\theta}{\cos\theta-\cos\theta_0}+\int_0^\pi\frac{\cos\theta\,d\theta}{\cos\theta-\cos\theta_0}\right] = \frac{V_\infty\alpha}{\pi}[0+\pi] = V_\infty\alpha \;✔
$$

**Kutta condition.** At $\theta=\pi$ the expression is $0/0$. L'Hôpital: $\lim\frac{1+\cos\theta}{\sin\theta} = \lim\frac{-\sin\theta}{\cos\theta} = \frac{0}{-1} = 0$, so $\gamma(\pi)=0$ ✔.

**Lift:**

$$
c_l = \frac{1}{V_\infty}\int_0^\pi 2V_\infty\alpha(1+\cos\theta)\,d\theta = 2\alpha[\theta+\sin\theta]_0^\pi = 2\pi\alpha\qquad\boxed{\frac{dc_l}{d\alpha} = 2\pi}
$$

**Loading in $x$.** With $1-\cos\theta = 2x/c$ and $1+\cos\theta = 2(1-x/c)$, $\frac{1+\cos\theta}{\sin\theta} = \sqrt{\frac{1+\cos\theta}{1-\cos\theta}} = \sqrt{\frac{c-x}{x}}$:

$$
\gamma(x) = 2V_\infty\alpha\sqrt{\frac{c-x}{x}}
$$

The leading-edge suction peak is infinite at the LE (a real aerofoil's rounded nose makes it finite), and the loading is zero at the TE. The adverse pressure gradient behind the peak drives [[Boundary Layer Separation]] and laminar separation bubbles; the separated shear layer has an inflection point, is very unstable and usually triggers transition (30 Oct, ll. 146–185; §8).

> [!check] How good is $2\pi$?
> Real sections give about $5.8$–$6.0$ per radian, even at 12% thickness (30 Oct, ll. 108–121); XFLR5 gives $6.1$ for a 12% section including boundary layers (5 Nov, ll. 733–739). *"One of the first big successes of the theory."* TAT is good to at least 6% camber and roughly 10% thickness, wherever $\cos$ of the surface angle is close to 1 (31 Oct, ll. 239–248).

**Moment.** $c_{m,le} = -\frac{1}{2V_\infty}\int_0^\pi2V_\infty\alpha(1+\cos\theta)(1-\cos\theta)\,d\theta = -\alpha\int_0^\pi\sin^2\theta\,d\theta = -\frac{\pi\alpha}{2} = -\frac{c_l}{4}$. So the lift acts at the quarter chord: $x_{cp} = c/4$ for a flat plate.

## 5. General cambered aerofoil (30 Oct lecture)

Propose a flat-plate term plus a Fourier sine series. Every term vanishes at the TE ($\sin n\pi = 0$), so the Kutta condition holds automatically:

$$
\boxed{\gamma(\theta) = 2V_\infty\left(A_0\frac{1+\cos\theta}{\sin\theta}+\sum_{n=1}^\infty A_n\sin n\theta\right)}
$$

### Substitution

Multiply by $\sin\theta$ and put into the left-hand side of the fundamental equation:

$$
\frac{V_\infty}{\pi}\left[A_0\int_0^\pi\frac{1+\cos\theta}{\cos\theta-\cos\theta_0}d\theta+\sum_{n=1}^\infty A_n\int_0^\pi\frac{\sin n\theta\sin\theta}{\cos\theta-\cos\theta_0}d\theta\right].
$$

G1 with $n = 0$ and $n = 1$ gives $0+\pi$ for the first integral; G2 gives $-\pi\cos n\theta_0$ for the second:

$$
\frac{V_\infty}{\pi}\left[A_0\pi-\sum_{n=1}^\infty A_n\pi\cos n\theta_0\right] = V_\infty\left(\alpha-\frac{dz}{dx}\right).
$$

Divide by $V_\infty$ (30 Oct, ll. 305–312):

$$
A_0 - \sum_{n=1}^\infty A_n\cos n\theta_0 = \alpha - \frac{dz}{dx}
$$

### Fourier coefficients by orthogonality

Rearranged, $\frac{dz}{dx} = (\alpha-A_0)+\sum A_n\cos n\theta_0$: a Fourier cosine series for the camber slope.

**$A_0$.** Integrate both sides over $0\le\theta_0\le\pi$; every $\int_0^\pi\cos n\theta_0\,d\theta_0 = 0$:

$$
\int_0^\pi\frac{dz}{dx}d\theta_0 = (\alpha-A_0)\pi\quad\Rightarrow\quad A_0 = \alpha-\frac1\pi\int_0^\pi\frac{dz}{dx}d\theta_0.
$$

**$A_m$.** Multiply by $\cos m\theta_0$ and integrate; only $n = m$ survives, with $\int_0^\pi\cos^2m\theta_0\,d\theta_0 = \pi/2$ (*"Pi by 2 is the only number you need to remember"*, 31 Oct, l. 117):

$$
\int_0^\pi\frac{dz}{dx}\cos m\theta_0\,d\theta_0 = A_m\frac\pi2\quad\Rightarrow\quad A_m = \frac2\pi\int_0^\pi\frac{dz}{dx}\cos m\theta_0\,d\theta_0.
$$

$$
\boxed{A_0 = \alpha-\frac1\pi\int_0^\pi\frac{dz}{dx}d\theta_0,\qquad A_n = \frac2\pi\int_0^\pi\frac{dz}{dx}\cos n\theta_0\,d\theta_0\;(n\ge1)}
$$

Only $A_0$ depends on $\alpha$. For a smooth camber line the $A_n$ decay to zero; for a NACA 4-digit section they can be found numerically by the trapezoidal rule, as in the SESA2029 coursework code (31 Oct, ll. 14–29).

### Lift

$$
c_l = \frac{1}{V_\infty}\int_0^\pi\gamma\sin\theta\,d\theta = 2\left[A_0\int_0^\pi(1+\cos\theta)\,d\theta+\sum_{n=1}^\infty A_n\int_0^\pi\sin n\theta\sin\theta\,d\theta\right]
$$

$\int_0^\pi(1+\cos\theta)\,d\theta = \pi$; $\int_0^\pi\sin n\theta\sin\theta\,d\theta = \pi/2$ for $n = 1$ and $0$ otherwise:

$$
c_l = 2\left[A_0\pi+A_1\frac\pi2\right] = \pi(2A_0+A_1)
$$

Substitute $A_0$ and $A_1$:

$$
c_l = 2\pi\alpha+2\int_0^\pi\frac{dz}{dx}(\cos\theta_0-1)\,d\theta_0 = 2\pi\left[\alpha-\frac1\pi\int_0^\pi\frac{dz}{dx}(1-\cos\theta_0)\,d\theta_0\right]
$$

$$
\boxed{c_l = 2\pi(\alpha-\alpha_{L=0}),\qquad \alpha_{L=0} = \frac1\pi\int_0^\pi\frac{dz}{dx}(1-\cos\theta_0)\,d\theta_0}
$$

The lift slope is still $2\pi$; positive camber makes $\alpha_{L=0}$ negative and shifts the curve left.

![[tat_lift_curve.png|520]]

### Ideal angle of attack

At the ideal (design) angle, the flow joins the leading edge smoothly: $\gamma(0) = 0$, a "Kutta condition at the leading edge" (31 Oct, ll. 160–195). Every $A_n\sin n\theta$ term is zero at $\theta = 0$, so only the $A_0$ term can be singular there. So we need $A_0 = 0$:

$$
\alpha_{ideal} = \frac1\pi\int_0^\pi\frac{dz}{dx}\,d\theta_0
$$

No leading-edge loading means no suction peak and so no leading-edge separation bubble: a design condition.

## 6. Moments, aerodynamic centre, centre of pressure (4 Nov lecture)

### Leading-edge moment

Substitute the series into $c_{m,le} = -\frac{1}{2V_\infty}\int_0^\pi\gamma\sin\theta(1-\cos\theta)\,d\theta$:

$$
c_{m,le} = -\left[A_0\int_0^\pi(1+\cos\theta)(1-\cos\theta)\,d\theta+\sum A_n\int_0^\pi\sin n\theta\sin\theta(1-\cos\theta)\,d\theta\right]
$$

Evaluate each integral:
- $(1+\cos\theta)(1-\cos\theta) = \sin^2\theta$, and $\int_0^\pi\sin^2\theta\,d\theta = \pi/2$.
- $\int_0^\pi\sin n\theta\sin\theta\,d\theta = \pi/2$ for $n = 1$, else $0$.
- $\sin\theta\cos\theta = \tfrac12\sin2\theta$, so $\int_0^\pi\sin n\theta\sin\theta\cos\theta\,d\theta = \pi/4$ for $n=2$, else $0$.

$$
c_{m,le} = -\left[A_0\frac\pi2+A_1\frac\pi2-A_2\frac\pi4\right] = -\frac\pi2\left(A_0+A_1-\frac{A_2}{2}\right)
$$

Use $c_l = \pi(2A_0+A_1)$, i.e. $\frac\pi2A_0 = \frac{c_l}{4}-\frac\pi4A_1$:

$$
c_{m,le} = -\left[\frac{c_l}{4}+\frac\pi4(A_1-A_2)\right]
$$

### Moment about the quarter chord

The same loading can be represented as lift plus moment at the LE, or lift plus moment at $c/4$ (4 Nov, ll. 176–200). Taking moments about the LE (nose-up positive), lift at $c/4$ gives a nose-down contribution:

$$
M'_{LE} = M'_{c/4}-\frac c4L'\quad\Rightarrow\quad c_{m,le} = c_{m,c/4}-\frac{c_l}{4}.
$$

So

$$
\boxed{c_{m,c/4} = c_{m,le}+\frac{c_l}{4} = \frac\pi4(A_2-A_1)}\quad\text{independent of }\alpha
$$

- The aerodynamic centre is the point where $dc_m/d\alpha = 0$. In thin-aerofoil theory it is the quarter chord, for any camber line (4 Nov, ll. 257–286).
- Symmetric aerofoil: $c_{m,c/4}=0$. Positive camber: $A_1>A_2$ typically, so $c_{m,c/4}<0$ (nose-down).

### Centre of pressure

The point about which the moment is zero: $M'_{LE} = -x_{cp}L'$, so

$$
\frac{x_{cp}}{c} = -\frac{c_{m,le}}{c_l} = \frac14\left[1+\frac{\pi(A_1-A_2)}{c_l}\right] = \frac14-\frac{c_{m,c/4}}{c_l}
$$

For a flat plate $x_{cp} = c/4$. For a cambered aerofoil it moves with $\alpha$, towards $\pm\infty$ as $c_l\to0$, *"so the centre of pressure doesn't even have to be on the wing"* (4 Nov, ll. 321–331). That is why the AC, not the CP, is the reference point. See [[Aerodynamic Centre and Centre of Pressure]].

![[tat_loading.png|560]]

### Worked example 1: NACA 6500 (lecture, 31 Oct and 4 Nov)

$z = 0.24x(1-x)$, unit chord.

1. $\frac{dz}{dx} = 0.24(1-2x)$. With $x = \tfrac12(1-\cos\theta_0)$: $1-2x = \cos\theta_0$, so $\frac{dz}{dx} = 0.24\cos\theta_0$.
2. $A_0 = \alpha-\frac{0.24}{\pi}\int_0^\pi\cos\theta_0\,d\theta_0 = \alpha$.
3. $A_1 = \frac{2}{\pi}(0.24)\int_0^\pi\cos^2\theta_0\,d\theta_0 = \frac2\pi(0.24)\frac\pi2 = 0.24$; $A_{n\ge2} = 0$ by orthogonality.
4. $c_l = \pi(2\alpha+0.24)$; $dc_l/d\alpha = 2\pi$ ✔.
5. $\alpha_{L=0} = -0.12$ rad $= -6.88^\circ$.
6. $\alpha_{ideal} = \frac{0.24}{\pi}\int_0^\pi\cos\theta_0\,d\theta_0 = 0$.
7. $c_{m,c/4} = \frac\pi4(0-0.24) = -0.06\pi = -0.188$ (*"your key number for this aerofoil"*, 4 Nov, ll. 400–404).
8. $\dfrac{x_{cp}}{c} = \dfrac14\left(1+\dfrac{0.24}{2\alpha+0.24}\right)$: at $\alpha=0$, $x_{cp} = 0.5c$ (the loading is symmetric about mid-chord); as $\alpha\to\alpha_{L=0}$, $x_{cp}\to\pm\infty$.
9. Loading: $\Delta C_p = \frac{2\gamma}{V_\infty} = 4\alpha\dfrac{1+\cos\theta}{\sin\theta}+0.96\sin\theta$. At $\alpha = 0$ only the $\sin\theta$ hump remains: no LE loading.

> [!check] Python check
> Trapezoidal integration of $dz/dx = 0.24\cos\theta_0$ on 2001 points: $A_0-\alpha = 0$, $A_1 = 0.2400$, $A_2 = 0$ to $10^{-6}$; $c_{m,c/4} = -0.1885$ ✔.

> [!check] Lecture XFOIL comparison (5 Nov, ll. 420–525; 31 Oct, ll. 204–236)
>
> | Quantity | TAT (NACA 6500) | XFOIL, NACA 6510, $Re = 3\times10^6$ |
> |---|---|---|
> | $\alpha_{L=0}$ | $-6.9^\circ$ | $-6.80^\circ$ |
> | $c_l$ at $\alpha = 0$ | $0.754$ | $0.779$ |
> | $c_{m,c/4}$ | $-0.188$ | $-0.180$ ($\alpha_{L=0}$), $-0.186$ ($0^\circ$), $-0.183$ ($4^\circ$, $c_l = 1.2$) |
>
> A 10%-thick, 6%-cambered section, viscous, still within a few per cent; $c_{m,c/4}$ barely moves while $c_l$ goes from 0 to 1.2. For NACA 6502 at $\alpha_{ideal}$, XFOIL gives $\Delta C_p\approx0.95$ at mid-chord against $4A_1 = 0.96$.

### Parabolic camber z/c = ε (x/c)(1 − x/c) (about eight past papers)

Same algebra with $0.24\to\epsilon$: $A_0=\alpha$, $A_1=\epsilon$, $A_{n\ge2}=0$; $c_l = 2\pi\alpha+\pi\epsilon$, $\alpha_{L=0} = -\epsilon/2$, $c_{m,c/4} = -\pi\epsilon/4$. Maximum camber $z_{max}/c = \epsilon/4$ at $x=c/2$.

## 7. Trailing-edge flaps (31 Oct lecture)

Model a plain flap as a kink in the camber line. Unit chord, hinge at $x_h = 1-E$ (flap-chord ratio $E$), deflection $\eta$ positive trailing edge down, $\alpha$ measured from the chord ahead of the hinge:

$$
\frac{dz}{dx} = \begin{cases}0 & 0<\theta_0<\theta_h\\ -\eta & \theta_h<\theta_0<\pi\end{cases},\qquad \cos\theta_h = 1-2x_h = 2E-1
$$

### General hinge position

$$
A_0 = \alpha-\frac1\pi\int_{\theta_h}^\pi(-\eta)\,d\theta_0 = \alpha+\frac\eta\pi(\pi-\theta_h)
$$

$$
A_n = \frac2\pi\int_{\theta_h}^\pi(-\eta)\cos n\theta_0\,d\theta_0 = -\frac{2\eta}{\pi}\left[\frac{\sin n\theta_0}{n}\right]_{\theta_h}^\pi = \frac{2\eta}{n\pi}\sin n\theta_h
$$

So $A_1 = \frac{2\eta}{\pi}\sin\theta_h$ and $A_2 = \frac{\eta}{\pi}\sin2\theta_h$.

**Lift:**

$$
c_l = \pi(2A_0+A_1) = 2\pi\alpha+2\eta(\pi-\theta_h)+2\eta\sin\theta_h
$$

$$
\boxed{\frac{\partial c_l}{\partial\eta} = 2(\pi-\theta_h+\sin\theta_h)}\qquad(\text{flap effectiveness, an aerodynamic derivative})
$$

**Moment:**

$$
c_{m,c/4} = \frac\pi4(A_2-A_1) = \frac\eta4(\sin2\theta_h-2\sin\theta_h) = \frac\eta2\sin\theta_h(\cos\theta_h-1)
$$

**Zero-lift angle:** $\alpha_{L=0} = -\frac{\eta}{\pi}(\pi-\theta_h+\sin\theta_h)$.

![[tat_flap_effectiveness.png|700]]

### Worked example 2: 20% flap effectiveness (lecture, 31 Oct)

*"What's the flap effectiveness if E equals 0.2?"* (31 Oct, ll. 375–404).

1. $\cos\theta_h = 2(0.2)-1 = -0.6$, so $\theta_h = 2.214$ rad, $\sin\theta_h = 0.8$.
2. $\partial c_l/\partial\eta = 2(\pi-2.214+0.8) = 3.455$ per radian.
3. $\partial c_{m,c/4}/\partial\eta = \tfrac12(0.8)(-0.6-1) = -0.640$.
4. $\partial\alpha_{L=0}/\partial\eta = -3.455/(2\pi) = -0.550$.

Check: $\partial c_l/\partial\alpha = 2\pi$ still (*"If we didn't get 2 pi alpha, we would be worried"*, 31 Oct, ll. 393–394). The same derivative models elevators, rudders and ailerons in [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability|T6]] (31 Oct, ll. 276–286).

### 25% flap

$x_h = 0.75$: $\cos\theta_h = -0.5$, $\theta_h = 2\pi/3$, $\sin\theta_h = \sqrt3/2$:

$$
A_0 = \alpha+\frac{\eta}{3},\quad A_1 = \frac{\sqrt3}{\pi}\eta,\quad A_2 = -\frac{\sqrt3}{2\pi}\eta
$$

$$
c_l = 2\pi\alpha + \left(\frac{2\pi}{3}+\sqrt3\right)\eta = 2\pi\alpha+3.826\,\eta,\qquad c_{m,c/4} = -\frac{3\sqrt3}{8}\eta = -0.6495\,\eta,\qquad \alpha_{L=0} = -0.609\,\eta
$$

A small flap is surprisingly effective: a 20 % flap gives 3.455/6.283 = 55 % of the lift per radian of rotating the whole aerofoil. Deflecting the trailing edge changes the circulation needed to satisfy the Kutta condition, and that changes the loading over the whole chord, not just over the flap.

Full derivation and other hinge positions: [[Trailing-Edge Flap in Thin Aerofoil Theory]]. Hinge moments of the elevator ($b_1$, $b_2$) used in [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]] come from the same model.

### High-lift devices (31 Oct, ll. 414–464)

$V_{stall} = \sqrt{2W/(\rho_\infty S C_{L,max})}$.
- TE flaps make $\alpha_{L=0}$ more negative and raise $C_{L,max}$. Small settings for take-off (less drag, faster acceleration), large for landing (more $C_{L,max}$, and drag is welcome).
- LE slats do not change $\alpha_{L=0}$. They create a fresh, thin boundary layer on the main element, which resists separation better, so the stall angle and $C_{L,max}$ rise.
- Multi-element flaps effectively add camber.

## 8. Real flow effects (28 Oct and 5 Nov lectures)

### Kelvin's circulation theorem and the starting vortex

[[Kelvin's Circulation Theorem]] says that in inviscid flow with conservative body forces, the circulation round a closed curve moving with the fluid is constant, $D\Gamma/Dt = 0$ (28 Oct, ll. 458–500). Start an aerofoil from rest: a curve enclosing the aerofoil and its wake has $\Gamma = 0$ before and after. When the aerofoil develops circulation $\Gamma$, a starting vortex of $-\Gamma$ is shed from the trailing edge, so the total stays zero.

- A sudden start sheds a discrete vortex; a gradual one sheds a sheet of vorticity that rolls up (5 Nov, ll. 107–111). In a viscous flow the circulation slowly dissipates (ll. 77–79).
- Every change of lift sheds one: a manoeuvre, an elevator movement on the tailplane, or starting a wind tunnel, where it circulates round the circuit (5 Nov, ll. 134–150).
- Wake turbulence behind a heavy aircraft is mainly its trailing (tip) vortices, plus the wing wake and engine jets (5 Nov, ll. 113–129; [[SESA2022 T5 - Finite Wing Theory|T5]]), not chiefly the starting vortex as first suggested (28 Oct, ll. 495–499).

### Stall types

See [[Aerofoil Stall]].

| Type | Typical aerofoils | Behaviour |
|---|---|---|
| Trailing-edge stall | Thick (e.g. NACA 4421) | Separation creeps forward from the TE and $c_l$ drops gradually |
| Leading-edge stall | Moderately thin, $t/c \lesssim 15\%$ (e.g. NACA 4412) | Sudden separation from the LE over the whole upper surface, with a sharp drop in $c_l$ |
| Thin-aerofoil stall | Flat plate, very thin sections | Separation bubble even at low $\alpha$ that grows and moves downstream; lower $c_{l,max}$, gentle stall |

(5 Nov, ll. 170–330.) The laminar separation bubble links back to [[SESA2022 T2 - Boundary Layers#8. Pressure gradients and separation|T2 §8]].

### Panel methods

Cover both surfaces with panels, each carrying a constant-strength vortex (and, in a source–vortex panel method, a source) sheet. Apply tangency at the centre of every panel, with the full $V_\infty\sin(\beta-\alpha)$ normal component (no small angles, since thickness is now included), and the Kutta condition, giving a linear system $\mathbf{A}\mathbf{x} = \mathbf{B}$ for the strengths; $\mathbf A$ holds geometric influence coefficients (5 Nov, ll. 336–375). Lift follows either by integrating the pressures or from $L' = \rho V_\infty\Gamma$ (ll. 382–388). Used in industry since the 1960s. XFOIL and XFLR5 add viscous boundary-layer coupling, so they predict profile drag, separation bubbles and stall. More in [[SESA3043 2.3 - Panel Methods]] and [[SESA3043 3.6 - Viscous-Inviscid Interaction]].

## Assumptions and summary

- Incompressible, irrotational, inviscid (so drag $=0$), small $\alpha$, small thickness and camber; thickness does not affect lift or moment at this order.
- $L' = \rho V_\infty\Gamma$, $\Delta p = \rho V_\infty\gamma$, $\Gamma = \int\gamma\,ds$, $\gamma(TE)=0$.
- $c_l = 2\pi(\alpha-\alpha_{L=0}) = \pi(2A_0+A_1)$, $dc_l/d\alpha = 2\pi$ per radian.
- $c_{m,c/4} = \frac\pi4(A_2-A_1)$. The quarter chord is the aerodynamic centre; the centre of pressure moves with $\alpha$.
- Real aerofoils: $dc_l/d\alpha$ slightly below $2\pi$ (viscous decambering), AC slightly ahead of or behind $c/4$, and stall, none of which TAT predicts.

### What XFOIL shows (5 Nov demonstration)

- **Why XFOIL, not CFD, for aerofoils:** the coupled boundary-layer method has a physically based $e^N$ transition model; RANS CFD usually does not, and rarely resolves small separation bubbles (5 Nov, ll. 403–417, 675–679).
- Reading $c_f$ and $H$ (NACA 6510, $Re = 3\times10^6$): laminar $c_f$ low, a jump at transition, then turbulent $c_f$ falling in the adverse gradient; $H$ about 2.6–2.8 laminar, about 1.4 turbulent, rising again towards the TE. $c_f<0$ means separation (ll. 529–566).
- Laminar separation bubble (NACA 2412, $Re = 3\times10^5$, $5^\circ$): $c_f$ dips below zero, laminar $H$ exceeds 4, transition, reattachment, turbulent $H\approx1.5$. At $10^\circ$ the bubble moves to the LE; at $15^\circ$ a flat spot in $C_p$ near the TE marks turbulent separation at $0.65c$, at $17^\circ$ at $0.40c$: trailing-edge stall (ll. 594–672).
- **Separation ≠ transition.** Separation is reverse flow; transition is the growth of disturbances into turbulence. Transition often follows laminar separation, and the turbulent mixing then reattaches the layer (ll. 691–720).
- **Design use:** keep the flow laminar over about 60% of the chord, then trip it with an engineered bubble so the turbulent layer resists separation (human-powered aircraft, gliders; next, laminar transonic wings) (ll. 572–593).
- Convergence trouble near transition: reinitialise the boundary layer (ll. 500–511).

## Transcript slips (28 Oct – 5 Nov)

> [!warning] Slips in `SESA2022 Lecture 2025-10-28.txt` to `2025-11-05.txt` (Whisper transcripts)
> Recurring transcriptions: *"Glowatt"*/*"Glauer"* = Glauert, *"Kutajkowski"* = Kutta–Joukowski, *"Kutter"*/*"Kutte"* = Kutta, *"Canberra"*/*"Camberline"* = camber line, *"cord"* = chord, *"aerodynamic sensor"* = aerodynamic centre, *"central pressure"* = centre of pressure, *"venerofoil"* = thin aerofoil.
>
> | Line | Said | Correct |
> |---|---|---|
> | 4 Nov, l. 355 | the NACA 6500 zero-lift angle *"came out at minus 0.02 radians"* | $-0.12$ rad ($-6.9^\circ$), as found on 31 Oct, ll. 146–150 and repeated at 4 Nov, l. 392 |
> | 4 Nov, l. 283 | *"that is the aerodynamic sensor"* | aerodynamic centre |
> | 31 Oct, l. 168 | *"the equivalent of a Kutter condition at the leading edge"* | Kutta-like condition $\gamma(0) = 0$ at the LE (ideal $\alpha$) |
> | 30 Oct, l. 272 | *"an example of the Glowatt integral with n equals 0"* | Glauert integral G1 with $n = 0$, which is zero |
> | 4 Nov, l. 187 | *"a nose-up pitching moment from the quarter-cord pitching moment"* | drawn positive (nose-up) by convention; for positive camber $c_{m,c/4}$ is actually negative (nose-down), as stated at ll. 296–299 |
> | 28 Oct, ll. 224–225 | NACA 6502 *"It's got 5% camber"* | 6% camber, at 50% chord (the 5 is the position) |
> | 28 Oct, ll. 495–499 | the hazard behind a heavy aircraft is *"all the starting vortices"* | mainly the trailing vortices, as the lecturer says on 5 Nov, ll. 113–129 ([[#8. Real flow effects (28 Oct and 5 Nov lectures)]]) |
> | 31 Oct, ll. 322, 337 | the flap integral runs *"from theta f up to 1"* | from $\theta_f$ up to $\pi$ |
> | 4 Nov, ll. 110–112 | the first term *"reduces to a0 times the integral of 1 minus cosine theta"* | the integral of $1-\cos^2\theta$ ($= \sin^2\theta$), giving $\pi/2$ as computed at ll. 122–135 |
> | 5 Nov, l. 429 | TAT gives an ideal lift coefficient of *"0.765"* | $0.754$ ($= 0.24\pi$), as said at l. 489 |
> | L1, l. 326 | the streamline-curvature explanation of lift *"was not discovered until 2022"* | it is long established (e.g. Babinsky 2003) ([[#Kutta condition]]) |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| thin aerofoil theory | thin airfoil theory (US) | throughout | Slides use "airfoil" in the title |
| camber line $z$ (past papers $Z$) | mean line, mean camber line | 29 Oct, ll. 63–66 | |
| vortex sheet strength $\gamma$ | circulation density, bound vorticity per unit length | 28 Oct | |
| Fourier coefficients $A_0, A_n$ | Glauert coefficients | 30 Oct; 31 Oct, l. 9 | |
| Glauert integrals | Glauert's integral | 29 Oct, ll. 470–493 | |
| zero-lift angle $\alpha_{L=0}$ ($\alpha_0$ in T6) | angle of zero lift | 30 Oct, l. 586; 31 Oct, l. 150 | T6 writes $\alpha_0$ |
| ideal angle of attack | design angle, optimum angle, Theodorsen angle | 31 Oct, ll. 170–195 | |
| flap effectiveness $\partial c_l/\partial\eta$ | flap lift derivative, $c_{l_\delta}$, $a_2$ in T6 | 31 Oct, ll. 275–405 | "aerodynamic derivative" (l. 277) |
| aerodynamic centre | neutral point of the section, AC | 4 Nov, ll. 257–286 | |
| centre of pressure | CP | 4 Nov, ll. 302–335 | |
| trailing-edge, leading-edge, thin-aerofoil stall | | 5 Nov, ll. 170–330 | |

## Links

- Parent: [[SESA2022 Aerodynamics Hub]] · Previous: [[SESA2022 T3 - Potential Flow]] · Next: [[SESA2022 T5 - Finite Wing Theory]]
- Concepts: [[Vortex Sheet]] · [[Kutta Condition]] · [[Glauert Integrals]] · [[Aerodynamic Centre and Centre of Pressure]] · [[Kelvin's Circulation Theorem]] · [[Aerofoil Stall]] · [[Trailing-Edge Flap in Thin Aerofoil Theory]]
- Problems: [[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]] · Formulae: [[SESA2022 Formula Sheet]]
- Maths: Fourier series and orthogonality (MATH2048). Numerical TAT code: SESA2029 Digital Aerospace Methods coursework.
- Feeds: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]] (tailplane $a_1$, $a_2$, hinge moments and $c_{m,0}$).
- Feeds into (Year 3):
  - [[SESA3043 2.2 - Lumped Vortex Method]]: one vortex at $c/4$ and a collocation point at $3c/4$ reproduce $c_l = 2\pi\alpha$, a discrete version of this note.
  - [[SESA3043 2.1 - Complex Functions and Conformal Mapping]]: the exact (Joukowski) aerofoil, which confirms TAT for thin sections.

## Sources

- `02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf` (slides 1–63), `Examples4(1).pdf`.
- 2025-26 transcripts in `02 - Sources/Lectures/`, cited by date: `SESA2022 Lecture 2025-10-28.txt` (concepts, Kutta, Kelvin), `2025-10-29.txt` (fundamental equation, flat plate), `2025-10-30.txt` (camber, Fourier series), `2025-10-31.txt` (examples: NACA 6500, flap), `2025-11-04.txt` (moments, AC, CP), `2025-11-05.txt` (stall, panel methods, XFOIL). Line numbers refer to these files. Revision: `SESA2022 Lecture 2026-01-07.txt`.
- All six 2025-26 lectures above were read in full (second pass, 28 Oct 2026); every set task, exam remark and slip found is cited in this note.
- Revision lecture 2 (`SESA2022 Lecture 2026-01-07.txt`, Part B), read in full and cited as "7 Jan revision". Slip there: l. 88 *"There isn't an epsilon. There's a psi term"* means the dummy variable $\xi$ (xi), as l. 95 says.
- Earlier-year recording `02 - Sources/Airfoils and Wings/TAT.txt`.
- Anderson, *Fundamentals of Aerodynamics*, Ch. 4.
- Figures: `generate_aero_t4_figures.py` (`tat_vortex_sheet_model`, `tat_theta_transform`, `tat_flap_effectiveness`); older figures (`tat_lift_curve`, `tat_loading`) predate the script. Worked-example numbers recomputed in Python (NumPy).

## Self-study tasks

The lecturer takes you through every step and says you *"won't have to reproduce all of that in an exam"*, but should check you can follow each step (28 Oct, ll. 43–48). The exam asks the two question types below. Attempt each task closed-book first.

### Core

- [ ] Linearised $C_p = -2v/V_\infty$ and $\Delta C_p = 2\gamma/V_\infty$ (lectured, 28 Oct, ll. 160–284). → [[#Linearised pressure coefficient]] · [[#Vortex sheet and loading]]
- [ ] Flat-plate check with G1 and the Kutta condition by L'Hôpital (lectured, 29 Oct, ll. 527–580). → [[#4. Symmetric aerofoil (flat plate)]]
- [ ] Fourier coefficients by substitution and orthogonality — *"You should just be trying to follow each step of the analysis"* (30 Oct, l. 314). → [[#5. General cambered aerofoil (30 Oct lecture)]]
- [ ] Question type 1: given $z = 0.24x(1-x)$ find $A_n$, $c_l$, $\alpha_{L=0}$, $\alpha_{ideal}$, $c_{m,c/4}$, $x_{cp}$ (31 Oct, ll. 45–195; 4 Nov, ll. 344–404). → [[#Worked example 1: NACA 6500 (lecture, 31 Oct and 4 Nov)]]
- [ ] Question type 2: flap with $E = 0.2$, find $\partial c_l/\partial\eta$ (31 Oct, ll. 266–412). → [[#Worked example 2: 20% flap effectiveness (lecture, 31 Oct)]]
- [ ] Examples Sheet 4: Q1 (parabolic camber), Q2 (derive $\alpha_{ideal}$), and the last question (NACA 2412) — *"worth just looking at that in the examples sheet"*; there is a slow analytical way and a quick numerical way (31 Oct, ll. 195–200; 4 Nov, ll. 416–440). → [[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]]

### Further practice

- [ ] Derive $c_{m,le} = -\frac\pi2(A_0+A_1-A_2/2)$ and the transfer to $c/4$ — *"you should be able to follow through the little derivation there"* (4 Nov, ll. 337–338). → [[#6. Moments, aerodynamic centre, centre of pressure (4 Nov lecture)]]
- [ ] Explain why slats do not change $\alpha_{L=0}$ but raise the stall angle, using boundary-layer ideas (31 Oct, ll. 442–462). → [[#High-lift devices (31 Oct, ll. 414–464)]]
- [ ] Run XFOIL/XFLR5 on NACA 0012 and NACA 4412: compare $dc_l/d\alpha$, $\alpha_{L=0}$ and $c_{m,c/4}$ with TAT, and identify the stall type (5 Nov lecture and the XFOIL/XFLR5 videos in `02 - Sources/Lectures/`). → [[#8. Real flow effects (28 Oct and 5 Nov lectures)]]
- [ ] *(Optional, not lectured)* Derive G1 and G2 from $I_0 = 0$ and the recursion. → [[#Glauert integrals]]
- [ ] *(Suggested, not lecturer-set)* Show that a 10% flap gives $\partial c_l/\partial\eta = 2.49$ and $\partial c_{m,c/4}/\partial\eta = -0.54$. → [[#General hinge position]]
- [ ] Explain the circulation theory of lift in words: vortex sheet, Kutta condition, Kutta–Joukowski — set as preparation for the 29 Oct lecture (28 Oct, ll. 502–505). → [[#SESA2022 T4 - Thin Aerofoil Theory|opening section]]
- [ ] Evaluate $\mathrm{PV}\!\int_0^1 dx/(x-x_0)$ yourself, then check $I_0 = 0$ (29 Oct, ll. 375–457). → [[#Improper integrals (lecture example)]]
- [ ] Repeat the XFOIL runs: NACA 6510 at $Re = 3\times10^6$ ($\alpha_{L=0}$, $c_l$ and $c_{m,c/4}$ at $0^\circ$ and $4^\circ$), then NACA 2412 at $Re = 3\times10^5$ from $5^\circ$ to $17^\circ$, and read the bubble and the separation point off $c_f$ and $H$ (5 Nov, ll. 420–672). → [[#What XFOIL shows (5 Nov demonstration)]]
- [ ] Past papers: the thin-aerofoil questions listed in [[SESA2022 Past Paper Map]].
