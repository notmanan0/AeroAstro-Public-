---
title: "SESA3029 Tutorial Lecture 2 - Diamond Aerofoil by Ackeret Theory"
module: "SESA3029 Aerothermodynamics"
type: tutorial
stream: "Block 4: High-speed aerodynamics"
tags: [sesa3029, tutorial-lecture, ackeret, diamond-aerofoil, aerodynamic-centre, weak-shocks, stagnation-pressure]
aliases: ["SESA3029 Tutorial 2", "SESA3029 Tutorial Lecture 2"]
date: 2026-11-16
status: lectured
coverage: "Tutorial Lecture 2 (Mon 16 Nov), in full: ES2 Q3 set as own work, ES2 Q5 diamond aerofoil by Ackeret theory, the proof that x_AC = c/2 for a thin diamond, and why Ackeret theory holds across weak shocks"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
theory_notes: ["[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
prerequisites: ["[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]", "[[Ackeret Theory]]", "[[Entropy Change Across a Shock]]", "[[Theta-Beta-Mach Relation]]"]
next_topics: []
key_concepts: ["[[Ackeret Theory]]", "[[Entropy Change Across a Shock]]", "[[Aerodynamic Centre and Centre of Pressure]]", "[[Supersonic Wave Drag]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]", "[[SESA3029 Example Sheet 1 - Solutions]]"]
sources: ["02 - Sources/Lectures/Tutorial Lecture #2.txt", "03 - Exams & Past Papers/ExamplesSheet2.pdf", "03 - Exams & Past Papers/ExamplesSheet1.pdf"]
---

# SESA3029 Tutorial Lecture 2 - Diamond Aerofoil by Ackeret Theory

> [!abstract] Summary
> Example Sheet 2 Q5 puts a 5 % diamond aerofoil at $\alpha=2^\circ$ in a $M_\infty=1.8$, $p_\infty=50$ kPa stream; Ackeret theory, face by face, gives pressures of 52.3, 37.1, 62.9 and 47.7 kPa, $L'=10.55$ kN/m, $D'=1.13$ kN/m, $M'_{LE}=-5.29$ kN m/m and $x_{CP}=0.50c$. Once the four face angles are right the rest is mechanical, so the angles decide the marks. Integrating Ackeret's $C_p$ over a thin diamond gives $C_{m,LE}=-C_l/2$, which puts the aerodynamic centre at half chord. Ackeret theory assumes isentropic flow everywhere, yet the shocks on this section lose only 0.16 % of the stagnation pressure, because that loss grows like the cube of the turning angle.

> [!summary]- Exam use: quick path
> - **Use it when:** a faceted section (diamond, half-diamond, wedge) in supersonic flow is to be solved face by face with Ackeret theory, or the question asks for the aerodynamic centre or whether linear theory is valid across the shocks.
> - **Assumptions:** thin section, small angles **in radians**, $M_\infty$ from about 1.2 to 3–4, perfect gas with $\gamma=1.4$; shocks weak enough that $p_{02}/p_{01}\approx1$ ($M_{n1}\lesssim1.2$); moments nose-up positive about the leading edge.
> - **Method:** 1. $\phi=\tan^{-1}(t/c)$, then each face's $\theta$ from the free-stream direction, signed by the duct test. 2. $C_p=2\theta/\lambda$ and $p=p_\infty\left(1+\tfrac12\gamma M_\infty^2C_p\right)$. 3. $N'$ from the pressure differences times $c/2$; $A'$ from the front-face sum minus the rear-face sum, times $t/2$. 4. $L'=N'\cos\alpha-A'\sin\alpha$, $D'=A'\cos\alpha+N'\sin\alpha$. 5. $M'_{LE}$ with arms $c/4$ and $3c/4$, then $x_{CP}/c=-M'_{LE}/(L'c)$.
> - **Common mistakes:** measuring $\theta$ from the chord instead of from $\vec U_\infty$, or missing that the upper front face becomes an expansion once $\alpha>\phi$; giving the rear faces' chordwise force the same sign as the front faces' (rear faces push forwards).
> - **Practise:** [[#3. Lift and drag from the face forces|ES2 Q5, worked here]] · [[SESA3029 Past Paper 2024-25 A - Solutions#Q1. Nozzle flow, wall shock reflection and half-diamond aerofoil (34 marks)|2024–25 A Q1(iii)–(v)]]

A diamond aerofoil is four flat faces, so in Ackeret theory each face carries a single uniform pressure, fixed by nothing but its inclination to the free stream. The two front faces meet the flow at the leading edge and the two rear faces at the crests at mid-chord. At small incidence the front pair compress the flow and the rear pair expand it. Incidence tilts the whole section: it steepens the lower front and upper rear faces and flattens the other two, and the pressure difference across the section that results is the same on both halves of the chord.

The calculation runs from angles to pressure coefficients, then to pressures, to forces normal and parallel to the chord, and finally to lift, drag and moment. The same four faces solved exactly, with an oblique shock or a Prandtl–Meyer fan at each corner, are [[SESA3029 Example Sheet 1 - Solutions#Q6. Diamond aerofoil by shock-expansion theory|Example Sheet 1 Q6]]. Comparing the two answers is the most common compressible-flow exam question ([[SESA3029 Past Papers - Question Map#R2. Shock-expansion against Ackeret theory on supersonic aerofoils|question map, R2]]).

Example Sheet 2 Q3 is a method-of-characteristics question in mock-exam form. It differs from the MoC coursework only in that the wall shape, $y=1+0.1x+0.5x^2$, is given; it asks for the flow at points A, B, C, D and F and is left as your own work (T2, ll. 3–12). It is solved in [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|ES2 Q3]].

## 1. The four face angles

The thickness $t$ sits at mid-chord, so each face spans half the chord and rises through half the thickness. The half vertex angle is

$$
\tan\phi=\frac{t/2}{c/2}=\frac tc=0.05,
$$

$$
\phi=\tan^{-1}0.05=2.862^\circ=0.04996\ \text{rad}.
$$

In thin-aerofoil terms the face slope is $t/c=0.05$ rad, the value used in [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#9. Thickness drag and the optimum section|W07c §9]]; the two differ by 0.08 %.

Ackeret's $\theta$ is the angle between a face and the free-stream vector $\vec U_\infty$, not the chord, and it is positive when the face turns the flow into itself ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#3. Ackeret's formula|W07c §3]]). Draw a line parallel to $\vec U_\infty$ through the leading edge and one through each crest; each face's angle is read from the line where the face starts. The sign comes from the duct test: a face and a streamline just outside it, running parallel to $\vec U_\infty$, bound a channel. If the channel narrows downstream the supersonic flow in it is compressed, and if it widens the flow expands. With the section pitched nose-up by $\alpha=2^\circ$:

- the upper front face (1u) rises $\phi-\alpha$ above the leading-edge line, towards the streamline above it, so the channel narrows: $\theta_{1u}=+(\phi-\alpha)=+0.862^\circ$;
- the lower front face (1l) drops $\phi+\alpha$ below the same line, towards the streamline beneath it: $\theta_{1l}=+(\phi+\alpha)=+4.862^\circ$;
- the upper rear face (2u) falls $\phi+\alpha$ below the line through the upper crest, away from the flow above: $\theta_{2u}=-(\phi+\alpha)=-4.862^\circ$;
- the lower rear face (2l) rises $\phi-\alpha$ above the line through the lower crest, away from the flow below: $\theta_{2l}=-(\phi-\alpha)=-0.862^\circ$.

In radians, $\phi-\alpha=0.01505$ and $\phi+\alpha=0.08486$.

![[at_tut2_diamond_faces.png|900]]

> [!warning] The angles carry the rest of the question
> About half of last year's candidates got at least one of the four angles wrong (T2, ll. 115–117), and an angle error at the start costs most of the marks that follow (ll. 124–125). Incidence adds to one face's angle and subtracts from the other's, so neither front face has angle $\phi$. Once $\alpha>\phi$ the upper front face turns away from the flow and becomes an expansion, and the lower rear face becomes a compression: at $\alpha=3^\circ$, $\theta_{1u}=-0.138^\circ$ and $\theta_{2l}=+0.138^\circ$.

## 2. Pressure on each face

Ackeret's formula, with $\theta$ in radians, is

$$
C_p=\frac{2\theta}{\lambda},\qquad\lambda=\sqrt{M_\infty^2-1}=\sqrt{1.8^2-1}=\sqrt{2.24}=1.4967 .
$$

Turning $C_p$ into a pressure needs the dynamic pressure in terms of the Mach number. Start from the definition:

$$
C_p=\frac{p-p_\infty}{\tfrac12\rho_\infty U_\infty^2}.
$$

For a perfect gas $a^2=\gamma p/\rho$, and $U_\infty=M_\infty a_\infty$:

$$
\tfrac12\rho_\infty U_\infty^2=\tfrac12\rho_\infty M_\infty^2a_\infty^2=\tfrac12\rho_\infty M_\infty^2\,\frac{\gamma p_\infty}{\rho_\infty}=\tfrac12\gamma p_\infty M_\infty^2 .
$$

Substitute and rearrange for $p$:

$$
p-p_\infty=\tfrac12\gamma p_\infty M_\infty^2\,C_p,
$$

$$
p=p_\infty\left(1+\tfrac12\gamma M_\infty^2C_p\right).
$$

Here $q_\infty=\tfrac12\gamma p_\infty M_\infty^2=0.7\times50\times3.24=113.4$ kPa, so $p=50+113.4\,C_p$ kPa.

| Face | $\theta$ | $\theta$ (rad) | $C_p=2\theta/\lambda$ | $p$ (kPa) | Shock-expansion $p$ (ES1 Q6) |
|---|---|---:|---:|---:|---:|
| 1u | $+(\phi-\alpha)=+0.862^\circ$ | $+0.01505$ | $+0.02011$ | **52.28** | 52.32 |
| 1l | $+(\phi+\alpha)=+4.862^\circ$ | $+0.08486$ | $+0.11341$ | **62.86** | 64.28 |
| 2u | $-(\phi+\alpha)=-4.862^\circ$ | $-0.08486$ | $-0.11341$ | **37.14** | 38.39 |
| 2l | $-(\phi-\alpha)=-0.862^\circ$ | $-0.01505$ | $-0.02011$ | **47.72** | 47.77 |

These are the sheet's 52.3, 62.9, 37.1 and 47.7 kPa. In Ackeret theory the faces pair off symmetrically about $p_\infty$ (1u with 2l, 1l with 2u) because $|\theta|$ repeats. The exact pressures do not: a shock compresses more than the linear formula predicts and a fan expands less ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#3. Ackeret's formula|W07c §3]] figure), so both exact values on the strongly turned faces sit above the linear ones.

