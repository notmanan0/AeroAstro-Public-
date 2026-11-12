---
title: "SESA3029 Deep Dive - Riemann Invariants, Full Derivation"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 3: Nozzles and the Method of Characteristics"
order: 5.5
tags: [sesa3029, compressible-flow, method-of-characteristics, riemann-invariants, prandtl-meyer, eigenvalues, derivation, deep-dive]
aliases: ["Riemann invariants derivation", "Riemann invariants deep dive", "Compatibility conditions derivation", "MoC derivation in full"]
date: 2026-11-12
status: lectured
coverage: "Every step of the Riemann-invariant derivation of Lectures 3.1–3.2 (streamtube and eigenvalue routes), the integration of the Prandtl–Meyer function, and checks against the L2.4 corner, the L3.2 slide 9 unit process and the Ackeret limit"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]"]
next_topics: ["[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
key_concepts: ["[[Riemann Invariants]]", "[[Method of Characteristics]]", "[[Prandtl-Meyer Function]]", "[[Homentropic Flow]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture3-1.pdf", "02 - Sources/Lectures/Lecture3-2.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-1.txt", "02 - Sources/Lectures/Lecture 3-2.txt"]
---

# SESA3029 Deep Dive - Riemann Invariants, Full Derivation

> [!abstract] Summary
> In steady, planar, homentropic, irrotational supersonic flow, $R^+=\nu-\theta$ is constant along each $C^+$ characteristic and $R^-=\nu+\theta$ along each $C^-$. Mass, streamwise momentum and zero vorticity on a curved streamtube give two coupled equations in the speed and the flow angle; writing the speed as the Prandtl–Meyer angle $\nu$ and taking their sum and difference separates them into derivatives along the lines at $\pm\mu$ to the flow. Diagonalising the same $2\times2$ system gives the invariants as $\underline E^{-1}[\nu,\theta]^T$ and shows why the method needs $M>1$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks you to derive the compatibility conditions or the Riemann invariants, or to justify the unit process, a simple flow region or the need for $M>1$.
> - **Assumptions:** steady, planar, inviscid, adiabatic, homentropic (no shocks), irrotational, $M>1$; $\gamma$ constant and $T_0$ uniform; angles in radians inside the calculus.
> - **Method:** 1. Streamtube geometry: $\partial\theta/\partial n=(1/\Delta n)\,\partial(\Delta n)/\partial l$. 2. Mass, $l$-momentum and $(\partial p/\partial\rho)_s=a^2$ give $(M^2-1)\frac1u\frac{\partial u}{\partial l}=\frac{\partial\theta}{\partial n}$. 3. Zero vorticity gives $\frac{\partial\theta}{\partial l}-\frac1u\frac{\partial u}{\partial n}=0$. 4. $\mathrm du/u=\tan\mu\,\mathrm d\nu$ turns these into Eq. 1 and Eq. 2; subtract and add them. 5. Read each bracket as a derivative along $\pm\mu$: $\nu-\theta$ is constant on $C^+$, $\nu+\theta$ on $C^-$.
> - **Common mistakes:** swapping the families (the $C^+$ reaching P comes from the known point below it and carries $R^+=\nu-\theta$); putting a factor $\tfrac12$ into the invariants, which belongs only to $\nu=\tfrac12(R^++R^-)$ and $\theta=\tfrac12(R^--R^+)$.
> - **Practise:** [[#One unit-process point (L3.2 slides 7–9)|the L3.2 slide 9 point]] · [[SESA3029 Example Sheet 2 - Solutions#Q1. Eigenvalues and left eigenvectors|ES2 Q1]]

In steady, planar, homentropic, irrotational supersonic flow, two combinations of the Prandtl–Meyer function $\nu$ and the flow angle $\theta$ stay constant along the Mach lines. These combinations are the **Riemann invariants** (L3.1 slide 12):

$$
R^+=\nu-\theta\quad\text{is constant along }C^+
$$

$$
R^-=\nu+\theta\quad\text{is constant along }C^-
$$

The two statements together are the **compatibility conditions**. Here $\theta$ is the inclination of the local velocity to the fixed $x$-axis, not a deflection from the upstream flow as in oblique-shock theory. $\nu(M)$ is the [[Prandtl-Meyer Function|Prandtl–Meyer function]], and $\mu=\arcsin(1/M)$ is the Mach angle. $C^+$ and $C^-$ are the **characteristics** (characteristic lines): $C^+$ is the left-running Mach line, at $+\mu$ to the local flow and so at $\theta+\mu$ to the $x$-axis, and $C^-$ is the right-running one, at $-\mu$ to the flow and $\theta-\mu$ to the $x$-axis.

The invariants replace a pair of coupled nonlinear PDEs by arithmetic. Where a $C^+$ and a $C^-$ cross, the two numbers they carry fix both unknowns at that point:

$$
\nu=\tfrac12\left(R^++R^-\right),\qquad\theta=\tfrac12\left(R^--R^+\right)
$$

The Mach number follows from $\nu$, and then $\mu$ and the isentropic ratios $p/p_0$, $T/T_0$ and $\rho/\rho_0$ follow from $M$. The result is used in four places:

- the **unit process** (L3.2 slides 7–9), which finds the state and position of a new point from two known upstream points and is repeated to march through a flow ([[SESA3029 W05a - Method of Characteristics#10. The unit process (3.2 slides 7–9)|W05a §10]]);
- **boundary conditions and nozzle design** (L3.3–3.4): at a wall one invariant arrives along its characteristic and the wall supplies $\theta$, on a centreline $\theta=0$, and the minimum-length nozzle of the MoC coursework is built from these rules ([[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]]);
- **simple flow regions**: where every line of one family starts in uniform flow, that family's invariant is the same everywhere, which reproduces the Prandtl–Meyer expansion of L2.4;
- **Ackeret theory** (L4.5): above a thin aerofoil every $C^-$ starts in the free stream, so $\nu+\theta=\nu_\infty$ everywhere. For small turns $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm dV/V$, which gives $C_p=2\theta/\sqrt{M_\infty^2-1}$ ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]]). Ackeret's linearised flow is a simple flow region in MoC terms, in the limit of weak waves.

## 1. Assumptions, notation and the curved streamtube (L3.1 slides 2–3)

The derivation (L3.1 slides 2–12) rests on these assumptions, each used at a definite step:

- **steady**: $\partial/\partial t=0$, so the streamlines are fixed in space and a streamtube is a fixed control volume;
- **planar (2D)**: the geometry lies in the $x$–$y$ plane and is infinite in $z$, so every flux is per unit span (an axisymmetric nozzle adds an extra term and the invariants stop being constant);
- **inviscid and adiabatic**: only pressure acts on the faces of the element, with no shear or heat flux;
- **homentropic**: the entropy is the same everywhere, not just along each streamline, so $p=C\rho^\gamma$ with one constant $C$ for the whole flow. This rules out shocks, whose entropy jump differs from streamline to streamline ([[Homentropic Flow]]);
- **irrotational**: zero vorticity. With uniform entropy and uniform $T_0$, Crocco's theorem $T\nabla s=\nabla h_0-\vec u\times\vec\omega$ leaves $\vec u\times\vec\omega=\vec 0$. In planar flow $\vec\omega$ points along $z$ and $\vec u$ lies in the plane, so $\vec\omega=\vec 0$ (Supplementary Note p. 2);
- **supersonic**: $M>1$, so that $\mu=\arcsin(1/M)$ exists and the Mach lines are real;
- **calorically perfect gas**: $\gamma$ constant ($\gamma=1.4$ for air), needed for $a(M)$ and the closed form of $\nu(M)$.

The Supplementary Note writes $s$ for the streamwise coordinate $l$, and Anderson writes $V$ for the speed $u$.

| Symbol | Meaning |
|---|---|
| $l$ | distance along the local streamline, in the direction of the velocity |
| $n$ | distance normal to the streamline, $l$ rotated $90^\circ$ anticlockwise (to the left of the flow) |
| $u$ | flow speed, the velocity component along $l$ |
| $v$ | velocity component along $n$, zero at the corner where $l$ is aligned with the flow |
| $\theta$ | inclination of the velocity to the $x$-axis, anticlockwise positive |
| $M$, $a$ | Mach number $u/a$ and speed of sound |
| $\mu$ | Mach angle, $\sin\mu=1/M$, so $\tan\mu=1/\sqrt{M^2-1}$ |
| $\nu$ | Prandtl–Meyer function, with $\nu(1)=0$ |
| $C^+$, $C^-$ | left-running characteristic at $+\mu$ to the flow ($\theta+\mu$ to $x$); right-running at $-\mu$ ($\theta-\mu$ to $x$) |
| $\Delta l$, $\Delta n$, $\Delta n'$ | element length along the lower streamline, height of the inlet face, height of the outlet face |

All angles are in radians inside the derivation, because small-angle steps such as $\tan\Delta\theta\approx\Delta\theta$ and the calculus on $\nu$ need them. Degrees appear only in tables and worked numbers.

![[at_moc_streamtube_geometry.png|900]]

The control volume is a small element of a curved streamtube between two neighbouring streamlines (L3.1 slide 3). Its lower streamline has inclination $\theta$. The upper streamline lies a distance $\Delta n$ further along $n$, so to first order its inclination is $\theta+\Delta\theta$, with

$$
\Delta\theta=\frac{\partial\theta}{\partial n}\,\Delta n .
$$

Over the length $\Delta l$ the upper streamline climbs away from the lower one by $\Delta l\tan\Delta\theta\approx\Delta\theta\,\Delta l$, so the outlet face is taller than the inlet face by that amount:

$$
\Delta n'-\Delta n=\Delta\theta\,\Delta l .
$$

Substitute for $\Delta\theta$:

$$
\Delta n'-\Delta n=\left(\frac{\partial\theta}{\partial n}\,\Delta n\right)\Delta l .
$$

Divide both sides by $\Delta n\,\Delta l$:

$$
\frac{\partial\theta}{\partial n}=\frac{1}{\Delta n}\,\frac{\Delta n'-\Delta n}{\Delta l} .
$$

Let $\Delta l\to0$. The difference quotient becomes the rate at which the streamtube height grows along $l$:

$$
\frac{\partial\theta}{\partial n}=\frac{1}{\Delta n}\,\frac{\partial(\Delta n)}{\partial l} .
$$

When the streamlines fan apart ($\partial\theta/\partial n>0$) the streamtube widens along the flow. $\partial\theta/\partial n$ therefore plays the part that $(1/A)\,\mathrm dA/\mathrm dx$ played in the quasi-1D nozzle ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]), with the local streamtube height in place of the duct area.

## 2. Mass conservation along the streamtube (L3.1 slide 4)

No flow crosses a streamline, so the mass flow per unit span entering the element equals the mass flow leaving it. At the inlet face the density, speed and height are $\rho$, $u$ and $\Delta n$. At the outlet face, a distance $\Delta l$ downstream, each is expanded to first order in a Taylor series. The velocity crosses each face at right angles to first order, because the cosine of an angle of order $\Delta\theta$ differs from 1 only at second order:

$$
\rho u\,\Delta n=\left(\rho+\frac{\partial\rho}{\partial l}\Delta l\right)\left(u+\frac{\partial u}{\partial l}\Delta l\right)\left(\Delta n+\frac{\partial(\Delta n)}{\partial l}\Delta l\right) .
$$

Multiply out the first two brackets:

$$
\left(\rho+\frac{\partial\rho}{\partial l}\Delta l\right)\left(u+\frac{\partial u}{\partial l}\Delta l\right)=\rho u+\rho\frac{\partial u}{\partial l}\Delta l+u\frac{\partial\rho}{\partial l}\Delta l+\frac{\partial\rho}{\partial l}\frac{\partial u}{\partial l}\Delta l^2 .
$$

The last term is second order in $\Delta l$ and is dropped:

$$
\left(\rho+\frac{\partial\rho}{\partial l}\Delta l\right)\left(u+\frac{\partial u}{\partial l}\Delta l\right)\approx\rho u+\rho\frac{\partial u}{\partial l}\Delta l+u\frac{\partial\rho}{\partial l}\Delta l .
$$

Multiply this by the third bracket, one term at a time:

$$
\begin{aligned}
\left(\rho u+\rho\frac{\partial u}{\partial l}\Delta l+u\frac{\partial\rho}{\partial l}\Delta l\right)\left(\Delta n+\frac{\partial(\Delta n)}{\partial l}\Delta l\right)
&=\rho u\,\Delta n+\rho\frac{\partial u}{\partial l}\Delta l\,\Delta n+u\frac{\partial\rho}{\partial l}\Delta l\,\Delta n\\
&\quad+\rho u\frac{\partial(\Delta n)}{\partial l}\Delta l+\rho\frac{\partial u}{\partial l}\frac{\partial(\Delta n)}{\partial l}\Delta l^2+u\frac{\partial\rho}{\partial l}\frac{\partial(\Delta n)}{\partial l}\Delta l^2 .
\end{aligned}
$$

Drop the two $\Delta l^2$ terms. Together with the $\Delta l^2$ term dropped above, these are all the $\Delta l^2$ and $\Delta l^3$ terms of the full product. The mass balance becomes

$$
\rho u\,\Delta n=\rho u\,\Delta n+\rho\frac{\partial u}{\partial l}\Delta l\,\Delta n+u\frac{\partial\rho}{\partial l}\Delta l\,\Delta n+\rho u\frac{\partial(\Delta n)}{\partial l}\Delta l .
$$

Cancel $\rho u\,\Delta n$ from both sides:

$$
0=\rho\frac{\partial u}{\partial l}\Delta l\,\Delta n+u\frac{\partial\rho}{\partial l}\Delta l\,\Delta n+\rho u\frac{\partial(\Delta n)}{\partial l}\Delta l .
$$

Divide by $\Delta l$:

$$
0=\rho\frac{\partial u}{\partial l}\Delta n+u\frac{\partial\rho}{\partial l}\Delta n+\rho u\frac{\partial(\Delta n)}{\partial l} .
$$

Divide by $\rho u\,\Delta n$:

$$
\frac1u\frac{\partial u}{\partial l}+\frac1\rho\frac{\partial\rho}{\partial l}+\frac{1}{\Delta n}\frac{\partial(\Delta n)}{\partial l}=0 .
$$

The last term is the streamtube result of §1, $(1/\Delta n)\,\partial(\Delta n)/\partial l=\partial\theta/\partial n$. Substituting it gives the mass equation in its final form (Supplementary Note eq. 2):

$$
\frac1u\frac{\partial u}{\partial l}+\frac1\rho\frac{\partial\rho}{\partial l}+\frac{\partial\theta}{\partial n}=0 .
$$

This is the same bracket expansion as the quasi-1D nozzle mass balance of L2.6, $\mathrm d\rho/\rho+\mathrm du/u+\mathrm dA/A=0$ ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]), with the turning of the streamlines, $\partial\theta/\partial n$, standing in for the fractional area change.

