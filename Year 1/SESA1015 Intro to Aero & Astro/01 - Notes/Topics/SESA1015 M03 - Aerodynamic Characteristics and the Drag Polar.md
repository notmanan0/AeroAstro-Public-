---
title: "SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 3
tags:
  - sesa1015
  - mechanics-of-flight
  - lift-curve
  - drag-polar
  - pitching-moment
  - aerodynamic-centre
  - lift-generation
aliases: ["SESA1015 Mechanics 3", "Aerodynamic Characteristics", "Typical Aerodynamic Characteristics for Conventional Aircraft"]
date: 2026-09-27
status: lectured
coverage: "Lecture Slides v2 pp. 25–33 (how lift is generated: momentum deflection, Venturi and equal-transit explanations, streamline curvature and circulation); Course notes §3.1–3.5 (lift coefficient, drag coefficient, pitching moment coefficient, centre of pressure, aerodynamic centre); Lecture Slides v2 pp. 49–63 (lift coefficient, finite-wing lift-curve slope, drag sources, drag polar, worked example p. 59) and pp. 196–200 (aerodynamic moment and the wind-tunnel location of the aerodynamic centre)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]"]
next_topics: ["[[SESA1015 M04 - Steady Level Flight and Stall]]"]
key_concepts: ["[[Kutta-Joukowski Theorem]]", "[[Lift-Curve Slope]]", "[[Parabolic Drag Polar]]", "[[Aerodynamic Centre and Centre of Pressure]]", "[[Dynamic Pressure and Aerodynamic Coefficients]]", "[[Downwash and Induced Drag]]"]
tutorial_sheets: ["[[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§3.1–3.5, pp. 12–18)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 25–33, 49–63, 196–200)", "04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (Q9–Q12)"]
---

# SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar

> [!abstract] Summary
> Lift comes from the pressure field of the curved flow round the wing: across curved streamlines $\partial p/\partial n=\rho V^2/R$, which lowers the pressure on the upper surface (inside the bend) and raises it on the lower surface (outside the bend); the popular equal-transit explanation is false. A conventional subsonic aircraft is then described by three curves. Below the stall the lift coefficient is linear in angle of attack, $C_L=a(\alpha-\alpha_0)$, with a negative no lift angle $\alpha_0$ for a cambered wing and $C_{L\max}\approx1.2$ clean. The drag coefficient is the parabolic polar $C_D=C_{D0}+KC_L^2$ with $K=1/\pi eAR$, profile drag plus induced drag. The pitching moment coefficient about any axis is linear in $C_L$, $C_m=C_{mo}-hC_L$; the point about which it does not vary is the aerodynamic centre ($x_{AC}/c=-h$, near the quarter chord), while the centre of pressure, where the lift acts with no moment, moves with $C_L$ as $x_{cp}/c=C_{mo}/C_L-h$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives wind-tunnel forces or moments, a lift curve, a drag polar or moment data and asks for $a$, $\alpha_0$, $C_{D0}$, $K$ (or $e$), the aerodynamic centre or the centre of pressure.
> - **Assumptions:** attached, incompressible flow below the stall; linear lift curve; parabolic polar; moments positive nose up and distances $x$ measured forward of the CG; $C_m$ based on $\tfrac12\rho V^2Sc$.
> - **Method:** 1. Turn every force into a coefficient with $qS$ (and every moment with $qSc$). 2. Two points on the lift line give $a$ and $\alpha_0$. 3. Write $C_D=C_{D0}+KC_L^2$ at two points and subtract to get $K$, then $C_{D0}$. 4. Two moment readings in $C_{m,CG}=C_{mo}+(x_{AC}/c)C_L$ give $x_{AC}$ and $C_{mo}$. 5. $x_{cp}/c=x_{AC}/c+C_{mo}/C_L$.
> - **Common mistakes:** mixing per-degree and per-radian slopes; taking $C_D$ at the lowest test angle as $C_{D0}$ when $C_L$ there is not zero.
> - **Practise:** [[#Locating the aerodynamic centre from tunnel data]] · [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 12]]

Lift, drag and pitching moment reduce to coefficients ([[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients|M02]]): $L=\tfrac12\rho V^2SC_L$, $D=\tfrac12\rho V^2SC_D$ and $M=\tfrac12\rho V^2ScC_m$. For a given shape, at low Mach number and with the Reynolds-number dependence ignored, each coefficient depends on angle of attack alone, so an aircraft's aerodynamics can be summarised by three graphs. Performance and stability calculations need only a handful of numbers read from them: the lift-curve slope and no lift angle, $C_{L\max}$, the profile drag coefficient and induced drag factor, and the moment at zero lift with the position of the aerodynamic centre.

Lift grows linearly with angle of attack because the flow stays attached and the circulation round the wing is set by the Kutta condition; it stops growing when the boundary layer separates from the upper surface and the wing stalls. Drag has a part that is present even at zero lift, from skin friction and the pressure imbalance caused by the boundary layer, and a part that exists only because the wing lifts: the trailing vortices push down on the air at the wing, which tilts the lift vector back. The moment is linear in lift because, below the stall, adding lift amounts to adding a force at one fixed point of the wing, the aerodynamic centre.

The values here are typical of a conventional aircraft with an unswept wing and a conventional tailplane in subsonic flight, below the speeds where compressibility matters. Compressibility, the drag rise and the transonic case are outside this module apart from the brief remarks in [[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]].

---

## 1. How a wing generates lift

Lift is the resultant of the pressure and shear stress over the whole surface resolved perpendicular to the free stream ([[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients|M02]]), and the shear stress contributes almost nothing to it. Any explanation of lift is therefore an explanation of why the pressure on the upper surface is below the pressure on the lower surface. Three popular explanations are widely quoted. Two contain something true and one is wrong; the explanation that holds up is the curvature of the flow.

![[mof_m03_lift_curvature.png|900]]

### Momentum deflection: the skipping-stone picture

In this picture air molecules strike the lower surface and bounce off downwards, like a stone skipping on water, and the reaction pushes the wing up. Part of this is right. A lifting wing does leave the air moving downwards behind it (the downwash), and by Newton's second and third laws the lift equals the rate at which the wing gives downward momentum to the air. What is wrong is the mechanism. Air at these densities behaves as a continuum, not as independent particles, and the flow starts to bend well ahead of the wing (an upwash) and well above it. The air passing over the upper surface is turned downwards too, and the suction there usually supplies most of the lift.

The particle model can be tested. For a flat plate of chord $c$ at angle of attack $\alpha$, the air that strikes the plate per unit span and per unit time is the mass in a stream tube of height $c\sin\alpha$:

$$
\dot m'=\rho Vc\sin\alpha .
$$

If each particle loses its velocity component normal to the plate, $V\sin\alpha$, and keeps the tangential one, the normal force per unit span is the rate of loss of normal momentum:

$$
\begin{aligned}
N'&=\dot m'\,V\sin\alpha\\
&=\rho V^2c\sin^2\alpha .
\end{aligned}
$$

Dividing by $\tfrac12\rho V^2c$ and resolving perpendicular to the stream,

$$
\begin{aligned}
C_N&=2\sin^2\alpha,\\
C_L&=C_N\cos\alpha=2\sin^2\alpha\cos\alpha .
\end{aligned}
$$

At $\alpha=5^\circ$ this gives $C_L=0.015$, against $2\pi\alpha=0.548$ from thin aerofoil theory, which measured lift curves follow closely at small angles: the impact model is low by a factor of 36, and it grows as $\alpha^2$ where the real lift is linear in $\alpha$. The momentum statement on its own is not wrong, but it cannot say how much the air is deflected; that is set by the pressure field.

### The Venturi picture

Here the upper surface is treated as half of a Venturi nozzle. The flow is said to be squeezed, so by continuity ($VA$ constant) it speeds up, and by Bernoulli the faster flow has a lower pressure. The second half is right: the flow over the upper surface is faster than the free stream, and since every streamline starts from the same uniform upstream state, the [[Bernoulli Equation]] (steady, incompressible, inviscid flow outside the boundary layer) does give a lower pressure where the speed is higher. The first half is not. A Venturi tube has a second wall that fixes the throat area, so continuity then fixes the speed. Above a wing there is no outer wall. The stream tubes above the wing do narrow, but that narrowing is part of the flow solution, not a constraint that causes it, so the argument is circular and cannot predict how much faster the flow goes. Nor can it explain why lift depends so strongly on angle of attack, or why a flat plate, a symmetric aerofoil at incidence or an aircraft flying inverted produces lift.

### Equal transit is false

The longer-path or equal-transit explanation says that the upper surface is longer than the lower one, that air parcels separated at the leading edge must meet again at the trailing edge, and therefore that the upper parcels must travel faster, giving a lower pressure by Bernoulli. There is no physical law that makes the two parcels meet. Measured and computed flows show the opposite of what the argument needs: the parcel that passes over the upper surface reaches the trailing edge well before its neighbour that went underneath, and the two never rejoin (panel (c) of the figure: 0.36 chord lengths of free-stream travel earlier for that aerofoil at $5^\circ$).

Even taken at face value the argument fails quantitatively. Equal transit times over surface lengths $s_u$ and $s_l$ mean $V_u/V_l=s_u/s_l$. With $V_l=V_\infty$ on the lower surface, Bernoulli between the two surfaces gives

$$
\begin{aligned}
p_l-p_u&=\tfrac12\rho\left(V_u^2-V_l^2\right)\\
&=\tfrac12\rho V_\infty^2\left[\left(\frac{s_u}{s_l}\right)^2-1\right],\\
\Delta C_p&=\left(\frac{s_u}{s_l}\right)^2-1 ,
\end{aligned}
$$

and if this pressure difference acted over the whole chord, $C_l=\Delta C_p$. For the NACA 4412 of [[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients|M02]], $s_u=1.0385c$ and $s_l=1.0095c$, so $s_u/s_l=1.0288$ and $C_l=0.058$ at zero incidence. Thin aerofoil theory gives $C_l=2\pi\times4.15^\circ\times\pi/180=0.456$ for the same section (its no lift angle is $-4.15^\circ$), about eight times more. The path lengths are also fixed by the shape, so equal transit predicts no change of lift with angle of attack and no lift at all from a flat plate or a symmetric section, all contradicted by every lift curve in [[#2. The lift coefficient]].

### Curved streamlines and the pressure across them

A wing at a small angle of attack, with a rounded leading edge and a sharp trailing edge, turns the flow that passes it: the flow follows the surface and leaves the trailing edge smoothly. Any fluid parcel moving on a curved path accelerates towards the centre of curvature, and a centripetal acceleration needs a force, $F=mV^2/R$. Outside the thin boundary layer friction is negligible, and gravity changes the pressure only hydrostatically, by an amount far below the dynamic pressures here, so the force must come from a pressure difference across the streamlines.

Take a small element of fluid on a streamline of local radius of curvature $R$ (panel (a) of the figure), of length $\delta s$ along the streamline, thickness $\delta n$ across it and unit depth. Let $n$ be measured along the normal, away from the centre of curvature. The element's mass and its acceleration towards the centre are

$$
m=\rho\,\delta s\,\delta n,\qquad a=\frac{V^2}{R}.
$$

The pressure on its inner face is $p$ and on its outer face $p+(\partial p/\partial n)\,\delta n$. The inner face pushes the element away from the centre and the outer face pushes it towards the centre, so the net pressure force towards the centre is

$$
\begin{aligned}
F&=\left(p+\frac{\partial p}{\partial n}\delta n\right)\delta s-p\,\delta s\\
&=\frac{\partial p}{\partial n}\,\delta n\,\delta s ,
\end{aligned}
$$

where the small difference between the lengths of the inner and outer faces only adds terms of higher order in $\delta n$. Newton's second law towards the centre, $F=ma$, then gives

$$
\begin{aligned}
\frac{\partial p}{\partial n}\,\delta n\,\delta s&=\rho\,\delta s\,\delta n\,\frac{V^2}{R}\\
\frac{\partial p}{\partial n}&=\frac{\rho V^2}{R} .
\end{aligned}
$$

The pressure rises with distance from the centre of curvature, and the gradient is steeper the faster and the more tightly curved the flow. A straight streamline ($R\to\infty$) has no pressure gradient across it. This is the cross-stream half of the Euler equation, derived in general in [[SESA1016 T10 - Euler and Bernoulli Equations#Acceleration along and across the path]].

Applied to the wing, the result gives the sign of the pressure on each surface without any appeal to path lengths. The flow over the upper surface bends round the wing, so its centre of curvature lies on the wing side, below the streamlines. Moving upwards from the surface is moving away from that centre, so the pressure rises from the surface value to $p_\infty$ far above:

$$
p_\infty-p_{upper}=\int_{\text{surface}}^{\infty}\frac{\rho V^2}{R}\,dn>0 .
$$

The upper surface sits on the inside of the bend and its pressure is below ambient. Below the wing the flow rises ahead of the wing (upwash) and is turned downwards along the lower surface, so it curves the same way, with its centre of curvature below it. The lower surface is now on the outside of the bend: moving up from the undisturbed air far below towards the wing is moving away from the centre, so the pressure rises towards the surface and $p_{lower}>p_\infty$. Suction above and raised pressure below both push the wing up (panel (b)). Where the flow bends most sharply, round the leading edge and over the front of the upper surface, $R$ is smallest and the speed largest, so for the same mass and speed $mV^2/R_1>mV^2/R_2$ when $R_1<R_2$ and the pressure difference across the flow is largest there; this is the suction peak near the leading edge.

> [!check] Curvature integral against Bernoulli
> In the potential flow of panel (b) ($C_l=0.966$), integrating $V^2/R$ up the vertical line above mid-chord from the surface to ten chords above it gives $\Delta p/\rho=0.3136\,V_\infty^2$; Bernoulli between the same two points gives $0.3136\,V_\infty^2$ (agreement to 0.02 %, the residual coming from the line not being exactly normal to the streamlines). The surface pressure coefficient there is $C_p=-0.64$.

The pressure differences involved are small. A 1350 kg light aircraft with $S=16.25$ m² needs an average pressure difference across the wing of $W/S=814$ Pa, under 1 % of sea-level atmospheric pressure.

The flow follows the surface because a pressure field forms that bends it round, not because friction holds it on. Viscosity matters in two places: at the sharp trailing edge, where it makes the flow leave smoothly (the [[Kutta Condition]], [[SESA2022 T4 - Thin Aerofoil Theory#Kutta condition]]), and in the boundary layer, which separates if the pressure rise towards the trailing edge is too steep. Separation is the stall of [[#2. The lift coefficient]] ([[Boundary Layer Separation]]).

### Circulation and lift

The flow over the upper surface is faster than the flow under the lower surface, so the motion round the wing has a net circulating part, the difference in the circular motion at the top and at the bottom. It is measured by the **circulation** $\Gamma$, the line integral of the velocity round a closed loop enclosing the aerofoil. Taking the loop clockwise round a thin aerofoil, along the upper surface from leading to trailing edge with the flow and back along the lower surface against it,

$$
\Gamma=\int_0^c V_u\,dx-\int_0^c V_l\,dx=\int_0^c\left(V_u-V_l\right)dx .
$$

The pressure difference at each chordwise station follows from Bernoulli:

$$
\begin{aligned}
p_l-p_u&=\tfrac12\rho\left(V_u^2-V_l^2\right)\\
&=\tfrac12\rho\left(V_u+V_l\right)\left(V_u-V_l\right)\\
&\approx\rho V_\infty\left(V_u-V_l\right),
\end{aligned}
$$

where the last line uses $V_u+V_l\approx2V_\infty$ for a thin aerofoil at a small angle of attack, whose surface speeds differ from $V_\infty$ by small amounts. Integrating along the chord gives the lift per unit span:

$$
\begin{aligned}
L'&=\int_0^c\left(p_l-p_u\right)dx\\
&=\rho V_\infty\int_0^c\left(V_u-V_l\right)dx\\
&=\rho V_\infty\Gamma .
\end{aligned}
$$

This is the [[Kutta-Joukowski Theorem]], which holds exactly for any two-dimensional aerofoil in incompressible potential flow. The lift is fixed once the circulation is known, and the Kutta condition fixes the circulation for a given shape and angle of attack. Designing an aerofoil or wing is largely a matter of shaping its camber, thickness and planform to produce the circulation, and the distribution of it, that the mission needs. For the aerofoil in the figure, $\Gamma=0.483\,V_\infty c$ and $C_l=2\Gamma/(V_\infty c)=0.966$. For the full theory, including how the Kutta condition sets $\Gamma$ and why $dC_l/d\alpha=2\pi$, see [[SESA2022 T3 - Potential Flow]] and [[SESA2022 T4 - Thin Aerofoil Theory]].

## 2. The lift coefficient

For a conventional aircraft $C_L$ rises approximately linearly with angle of attack up to about 10 to 15 degrees. Beyond that the flow separates from the upper surface of the wing, $C_L$ stops rising, then falls, and the drag rises sharply: the aircraft has **stalled**. In the clean configuration (flaps, slats and undercarriage retracted) the **maximum lift coefficient** is about

$$
C_{L\max}\approx1.2,
$$

and this is the number to carry into any first design estimate; taking $C_{L\max}=1$ is a conservative start. Values from 1.2 to about 2.5 cover most aircraft, and sophisticated flaps and slats reach 3.0 or more.

![[mof_m03_lift_curve.png|900]]

### The linear lift curve

On the straight part of the curve the lift coefficient is fixed by two numbers. The **no lift angle** $\alpha_0$ is the angle of attack at which $C_L=0$; it is negative for a cambered wing, which lifts at zero angle, and zero for a symmetric one. The **lift-curve slope** is

$$
a=\frac{dC_L}{d\alpha},
$$

so the equation of the straight line through $(\alpha_0,0)$ with slope $a$ is

$$
C_L=a(\alpha-\alpha_0).
$$

A typical aircraft in the clean configuration has

$$
C_L=0.09(\alpha+2)\qquad(\alpha\ \text{in degrees}),
$$

that is $a=0.09$ per degree and $\alpha_0=-2^\circ$.

The slope depends on the unit of angle. Since $1\ \text{rad}=180/\pi=57.3^\circ$, a change of one radian is a change of $57.3$ degrees and

$$
\begin{aligned}
a_{\text{per rad}}&=\frac{dC_L}{d\alpha_{\text{rad}}}=\frac{dC_L}{d\alpha_{\text{deg}}}\,\frac{d\alpha_{\text{deg}}}{d\alpha_{\text{rad}}}\\
&=\frac{180}{\pi}\,a_{\text{per deg}} .
\end{aligned}
$$

For the typical aircraft, $a=0.09\times57.30=5.16$ per radian, and $\alpha_0=-2/57.3=-0.0349$ rad, so

$$
C_L=5.16\,(\alpha+0.0349)\qquad(\alpha\ \text{in radians}),
$$

usually rounded to $5(\alpha+2/57.3)$ or $5.2(\alpha+0.035)$. A slope near 0.1 per degree, or near 5 to 6 per radian, is the sanity check on any reduced tunnel data.

In the cruise $C_L$ is typically 0.2 to 0.5 (0.3 to 0.6 for some designs). Take-off and landing are flown much more slowly, and since $L=W$ the lift coefficient must then be much larger, so the aircraft operates close to $C_{L\max}$. That is why high-lift devices exist: deploying flaps and slats raises $C_{L\max}$, moves $\alpha_0$ more negative (the line shifts up) and, with slats, raises the stall angle too. The flapped curve in the figure is illustrative.

### Two-point reduction of a lift curve

A wind-tunnel balance gives lift $L_1$ and $L_2$ at angles $\alpha_1$ and $\alpha_2$ for a tunnel speed $V$. With $q=\tfrac12\rho V^2$, each reading becomes

$$
C_{L1}=\frac{L_1}{qS},\qquad C_{L2}=\frac{L_2}{qS}.
$$

Both points lie on $C_L=a(\alpha-\alpha_0)$:

$$
C_{L1}=a(\alpha_1-\alpha_0),\qquad C_{L2}=a(\alpha_2-\alpha_0).
$$

Subtracting the first from the second removes $\alpha_0$:

$$
\begin{aligned}
C_{L2}-C_{L1}&=a(\alpha_2-\alpha_1)\\
a&=\frac{C_{L2}-C_{L1}}{\alpha_2-\alpha_1}.
\end{aligned}
$$

Rearranging the first equation then gives the intercept on the $\alpha$ axis:

$$
\begin{aligned}
\alpha_1-\alpha_0&=\frac{C_{L1}}{a}\\
\alpha_0&=\alpha_1-\frac{C_{L1}}{a}.
\end{aligned}
$$

Both points must be on the straight part of the curve; with more than two points a least-squares line over the linear range does the same job. Revision Q9 and Q10 are exactly this calculation ([[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 9]], [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 10]]).

### The finite wing has a smaller slope than its aerofoil

Thin aerofoil theory gives a two-dimensional section the slope $a_0=2\pi$ per radian ([[SESA2022 T4 - Thin Aerofoil Theory]]). A wing of finite span has a smaller slope because its trailing vortices induce a downwash at the wing, which reduces the angle of attack each section actually sees by the **induced angle** $\alpha_i$. Finite-wing theory ([[SESA2022 T5 - Finite Wing Theory]]) gives, for a wing of aspect ratio $AR$,

$$
\alpha_i=\frac{C_L}{\pi AR}(1+\tau),
$$

where $\tau\ge0$ depends on the planform and its spanwise lift distribution, with $\tau=0$ for the elliptic distribution and $\tau\approx0$ to $0.3$ in practice. The sections work at the effective angle $\alpha-\alpha_i$, so

$$
C_L=a_0(\alpha-\alpha_0-\alpha_i).
$$

Substituting $\alpha_i$ and collecting the $C_L$ terms,

$$
\begin{aligned}
C_L&=a_0(\alpha-\alpha_0)-\frac{a_0(1+\tau)}{\pi AR}\,C_L\\
C_L\left[1+\frac{a_0(1+\tau)}{\pi AR}\right]&=a_0(\alpha-\alpha_0)\\
C_L&=\underbrace{\frac{a_0}{1+\dfrac{a_0(1+\tau)}{\pi AR}}}_{a}\,(\alpha-\alpha_0).
\end{aligned}
$$

The wing slope is therefore

$$
a=\frac{a_0}{1+\dfrac{a_0}{\pi AR}(1+\tau)}\qquad(a,\ a_0\ \text{per radian}),
$$

which is always less than $a_0$ and tends to it as $AR\to\infty$ (right-hand panel of the figure). The formula holds with both slopes per radian; the angles in $C_L=a(\alpha-\alpha_0)$ must then be in radians too. See [[Lift-Curve Slope]].

> [!check] Wing slope against the typical value
> With $a_0=2\pi$ and $\tau=0.1$, an aspect ratio of 7 gives $a=2\pi/(1+2\pi\times1.1/7\pi)=2\pi/1.314=4.78$ per radian, or $0.083$ per degree, and $AR=13.3$ gives $5.39$ per radian ($0.094$ per degree). Both bracket the typical $0.09$ per degree.

## 3. The drag coefficient and the drag polar

Plotted against angle of attack, $C_D$ has a minimum near the no lift angle and rises on both sides until the stall. The value of $C_D$ at $C_L=0$ is the **profile drag coefficient** $C_{D0}$, and the rest is the **induced drag coefficient** $C_{Di}$:

$$
C_D=C_{D0}+C_{Di}.
$$

### Profile drag

Profile drag comes from the boundary layer, the thin layer next to the surface in which viscosity acts, so it is also called boundary-layer drag. It has two parts. **Skin friction drag** is the tangential shear stress of the air on every wetted surface. **Form drag** (boundary-layer normal pressure drag) is a pressure effect: without viscosity the pressures on forward- and rearward-facing surfaces would balance exactly and there would be no net pressure drag ([[D'Alembert's Paradox]]), but the boundary layer thickens towards the rear, and separates on a bluff body, which changes the effective shape so that the pressures no longer balance. Form drag therefore depends strongly on how streamlined the body is ([[SESA1016 T14 - Boundary Layers and the Origin of Drag]]).

Skin friction is estimated from the flat-plate coefficient based on the wetted area $S_w$:

$$
C_F=\frac{D_F}{\tfrac12\rho V^2S_w},\qquad C_F=\frac{1.328}{\sqrt{Re_L}}\ \text{(laminar)},\qquad C_F=\frac{0.074}{Re_L^{0.2}}\ \text{(turbulent)},
$$

with $Re_L=\rho VL/\mu$ and laminar flow only for $Re_L<5\times10^5$. Because $C_F$ is based on $S_w$, it is scaled by $S_w/S$ before it is added to coefficients based on the wing area. The complete build-up is

$$
C_D=C_{Di}+C_{Dw}+C_F\frac{S_w}{S}+C_{DP}+C_{Dint}+C_{De},
$$

with wave drag $C_{Dw}$ (zero in subsonic flow), form drag $C_{DP}$, interference drag $C_{Dint}$ from components whose wakes interact, and excrescence drag $C_{De}$ from small items not counted elsewhere. Everything except $C_{Di}$ is lumped into $C_{D0}$, which in the cruise configuration is about 0.01 to 0.025 for a streamlined aircraft and up to about 0.055 for a small aircraft with a fixed undercarriage.

### Induced drag

The trailing vortices shed by a lifting wing produce the downwash of Section 2. The local relative wind at the wing is tilted down by $\alpha_i$, and the lift, being perpendicular to that local wind, is tilted back by the same angle. Its component along the free stream is the **induced drag** (also called lift-dependent or vortex drag):

$$
D_i=L\sin\alpha_i\approx L\alpha_i\qquad(\alpha_i\ \text{small, in radians}).
$$

Dividing by $qS$ gives $C_{Di}=C_L\alpha_i$. For a wing with an elliptic lift distribution $\alpha_i=C_L/\pi AR$, so

$$
\begin{aligned}
C_{Di}&=C_L\cdot\frac{C_L}{\pi AR}\\
&=\frac{C_L^2}{\pi AR}.
\end{aligned}
$$

Any other planform does worse. The penalty is written either as a factor $1+\delta$ with $\delta\ge0$ or through the span efficiency (Oswald) factor $e=1/(1+\delta)$, typically 0.6 to 1, and both are absorbed into a single **induced drag factor** $K$ ([[Oswald Efficiency Factor]]):

$$
C_{Di}=KC_L^2,\qquad K=\frac{1+\delta}{\pi AR}=\frac{1}{\pi eAR}.
$$

The elliptic planform has $\delta=0$ and $e=1$, the least induced drag of all. The planform factor $1+\delta=1/e$ is somewhat above 1 for practical wings and exactly 1 for the elliptic planform (the course notes' alternative $k$ and $K$ are in the terminology table).

Induced drag grows with the square of $C_L$ because both the vortex strength and the tilt angle are proportional to the lift, and it falls as $1/AR$ because a long, slender wing spreads the lift over more span and needs a weaker downwash. See [[Downwash and Induced Drag]].

### The parabolic drag polar

Adding the two parts gives the **parabolic drag polar**:

$$
C_D=C_{D0}+KC_L^2=C_{D0}+\frac{C_L^2}{\pi eAR} .
$$

A typical cruise-configuration polar is $C_D=0.02+0.055C_L^2$. Plotted as $C_L$ against $C_D$ it is a parabola with its nose at $(C_{D0},0)$; plotted against $C_L^2$ it is a straight line with intercept $C_{D0}$ and slope $K$, which is how polar constants are read from data. The real polar of an aircraft departs from the parabola near the stall and at high Mach number, and every configuration change (flaps, undercarriage) gives a different pair of constants, so a clean $C_{D0}$ is never combined with a landing $C_{L\max}$ unless the question sets it up that way.

![[mof_m03_drag_polar.png|900]]

Along a level flight the aircraft weight is fixed, so $C_L$ is large at low speed and small at high speed; $C_D$ therefore changes with speed, and there is one speed at which the drag is least. That speed, and the tangent from the origin to the polar that marks $(C_L/C_D)_{max}$, are found in [[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]]; see also [[Parabolic Drag Polar]].

### Two-point reduction of a drag polar

With $C_{L1},C_{D1}$ and $C_{L2},C_{D2}$ from two tunnel readings (each force divided by $qS$), both points satisfy the polar:

$$
C_{D1}=C_{D0}+KC_{L1}^2,\qquad C_{D2}=C_{D0}+KC_{L2}^2 .
$$

Subtracting removes $C_{D0}$:

$$
\begin{aligned}
C_{D2}-C_{D1}&=K\left(C_{L2}^2-C_{L1}^2\right)\\
K&=\frac{C_{D2}-C_{D1}}{C_{L2}^2-C_{L1}^2},
\end{aligned}
$$

and back-substituting in the first equation,

$$
C_{D0}=C_{D1}-KC_{L1}^2 .
$$

> [!warning] The lowest test angle is not zero lift
> Using $C_{D1}$ directly as $C_{D0}$ assumes the first reading is at $C_L=0$. A reading at $\alpha=0$ or $0.5^\circ$ still has lift unless $\alpha_0=0$, so $KC_{L1}^2$ must be subtracted. In Revision Q12 the reading at $\alpha=0^\circ$ has $C_L=0.105$, and the correction lowers $C_{D}$ from $0.0324$ to $C_{D0}=0.0317$ ([[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 12]]).

## 4. The pitching moment coefficient

The pitching moment of the wing plus fuselage without the tailplane depends on the axis it is taken about. Taken about the leading edge it falls as $\alpha$ rises, because the lift acts behind the leading edge and turns the nose down more strongly as the lift grows; about the trailing edge it rises; about one particular point it does not change at all. Moments are positive nose up.

![[mof_m03_moment_reference.png|900]]

### Why the moment is linear in the lift coefficient

Below the stall the wing's aerodynamic load is equivalent to the lift $L$ acting at a fixed point, the aerodynamic centre, together with a moment $M_o$ that does not change with $\alpha$ ([[#6. The aerodynamic centre]]). Let the reference axis be the CG and let $x_{AC}$ be the distance of the aerodynamic centre forward of the CG. A lift acting a distance $x_{AC}$ ahead of the CG turns the nose up, so the moment about the CG is

$$
M_{CG}=M_o+x_{AC}L .
$$

Dividing by $\tfrac12\rho V^2Sc$, with $c$ the mean chord,

$$
\begin{aligned}
\frac{M_{CG}}{\tfrac12\rho V^2Sc}&=\frac{M_o}{\tfrac12\rho V^2Sc}+\frac{x_{AC}}{c}\,\frac{L}{\tfrac12\rho V^2S}\\
C_{m,CG}&=C_{mo}+\frac{x_{AC}}{c}\,C_L .
\end{aligned}
$$

This is a straight line in $C_L$, written with a single constant $h$ as

$$
C_m=C_{mo}-hC_L ,
$$

where $h$ is a constant whose value and sign depend on the axis position: positive for an axis forward of the aerodynamic centre, negative for one aft of it. Comparing the two forms, $h=-x_{AC}/c$. At $C_L=0$ every axis gives the same moment, because a pure couple is the same about every point, so $C_{mo}$, the **pitching moment coefficient at zero lift**, does not depend on the axis. It depends on the shape: it is zero for an aircraft that is symmetric about its datum line, and usually negative (nose down) for a cambered wing.

### Trim needs a tailplane

For trimmed steady flight at a given speed, and hence at a given $C_L$, the moment about the CG must be zero, so the $C_{m,CG}$ line must cross zero at that $C_L$. For static stability the slope $dC_{m,CG}/dC_L$ must be negative, so that a gust which raises $\alpha$ produces a nose-down moment that restores it. With the CG aft of the aerodynamic centre, the wing and body alone have a positive slope (unstable) and a negative $C_{mo}$, so they can be trimmed only at the one positive $C_L$ where the line crosses zero, and that trim is unstable. The tailplane supplies a moment that makes the complete aircraft's line cross zero with a negative slope; the moment it must supply changes with the trimmed $C_L$, which is what the trim tab, elevator or all-moving tailplane provides. The full analysis is in [[SESA1015 M11 - Longitudinal Trim and Static Stability|M11]].

## 5. The centre of pressure

The **centre of pressure** is the axis position about which the pitching moment is zero, $M_{cp}=0$: the point at which the resultant lift of the wing plus body appears to act with no moment. Let $x_{cp}$ be its distance forward of the CG. Placing the whole lift there (figure below, panel (a)) gives the moment about the CG,

$$
M_{CG}=x_{cp}L .
$$

Dividing by $\tfrac12\rho V^2Sc$ and using the linear moment law,

$$
\begin{aligned}
C_{m,CG}&=\frac{x_{cp}}{c}\,C_L\\
\frac{x_{cp}}{c}C_L&=C_{mo}-hC_L\\
\frac{x_{cp}}{c}&=\frac{C_{m,CG}}{C_L}=\frac{C_{mo}}{C_L}-h .
\end{aligned}
$$

With $h=-x_{AC}/c$ this reads

$$
\frac{x_{cp}}{c}=\frac{x_{AC}}{c}+\frac{C_{mo}}{C_L},
$$

which says the centre of pressure sits a distance $c\,C_{mo}/C_L$ from the aerodynamic centre. With $C_{mo}<0$ it lies aft of the aerodynamic centre, and the distance shrinks as $C_L$ grows: the **centre of pressure moves forward as the angle of attack increases**, approaching the aerodynamic centre at high $C_L$ and running far aft (towards $-\infty$) as $C_L\to0^+$, where the zero-lift couple can only be produced by a vanishing force at a large arm. That makes the centre of pressure a poor reference for analysis. The sign of $x_{cp}$ itself depends on where the CG is; see [[#Transcript and slide slips]].

![[mof_m03_force_systems.png|800]]

## 6. The aerodynamic centre

The **aerodynamic centre** is the axis position about which the pitching moment coefficient does not vary with angle of attack:

$$
\frac{dM_{AC}}{d\alpha}=0 .
$$

The force and moment on the wing can then be replaced by a constant moment $M_o$, independent of $\alpha$ and of $L$, together with the lift acting at the aerodynamic centre (panel (b) of the figure above). Unlike the centre of pressure, the aerodynamic centre does not move as the angle of attack changes.

Taking moments about the CG with this replacement,

$$
M_{CG}=M_o+x_{AC}L .
$$

Dividing by $\tfrac12\rho V^2Sc$ and equating to the linear law,

$$
C_{m,CG}=C_{mo}+\frac{x_{AC}}{c}C_L=C_{mo}-hC_L .
$$

The two lines agree for every $C_L$ only if their slopes are equal:

$$
\frac{x_{AC}}{c}=-h .
$$

More generally, differentiating $C_{m,CG}=C_{mo}+(x_{AC}/c)C_L$ with respect to $C_L$ gives

$$
\frac{x_{AC}}{c}=\frac{dC_{m,CG}}{dC_L}=-h .
$$

Since $h$ is a constant, the aerodynamic centre is at a fixed position, and it is found from the slope of the moment curve about any known point. Classical (thin aerofoil) theory places it at the **quarter chord**, measured from the leading edge, and the moment about it equals the zero-lift moment, $C_{m,AC}=C_{mo}$. For a wing-body combination the aerodynamic centre need not be exactly at the quarter chord; with no other information, assume it is. See [[Aerodynamic Centre and Centre of Pressure]].

The stability condition of Section 4 reads directly off this result: $dC_{m,CG}/dC_L=x_{AC}/c<0$ requires the aerodynamic centre to be aft of the CG, that is the CG ahead of the aerodynamic centre, for the wing-body alone. With a tailplane the same argument applies with the neutral point of the whole aircraft in place of the wing-body aerodynamic centre ([[Static Margin and Tail Volume]]).

## Worked examples

### Reading the typical lift curve

For $C_L=0.09(\alpha+2)$ with $\alpha$ in degrees, the angle for the cruise value $C_L=0.5$ is

$$
\alpha=\frac{0.5}{0.09}-2=3.56^\circ .
$$

The linear law reaches $C_{L\max}=1.2$ at $\alpha=1.2/0.09-2=11.3^\circ$, inside the 10 to 15 degree range where the stall begins. The same line per radian is $C_L=5.157(\alpha+0.0349)$: at $\alpha=3.56^\circ=0.0621$ rad it gives $5.157\times0.0970=0.500$.

### Lift and drag of a rectangular wing

A rectangular wing of chord 0.6 m and span 8 m flies at 90 m/s at 1000 m ($\rho=1.116$ kg/m³, $\mu=1.761\times10^{-5}$ Pa s) at a geometric angle of $4^\circ$. The zero-lift angle is $-1^\circ$, the lift-curve slope factor is $\tau=0.1$ and $e=0.9$. Treating the wing as a flat plate, with drag limited to induced drag and skin friction, the lift and the total drag are wanted.

The geometry is $S=8\times0.6=4.8$ m² and $AR=8/0.6=13.33$. With $a_0=2\pi$,

$$
\begin{aligned}
a&=\frac{2\pi}{1+\dfrac{2\pi(1.1)}{\pi(13.33)}}\\
&=\frac{6.283}{1.165}=5.393\ \text{per radian}.
\end{aligned}
$$

In radians $\alpha=0.0698$ and $\alpha_0=-0.0175$, so

$$
\begin{aligned}
C_L&=5.393\,(0.0698+0.0175)=0.471,\\
L&=\tfrac12(1.116)(90)^2(4.8)(0.471)=10\,210\ \text{N}.
\end{aligned}
$$

The induced drag coefficient and drag are

$$
\begin{aligned}
C_{Di}&=\frac{C_L^2}{\pi eAR}=\frac{0.471^2}{\pi(0.9)(13.33)}=0.00588,\\
D_i&=\tfrac12(1.116)(90)^2(4.8)(0.00588)=127.5\ \text{N}.
\end{aligned}
$$

For skin friction, the chord Reynolds number is $Re_c=\rho Vc/\mu=1.116\times90\times0.6/1.761\times10^{-5}=3.42\times10^6$, far above $5\times10^5$, so the boundary layer is turbulent:

$$
C_F=\frac{0.074}{(3.42\times10^6)^{0.2}}=0.00365 .
$$

Both surfaces are wetted, so the wetted area is $2S_w=2\times4.8=9.6$ m² and

$$
D_F=\tfrac12(1.116)(90)^2(9.6)(0.00365)=158.4\ \text{N}.
$$

The total is $D=127.5+158.4=285.9$ N, and $L/D=10\,210/285.9=35.7$. Skin friction is more than half the drag at this low $C_L$, which is the cruise situation; at high $C_L$ the induced term takes over.

> [!check] Recomputed
> Python with unrounded intermediate values: $a=5.3933$, $C_L=0.47065$, $L=10\,210.8$ N, $C_{Di}=0.0058759$, $D_i=127.48$ N, $Re_c=3.4221\times10^6$, $C_F=0.0036507$, $D_F=158.40$ N, $D=285.88$ N.

### Splitting a typical polar

For $C_D=0.02+0.055C_L^2$ on a wing of aspect ratio 7, $K=0.055$, so the span efficiency and the penalty factor are

$$
\begin{aligned}
1+\delta&=\pi AR\,K=\pi(7)(0.055)=1.21,\\
e&=\frac{1}{1+\delta}=0.83 .
\end{aligned}
$$

The $1.21$ is the planform factor $1+\delta$.

The share of induced drag in the total grows quickly with $C_L$:

| $C_L$ | $C_{Di}=0.055C_L^2$ | $C_D$ | induced share |
|---|---|---|---|
| 0.3 (fast cruise) | 0.00495 | 0.02495 | 20% |
| 0.5 | 0.01375 | 0.03375 | 41% |
| 1.0 | 0.0550 | 0.0750 | 73% |
| 1.2 (near clean stall) | 0.0792 | 0.0992 | 80% |

The two parts are equal at $C_L=\sqrt{0.02/0.055}=0.603$, the minimum-drag condition of [[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]].

### Locating the aerodynamic centre from tunnel data

A wing-body model has zero lift at $\alpha=-1.5^\circ$ and $C_L=0.52$ at $5^\circ$. About the CG, at $0.35c$ behind the leading edge, the moment coefficient is $-0.01$ at $1^\circ$ and $0.05$ at $7.88^\circ$. The aerodynamic centre and $C_{mo}$ are wanted.

The lift-curve slope is

$$
a=\frac{0.52-0}{5-(-1.5)}=0.08\ \text{per degree},
$$

so $C_L=0.08(\alpha+1.5)$, which is $0.20$ at $1^\circ$ and $0.7504$ at $7.88^\circ$. Each moment reading satisfies $C_{m,CG}=C_{mo}+(x_{AC}/c)C_L$:

$$
\begin{aligned}
-0.01&=C_{mo}+0.20\,\frac{x_{AC}}{c},\\
0.05&=C_{mo}+0.7504\,\frac{x_{AC}}{c}.
\end{aligned}
$$

Subtracting the first from the second,

$$
\begin{aligned}
0.06&=0.5504\,\frac{x_{AC}}{c}\\
\frac{x_{AC}}{c}&=0.109,
\end{aligned}
$$

and back-substituting,

$$
C_{mo}=-0.01-0.20(0.109)=-0.032 .
$$

The aerodynamic centre is $0.109c$ forward of the CG, at $0.35-0.109=0.241c$ from the leading edge, close to the quarter chord. In the notation $C_m=C_{mo}-hC_L$, $h=-0.109$: the CG is aft of the aerodynamic centre and $dC_{m,CG}/dC_L=+0.109>0$, so the wing-body alone is statically unstable, as the rising moment readings already show.

The centre of pressure then follows from $x_{cp}/c=x_{AC}/c+C_{mo}/C_L$:

| $C_L$ | $x_{cp}/c$ forward of CG | position from leading edge |
|---|---|---|
| 0.1 | $-0.209$ | $0.559c$ |
| 0.2 | $-0.050$ | $0.400c$ |
| 0.5 | $+0.045$ | $0.305c$ |
| 1.0 | $+0.077$ | $0.273c$ |

It passes the CG at $C_L=-C_{mo}/(x_{AC}/c)=0.032/0.109=0.29$, which is the only lift coefficient at which this wing-body could be trimmed without a tail, and it moves forward towards $0.241c$ as $C_L$ grows.

> [!check] Recomputed
> Solving the two equations exactly gives $x_{AC}/c=0.109012$ and $C_{mo}=-0.031802$, so the aerodynamic centre is at $0.24099c$. Check at $\alpha=4^\circ$: $C_L=0.44$ and $C_{m,CG}=-0.0318+0.109(0.44)=+0.0162$, on the line through the two readings.

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| lift-curve slope $a$ (written $a_o$ in the notes, $C_{L_\alpha}$ on the slides) | lift slope | $a_0=2\pi$ on the slides is the two-dimensional aerofoil slope, not the aircraft's |
| no lift angle $\alpha_0$ | zero-lift angle, $\alpha_{L=0}$ | negative for positive camber |
| profile drag coefficient $C_{D0}$ | zero-lift drag, parasite drag, boundary-layer drag | the workbook also says profile drag |
| induced drag coefficient $C_{Di}$ | lift-dependent drag, vortex drag | |
| induced drag factor $K=1/\pi eAR$ (slides) | $k=K/\pi A$ (course notes, workbook); $e$ = Oswald or span efficiency | the notes' $k$ is the slides' $K$; the notes' $K$ is a planform factor equal to $1/e$, and their $A$ is the aspect ratio |
| $h$ in $C_m=C_{mo}-hC_L$ | $-x_{AC}/c$; on the slides $\tilde l_{CG}=h-h_{ac}$ with $h$ the CG position | the slides' $h$ is a position, not the notes' constant |

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Solutions: [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions]]
- Previous: [[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]] · Next: [[SESA1015 M04 - Steady Level Flight and Stall]]
- Uses: [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]] (minimum drag and $(L/D)_{max}$ from the polar), [[SESA1015 M11 - Longitudinal Trim and Static Stability]] (trim and the tailplane)
- Concepts: [[Kutta-Joukowski Theorem]] · [[Kutta Condition]] · [[Bernoulli Equation]] · [[Lift-Curve Slope]] · [[Parabolic Drag Polar]] · [[Aerodynamic Centre and Centre of Pressure]] · [[Dynamic Pressure and Aerodynamic Coefficients]] · [[Downwash and Induced Drag]] · [[Oswald Efficiency Factor]] · [[Aerofoil Stall]] · [[Reynolds Number]]
- Builds on: [[SESA1016 T10 - Euler and Bernoulli Equations]] (pressure gradient across curved streamlines, Bernoulli round an aerofoil)
- Later in the degree: [[SESA2022 T3 - Potential Flow]] (circulation and the Kutta-Joukowski theorem), [[SESA2022 T2 - Boundary Layers]] (skin friction, form drag and the [[Boundary Layer Separation]] behind the stall), [[SESA2022 T4 - Thin Aerofoil Theory]] ($a_0=2\pi$ and the quarter-chord aerodynamic centre), [[SESA2022 T5 - Finite Wing Theory]] (downwash, $\tau$, $\delta$ and the [[Elliptic Lift Distribution]]), [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]] (the complete aircraft moment and the [[Neutral Point and Static Margin]]), [[Maximum Lift-to-Drag Ratio]]

## Sources

- Mechanics of Flight Course Notes (Keane, October 2020), §3 intro and §3.1–3.5, pp. 12–18, Figs. 3.1–3.4
- Lecture Slides version 2: pp. 25–30 and 32 (skipping-stone, Venturi and equal-transit explanations of lift), p. 33 (streamline curvature, $F=mV^2/R$, circulation), pp. 49–50 (lift coefficient, finite-wing slope), 51–57 (drag sources, skin friction, drag build-up), 58 (Reynolds-number similarity), 59 (rectangular-wing example), 62–63 (drag polar), 196–200 (aerodynamic moment, aerodynamic centre, wind-tunnel example)
- Revision workbook, Questions 9–12 and 41: [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions]]
- Every number in this note was recomputed in Python; the flow in the lift figure is the potential flow past a Joukowski aerofoil (`generate_mof_m03_figures.py`).

## Self-study tasks

### Core

- [ ] Revision Q9: lift-curve slope from two tunnel readings. → [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 9]] · [[#Two-point reduction of a lift curve]]
- [ ] Revision Q10: no lift angle from two tunnel readings. → [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 10]]
- [ ] Revision Q11: profile drag coefficient from two force pairs. → [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 11]] · [[#Two-point reduction of a drag polar]]
- [ ] Revision Q12: induced drag factor $K$ and $C_{D0}$ from two force pairs. → [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 12]]
- [ ] Wind-tunnel location of the aerodynamic centre (Slides v2, p. 200), without looking. → [[#Locating the aerodynamic centre from tunnel data]]
- [ ] Derive $\partial p/\partial n=\rho V^2/R$ from a fluid element on a curved streamline and use it to explain why the pressure is below ambient on the upper surface and above ambient on the lower surface (Slides v2, p. 33; suggested, not lecturer-set). → [[#Curved streamlines and the pressure across them]]

### Further practice

- [ ] Show that particle impact gives $C_L=2\sin^2\alpha\cos\alpha$ for a flat plate and that equal transit gives $C_l=(s_u/s_l)^2-1$; evaluate both (at $5^\circ$, and for the NACA 4412 at zero incidence) against thin aerofoil theory (Slides v2, pp. 26–28; suggested, not lecturer-set). → [[#Momentum deflection: the skipping-stone picture]] · [[#Equal transit is false]]
- [ ] Rectangular-wing lift and drag (Slides v2, p. 59). → [[#Lift and drag of a rectangular wing]]
- [ ] Derive $x_{AC}/c=-h$ and $x_{cp}/c=C_{mo}/C_L-h$ from moments about the CG (Notes §3.4–3.5, pp. 16–17). → [[#5. The centre of pressure]] · [[#6. The aerodynamic centre]]
- [ ] Revision Q41: tunnel load-cell capacity under Reynolds-number scaling. → [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 41]]

## Transcript and slide slips

> [!warning] Slide slip (Slides v2, p. 33)
> Where: [[#Curved streamlines and the pressure across them]].
>
> The slide attributes the flow following the surface to friction, the flow "sticks" to the surface. Friction gives zero velocity at the wall but does not turn the flow; the flow is bent round the surface by the pressure field across the curved streamlines, and viscosity acting through the boundary layer works against attachment, causing separation (the stall) when the pressure rise along the upper surface is too steep. The role of viscosity in setting the lift is the Kutta condition at the sharp trailing edge.

> [!warning] Course-notes slip (Notes §3.4, p. 17)
> Where: [[#5. The centre of pressure]].
>
> After $x_{cp}/c=C_{mo}/C_L-h$, the notes state that for negative $C_{mo}$ the whole expression is negative. That holds only when $h\ge0$, that is with the CG at or ahead of the aerodynamic centre. With the CG aft of the aerodynamic centre ($h<0$) the centre of pressure lies ahead of the CG once $C_L>-C_{mo}/(-h)$; in the Slides p. 200 example that is $C_L>0.29$. The conclusion that the centre of pressure moves forward as $C_L$ rises holds for any $h$ when $C_{mo}<0$.

> [!warning] Course-notes slip (Notes Fig. 3.2, p. 13)
> Where: [[#3. The drag coefficient and the drag polar]].
>
> The $C_D$ against $\alpha$ sketch labels the left branch "induced drag dominant at large angles of attack" and the right branch "profile drag dominant". In the parabolic model profile drag dominates near the minimum, at $\alpha\approx\alpha_0$, and induced drag dominates on both branches as $|C_L|$ grows.