## 3. Lift and drag from the face forces

Each face's pressure acts normal to the face. A face of length $\ell$ inclined at $\phi$ to the chord projects onto the chord as $\ell\cos\phi=c/2$ and onto the chord-normal as $\ell\sin\phi=t/2$. Per unit span, its force therefore has a component $p\,c/2$ normal to the chord and a component $p\,t/2$ along it.

Normal to the chord, positive upwards, the lower faces push up and the upper faces push down:

$$
N'=(p_{1l}-p_{1u})\frac c2+(p_{2l}-p_{2u})\frac c2 .
$$

Along the chord, which is drawn horizontal, the horizontal force $A'$ is positive towards the trailing edge. The front faces face forwards and are pushed rearwards, while the rear faces face backwards and are pushed forwards, in the negative $x$ direction:

$$
A'=(p_{1u}+p_{1l})\frac t2-(p_{2u}+p_{2l})\frac t2 .
$$

With $c=1$ m and $t=0.05$ m:

$$
N'=(62.86-52.28)(0.5)+(47.72-37.14)(0.5)=5.290+5.290=10.579\ \text{kN/m},
$$

$$
A'=(52.28+62.86)(0.025)-(37.14+47.72)(0.025)=2.879-2.121=0.757\ \text{kN/m}.
$$