## 3. Momentum along the streamline and the area–velocity relation (L3.1 slides 5–6)

The $l$-momentum balance on the same element is momentum flux out minus momentum flux in equals the net external force in the $l$-direction. Per unit span the mass flow is $\dot m=\rho u\,\Delta n$, the same at both faces. The flow is inviscid, so the only external forces are pressures:

- $p\,\Delta n$ on the inlet face, pushing in $+l$;
- the mean pressure $p+\tfrac12(\partial p/\partial l)\Delta l$ on the inclined upper face. That face is tilted by $\Delta\theta$, so the $l$-component of its force is the pressure times its rise, $\Delta n'-\Delta n$, pushing in $+l$;
- $\left(p+(\partial p/\partial l)\Delta l\right)\Delta n'$ on the outlet face, pushing in $-l$;
- nothing from the lower face, which lies along $l$.

$$
\dot m\left(u+\frac{\partial u}{\partial l}\Delta l\right)-\dot m u=p\,\Delta n+\left(p+\frac12\frac{\partial p}{\partial l}\Delta l\right)(\Delta n'-\Delta n)-\left(p+\frac{\partial p}{\partial l}\Delta l\right)\Delta n'
$$

The left side collapses to one term:

$$
\dot m\,\frac{\partial u}{\partial l}\Delta l=\rho u\,\Delta n\,\frac{\partial u}{\partial l}\Delta l .
$$

Expand the right side term by term:

$$
p\,\Delta n+p\,\Delta n'-p\,\Delta n+\frac12\frac{\partial p}{\partial l}\Delta l\,(\Delta n'-\Delta n)-p\,\Delta n'-\frac{\partial p}{\partial l}\Delta l\,\Delta n' .
$$

The two $p\,\Delta n$ terms cancel, and so do the two $p\,\Delta n'$ terms:

$$
\frac12\frac{\partial p}{\partial l}\Delta l\,(\Delta n'-\Delta n)-\frac{\partial p}{\partial l}\Delta l\,\Delta n' .
$$

From the geometry, $\Delta n'-\Delta n=\Delta\theta\,\Delta l$, which is itself of order $\Delta l$. The first term is therefore of order $\Delta l^2$ and is dropped, leaving

$$
\rho u\,\Delta n\,\frac{\partial u}{\partial l}\Delta l=-\frac{\partial p}{\partial l}\Delta l\,\Delta n' .
$$

Divide by $\Delta n\,\Delta l$:

$$
\rho u\,\frac{\partial u}{\partial l}=-\frac{\partial p}{\partial l}\,\frac{\Delta n'}{\Delta n} .
$$

As $\Delta l\to0$, $\Delta n'=\Delta n+\Delta\theta\,\Delta l$ tends to $\Delta n$, so the ratio tends to 1. The result is Euler's equation along a streamline (Supplementary Note, before eq. 1):

$$
\rho u\,\frac{\partial u}{\partial l}=-\frac{\partial p}{\partial l} .
$$

The pressure is removed with the isentropic link between $p$ and $\rho$ (L3.1 slide 6). Along a streamline of isentropic flow $p$ depends only on $\rho$, so by the chain rule

$$
\frac{\partial p}{\partial l}=\left(\frac{\partial p}{\partial\rho}\right)_s\frac{\partial\rho}{\partial l} .
$$

For a perfect gas at constant entropy, $p=C\rho^\gamma$. Differentiate:

$$
\left(\frac{\partial p}{\partial\rho}\right)_s=\gamma C\rho^{\gamma-1} .
$$

Multiply and divide by $\rho$, then use $C\rho^\gamma=p$ and $p/\rho=RT$:

$$
\gamma C\rho^{\gamma-1}=\gamma\,\frac{C\rho^\gamma}{\rho}=\gamma\,\frac p\rho=\gamma RT=a^2 .
$$

So Euler's equation becomes (Supplementary Note eq. 1)

$$
\rho u\,\frac{\partial u}{\partial l}=-a^2\,\frac{\partial\rho}{\partial l} .
$$

This step only needs the flow to be isentropic along each streamline. Homentropy, the same entropy on every streamline, enters through the zero-vorticity condition of §4.

The mass equation eliminates $\partial\rho/\partial l$. Rearranged for the density term, it reads

$$
\frac{\partial\rho}{\partial l}=-\rho\left(\frac{\partial\theta}{\partial n}+\frac1u\frac{\partial u}{\partial l}\right) .
$$

Substitute into the momentum equation; the two minus signs give a plus:

$$
\rho u\,\frac{\partial u}{\partial l}=\rho a^2\left(\frac{\partial\theta}{\partial n}+\frac1u\frac{\partial u}{\partial l}\right) .
$$

Divide by $\rho a^2$:

$$
\frac{u}{a^2}\,\frac{\partial u}{\partial l}=\frac{\partial\theta}{\partial n}+\frac1u\frac{\partial u}{\partial l} .
$$

Write $u/a^2$ as $(u^2/a^2)(1/u)=M^2(1/u)$:

$$
M^2\,\frac1u\frac{\partial u}{\partial l}=\frac{\partial\theta}{\partial n}+\frac1u\frac{\partial u}{\partial l} .
$$

Subtract $(1/u)\,\partial u/\partial l$ from both sides and collect:

$$
\boxed{\left(M^2-1\right)\frac1u\frac{\partial u}{\partial l}=\frac{\partial\theta}{\partial n}}
$$

This is the Supplementary Note's eq. 3, and it is the area–velocity relation $\mathrm dA/A=(M^2-1)\,\mathrm du/u$ of the Laval nozzle, applied to the local streamtube. For $M>1$ the flow speeds up where the streamlines diverge ($\partial\theta/\partial n>0$); for $M<1$ it slows down. The equation contains two unknowns, $u$ and $\theta$, so a second equation is needed.

## 4. Zero vorticity and the turning of the flow (L3.1 slide 7)

The second equation comes from irrotationality. Take the $l$ and $n$ axes as a fixed local Cartesian frame at the corner of the element, with $u$ the velocity component along $l$ and $v$ the component along $n$. The vorticity there is

$$
\omega=\frac{\partial v}{\partial l}-\frac{\partial u}{\partial n} .
$$

At the corner the velocity points along $l$, so $v=0$ there. At the outlet face, a distance $\Delta l$ downstream, the speed has grown to $u+(\partial u/\partial l)\Delta l$ and the flow has turned through a small angle $\Delta\theta$ relative to $l$. This $\Delta\theta$ is the turn along the streamline, $(\partial\theta/\partial l)\Delta l$, not the change across the streamtube used in §1; the same symbol serves for both (L3.1 slides 3 and 7). Resolving the outlet velocity along $n$ gives

$$
\Delta v=\left(u+\frac{\partial u}{\partial l}\Delta l\right)\sin\Delta\theta .
$$

For a small angle in radians, $\sin\Delta\theta\approx\Delta\theta$:

$$
\Delta v=\left(u+\frac{\partial u}{\partial l}\Delta l\right)\Delta\theta .
$$

Divide by $\Delta l$ and let $\Delta l\to0$. The $(\partial u/\partial l)\Delta l$ term vanishes and $\Delta\theta/\Delta l$ becomes $\partial\theta/\partial l$:

$$
\frac{\partial v}{\partial l}=\lim_{\Delta l\to0}\left(u+\frac{\partial u}{\partial l}\Delta l\right)\frac{\Delta\theta}{\Delta l}=u\,\frac{\partial\theta}{\partial l} .
$$

Substitute into $\omega=0$:

$$
u\,\frac{\partial\theta}{\partial l}-\frac{\partial u}{\partial n}=0 .
$$

Divide by $u$ (Supplementary Note, p. 2):

$$
\boxed{\frac{\partial\theta}{\partial l}-\frac1u\frac{\partial u}{\partial n}=0}
$$

Physically, in irrotational flow a streamline can only curve ($\partial\theta/\partial l\ne0$) if the speed varies across it. With $\partial\theta/\partial l>0$ the streamline curves towards $+n$, and $\partial u/\partial n=u\,\partial\theta/\partial l>0$ makes the flow faster on the inside of the bend, as in a free vortex.

The flow is described by two equations in the two unknowns $u$ and $\theta$ (L3.1 slide 8):

$$
\left(M^2-1\right)\frac1u\frac{\partial u}{\partial l}=\frac{\partial\theta}{\partial n},\qquad
\frac{\partial\theta}{\partial l}-\frac1u\frac{\partial u}{\partial n}=0 .
$$

They are coupled, since each contains derivatives of both unknowns, and nonlinear, since $M$ depends on $u$. In this form they have no general solution. Replacing $u$ by an angle makes both unknowns angles and gives the two equations the same structure, after which they can be separated.

## 5. Combining the equations along the Mach lines (L3.1 slides 8–12)

The speed is replaced by the Prandtl–Meyer angle using the Prandtl–Meyer differential relation ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#5. Expansion waves and the Prandtl–Meyer function|W03 §5]]). Across a Mach wave at $\mu$ to the flow the tangential velocity is unchanged, so a turn $\mathrm d\nu$ changes the speed according to

$$
u\cos\mu=(u+\mathrm du)\cos(\mu+\mathrm d\nu) .
$$

Expand $\cos(\mu+\mathrm d\nu)\approx\cos\mu-\sin\mu\,\mathrm d\nu$:

$$
u\cos\mu=(u+\mathrm du)(\cos\mu-\sin\mu\,\mathrm d\nu) .
$$

Multiply out, cancel $u\cos\mu$ and drop the product $\mathrm du\,\mathrm d\nu$:

$$
\mathrm du\cos\mu=u\sin\mu\,\mathrm d\nu
\quad\Rightarrow\quad
\frac{\mathrm du}{u}=\tan\mu\,\mathrm d\nu .
$$

From $\sin\mu=1/M$, a right triangle with hypotenuse $M$, opposite side 1 and adjacent side $\sqrt{M^2-1}$ gives

$$
\tan\mu=\frac{1}{\sqrt{M^2-1}} ,
$$

so the relation can also be written $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm du/u$. With $T_0$ uniform, $M$ depends on $u$ alone, so $\nu$ is a function of $u$ alone and this is a change of variable rather than a statement about one wave. By the chain rule it holds for a change in any direction:

$$
\frac1u\frac{\partial u}{\partial l}=\tan\mu\,\frac{\partial\nu}{\partial l},\qquad\frac1u\frac{\partial u}{\partial n}=\tan\mu\,\frac{\partial\nu}{\partial n} .
$$

![[at_moc_characteristic_geometry.png|900]]

Substitute the first into the area–velocity relation:

$$
\left(M^2-1\right)\tan\mu\,\frac{\partial\nu}{\partial l}=\frac{\partial\theta}{\partial n} .
$$

Simplify the coefficient using $\tan\mu=1/\sqrt{M^2-1}$:

$$
\left(M^2-1\right)\tan\mu=\frac{M^2-1}{\sqrt{M^2-1}}=\sqrt{M^2-1}=\frac{1}{\tan\mu} .
$$

So the equation becomes

$$
\frac{1}{\tan\mu}\,\frac{\partial\nu}{\partial l}=\frac{\partial\theta}{\partial n} .
$$

Multiply by $\tan\mu$ and move everything to the left. This is Eq. 1 (Supplementary Note eq. 5):

$$
\frac{\partial\nu}{\partial l}-\tan\mu\,\frac{\partial\theta}{\partial n}=0\qquad\text{(Eq. 1)}
$$

Substitute the second relation into the zero-vorticity equation, $\partial\theta/\partial l-(1/u)\,\partial u/\partial n=0$. This gives Eq. 2 (Supplementary Note eq. 6) directly:

$$
\frac{\partial\theta}{\partial l}-\tan\mu\,\frac{\partial\nu}{\partial n}=0\qquad\text{(Eq. 2)}
$$

Both equations are in angles only, and each is the other with $\nu$ and $\theta$ swapped. They are still coupled, but their sum and difference separate them (L3.1 slide 9). Eq. 1 minus Eq. 2:

$$
\frac{\partial\nu}{\partial l}-\frac{\partial\theta}{\partial l}-\tan\mu\,\frac{\partial\theta}{\partial n}+\tan\mu\,\frac{\partial\nu}{\partial n}=0 .
$$

Group the $l$-derivatives and the $n$-derivatives:

$$
\frac{\partial(\nu-\theta)}{\partial l}+\tan\mu\,\frac{\partial(\nu-\theta)}{\partial n}=0\qquad\text{(A)}
$$

Eq. 1 plus Eq. 2:

$$
\frac{\partial\nu}{\partial l}+\frac{\partial\theta}{\partial l}-\tan\mu\,\frac{\partial\theta}{\partial n}-\tan\mu\,\frac{\partial\nu}{\partial n}=0 .
$$

Group again:

$$
\frac{\partial(\nu+\theta)}{\partial l}-\tan\mu\,\frac{\partial(\nu+\theta)}{\partial n}=0\qquad\text{(B)}
$$

Each equation contains a single unknown combination, and the bracket in each is a derivative along a particular direction (L3.1 slides 9–10). For any function $f(l,n)$, a small step $\Delta l$ along the flow and $\Delta n$ across it changes $f$ by

$$
\Delta f=\frac{\partial f}{\partial l}\Delta l+\frac{\partial f}{\partial n}\Delta n .
$$

Take $\Delta l$ outside:

$$
\Delta f=\Delta l\left(\frac{\partial f}{\partial l}+\frac{\Delta n}{\Delta l}\,\frac{\partial f}{\partial n}\right) .
$$

If the step is along a line at $+\mu$ to the flow, $\Delta n/\Delta l=\tan\mu$:

$$
\Delta f=\Delta l\left(\frac{\partial f}{\partial l}+\tan\mu\,\frac{\partial f}{\partial n}\right) .
$$

Put $f=\nu-\theta$. By (A) the bracket is zero (L3.1 slide 11), so

$$
\Delta(\nu-\theta)=\Delta l\left[\frac{\partial(\nu-\theta)}{\partial l}+\tan\mu\,\frac{\partial(\nu-\theta)}{\partial n}\right]=0\quad\text{along the line at }+\mu .
$$

For a step along a line at $-\mu$, $\Delta n/\Delta l=-\tan\mu$. Put $f=\nu+\theta$ and use (B):

$$
\Delta(\nu+\theta)=\Delta l\left[\frac{\partial(\nu+\theta)}{\partial l}-\tan\mu\,\frac{\partial(\nu+\theta)}{\partial n}\right]=0\quad\text{along the line at }-\mu .
$$

The lines at $\pm\mu$ to the local velocity are the Mach lines, which are the characteristics. Measured from the $x$-axis, $C^+$ is inclined at $\theta+\mu$ and $C^-$ at $\theta-\mu$, so in $x$–$y$ coordinates

$$
\left(\frac{\mathrm dy}{\mathrm dx}\right)_{C^+}=\tan(\theta+\mu),\qquad\left(\frac{\mathrm dy}{\mathrm dx}\right)_{C^-}=\tan(\theta-\mu) .
$$

Both $\theta$ and $\mu$ change from point to point, so the characteristics are curves, not straight lines, except where the flow is uniform or in a simple flow region (§8). They exist only for $M>1$; below $M=1$, $\mu=\arcsin(1/M)$ has no real value.

Written as differentials along these curves, the two results are $\mathrm d(\nu-\theta)=0$ on $C^+$ and $\mathrm d(\nu+\theta)=0$ on $C^-$. With $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm du/u$ they become the compatibility conditions in differential form:

$$
\mathrm d\theta=+\sqrt{M^2-1}\,\frac{\mathrm du}{u}\quad\text{along }C^+,\qquad
\mathrm d\theta=-\sqrt{M^2-1}\,\frac{\mathrm du}{u}\quad\text{along }C^- .
$$

With $V$ for the speed (Anderson's notation), this is $\mathrm d\theta=\pm\sqrt{M^2-1}\,\mathrm dV/V$ along $C^\pm$. Moving along a $C^+$, the flow turns anticlockwise exactly as fast as $\nu$ grows; moving along a $C^-$, it turns clockwise as $\nu$ grows.

## 6. The Prandtl–Meyer function and the integrated invariants

The differential conditions $\mathrm d(\nu\mp\theta)=0$ on $C^\pm$ integrate to finite statements only if $\nu$ is a single function of the local state. It is: $\nu$ is defined by integrating $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm du/u$ from the sonic state, where $\nu(1)=0$ by definition (L2.4; Supplementary Note p. 1). The integration starts by changing the variable from $u$ to $M$. The speed is the Mach number times the speed of sound:

$$
u=Ma .
$$

Take logarithms and differentiate:

$$
\frac{\mathrm du}{u}=\frac{\mathrm dM}{M}+\frac{\mathrm da}{a} .
$$

The flow is adiabatic with the same $T_0$ on every streamline, so $T_0/T=1+\tfrac12(\gamma-1)M^2$ everywhere, and $a=\sqrt{\gamma RT}$ gives

$$
a=a_0\left(1+\frac{\gamma-1}{2}M^2\right)^{-1/2} .
$$

Take logarithms and differentiate:

$$
\frac{\mathrm da}{a}=-\frac12\,\frac{(\gamma-1)M\,\mathrm dM}{1+\frac{\gamma-1}{2}M^2} .
$$

Substitute into $\mathrm du/u$ and take $\mathrm dM/M$ outside:

$$
\frac{\mathrm du}{u}=\frac{\mathrm dM}{M}\left[1-\frac{\frac{\gamma-1}{2}M^2}{1+\frac{\gamma-1}{2}M^2}\right] .
$$

Put the bracket over its common denominator; the numerator is 1:

$$
\frac{\mathrm du}{u}=\frac{1}{1+\frac{\gamma-1}{2}M^2}\,\frac{\mathrm dM}{M} .
$$

So the Prandtl–Meyer differential, in terms of $M$ alone, is

$$
\mathrm d\nu=\frac{\sqrt{M^2-1}}{1+\frac{\gamma-1}{2}M^2}\,\frac{\mathrm dM}{M} .
$$

Integrate from $M=1$, where $\nu=0$:

$$
\nu(M)=\int_1^M\frac{\sqrt{M^2-1}}{1+\frac{\gamma-1}{2}M^2}\,\frac{\mathrm dM}{M} .
$$

Substitute $t=\sqrt{M^2-1}$, so $M^2=1+t^2$ and the limits become $t=0$ and $t=\sqrt{M^2-1}$. Differentiating $M^2=1+t^2$ gives $2M\,\mathrm dM=2t\,\mathrm dt$, so

$$
\frac{\mathrm dM}{M}=\frac{t\,\mathrm dt}{M^2}=\frac{t\,\mathrm dt}{1+t^2} .
$$

The denominator becomes

$$
1+\frac{\gamma-1}{2}\left(1+t^2\right)=\frac{(\gamma+1)+(\gamma-1)t^2}{2} .
$$

Put the three pieces together:

$$
\nu=\int_0^t\frac{2t^2}{\left(1+t^2\right)\left[(\gamma+1)+(\gamma-1)t^2\right]}\,\mathrm dt .
$$

Split the integrand into partial fractions with unknown constants $A$ and $B$:

$$
\frac{2t^2}{\left(1+t^2\right)\left[(\gamma+1)+(\gamma-1)t^2\right]}=\frac{A}{1+t^2}+\frac{B}{(\gamma+1)+(\gamma-1)t^2} .
$$

Multiply through by the denominator:

$$
2t^2=A\left[(\gamma+1)+(\gamma-1)t^2\right]+B\left(1+t^2\right) .
$$

Match the constant terms and the $t^2$ terms:

$$
0=A(\gamma+1)+B,\qquad2=A(\gamma-1)+B .
$$

Subtract the first from the second: $2=-2A$, so $A=-1$ and then $B=\gamma+1$. The integral is

$$
\nu=\int_0^t\left[\frac{\gamma+1}{(\gamma+1)+(\gamma-1)t^2}-\frac{1}{1+t^2}\right]\mathrm dt .
$$

Divide the top and bottom of the first fraction by $\gamma+1$ and write $k=(\gamma-1)/(\gamma+1)$:

$$
\nu=\int_0^t\frac{\mathrm dt}{1+kt^2}-\int_0^t\frac{\mathrm dt}{1+t^2} .
$$

Both are standard integrals, and both vanish at $t=0$:

$$
\nu=\frac{1}{\sqrt k}\arctan\left(\sqrt k\,t\right)-\arctan t .
$$

Put back $k$ and $t=\sqrt{M^2-1}$:

$$
\boxed{\nu(M)=\sqrt{\frac{\gamma+1}{\gamma-1}}\,\arctan\sqrt{\frac{(\gamma-1)\left(M^2-1\right)}{\gamma+1}}-\arctan\sqrt{M^2-1}}
$$

The result is in radians. For air ($\gamma=1.4$), $\nu(2)=\sqrt6\arctan(1/\sqrt2)-\pi/3=0.46041$ rad $=26.380^\circ$, the value in the $\nu$ column of the isentropic flow table. As $M\to\infty$ both arctangents tend to $\pi/2$, so $\nu$ is bounded by $\nu_{max}=(\pi/2)(\sqrt6-1)=2.2769$ rad $=130.45^\circ$ at $\gamma=1.4$. Differentiating the closed form returns $\mathrm d\nu/\mathrm dM=\sqrt{M^2-1}/\left[M\left(1+\tfrac12(\gamma-1)M^2\right)\right]$, the integrand (checked symbolically).

With $\nu$ a function of $M$ only, $\mathrm d(\nu-\theta)$ is an exact differential. Integrate it along a $C^+$ from any point 1 to any point 2 on the same line:

$$
\int_1^2\mathrm d(\nu-\theta)=0
\quad\Rightarrow\quad
\nu_2-\theta_2=\nu_1-\theta_1 .
$$

The common value is the Riemann invariant of that line:

$$
R^+=\nu-\theta=\text{constant along }C^+ .
$$

Integrating $\mathrm d(\nu+\theta)=0$ along a $C^-$ in the same way:

$$
R^-=\nu+\theta=\text{constant along }C^- .
$$

Each $C^+$ carries its own value of $R^+$ and each $C^-$ its own $R^-$; the invariants are constant along a line, not across the whole flow, unless one family all starts in uniform flow. The integration crosses streamlines, so it relies on the same $\nu(M)$ holding on every streamline: $\gamma$ constant and $T_0$ uniform. Once integrated, $R^\pm$ is a sum of angles, so tables may use degrees, provided $\nu$ and $\theta$ are in the same unit.

## 7. The same result by eigenvalues (L3.2 slides 2–4)

Adding and subtracting Eq. 1 and Eq. 2 relies on spotting the right combinations. Diagonalising the system finds them systematically and also shows why the method needs $M>1$ (Supplementary Note §2). A hat marks a vector and an underline a matrix (L3.2 slide 2). Write Eq. 1 and Eq. 2 as one vector equation with $\hat Q=[\nu,\theta]^T$:

$$
\frac{\partial}{\partial l}\begin{bmatrix}\nu\\ \theta\end{bmatrix}+\begin{bmatrix}0&-\tan\mu\\ -\tan\mu&0\end{bmatrix}\frac{\partial}{\partial n}\begin{bmatrix}\nu\\ \theta\end{bmatrix}=\hat 0 .
$$

The first row reads $\partial\nu/\partial l-\tan\mu\,\partial\theta/\partial n=0$, which is Eq. 1, and the second reads $\partial\theta/\partial l-\tan\mu\,\partial\nu/\partial n=0$, which is Eq. 2. In compact form:

$$
\frac{\partial\hat Q}{\partial l}+\underline A\,\frac{\partial\hat Q}{\partial n}=\hat 0,\qquad\underline A=\begin{bmatrix}0&-\tan\mu\\ -\tan\mu&0\end{bmatrix} .
$$

The eigenvalues come from $\det(\underline A-\lambda\underline I)=0$:

$$
\det(\underline A-\lambda\underline I)=\begin{vmatrix}-\lambda&-\tan\mu\\ -\tan\mu&-\lambda\end{vmatrix}=\lambda^2-\tan^2\mu=0 .
$$

The determinant is the product of the diagonal terms, $(-\lambda)(-\lambda)$, minus the product of the off-diagonal terms, $\tan^2\mu$. So

$$
\lambda_1=+\tan\mu,\qquad\lambda_2=-\tan\mu .
$$

The eigenvectors satisfy $(\underline A-\lambda\underline I)\hat v=\hat 0$. For $\lambda_1=\tan\mu$ the first row gives $-\tan\mu\,v_1-\tan\mu\,v_2=0$, so $v_2=-v_1$. For $\lambda_2=-\tan\mu$ the first row gives $\tan\mu\,v_1-\tan\mu\,v_2=0$, so $v_2=v_1$. In each case the second row repeats the first. Choose $v_1=\tfrac12$ in both and place the eigenvectors side by side:

$$
\underline E=\left[\hat v_1,\ \hat v_2\right]=\frac12\begin{bmatrix}1&1\\ -1&1\end{bmatrix} .
$$

Its determinant is $(\tfrac12)(\tfrac12)-(\tfrac12)(-\tfrac12)=\tfrac12$. Swap the diagonal, negate the off-diagonal and divide by the determinant:

$$
\underline E^{-1}=\frac{1}{1/2}\cdot\frac12\begin{bmatrix}1&-1\\ 1&1\end{bmatrix}=\begin{bmatrix}1&-1\\ 1&1\end{bmatrix} .
$$

Check the diagonalisation one product at a time. First $\underline A\,\underline E$:

$$
\underline A\,\underline E=\frac12\begin{bmatrix}\tan\mu&-\tan\mu\\ -\tan\mu&-\tan\mu\end{bmatrix} .
$$

Then premultiply by $\underline E^{-1}$:

$$
\underline E^{-1}\underline A\,\underline E=\frac12\begin{bmatrix}\tan\mu+\tan\mu&-\tan\mu+\tan\mu\\ \tan\mu-\tan\mu&-\tan\mu-\tan\mu\end{bmatrix}=\begin{bmatrix}\tan\mu&0\\ 0&-\tan\mu\end{bmatrix}=\underline\Lambda .
$$

So $\underline A=\underline E\,\underline\Lambda\,\underline E^{-1}$. Substitute this into the system:

$$
\frac{\partial\hat Q}{\partial l}+\underline E\,\underline\Lambda\,\underline E^{-1}\frac{\partial\hat Q}{\partial n}=\hat 0 .
$$

Premultiply every term by $\underline E^{-1}$, on the left because matrix products do not commute, and use $\underline E^{-1}\underline E=\underline I$:

$$
\underline E^{-1}\frac{\partial\hat Q}{\partial l}+\underline\Lambda\,\underline E^{-1}\frac{\partial\hat Q}{\partial n}=\hat 0 .
$$

$\underline E$ contains no $\mu$, so it is a constant matrix and passes inside the derivatives. Define the vector of invariants:

$$
\hat R=\underline E^{-1}\hat Q=\begin{bmatrix}1&-1\\ 1&1\end{bmatrix}\begin{bmatrix}\nu\\ \theta\end{bmatrix}=\begin{bmatrix}\nu-\theta\\ \nu+\theta\end{bmatrix} .
$$

The system becomes diagonal:

$$
\frac{\partial\hat R}{\partial l}+\underline\Lambda\,\frac{\partial\hat R}{\partial n}=\hat 0 .
$$

Row by row, this is (A) and (B) of §5:

$$
\frac{\partial(\nu-\theta)}{\partial l}+\tan\mu\,\frac{\partial(\nu-\theta)}{\partial n}=0,\qquad\frac{\partial(\nu+\theta)}{\partial l}-\tan\mu\,\frac{\partial(\nu+\theta)}{\partial n}=0 .
$$

The rows of $\underline E^{-1}$ are the left eigenvectors, and $\underline E$ is the right eigenvector matrix (written $S$ in the Supplementary Note). They fix which combinations to form: the difference $\nu-\theta$ and the sum $\nu+\theta$. Each eigenvalue is the slope $\Delta n/\Delta l$, relative to the streamline, of the line along which its combination is constant: $\lambda=+\tan\mu$ is the line at $+\mu$ to the flow, $C^+$, and $\lambda=-\tan\mu$ is the line at $-\mu$, $C^-$. Eigenvectors are fixed only up to a scale factor, so software may scale them differently; any choice with $\underline E\,\underline E^{-1}=\underline I$ gives the same invariants up to a constant factor.

### Characteristic slopes in x–y coordinates

The same slopes appear directly in $x$–$y$ coordinates. With $l$ at angle $\theta$ to $x$,

$$
\frac{\partial}{\partial l}=\cos\theta\,\frac{\partial}{\partial x}+\sin\theta\,\frac{\partial}{\partial y},\qquad\frac{\partial}{\partial n}=-\sin\theta\,\frac{\partial}{\partial x}+\cos\theta\,\frac{\partial}{\partial y},
$$

so the system becomes

$$
\left(\cos\theta\,\underline I-\sin\theta\,\underline A\right)\frac{\partial\hat Q}{\partial x}+\left(\sin\theta\,\underline I+\cos\theta\,\underline A\right)\frac{\partial\hat Q}{\partial y}=\hat 0 .
$$

Its characteristic slopes $\mathrm dy/\mathrm dx=\lambda$ satisfy $\det\left[(\sin\theta\,\underline I+\cos\theta\,\underline A)-\lambda(\cos\theta\,\underline I-\sin\theta\,\underline A)\right]=0$. Write $T=\tan\mu$. The matrix has equal diagonal entries $\sin\theta-\lambda\cos\theta$ and equal off-diagonal entries $-T(\cos\theta+\lambda\sin\theta)$, so

$$
\left(\sin\theta-\lambda\cos\theta\right)^2-T^2\left(\cos\theta+\lambda\sin\theta\right)^2=0 .
$$

Take the square root of both sides:

$$
\sin\theta-\lambda\cos\theta=\pm T\left(\cos\theta+\lambda\sin\theta\right) .
$$

Solve for $\lambda$:

$$
\lambda=\frac{\sin\theta\mp T\cos\theta}{\cos\theta\pm T\sin\theta} .
$$

Multiply the top and bottom by $\cos\mu$ and use $T\cos\mu=\sin\mu$:

$$
\lambda=\frac{\sin\theta\cos\mu\mp\cos\theta\sin\mu}{\cos\theta\cos\mu\pm\sin\theta\sin\mu}=\tan(\theta\mp\mu) .
$$

The two roots are $\tan(\theta+\mu)$ and $\tan(\theta-\mu)$, the slopes of $C^+$ and $C^-$ in the $x$–$y$ plane.

### Why the method needs M > 1

The requirement $M>1$ shows most clearly before $u$ is replaced by $\nu$. With $w=\ln u$, the area–velocity and zero-vorticity equations are

$$
\left(M^2-1\right)\frac{\partial w}{\partial l}-\frac{\partial\theta}{\partial n}=0,\qquad\frac{\partial\theta}{\partial l}-\frac{\partial w}{\partial n}=0 .
$$

Divide the first by $M^2-1$. With $\hat Q=[w,\theta]^T$ the coefficient matrix is

$$
\underline A_w=\begin{bmatrix}0&-\dfrac{1}{M^2-1}\\ -1&0\end{bmatrix},
$$

and its eigenvalues satisfy

$$
\lambda^2=\frac{1}{M^2-1} .
$$

For $M>1$ the roots $\lambda=\pm1/\sqrt{M^2-1}=\pm\tan\mu$ are real and distinct: the system is hyperbolic, information travels along the two characteristics, and the solution can be marched downstream. For $M<1$ the roots are imaginary: the system is elliptic, there are no real characteristics, and every point influences every other, so the method of characteristics does not apply to subsonic flow. The same sign change separates Ackeret theory from Prandtl–Glauert in [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]] and [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]].

## 8. Checks and worked examples

All numbers below use $\gamma=1.4$, with angles in degrees, $\nu(M)$ from the closed form of §6 and $M$ from $\nu$ by numerical inversion.

### Prandtl–Meyer corner

A uniform stream at $M_1=2.0$, $\theta_1=0$ flows along a lower wall that turns down through $10^\circ$ at a convex corner, so $\theta_2=-10^\circ$ downstream. The corner sends out $C^+$ waves, which run up and away from the lower wall. Every $C^-$ reaching the fan starts in the uniform stream above, so all of them carry the same invariant:

$$
R^-=\nu_1+\theta_1=26.380^\circ+0=26.380^\circ .
$$

The $C^-$ through any point downstream of the fan carries the same value:

$$
\nu_2+\theta_2=R^-
\quad\Rightarrow\quad
\nu_2=26.380^\circ-(-10^\circ)=36.380^\circ .
$$

Inverting $\nu$ gives $M_2=2.385$, and with $p_0$ constant $p_2/p_1=0.5480$. This is the L2.4 result $\nu(M_2)=\nu(M_1)+10^\circ$, recovered from one invariant. The mirror case, an upper wall turning up by $10^\circ$, sends out $C^-$ waves with $R^+$ uniform, and $\nu_2-10^\circ=\nu_1$ gives the same $M_2$.

Inside the fan each $C^+$ keeps its own $R^+$, and $R^-$ is the same everywhere, so $\nu=\tfrac12(R^++R^-)$ and $\theta=\tfrac12(R^--R^+)$ are both constant along it. Then $\mu$ is constant too, and each $C^+$ is a straight ray from the corner: the centred fan. The first ray lies at $\theta+\mu=0+30.000^\circ=30.000^\circ$ and the last at $-10^\circ+24.791^\circ=14.791^\circ$, so the fan spans $15.209^\circ$. These are the same numbers as the upper surface of the $M_\infty=2$, $\alpha=10^\circ$ flat plate in [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]].