Lift is perpendicular to $\vec U_\infty$ and drag parallel to it. The chord is pitched nose-up by $\alpha$, so the chord-normal direction is tilted back from the lift direction by $\alpha$, and the chordwise direction points downstream and down by $\alpha$. Resolving,

$$
L'=N'\cos\alpha-A'\sin\alpha=10.579\times0.99939-0.757\times0.03490=10.573-0.026=\boxed{10.55\ \text{kN/m}},
$$

$$
D'=A'\cos\alpha+N'\sin\alpha=0.757\times0.99939+10.579\times0.03490=0.757+0.369=\boxed{1.13\ \text{kN/m}}.
$$

So $L/D=9.37$. The sheet gives $L=10.5$ kN/m and $D=1.13$ kN/m.

The two force components separate the two kinds of wave drag. Put $p=p_\infty+q_\infty C_p$ into $N'$; the $p_\infty$ terms cancel, and on each half

$$
C_{p,1l}-C_{p,1u}=\frac2\lambda\left[(\phi+\alpha)-(\phi-\alpha)\right]=\frac{4\alpha}{\lambda},\qquad
C_{p,2l}-C_{p,2u}=\frac2\lambda\left[-(\phi-\alpha)+(\phi+\alpha)\right]=\frac{4\alpha}{\lambda},
$$

so

$$
N'=q_\infty c\,\frac{4\alpha}{\lambda}.
$$

In $A'$ the $p_\infty$ terms cancel too ($2p_\infty-2p_\infty$), and

$$
A'=\frac t2\,q_\infty\,\frac2\lambda\left[(\phi-\alpha)+(\phi+\alpha)+(\phi+\alpha)+(\phi-\alpha)\right]=\frac t2\,q_\infty\,\frac{8\phi}{\lambda}=\frac{4t\phi\,q_\infty}{\lambda}.
$$

With $\phi\simeq t/c$, $A'=q_\infty c\cdot4(t/c)^2/\lambda$: the chordwise force is the thickness wave drag, present at zero incidence. To first order in $\alpha$, $D'\simeq A'+N'\alpha$:

$$
\frac{D'}{q_\infty c}\simeq\frac{4}{\lambda}\left[\left(\frac tc\right)^2+\alpha^2\right],
$$

the diamond drag of [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#9. Thickness drag and the optimum section|W07c §9]], with drag due to thickness from $A'$ and drag due to lift from $N'\alpha$.

> [!check] Against the closed forms
> $C_l=4\alpha/\lambda=4(0.034907)/1.4967=0.09329$ gives $q_\infty cC_l=10.58$ kN/m, which is $N'$ (the closed form takes $L'\simeq N'$). $C_d=\frac4\lambda[\alpha^2+(t/c)^2]=0.00994$ gives 1.127 kN/m, against 1.126 face by face. $A'=4t\phi q_\infty/\lambda=0.7571$ kN/m reproduces the face sum.

## 4. Pitching moment and centre of pressure

Take moments about the leading edge, nose-up positive. A downward force behind the leading edge pitches the nose up, so each half of the chord contributes its net downward load, $(p_u-p_l)\,c/2$, times the distance to the middle of its projection, $c/4$ for the front half and $3c/4$ for the rear:

$$
M'_{LE}=(p_{1u}-p_{1l})\frac c2\cdot\frac c4+(p_{2u}-p_{2l})\frac c2\cdot\frac{3c}{4},
$$

$$
M'_{LE}=(52.28-62.86)(0.125)+(37.14-47.72)(0.375)=-1.322-3.967=\boxed{-5.29\ \text{kN m/m}},
$$

a nose-down moment, as on the sheet. The chordwise components act at the face midpoints, a height $t/4$ above or below the chord, and add $\frac{t^2}{8}\left[(p_{1u}-p_{1l})-(p_{2u}-p_{2l})\right]$ to the moment. That is zero here because both halves carry the same pressure difference, so the result above is exact for these pressures.

The centre of pressure, in the lift-based form of the formula sheet ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#2. Aerodynamic review and the low-speed baseline|W01 §2]]), is

$$
\frac{x_{CP}}{c}=-\frac{M'_{LE}}{L'c}=\frac{5.290}{10.546}=0.502,
$$

and with the chord-normal force, $-M'_{LE}/(N'c)=5.290/10.579=0.500$ exactly. The sheet's answer is 0.50.

Shock-expansion theory on the same section ([[SESA3029 Example Sheet 1 - Solutions#Q6. Diamond aerofoil by shock-expansion theory|ES1 Q6]]) gives $L'=10.64$ kN/m, $D'=1.13$ kN/m, $M'_{LE}=-5.01$ kN m/m and $x_{CP}=0.47c$. Lift and drag agree within 1 %, the moment within 6 %. The exact centre of pressure lies further forward because the front faces' shock on 1l compresses more than the linear formula allows, while the rear faces' fan on 2u expands less: the exact pressure difference is 11.96 kPa on the front half and 9.39 kPa on the rear (panel (c) of the figure), against 10.58 kPa on both in Ackeret theory.

## 5. The aerodynamic centre of a thin diamond is at half chord

For a very thin section at small incidence, $\cos\alpha\simeq1$ and $A'\sin\alpha$ is negligible, so $L'\simeq N'$. The lift per unit span is the pressure difference integrated along the chord:

$$
L'=\int_0^c(p_l-p_u)\,\mathrm dx .
$$

Add and subtract $p_\infty$ so that pressure coefficients can appear:

$$
L'=\int_0^c\left[(p_l-p_\infty)-(p_u-p_\infty)\right]\mathrm dx .
$$

Divide by $q_\infty c$:

$$
C_l=\frac1c\int_0^c\left(C_{p,l}-C_{p,u}\right)\mathrm dx .
$$

The faces change at mid-chord, so split the integral there:

$$
C_l=\frac1c\int_0^{c/2}\left(C_{p,1l}-C_{p,1u}\right)\mathrm dx+\frac1c\int_{c/2}^{c}\left(C_{p,2l}-C_{p,2u}\right)\mathrm dx .
$$

From §3 both integrands are the constant $4\alpha/\lambda$; the $\phi$ terms cancel on each half:

$$
C_l=\frac1c\cdot\frac{4\alpha}{\lambda}\cdot\frac c2+\frac1c\cdot\frac{4\alpha}{\lambda}\cdot\frac c2,
$$

$$
C_l=\frac{4\alpha}{\lambda}=\frac{4\alpha}{\sqrt{M_\infty^2-1}} .
$$

For the moment about the leading edge, the load $(p_u-p_l)\,\mathrm dx$ at distance $x$ pushes down and so pitches the nose up:

$$
M'_{LE}=\int_0^c(p_u-p_l)\,x\,\mathrm dx .
$$

A moment is a force times a length, so divide by $q_\infty c^2$:

$$
C_{m,LE}=\frac{1}{c^2}\int_0^c\left(C_{p,u}-C_{p,l}\right)x\,\mathrm dx .
$$

On each half $C_{p,u}-C_{p,l}=-4\alpha/\lambda$, the same magnitude as for the lift with the opposite sign, because the load now presses down:

$$
C_{m,LE}=-\frac{4\alpha}{\lambda c^2}\int_0^{c/2}x\,\mathrm dx-\frac{4\alpha}{\lambda c^2}\int_{c/2}^{c}x\,\mathrm dx .
$$

The constants come outside, leaving $\int x\,\mathrm dx=x^2/2$:

$$
C_{m,LE}=-\frac{4\alpha}{\lambda c^2}\left[\frac{x^2}{2}\right]_0^{c/2}-\frac{4\alpha}{\lambda c^2}\left[\frac{x^2}{2}\right]_{c/2}^{c},
$$

$$
C_{m,LE}=-\frac{4\alpha}{\lambda c^2}\cdot\frac{c^2}{8}-\frac{4\alpha}{\lambda c^2}\left(\frac{c^2}{2}-\frac{c^2}{8}\right),
$$

$$
C_{m,LE}=-\frac{4\alpha}{\lambda}\left(\frac18+\frac38\right)=-\frac{2\alpha}{\lambda}.
$$

Compare with $C_l=4\alpha/\lambda$:

$$
C_{m,LE}=-\tfrac12C_l .
$$

The aerodynamic centre is where the moment does not change with lift ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#2. Aerodynamic review and the low-speed baseline|W01 §2]]):

$$
\frac{\mathrm dC_{m,LE}}{\mathrm dC_l}=-\frac12
\quad\Rightarrow\quad
\boxed{\frac{x_{AC}}{c}=-\frac{\mathrm dC_{m,LE}}{\mathrm dC_l}=\frac12}
$$

Because $C_{m,LE}$ is proportional to $C_l$ with no constant term, $x_{CP}/c=-C_{m,LE}/C_l=\tfrac12$ as well: in Ackeret theory a symmetric diamond has its centre of pressure and its aerodynamic centre together at mid-chord at every incidence, against the quarter chord of subsonic thin-aerofoil theory ([[Aerodynamic Centre and Centre of Pressure]]). For ES2 Q5, $C_{m,LE}=-2(0.034907)/1.4967=-0.04665$, and $q_\infty c^2C_{m,LE}=-5.29$ kN m/m, the §4 moment.

The result does not depend on the diamond's shape. For any thin aerofoil with camber line $y_c(x)$ ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#6. A general thin aerofoil|W07c §6]]), the thickness slopes cancel and $C_{p,u}-C_{p,l}=\frac4\lambda\left(y_c'-\alpha\right)$, so

$$
C_{m,LE}=\frac{4}{\lambda c^2}\int_0^c\left(y_c'-\alpha\right)x\,\mathrm dx=-\frac{2\alpha}{\lambda}+\frac{4}{\lambda c^2}\int_0^cx\,y_c'\,\mathrm dx .
$$

Integrate the last term by parts, with $y_c(0)=y_c(c)=0$:

$$
\int_0^cx\,y_c'\,\mathrm dx=\Big[x\,y_c\Big]_0^c-\int_0^cy_c\,\mathrm dx=-\int_0^cy_c\,\mathrm dx,
$$

$$
C_{m,LE}=-\tfrac12C_l-\frac{4}{\lambda c^2}\int_0^cy_c\,\mathrm dx .
$$

The camber term does not depend on $\alpha$, so $\mathrm dC_{m,LE}/\mathrm dC_l=-\tfrac12$ again: every thin aerofoil has $x_{AC}=c/2$ in Ackeret theory, with $C_{m,AC}=-\frac{4}{\lambda c^2}\int_0^cy_c\,\mathrm dx$, nose-down for positive camber. A parabolic camber line of 2 % at $M_\infty=1.8$ gives $C_{m,AC}=-8(0.02)/(3\lambda)=-0.0356$.

The exact theory moves the point forward slightly. Shock-expansion theory at $\alpha=1.5^\circ$ and $2.5^\circ$ on this diamond gives $x_{AC}\approx0.47c$, and the triangular wing of [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing#Weekend homework: the aerodynamic centre|Tutorial 1]] gave $0.49c$: in both, the nonlinear difference between shock and fan loads the front of the section more.

## 6. Why Ackeret theory works across the shocks

Ackeret theory comes from the linearised potential equation, which assumes isentropic, irrotational flow everywhere ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]]). The diamond's front faces carry oblique shocks, across which the entropy rises and the isentropic relations no longer hold, and a shock is a jump rather than a small perturbation. Strictly the theory is wrong for this flow, and the shock-expansion method is the valid one. Yet the two answers for ES1 Q6 and ES2 Q5 differ by under 1 % in lift and drag.

The explanation is the size of the stagnation-pressure loss across these shocks, read from the normal-shock table (T2, ll. 252–293). Take the stronger shock, on the lower front face, which turns the flow by $\phi+\alpha=4.862^\circ$ at $M_\infty=1.8$; the upper front face turns it by only $0.862^\circ$. The oblique-shock chart gives $\beta\approx38^\circ$ ($38.30^\circ$ exactly), so

$$
M_{n1}=M_\infty\sin\beta=1.8\sin38.30^\circ=1.116 .
$$

The normal-shock table's nearest row, $M_{n1}=1.11$, gives $p_{02}/p_{01}=0.9986$; the exact value at 1.116 is 0.9984. The shock destroys 0.16 % of the stagnation pressure, so the flow is isentropic to within 0.2 % and the isentropic relations can be used across it with very little error. On the upper front face, $\beta=34.51^\circ$, $M_{n1}=1.020$ and $p_{02}/p_{01}=0.99999$.

The loss grows quickly with shock strength: $p_{02}/p_{01}=0.979$ at $M_{n1}=1.3$ (a 2 % loss) and $0.930$ at $M_{n1}=1.5$ (7 %); it reaches 1 % at $M_{n1}=1.23$, which at $M_\infty=1.8$ means a compression of $9.1^\circ$. While the normal Mach number stays below about 1.2, the error from assuming isentropic flow is small enough for engineering purposes; beyond that Ackeret theory loses accuracy.

![[at_tut2_weak_shock_loss.png|900]]

The reason the loss is so small is its order in the turning angle. For a weak shock write $m=M_{n1}^2-1$. The $\theta$–$\beta$–$M$ relation ([[Theta-Beta-Mach Relation]]) is

$$
\tan\theta=2\cot\beta\,\frac{M^2\sin^2\beta-1}{M^2(\gamma+\cos2\beta)+2}.
$$

As $\theta\to0$ the shock becomes a Mach wave, $\beta\to\mu$ with $\sin\mu=1/M$, so

$$
\cot\beta\to\cot\mu=\sqrt{M^2-1}=\lambda,\qquad\cos2\beta\to1-2\sin^2\mu=1-\frac{2}{M^2}.
$$

The denominator becomes

$$
M^2\left(\gamma+1-\frac2{M^2}\right)+2=(\gamma+1)M^2,
$$

and with $\tan\theta\simeq\theta$ and $M^2\sin^2\beta-1=m$,

$$
\theta\simeq\frac{2\lambda\,m}{(\gamma+1)M^2}
\quad\Rightarrow\quad
m\simeq\frac{(\gamma+1)M^2\,\theta}{2\lambda}.
$$

The shock strength is first order in $\theta$. The entropy jump is third order in $m$ ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#4. Entropy across a shock and why shocks compress|W03 §4]], [[Entropy Change Across a Shock]]):

$$
\frac{\Delta s}{c_v}\simeq\frac{2\gamma(\gamma-1)}{3(\gamma+1)^2}\,m^3 .
$$

With $c_v(\gamma-1)=R$,

$$
\frac{\Delta s}{R}\simeq\frac{2\gamma}{3(\gamma+1)^2}\,m^3,
$$

and since $p_{02}/p_{01}=e^{-\Delta s/R}\simeq1-\Delta s/R$,

$$
1-\frac{p_{02}}{p_{01}}\simeq\frac{2\gamma}{3(\gamma+1)^2}\cdot\frac{(\gamma+1)^3M^6\theta^3}{8\lambda^3}=\frac{\gamma(\gamma+1)M^6\,\theta^3}{12\lambda^3}\qquad(\theta\text{ in radians}).
$$

For face 1l, $\theta=0.08486$ rad: $1.4\times2.4\times34.01\times6.11\times10^{-4}/(12\times3.353)=0.0017$, against the exact 0.0016.

Ackeret theory itself is only first order: the terms it drops are of order $\theta^2$ in $C_p$, a relative error of order $\theta$. On face 1l its $C_p=0.1134$ is 9.9 % below the oblique-shock value of 0.1259, and on face 1u it is 1.8 % low. The isentropic assumption costs 0.16 % on the same face. So the error from ignoring the entropy rise is two orders of $\theta$ below the error the linearisation already accepts, and the shocks are not what limits the theory. On the panel (b) log scale the two errors have slopes 1 and 3. In the lift the linearisation errors on the upper and lower surfaces have opposite signs and largely cancel ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils#3. Ackeret's formula|W07c §3]]), which is why $C_l$ comes out within 1 %.

> [!tip] One order further (outside the course)
> Busemann's second-order theory adds a term to Ackeret's: $C_p=\dfrac{2\theta}{\lambda}+C_2\theta^2$ with $C_2=\dfrac{(\gamma+1)M_\infty^4-4M_\infty^2+4}{2\lambda^4}$, still for isentropic flow. At $M_\infty=1.8$, $C_2=1.618$, and face 1l gets $C_p=0.1250$, within 0.7 % of the shock value. Entropy first enters at third order, which is why a shock-free theory matches shocked flow to second order in $\theta$.

> [!check] Numerical check (Python)
> Exact $\theta$–$\beta$–$M$ roots, normal-shock and Prandtl–Meyer relations ($\gamma=1.4$) reproduce every number in this note: Ackeret pressures 52.281, 62.860, 37.140, 47.719 kPa; $N'=10.579$, $A'=0.757$, $L'=10.546$, $D'=1.126$ kN/m; $M'_{LE}=-5.290$ kN m/m by both the half-chord arms and the exact face-midpoint geometry; shock-expansion pressures 52.32, 64.28, 38.39, 47.77 kPa and $x_{CP}=0.471c$; $\beta=38.30^\circ$, $M_{n1}=1.1157$, $p_{02}/p_{01}=0.99839$.

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Theory: [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]] (Ackeret's formula, the diamond's drag) · [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#4. Entropy across a shock and why shocks compress|W03 §4]] (entropy jump) · [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#2. Aerodynamic review and the low-speed baseline|W01 §2]] ($x_{CP}$ and $x_{AC}$)
- Previous tutorial: [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing]]
- Worked sheets: [[SESA3029 Example Sheet 2 - Solutions#Q5. Diamond aerofoil by Ackeret theory|ES2 Q5]] · [[SESA3029 Example Sheet 1 - Solutions#Q6. Diamond aerofoil by shock-expansion theory|ES1 Q6]] · [[SESA3029 Example Sheet 1 - Solutions#Q7. Wave patterns at α = 5°, 2.86° and −2.86°|ES1 Q7]] (wave patterns) · [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|ES2 Q3]] (MoC)
- Past papers: [[SESA3029 Past Paper 2024-25 A - Solutions#Q1. Nozzle flow, wall shock reflection and half-diamond aerofoil (34 marks)|2024–25 A Q1]] · [[SESA3029 Past Paper 2015-16 - Solutions#Q2. 8° diamond aerofoil at Mach 1.6 (30 marks)|2015–16 Q2]] · [[SESA3029 Past Papers - Question Map]]
- Concepts: [[Ackeret Theory]] · [[Entropy Change Across a Shock]] · [[Theta-Beta-Mach Relation]] · [[Supersonic Wave Drag]] · [[Shock-Expansion Theory]] · [[Aerodynamic Centre and Centre of Pressure]] (SESA2022)
- Full derivations: [[SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils]]
- Formulae: [[SESA3029 Formula Sheet#Euler equations and compressible aerofoils|Formula sheet: Chapter 4]]
- Next: heat transfer (Section 5), from Thu 19 Nov

## Sources

- `02 - Sources/Lectures/Tutorial Lecture #2.txt` (T2): Mon 16 Nov, 298 lines copied from the Panopto captions, each line prefixed with its timestamp; Prof. Jae-Wook Kim. Ll. 1–25: ES2 Q3 as own work and the Blackboard resources; ll. 29–113: ES2 Q5 angles, $C_p$, pressures and forces; ll. 114–125: the exam warning on the angles; ll. 126–136: moment and centre of pressure; ll. 137–219: the proof that $x_{AC}=c/2$; ll. 220–297: why Ackeret theory survives the shocks. This was Prof. Kim's last lecture of the module; heat transfer starts on Thu 19 Nov (ll. 220–223).
- The tutorial slides are on Blackboard (Lecture slides → Tutorial lectures) and are not filed; the working here follows the transcript and the example sheets.
- `03 - Exams & Past Papers/ExamplesSheet2.pdf`, Q3 and Q5; `ExamplesSheet1.pdf`, Q6.
- Figures: `01 - Notes/Figures/generate_aerothermo_tutorial_figures.py` (`tut2_diamond_faces`, `tut2_weak_shock_loss`).

## Self-study tasks

Blackboard's *Example questions and solutions* folder also holds the three example sheets with solutions, Anderson's end-of-chapter questions with solutions, and feedback on past exams, for revision (T2, ll. 17–23).

### Core

- [ ] **(T2, ll. 29–136)** ES2 Q5 (a)–(c) by Ackeret theory, face by face, with $c=1$ m. Answers 52.3, 37.1, 62.9, 47.7 kPa; $L'=10.55$ kN/m, $D'=1.13$ kN/m; $M'_{LE}=-5.29$ kN m/m; $x_{CP}=0.50c$. → [[#1. The four face angles|§§1–4]]
- [ ] **(T2, ll. 115–125)** Practise the four angles until they are automatic, since an early angle error loses most of the question. Same diamond at $\alpha=1^\circ$, $3^\circ$ and $-2^\circ$ (these angles are suggested): give $\theta$ and compression or expansion for faces 1u, 2u, 1l, 2l. Answers: $1^\circ$: $+1.862^\circ$, $-3.862^\circ$, $+3.862^\circ$, $-1.862^\circ$; $3^\circ$: $-0.138^\circ$ (1u expands), $-5.862^\circ$, $+5.862^\circ$, $+0.138^\circ$ (2l compresses); $-2^\circ$: $+4.862^\circ$, $-0.862^\circ$, $+0.862^\circ$, $-4.862^\circ$. → [[#1. The four face angles|§1]]
- [ ] **(T2, ll. 137–219)** Derive $C_l=4\alpha/\lambda$ and $C_{m,LE}=-2\alpha/\lambda$ for a thin diamond, and show that $x_{AC}=c/2$. → [[#5. The aerodynamic centre of a thin diamond is at half chord|§5]]
- [ ] **(T2, ll. 220–244; answered ll. 252–293)** Explain why Ackeret theory, derived for isentropic flow, still works on a section carrying shocks. Use the table: $M_{n1}=1.11$ gives $p_{02}/p_{01}=0.9986$. → [[#6. Why Ackeret theory works across the shocks|§6]]
- [ ] **(T2, ll. 29–35)** ES1 Q6, the same diamond by shock-expansion theory, and compare. Answers 52.3, 38.4, 64.3, 47.8 kPa; $L'=10.6$ kN/m, $D'=1.13$ kN/m; $M'_{LE}=-5.01$ kN m/m; $x_{CP}=0.47c$. → [[SESA3029 Example Sheet 1 - Solutions#Q6. Diamond aerofoil by shock-expansion theory|ES1 Q6]], comparison in [[#4. Pitching moment and centre of pressure|§4]]

### Further practice

- [ ] **(T2, ll. 3–12)** ES2 Q3, the MoC question in mock-exam form with a given wall shape. Answers: flow angle at C $14.34^\circ$; $M_C=1.558$, $M_D=1.256$, $M_F=1.606$. → [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|ES2 Q3]]
- [ ] **(T2, ll. 115–117)** 2024–25 Paper A Q1(iii)–(v), the half-diamond on last year's paper. → [[SESA3029 Past Paper 2024-25 A - Solutions#Q1. Nozzle flow, wall shock reflection and half-diamond aerofoil (34 marks)|2024–25 A Q1]]
- [ ] 2015–16 Q2: an $8^\circ$ diamond at $M_\infty=1.6$ by both methods. → [[SESA3029 Past Paper 2015-16 - Solutions#Q2. 8° diamond aerofoil at Mach 1.6 (30 marks)|2015–16 Q2]]
- [ ] (suggested, not lecturer-set) Show that $x_{AC}=c/2$ for any thin cambered aerofoil in Ackeret theory, and find $C_{m,AC}$ for a 2 % parabolic camber line at $M_\infty=1.8$. Answer $-0.0356$. → [[#5. The aerodynamic centre of a thin diamond is at half chord|§5]]
- [ ] (suggested, not lecturer-set) Find the $M_{n1}$ at which $p_{02}/p_{01}$ falls to 0.99, and the compression angle that produces it at $M_\infty=1.8$. Answers $M_{n1}=1.23$, $\theta=9.1^\circ$. → [[#6. Why Ackeret theory works across the shocks|§6]]

## Transcript and slide slips

### Transcript slips (Tutorial 2)

Whisper writes Ackeret as *"accurate"*/*"occurs"*, aerofoil as *"air force"*/*"L4"*/*"office"*/*"airflow"*, chord as *"code"*/*"court"*, shock as *"shop"*/*"show"*/*"choke"*, expansion fan as *"extension fan"*, stagnation as *"Spanish"*/*"station"*/*"tension"*, free stream as *"friction"* (l. 81), lift and drag as *"left hand drag"* (l. 111), and moment arm as *"momentum"*; these are not listed below.

| Line | Said | Correct | Where |
|---|---|---|---|
| l. 3 | *"exemption number two"* | Example Sheet 2 | intro |
| l. 29 | *"diamond ring"* | diamond-shaped aerofoil | [[#1. The four face angles]] |
| ll. 37, 63–64, 77, 163, 167 | half vertex angle $\phi$ (ll. 49, 62, 70) written *"V"*, *"v"*, *"fy"*, *"Fi"* | $\phi=\tan^{-1}0.05=2.862^\circ$ | [[#1. The four face angles]] |
| l. 57 | $C_{p,1u}$ *"two times three minus alpha"* | $2(\phi-\alpha)/\lambda$ | [[#2. Pressure on each face]] |
| l. 58 | *"lambda is m squared minus one"* | $\lambda=\sqrt{M_\infty^2-1}$ | [[#2. Pressure on each face]] |
| l. 98 | *"one plus half gamma m squared times dt"* | $\times\,C_p$ | [[#2. Pressure on each face]] |
| l. 103 | normal force *"normal to the horizontal"* | normal to the chord (drawn horizontal) | [[#3. Lift and drag from the face forces]] |
| ll. 112–113 | drag *"horizontal force equals to alpha plus normal force sin alpha"* | $D'=A'\cos\alpha+N'\sin\alpha$ | [[#3. Lift and drag from the face forces]] |
| ll. 129–132 | *"the momentum is at the quarter chord… three quarters"* | moment arms $c/4$ and $3c/4$ | [[#4. Pitching moment and centre of pressure]] |
| l. 134 | centre of pressure *"pitch moment divided by lift times chord"* | $x_{CP}/c=-M'_{LE}/(L'c)$; the minus sign follows at l. 135 | [[#4. Pitching moment and centre of pressure]] |
| l. 149 | *"close to one, it's close to almost alpha"* | $\cos\alpha\simeq1$, so $L'\simeq N'$ | [[#5. The aerodynamic centre of a thin diamond is at half chord]] |
| l. 154 | *"divide this equation by half rho you see"* | divide by $\tfrac12\rho_\infty U_\infty^2c$ | [[#5. The aerodynamic centre of a thin diamond is at half chord]] |
| l. 173 | *"four alpha over v squared minus one"* | $4\alpha/\sqrt{M_\infty^2-1}$ | [[#5. The aerodynamic centre of a thin diamond is at half chord]] |
| l. 182 | divide by *"half rho u squared and z squared"* | $\tfrac12\rho_\infty U_\infty^2c^2$ | [[#5. The aerodynamic centre of a thin diamond is at half chord]] |
| ll. 201–204 | *"Alpha is equal. Lambda times c is equal to two c squared"* | $-\dfrac{4\alpha}{\lambda}\left(\dfrac18+\dfrac38\right)=-\dfrac{2\alpha}{\lambda}$ | [[#5. The aerodynamic centre of a thin diamond is at half chord]] |
| l. 253 | *"the key answer is in the isentropic flow table"* | the normal-shock table (corrected at ll. 271–273) | [[#6. Why Ackeret theory works across the shocks]] |
| l. 256 | *"cloning angle alpha is two degrees 22.862 degrees"* | $\alpha=2^\circ$, $\phi=2.862^\circ$ | [[#6. Why Ackeret theory works across the shocks]] |
| ll. 266–268 | shock angle *"3038… let's take 30 degrees… 38 degrees"* | $\beta\approx38^\circ$ from the chart ($38.30^\circ$) | [[#6. Why Ackeret theory works across the shocks]] |
| l. 270 | $1.8\sin38^\circ$ *"is 1.11"* | 1.108 (1.116 with $\beta=38.30^\circ$); the same table row | [[#6. Why Ackeret theory works across the shocks]] |
| l. 279 | $p_{02}/p_{01}$ *"0.998"* | 0.9986 at $M_{n1}=1.11$ (0.9984 at 1.116) | [[#6. Why Ackeret theory works across the shocks]] |
| l. 286 | at $M_{n1}=1.3$ the ratio *"is 0.79"* | 0.9794, the 2 % loss said at l. 287 | [[#6. Why Ackeret theory works across the shocks]] |
| ll. 287–288 | *"up to about 10% difference"* at $M_{n1}\approx1.5$ | 7.0 % ($p_{02}/p_{01}=0.9298$); 10 % is reached at $M_{n1}=1.59$ | [[#6. Why Ackeret theory works across the shocks]] |
| l. 291 | *"isentropic flow summation"* | isentropic-flow assumption | [[#6. Why Ackeret theory works across the shocks]] |