### One unit-process point (L3.2 slides 7–9)

Let A be the known point below P, whose $C^+$ reaches P, and B the known point above, whose $C^-$ reaches P. The invariants carry over unchanged:

$$
\nu_P-\theta_P=R^+_A=\nu_A-\theta_A,\qquad\nu_P+\theta_P=R^-_B=\nu_B+\theta_B .
$$

Add the two equations, then subtract the first from the second:

$$
2\nu_P=R^+_A+R^-_B
\quad\Rightarrow\quad
\nu_P=\frac{R^+_A+R^-_B}{2},
$$

$$
2\theta_P=R^-_B-R^+_A
\quad\Rightarrow\quad
\theta_P=\frac{R^-_B-R^+_A}{2} .
$$

The characteristics are curved, so each segment is approximated by a straight line at the average of its inclination angles at the two ends (L3.2 slide 8):

$$
\alpha_{AP}=\tfrac12\left[(\theta+\mu)_A+(\theta+\mu)_P\right],\qquad\alpha_{BP}=\tfrac12\left[(\theta-\mu)_B+(\theta-\mu)_P\right] .
$$

The two segments are

$$
y_P-y_A=(x_P-x_A)\tan\alpha_{AP},\qquad y_P-y_B=(x_P-x_B)\tan\alpha_{BP} .
$$

Subtract the second from the first to remove $y_P$:

$$
y_B-y_A=(x_P-x_A)\tan\alpha_{AP}-(x_P-x_B)\tan\alpha_{BP} .
$$

Collect the $x_P$ terms:

$$
x_P\left(\tan\alpha_{AP}-\tan\alpha_{BP}\right)=y_B-y_A+x_A\tan\alpha_{AP}-x_B\tan\alpha_{BP} .
$$

Divide, and change the sign of top and bottom:

$$
x_P=\frac{x_B\tan\alpha_{BP}-x_A\tan\alpha_{AP}-(y_B-y_A)}{\tan\alpha_{BP}-\tan\alpha_{AP}},\qquad y_P=y_A+(x_P-x_A)\tan\alpha_{AP} .
$$

![[at_moc_unit_process.png|900]]

In the L3.2 slide 9 example, point 1 is at $(0.69,\ 0.62)$ with $M_1=1.6$, $\theta_1=12^\circ$, and point 2 at $(1.08,\ 0)$ with $M_2=1.4$, $\theta_2=0$. Point 1 lies above, so it plays B; point 2 lies below, so it plays A. Intermediate values are carried at full precision and rounded for display.

| Quantity | Working | Value |
|---|---|---|
| $\nu_1$, $\mu_1$ | $\nu(1.6)$, $\arcsin(1/1.6)$ | $14.8604^\circ$, $38.6822^\circ$ |
| $\nu_2$, $\mu_2$ | $\nu(1.4)$, $\arcsin(1/1.4)$ | $8.9870^\circ$, $45.5847^\circ$ |
| $R^-_1$ | $14.8604+12$ | $26.8604^\circ$ |
| $R^+_2$ | $8.9870-0$ | $8.9870^\circ$ |
| $\nu_3$ | $\tfrac12(8.9870+26.8604)$ | $17.9237^\circ$ |
| $\theta_3$ | $\tfrac12(26.8604-8.9870)$ | $8.9367^\circ$ |
| $M_3$, $\mu_3$ | invert $\nu$; $\arcsin(1/M_3)$ | $1.7039$, $35.9371^\circ$ |
| $\alpha_{23}$ | $\tfrac12(45.5847+44.8738)$ | $45.2292^\circ$, $\tan=1.00803$ |
| $\alpha_{13}$ | $\tfrac12(-26.6822-27.0005)$ | $-26.8413^\circ$, $\tan=-0.50604$ |

The coordinates follow:

$$
x_3=\frac{0.69(-0.50604)-1.08(1.00803)-(0.62-0)}{-0.50604-1.00803}=\frac{-2.05785}{-1.51407}=1.3591,
$$

$$
y_3=0+(1.3591-1.08)(1.00803)=0.2814 .
$$

These agree with the L3.2 slide 9 answer, $M_3=1.7039$, $\theta_3=8.9367^\circ$ and $(1.3592,\ 0.2814)$, apart from the last digit of $x_3$, which comes from rounding of the intermediate angles. As a check, $\nu_3-\theta_3=8.9870^\circ=R^+_2$ and $\nu_3+\theta_3=26.8604^\circ=R^-_1$. Using the slopes at points 1 and 2 alone, without averaging, puts point 3 at $(1.3584,\ 0.2841)$.

### A simple flow region and the Ackeret limit

A stream at $M_\infty=2.0$ flows along a lower wall that curves down gradually to $-10^\circ$ instead of turning at a corner. Every $C^-$ again starts in the uniform stream, so $R^-=26.380^\circ$ throughout, which makes this a simple flow region. At a wall point of inclination $\theta_w$ the wall fixes $\theta$, so $\nu=R^--\theta_w$. The $C^+$ leaving that point has its own constant $R^+$, so, as in the fan, $\nu$, $\theta$ and $\mu$ are constant along it and it is a straight line at $\theta_w+\mu$.

| Wall angle $\theta_w$ | $\nu=26.380^\circ-\theta_w$ | $M$ | $\mu$ | $C^+$ inclination $\theta_w+\mu$ | $R^+=\nu-\theta_w$ |
|---|---|---|---|---|---|
| $0^\circ$ | $26.380^\circ$ | 2.000 | $30.000^\circ$ | $30.000^\circ$ | $26.380^\circ$ |
| $-2.5^\circ$ | $28.880^\circ$ | 2.092 | $28.557^\circ$ | $26.057^\circ$ | $31.380^\circ$ |
| $-5^\circ$ | $31.380^\circ$ | 2.186 | $27.217^\circ$ | $22.217^\circ$ | $36.380^\circ$ |
| $-7.5^\circ$ | $33.880^\circ$ | 2.284 | $25.966^\circ$ | $18.466^\circ$ | $41.380^\circ$ |
| $-10^\circ$ | $36.380^\circ$ | 2.385 | $24.791^\circ$ | $14.791^\circ$ | $46.380^\circ$ |

The $C^+$ lines get shallower downstream, so they fan apart: the expansion is spread over the curved part of the wall instead of being centred on a corner. The final state, $M=2.385$, is the same as for the sharp corner, because it depends only on $R^-$ and the final wall angle. On a concave wall the $C^+$ lines steepen downstream, converge and eventually form a shock, where the homentropic assumption fails.

The same invariant gives Ackeret theory in the limit of small angles. For a $2^\circ$ compression at $M_\infty=2$, $\nu=26.380^\circ-2^\circ=24.380^\circ$, $M=1.928$ and the isentropic pressure coefficient is $C_p=0.0421$. The linear formula $C_p=2\theta/\sqrt{M_\infty^2-1}$, with $\theta=0.0349$ rad, gives $0.0403$, so the isentropic value is 4.5 % higher, the error quoted in [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#3. Ackeret's formula (4.5 slide 5)|W07c §3]].

## 9. Common mistakes

Most lost marks come from sign and arithmetic errors rather than from the derivation itself:

- swapping the families: the $C^+$ reaching P comes from the known point below it and carries $R^+=\nu-\theta$; the $C^-$ comes from the point above and carries $R^-=\nu+\theta$;
- treating $\theta$ as a deflection: it is the inclination to the $x$-axis, negative for a flow pointing below it, and that sign enters $R^\pm$ (in the corner example $\theta_2=-10^\circ$ gives $\nu_2=R^-+10^\circ$);
- putting a factor of $\tfrac12$ into the invariants: $R^\pm=\nu\mp\theta$, and the $\tfrac12$ appears only when solving back for $\nu$ and $\theta$;
- mixing units: the calculus needs radians, the tables use degrees, and $R^\pm$ is only meaningful if $\nu$ and $\theta$ share a unit. A calculator left in radian mode returns $\arcsin(1/1.4)=0.7956$, which is $45.58^\circ$;
- using the slope at the starting point instead of the averaged slope when locating P, which moves point 3 of the L3.2 example by about 0.003;
- multiplying by $\underline E$ instead of $\underline E^{-1}$, or on the right instead of the left, in the eigenvalue route;
- using the invariants outside their assumptions: across a shock (the entropy jumps), for $M<1$ (no real characteristics), or in an axisymmetric nozzle, where an extra term makes $R^\pm$ change along the lines (Supplementary Note appendix);
- assuming the invariants are uniform: each line carries its own value, and one family's value is uniform only in a simple flow region.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| Riemann invariants $R^+=\nu-\theta$, $R^-=\nu+\theta$ | $K^+=\theta-\nu=-R^+$ and $K^-=\theta+\nu=R^-$ (Anderson); characteristic invariants | L3.1 slide 12; Supplementary Note eq. 11 | The course signs follow Liepmann & Roshko (Supplementary Note p. 5). With Anderson's, $\nu=\tfrac12(K^--K^+)$ and $\theta=\tfrac12(K^-+K^+)$ |
| compatibility conditions | compatibility relations; compatibility equations | L3.1 slide 12 | |
| characteristics $C^+$, $C^-$ (characteristic lines) | left-running and right-running characteristics; Mach lines | L3.1 slides 10–12; Supplementary Note p. 2 | |
| $l$, the streamwise coordinate | $s$ | L3.1 slides 3–8 | $s$ is the Supplementary Note's letter |
| $\underline E$, the eigenvector matrix | $S$, the right eigenvector matrix | L3.2 slides 3–4 | Supplementary Note §2; same entries |
| $u$, the flow speed | $V$ | L3.1 slides 4–8 | Anderson's letter |
| simple flow region | simple-wave region | L3.3 slides | Anderson's wording |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Lecture notes: [[SESA3029 W05a - Method of Characteristics]] (the same derivation, with zones of dependence and the unit process) · [[SESA3029 W05b - Minimum-Length Nozzle Design]] (boundary conditions and nozzle design)
- Used elsewhere: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]] (Prandtl–Meyer expansion) · [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]] (area–velocity relation) · [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] (Ackeret theory as the weak-wave limit)
- Concepts: [[Riemann Invariants]] · [[Method of Characteristics]] · [[Prandtl-Meyer Function]] · [[Homentropic Flow]] · [[Mach Waves and Mach Angle]] · [[Expansion Fan]]
- Earlier years: [[Eigenvalues and Eigenvectors]] (MATH1054)
- Worked sheets: [[SESA3029 Example Sheet 2 - Solutions#Q1. Eigenvalues and left eigenvectors|ES2 Q1]] (eigenvalues and left eigenvectors) · [[SESA3029 Example Sheet 2 - Solutions]] Q2–Q3 (MoC in the course's $R^\pm$ notation)
- Formulae: [[SESA3029 Formula Sheet]]

## Sources

- `Lecture3-1.pdf` (L3.1, MoC Theory Part A), slides 2–12: the curved-streamtube derivation and the compatibility conditions. Lectured Fri 16 Oct.
- `Lecture3-2.pdf` (L3.2, MoC Theory Part B), slides 2–4 and 7–9: the eigenvalue route, the unit process and its example. Lectured Mon 19 Oct.
- `Supplementary Note for MoC.pdf`, §§1–3 (eqs. 1–11): the same derivation in $s$–$n$ coordinates, the eigen-decomposition and the unit process; the appendix for the axisymmetric term.
- `Lecture 3-1.txt` and `Lecture 3-2.txt` (L3-1, L3-2): the recordings, for the slips below and the task line references.
- L2.4 (the Prandtl–Meyer function), L2.6 (the quasi-1D mass balance) and L4.5 (Ackeret theory), through [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]] and [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]].
- Anderson, *Modern Compressible Flow*, Ch. 11, and Liepmann & Roshko (1957), for the $K^\pm$ and $R^\pm$ conventions.
- Checks: the closed form of $\nu$ was differentiated symbolically (sympy) and compared with the integrand at $\gamma=1.4$ and $1.289$; the eigen-decomposition, $\underline E^{-1}\underline A\,\underline E=\underline\Lambda$ and the $x$–$y$ slopes $\tan(\theta\pm\mu)$ were checked symbolically; every number in §8 was computed in Python.

## Self-study tasks

Tasks citing L3-1 or L3-2 were set or worked in the lectures of Fri 16 and Mon 19 Oct (the same tasks appear in [[SESA3029 W05a - Method of Characteristics#Self-study tasks|W05a]]). Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(L3-1, ll. 56–204)** Derive $(M^2-1)\frac1u\frac{\partial u}{\partial l}=\frac{\partial\theta}{\partial n}$ from the streamtube geometry, mass, $l$-momentum and $(\partial p/\partial\rho)_s=a^2$, naming each dropped $\Delta l^2$ term. → [[#3. Momentum along the streamline and the area–velocity relation (L3.1 slides 5–6)|§§1–3]]
- [ ] **(L3-1, ll. 212–239)** Derive $\frac{\partial\theta}{\partial l}-\frac1u\frac{\partial u}{\partial n}=0$ from zero vorticity. → [[#4. Zero vorticity and the turning of the flow (L3.1 slide 7)|§4]]
- [ ] **(L3-1, ll. 249–357)** Convert to Eq. 1 and Eq. 2, subtract and add, and use the directional derivative to show that $\nu\mp\theta$ is constant along $C^\pm$. → [[#5. Combining the equations along the Mach lines (L3.1 slides 8–12)|§5]]
- [ ] **(L3-2, ll. 39–182)** Diagonalise $\underline A$: eigenvalues, eigenvectors, $\underline E^{-1}$, then decouple with $\underline E^{-1}$ on the left. Then try [[SESA3029 Example Sheet 2 - Solutions#Q1. Eigenvalues and left eigenvectors|ES2 Q1]]. → [[#7. The same result by eigenvalues (L3.2 slides 2–4)|§7]]
- [ ] **(L3-2, ll. 453–459; homework)** Find $M_3$, $\theta_3$ and $(x_3,y_3)$ for the slide 9 example. Answer $1.7039$, $8.9367^\circ$, $(1.3591,\ 0.2814)$. → [[#One unit-process point (L3.2 slides 7–9)|§8, unit process]]

### Further practice

- [ ] **(L3-2, l. 349)** Solve the two straight-line equations for $x_P$ and $y_P$ and recover the slide 8 formula. → [[#One unit-process point (L3.2 slides 7–9)|§8, unit process]]
- [ ] **(L3-1, ll. 170–184)** Show that $(\partial p/\partial\rho)_s=a^2$ from $p=C\rho^\gamma$. → [[#3. Momentum along the streamline and the area–velocity relation (L3.1 slides 5–6)|§3]]
- [ ] **(L3-1, l. 114)** Compare the streamtube mass balance with the quasi-1D bracket expansion of Lecture 2.6. → [[#2. Mass conservation along the streamtube (L3.1 slide 4)|§2]]
- [ ] (suggested, not lecturer-set) Integrate $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm du/u$ to the closed form of $\nu(M)$, including the partial fractions, and evaluate $\nu(2)$ and $\nu_{max}$ at $\gamma=1.4$. → [[#6. The Prandtl–Meyer function and the integrated invariants|§6]]
- [ ] (suggested, not lecturer-set) Show that the characteristic slopes in $x$–$y$ coordinates are $\tan(\theta\pm\mu)$, and that the $w=\ln u$ system is elliptic for $M<1$. → [[#Characteristic slopes in x–y coordinates|§7]]
- [ ] (suggested, not lecturer-set) Fill in the simple-flow-region table for a wall curving from $0$ to $-10^\circ$ at $M_\infty=2$ and show that the final Mach number equals the sharp-corner value. → [[#A simple flow region and the Ackeret limit|§8, simple flow region]]

## Transcript and slide slips

> [!warning] Differences between the sources
> Where: [[#1. Assumptions, notation and the curved streamtube (L3.1 slides 2–3)]] and [[#4. Zero vorticity and the turning of the flow (L3.1 slide 7)]].
>
> - $\Delta\theta$ denotes two different increments: $(\partial\theta/\partial n)\Delta n$ across the streamtube (L3.1 slide 3) and $(\partial\theta/\partial l)\Delta l$ along it (slide 7).
> - The division by $\Delta l$ in the mass balance is left implicit (L3.1 slide 4).
> - The Supplementary Note writes $s$ for $l$ and $S$ for $\underline E$, with the same entries.
> - L3.2 slide 9 gives $x_3=1.3592$; unrounded working gives $1.3591$.
>
> None of these changes the result.

### Transcript slips (L3-1, L3-2)

> [!warning] Slips in `Lecture 3-1.txt` and `Lecture 3-2.txt`
> | Where | Said | Correct |
> |---|---|---|
> | L3-1, ll. 105–113 | the $\mathrm d\rho/\rho+\mathrm du/u+\mathrm dA/A$ bracket expansion placed in Lecture 2.4 | Lecture 2.6; L2.4 supplies $\mathrm du/u=\tan\mu\,\mathrm d\nu$ |
> | L3-1, l. 252 | $\tan\mu=1/(M^2-1)$ | $\tan\mu=1/\sqrt{M^2-1}$ |
> | L3-1, ll. 338–343 | *"mu minus theta"* | $\nu-\theta$ |
> | L3-1, l. 362 | *"along C minus theta is constant"* | $\nu+\theta$ is constant along $C^-$ |
> | L3-2, l. 64 | *"diagonal terms minus half-diagonal terms"* | product of the diagonal terms minus product of the off-diagonal terms |
> | L3-2, l. 117 | premultiply by $\underline E$ | premultiply by $\underline E^{-1}$ (corrected at l. 130) |
