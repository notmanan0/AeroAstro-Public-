---
title: "SESA1015 M02 - Aircraft Geometry, Forces and Coefficients"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 2
tags:
  - sesa1015
  - mechanics-of-flight
  - aircraft-geometry
  - aerodynamic-coefficients
  - dimensional-analysis
aliases: ["SESA1015 Mechanics 2", "Aircraft Forces and Coefficients", "Wing geometry and coefficients"]
date: 2026-09-27
status: lectured
coverage: "Course notes §2.3–2.8 (flight path and relative wind, aerodynamic forces and moments, dimensional analysis, geometry, wing areas, aerofoil, aircraft components); Slides v2 pp. 11–14 (aircraft anatomy), p. 64 (pusher and tractor configurations, engine layouts), pp. 34–48 (pressure and friction, normal and axial force, aerofoil nomenclature and NACA 4-digit sections, wing areas, SMC and MAC, aspect ratio of an elliptic wing, similarity, dimensionless coefficients, Reynolds number), p. 58 (Reynolds numbers of real vehicles)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]"]
next_topics: ["[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]"]
key_concepts: ["[[Dynamic Pressure and Aerodynamic Coefficients]]", "[[Wing Planform Geometry]]", "[[Aerofoil Geometry and NACA Four-Digit Sections]]", "[[Reynolds Number]]", "[[Wing Loading]]"]
tutorial_sheets: ["[[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions]]", "[[SESA1015 T01 - Stall and Level-Flight Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§2.3–2.8, pp. 8–11)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 11–14, 34–48, 58, 64)", "02 - Sources/Mechanics of Flight/Aerodynamics - NACA 4-Digit Airfoil Generator.xlsx"]
---

# SESA1015 M02 - Aircraft Geometry, Forces and Coefficients

> [!abstract] Summary
> The air acts on an aircraft through a resultant force and a pitching moment, which are resolved into lift $L$ normal to the relative wind, drag $D$ along it and a moment $M$ about the centre of gravity. Dimensional analysis shows that each must scale as $\tfrac12\rho V^2$ times an area (and a length for the moment), so $L=\tfrac12\rho V^2SC_L$, $D=\tfrac12\rho V^2SC_D$ and $M=\tfrac12\rho V^2S\bar{\bar c}C_M$, with coefficients that depend only on shape, angle of attack, Reynolds number and Mach number. The reference quantities come from the wing planform: the gross area $S=\int c\,dy$, the span $b$, the aspect ratio $AR=b^2/S$, the taper ratio $\lambda=c_T/c_0$ and the mean aerodynamic chord $\bar{\bar c}=\int c^2dy\big/\int c\,dy$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives forces, areas or a wing shape and asks for a coefficient, a force from a coefficient, a wing area or aspect ratio from span and chord, a mean chord, or whether a model test reproduces full-scale conditions.
> - **Assumptions:** symmetric aircraft at zero sideslip and bank; coefficients referred to the gross wing area $S_G$ and, for moments, the mean aerodynamic chord; the same $\rho$ and $V$ pair as in [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number|M01]] (local density with true airspeed); angles in radians inside formulae.
> - **Method:** 1. Fix the reference area and length (gross area, MAC). 2. Compute $q=\tfrac12\rho V^2$. 3. Divide the force by $qS$ (moment by $qS\bar{\bar c}$), or multiply a coefficient by them. 4. For a planform, integrate $c(y)$ for $S$, then $AR=b^2/S$ and $\bar{\bar c}$. 5. For a model test, compare $Re=\rho Vc/\mu$ and $M=V/a$ with full scale.
> - **Common mistakes:** using the net instead of the gross wing area, or $b$ for the semi-span $s$; resolving forces from the body axes instead of the relative wind.
> - **Practise:** [[#An elliptic wing (Slides v2 p. 43)]] · [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 9|Revision Q9]]

An aircraft in flight has air flowing over every part of its surface. At each point the air pushes normal to the skin with a pressure and drags along it with a shear stress, and these small forces add up to one resultant force and one moment. Flight mechanics does not work with the distribution; it needs only the resultant, split into lift, which supports the weight, and drag, which the engine has to overcome, plus the pitching moment that has to be trimmed.

Those forces depend on the size of the aircraft, its speed, the air density, the attitude and the shape. Dimensional analysis collapses this list: once the forces are divided by $\tfrac12\rho V^2$ and a reference area, what remains, the coefficient, depends only on the shape and on a few dimensionless numbers such as the angle of attack, the Reynolds number and the Mach number. That is why a small model in a wind tunnel predicts the full-scale aircraft, and why all of the performance analysis can be written with $C_L$ and $C_D$.

The reference area and lengths come from the geometry of the wing. A wing whose chord varies along the span is replaced by an equivalent rectangular wing with the same area and a representative chord, and the words used for the parts of the aircraft and the shape of its sections need to be fixed before any calculation starts.

---

## 1. Flight path, relative wind and the aerodynamic forces (Notes §2.3–2.4, pp. 8–9)

### Definitions

The **flight path** is the path through space traced by the centre of gravity (CG). The **relative wind** is the apparent wind seen by the aircraft, equal and opposite to the instantaneous velocity of the CG. The air's action on the aircraft, referred to the CG, is the **aerodynamic reaction**: a resultant force $R$ and a moment $M$. For a symmetric aircraft at zero yaw and roll, $R$ is resolved into

- the **lift** $L$, normal to the relative wind, positive upwards;
- the **drag** $D$, parallel to the relative wind, positive pushing backwards;

and $M$ is the **pitching moment**, positive nose up.

Three angles describe the attitude in the plane of symmetry. The **angle of attack** (incidence) $\alpha$ is the angle between the body datum (a fixed reference line in the aircraft) and the relative wind. The **attitude** $\theta$ is the angle between the body datum and the Earth reference line (the horizontal). The **flight-path angle** $\gamma$ is the angle between the flight path and the horizontal. The angle of attack sets the aerodynamic force; the attitude matters for the pitch mechanics.

![[mof_m02_forces_angles.png|900]]

With wings level and no sideslip all three angles lie in one plane and are measured the same way, nose up positive. The velocity vector is at $\gamma$ above the horizontal and the body datum is at $\alpha$ above the velocity vector, so the body datum is at

$$
\theta=\gamma+\alpha
$$

above the horizontal. In level flight $\gamma=0$ and the attitude equals the angle of attack; in a climb at fixed $\alpha$ the nose is higher by $\gamma$.

### The four forces

Four forces act on an aircraft in flight. The weight $W=mg$ acts vertically down through the CG. The lift and drag act normal and parallel to the relative wind, so they rotate with the flight path. The thrust $T$ acts along the thrust line of the engines, fixed in the aircraft. In steady level flight with the thrust line along the flight path, resolving vertically and horizontally gives

$$
L=W,\qquad T=D,
$$

and in trimmed flight the moments about the CG balance, $M=0$ (Notes §1, p. 2). The forces do not act through one point, which is why the moment balance is a separate condition and leads to static stability ([[SESA1015 M11 - Longitudinal Trim and Static Stability]]). Climbing, gliding and turning flight resolve the same four forces with $\gamma$ or a bank angle in the geometry ([[SESA1015 M08 - Glide and Climb Performance]], [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]).

## 2. From surface pressure and friction to lift and drag (Slides v2 pp. 34–35)

### Pressure and shear stress on the surface

At each point of the surface two stresses act. The pressure $p$ acts normal to the surface. The **shear stress** $\tau_w$ acts tangentially and comes from viscosity: fluid sticks to the surface (the no-slip condition) and the velocity tangential to the wall rises across a thin layer, so for a Newtonian fluid

$$
\tau_w=\mu\left.\frac{dU}{dn}\right|_{\text{wall}} ,
$$

with $\mu$ the dynamic viscosity and $n$ the distance normal to the wall ([[Newtonian Fluid and Viscosity]]). For air, $\mu$ rises with temperature according to Sutherland's formula in the form used in the course,

$$
\mu_{air}=\left(\frac{6.6\times10^{-3}}{T+111}\right)\left(\frac{T}{273}\right)^{1.5}\ \text{Pa s},
$$

which gives $1.79\times10^{-5}$ Pa s at 288 K and $1.73\times10^{-5}$ Pa s at 275 K. Both stresses are made dimensionless with the free-stream dynamic pressure:

$$
C_p=\frac{p-p_\infty}{\tfrac12\rho V^2},\qquad C_f=\frac{\tau_w}{\tfrac12\rho V^2} .
$$

On a lifting aerofoil the upper surface has $C_p<0$ (the suction side) and the lower surface $C_p>0$ (the pressure side), and $-C_p$ is conventionally plotted upwards so that the suction side appears on top ([[Pressure Coefficient]]).

### Normal and axial force, lift and drag

Integrating pressure and shear stress round the section gives, per unit span (marked with a prime), a resultant $R'$. Resolved along chord-fixed axes it has a **normal force** $N'$ perpendicular to the chord and an **axial force** $A'$ along the chord. The lift and drag are the components of the same $R'$ perpendicular and parallel to the free stream $V_\infty$, which is inclined at $\alpha$ to the chord.

![[mof_m02_normal_axial.png|800]]

Rotating the axes through $\alpha$: the unit vector along $V_\infty$ has components $(\cos\alpha,\ \sin\alpha)$ in the (chord, normal) directions, and the unit vector normal to $V_\infty$ has components $(-\sin\alpha,\ \cos\alpha)$. Projecting $R'=(A',N')$ onto them,

$$
\boxed{L'=N'\cos\alpha-A'\sin\alpha,\qquad D'=N'\sin\alpha+A'\cos\alpha} .
$$

At $\alpha=0$ these reduce to $L'=N'$ and $D'=A'$, as they must.

> [!tip] Why the drag is so small
> At incidence the large normal force tilts back and contributes $N'\sin\alpha$ to the drag. Near the leading edge, though, the low pressure on the rounded nose pulls forward along the chord, so $A'$ is negative (leading-edge suction) and nearly cancels that contribution. With $N'=500$ N/m, $A'=-45$ N/m and $\alpha=6^\circ$: $L'=500\cos6^\circ+45\sin6^\circ=502.0$ N/m and $D'=500\sin6^\circ-45\cos6^\circ=52.3-44.8=7.5$ N/m. On a 0.5 m chord at 40 m/s at sea level ($q=980$ Pa) that is $C_l=1.02$ and $C_d=0.015$.

## 3. Dimensional analysis and the aerodynamic coefficients (Notes §2.4, p. 9; Slides v2 pp. 44–48)

### Lift from dimensional analysis

The lift depends on the air density $\rho$, the true airspeed $V$, a typical length $l$ (the wing chord or the fuselage length), the angle of attack $\alpha$ and the shape:

$$
L=L(\rho,V,l,\alpha,\text{shape}) .
$$

The angle of attack and the shape are already dimensionless, so the dimensional quantities must combine into a force on their own. Try

$$
L=k\,\rho^aV^bl^c ,
$$

with $k$ dimensionless. In terms of mass M, length L and time T, $[L]=\text{MLT}^{-2}$, $[\rho]=\text{ML}^{-3}$, $[V]=\text{LT}^{-1}$ and $[l]=\text{L}$, so

$$
\text{MLT}^{-2}=\text{M}^a\,\text{L}^{-3a+b+c}\,\text{T}^{-b} .
$$

Matching the powers:

$$
\begin{aligned}
\text{M}:&\quad a=1\\
\text{T}:&\quad -b=-2\ \Rightarrow\ b=2\\
\text{L}:&\quad -3a+b+c=1\ \Rightarrow\ c=1+3-2=2 .
\end{aligned}
$$

Hence $L=k\rho V^2l^2$, with $k$ a function of $\alpha$ and the shape only. By convention $l^2$ is replaced by a reference area $S$ and a factor $\tfrac12$ is taken out, so that the force scale is the dynamic pressure $q=\tfrac12\rho V^2$ of [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number|M01]]:

$$
\boxed{L=\tfrac12\rho V^2SC_L,\qquad D=\tfrac12\rho V^2SC_D,\qquad M=\tfrac12\rho V^2S\,l\,C_M} ,
$$

which define the **lift coefficient** $C_L$, the **drag coefficient** $C_D$ and the **pitching-moment coefficient** $C_M$. The moment needs one more length, the reference length $l$, the wing mean chord (Notes §2.4, p. 9). For the whole aircraft $l$ is the mean aerodynamic chord $\bar{\bar c}$ of [[#Mean aerodynamic chord]] and $S$ is the gross wing area (Slides v2, p. 45).

### Viscosity and compressibility: Reynolds and Mach numbers

The air also has a viscosity $\mu$ and a speed of sound $a$, and the lift may depend on them. With $L$, $\rho$, $V$, $l$, $\mu$ and $a$ there are six dimensional variables and three dimensions, so by the Buckingham $\Pi$ theorem ([[Buckingham Pi Theorem]], [[SESA1016 T6 - Dimensional Analysis and Similarity]]) three independent dimensionless groups describe the problem. Choosing $\rho$, $V$ and $l$ as repeating variables, they are

$$
C_L=\frac{L}{\tfrac12\rho V^2S},\qquad Re=\frac{\rho Vl}{\mu},\qquad M=\frac{V}{a},
$$

so

$$
C_L=f(\alpha,\ Re,\ M,\ \text{shape}) ,
$$

and likewise for $C_D$ and $C_M$ (Slides v2, p. 48). The **Reynolds number** is the ratio of inertial (pressure) forces to viscous forces. The inertial force on a body scales as the dynamic pressure times an area, $\rho V^2l^2$; the viscous force scales as a shear stress $\mu V/l$ times an area $l^2$, that is $\mu Vl$. Their ratio is

$$
Re=\frac{\rho V^2l^2}{\mu Vl}=\frac{\rho Vl}{\mu}=\frac{Vl}{\nu},
$$

with $\nu=\mu/\rho$ the kinematic viscosity ([[Reynolds Number]]).

### The coefficients in two and three dimensions

| Quantity | Coefficient | Divided by | Dimensions of the quantity |
|---|---|---|---|
| pressure, shear stress | $C_p=\dfrac{p-p_\infty}{\frac12\rho V^2}$, $C_f=\dfrac{\tau_w}{\frac12\rho V^2}$ | $q$ | N/m² $=\text{ML}^{-1}\text{T}^{-2}$ |
| section lift, drag per unit span | $C_l=\dfrac{L'}{\frac12\rho V^2c}$, $C_d=\dfrac{D'}{\frac12\rho V^2c}$ | $q\,c$ | N/m $=\text{MT}^{-2}$ |
| section moment per unit span | $C_m=\dfrac{M'}{\frac12\rho V^2c^2}$ | $q\,c^2$ | N m/m $=\text{MLT}^{-2}$ |
| wing or aircraft lift, drag | $C_L=\dfrac{L}{\frac12\rho V^2S}$, $C_D=\dfrac{D}{\frac12\rho V^2S}$ | $q\,S$ | N $=\text{MLT}^{-2}$ |
| wing or aircraft moment | $C_M=\dfrac{M}{\frac12\rho V^2S\bar{\bar c}}$ | $q\,S\,\bar{\bar c}$ | N m $=\text{ML}^2\text{T}^{-2}$ |

Lower-case subscripts ($C_l$, $C_d$, $C_m$) are section (two-dimensional) coefficients; upper-case subscripts are for the whole wing or aircraft (Slides v2, p. 45). Any coefficient is meaningful only with its reference area and length stated, which is why the gross wing area is fixed as the standard.

### Similarity

Two flows are **geometrically similar** when the shapes differ only in scale (Slides v2, p. 44). They are **dynamically similar** when, in addition, every relevant dimensionless group is the same; then the coefficients are the same, whatever the size. Dividing a distance by a natural length removes the dependence on size in the same way: a 5 km journey is 167 body lengths for a 30 m whale, 3125 for a 1.6 m human and $10^6$ for a 5 mm ant.
The Reynolds numbers of flying and swimming vehicles span four orders of magnitude (Slides v2, p. 58):

| Vehicle | Medium | Speed | Length | $\nu$ (m²/s) | $Re=Vl/\nu$ |
|---|---|---|---|---|---|
| small UAV | air | 10 m/s | 0.3 m | $1.5\times10^{-5}$ | $2\times10^5$ |
| underwater glider | water | 2 m/s | 2.5 m | $1\times10^{-6}$ | $5\times10^6$ |
| commercial aircraft | air | 230 m/s | 70 m | $1.5\times10^{-5}$ | $1.1\times10^9$ |

The lift-curve shape, and hence $C_L$ at a given $\alpha$ below the stall, is almost the same across this range, so for most subsonic flows $C_L$ is close to independent of $Re$ and $M$. The drag is not: skin friction and the separation that sets the profile drag depend on the state of the boundary layer, and so on $Re$ ([[SESA1016 T14 - Boundary Layers and the Origin of Drag]], [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]).

A wind-tunnel model at scale $1/n$ in air at the same conditions needs $n$ times the speed to match $Re$, and that raises its Mach number by the same factor. A 1:5 model of an aircraft landing at 60 m/s would have to be tested at 300 m/s, $M=0.88$, which no longer matches the low-speed full-scale flow; matching both $Re$ and $M$ in a small atmospheric tunnel is generally impossible, so test data always carry the conditions at which they were taken. Revision Q41 sizes a tunnel load cell on exactly this basis.

### Coefficients of a light aircraft in cruise

A light aircraft of mass 1100 kg, gross wing area $S=16.2$ m² and span $b=11.0$ m cruises level at $V=60$ m/s (true airspeed) at 2000 m in the ISA, where $T=275.15$ K and $\rho=1.0065$ kg/m³. The measured drag coefficient is $C_D=0.035$.

The weight and dynamic pressure are

$$
W=1100\times9.81=10\,791\ \text{N},\qquad q=\tfrac12\times1.0065\times60^2=1811.7\ \text{Pa}.
$$

In level flight $L=W$, so

$$
C_L=\frac{W}{qS}=\frac{10\,791}{1811.7\times16.2}=0.368,
$$

and the drag is

$$
D=qSC_D=1811.7\times16.2\times0.035=1027\ \text{N},\qquad\frac{L}{D}=\frac{C_L}{C_D}=10.5 .
$$

The aspect ratio and standard mean chord are $AR=b^2/S=121/16.2=7.47$ and $\bar c=S/b=1.473$ m. With Sutherland's formula at 275.15 K, $\mu=1.729\times10^{-5}$ Pa s, so

$$
Re=\frac{\rho V\bar c}{\mu}=\frac{1.0065\times60\times1.473}{1.729\times10^{-5}}=5.1\times10^6 ,
$$

and with $a=\sqrt{1.4\times287.05\times275.15}=332.5$ m/s, $M=60/332.5=0.18$. The flow is turbulent over most of the wing and effectively incompressible.

## 4. Wing geometry (Notes §2.5–2.6, pp. 9–10; Slides v2 pp. 38–43)

### Reference lengths, areas and shape parameters

The geometric quantities fall into three groups (Notes §2.5, pp. 9–10; Slides v2, p. 39).

| Group | Quantity | Symbol |
|---|---|---|
| reference lengths | root chord (centreline chord) | $c_R$ (slides: $c_0$) |
| | tip chord | $c_T$ |
| | mean chord | $\bar c$ |
| | tail moment arm, from the CG to the tailplane (end points fixed in M11) | $\ell_T$ |
| | wing span; semi-span | $b=2s$; $s$ |
| reference areas | wing plan area, gross or net | $S_G$, $S_N$ |
| | wetted area of a component | $S_W$ |
| shape parameters | taper ratio | $\lambda=c_T/c_R$ |
| | sweep | $\Lambda$ (leading edge $\Lambda_{LE}$, quarter chord $\Lambda_{c/4}$) |
| | aspect ratio | $A$ or $AR$ |

Two further shape features complete the description of a real wing (Slides v2, p. 40). Taper may be in planform, in thickness, or both. **Twist** rotates the sections along the span: **washout** sets the tip nose-down relative to the root, so that the root stalls first, and **washin** the reverse.

### Wing areas

The **net wing area** $S_N$ is the projected planform area of the exposed wings only. The **gross wing area** $S_G$ is the projected area with the leading and trailing edges carried in to the aircraft centreline, so it includes the part of the wing inside the fuselage. The **wetted area** $S_W$ is the actual surface area of both the upper and lower surfaces; because of the thickness, $S_W>2S_N$. The gross area is normally used as the reference area $S$ in the coefficients (Notes §2.6, p. 10); the wetted area is the one on which skin friction acts, so it appears in the skin-friction drag coefficient ([[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]).

![[mof_m02_planform.png|1000]]

With $y$ measured spanwise from the centreline and $c(y)$ the local chord, the gross area of a wing symmetric about the centreline is

$$
\boxed{S=\int_{-b/2}^{b/2}c\,dy=2\int_0^s c\,dy} .
$$

### Mean chords and aspect ratio

The **standard mean chord** (SMC) is the chord of the rectangular wing with the same span and area,

$$
\bar c=\frac{\int_0^s c\,dy}{s}=\frac{S}{b},
$$

and is used to describe the geometry. The **aspect ratio** measures how long and slender the wing is:

$$
\boxed{AR=\frac{b^2}{S}=\frac{b^2}{\int_{-b/2}^{b/2}c\,dy}=\frac{4s^2}{2\int_0^s c\,dy}} ,
$$

and since $S=b\bar c$, also $AR=b/\bar c$, the span over the mean chord (Notes §2.5, p. 10). A rectangular wing has $\lambda=1$, $S=bc$, $AR=b/c$ and all mean chords equal to $c$. Aspect ratio controls the induced drag, $C_{D_i}=C_L^2/(\pi e\,AR)$, which is why gliders have $AR$ of 20–40 ([[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]). Many exam questions give the span and aspect ratio and expect $S=b^2/AR$.

### Mean aerodynamic chord

The **mean aerodynamic chord** (MAC) weights each strip by its own chord:

$$
\boxed{\bar{\bar c}=\frac{\int_{-s}^{s}c^2\,dy}{\int_{-s}^{s}c\,dy}} .
$$

The reason for the extra factor of $c$ is the pitching moment. A strip of span $dy$ carries a section moment $\tfrac12\rho V^2c^2C_m\,dy$, proportional to $c^2$, so if every section has the same $C_m$, the whole-wing moment is $\tfrac12\rho V^2C_m\int c^2\,dy$. Writing this as $\tfrac12\rho V^2S\bar{\bar c}\,C_M$ with $C_M=C_m$ requires $\bar{\bar c}=\int c^2dy/S$, which is the definition above. The MAC is therefore the reference length for moments and for locating the CG and the aerodynamic centre, used for aerodynamics, while the SMC describes the geometry (Slides v2, p. 39). It is the chord of the equivalent rectangular wing that has the same area and the same pitching moment. The spanwise station of the MAC is the area centroid of the half-wing,

$$
\bar y=\frac{\int_0^s c\,y\,dy}{\int_0^s c\,dy} .
$$

### The straight-tapered wing

For a straight-tapered wing the chord falls linearly from $c_0$ at the root to $c_T=\lambda c_0$ at the tip:

$$
c(y)=c_0\left[1-(1-\lambda)\frac{y}{s}\right],\qquad 0\le y\le s .
$$

Write $k=(1-\lambda)/s$, so $c=c_0(1-ky)$. The half-wing area is

$$
\begin{aligned}
\int_0^s c\,dy&=c_0\left[s-\frac{ks^2}{2}\right]=c_0s\left[1-\frac{1-\lambda}{2}\right]\\
&=\frac{c_0s(1+\lambda)}{2},
\end{aligned}
$$

so

$$
\boxed{S=c_0s(1+\lambda)=\frac{c_0b(1+\lambda)}{2},\qquad\bar c=\frac{c_0(1+\lambda)}{2},\qquad AR=\frac{2b}{c_0(1+\lambda)}} .
$$

The SMC is the average of the root and tip chords. For the MAC,

$$
\begin{aligned}
\int_0^s c^2\,dy&=c_0^2\int_0^s(1-2ky+k^2y^2)\,dy\\
&=c_0^2\left[s-ks^2+\frac{k^2s^3}{3}\right]\\
&=c_0^2s\left[1-(1-\lambda)+\frac{(1-\lambda)^2}{3}\right]\\
&=c_0^2s\,\frac{3\lambda+1-2\lambda+\lambda^2}{3}=\frac{c_0^2s(1+\lambda+\lambda^2)}{3},
\end{aligned}
$$

and dividing by the half-wing area,

$$
\boxed{\bar{\bar c}=\frac{2}{3}\,c_0\,\frac{1+\lambda+\lambda^2}{1+\lambda}} .
$$

For its position,

$$
\begin{aligned}
\int_0^s c\,y\,dy&=c_0\left[\frac{s^2}{2}-\frac{ks^3}{3}\right]=c_0s^2\left[\frac12-\frac{1-\lambda}{3}\right]\\
&=\frac{c_0s^2(1+2\lambda)}{6},
\end{aligned}
$$

so

$$
\bar y=\frac{c_0s^2(1+2\lambda)/6}{c_0s(1+\lambda)/2}=\frac{s(1+2\lambda)}{3(1+\lambda)}=\frac{b}{6}\,\frac{1+2\lambda}{1+\lambda} .
$$

For a straight-tapered wing the local chord at $\bar y$ equals $\bar{\bar c}$. For a rectangular wing ($\lambda=1$), $\bar{\bar c}=\tfrac23c_0\cdot\tfrac32=c_0$ and $\bar y=s/2$; for a pointed wing ($\lambda=0$), $\bar{\bar c}=\tfrac23c_0$ and $\bar y=s/3$.

**Sweep** is the angle a spanwise line makes with the $y$ axis, positive backwards. Every constant-fraction chord line of a straight-tapered wing is straight, but they have different sweeps. If the leading edge is at $x_{LE}=y\tan\Lambda_{LE}$ (with $x$ measured aft), the point a fraction $n$ of the chord behind it is at

$$
x_n=y\tan\Lambda_{LE}+n\,c_0\left[1-(1-\lambda)\frac{y}{s}\right],
$$

so

$$
\tan\Lambda_n=\frac{dx_n}{dy}=\tan\Lambda_{LE}-\frac{n\,c_0(1-\lambda)}{s} .
$$

With $n=\tfrac14$ this gives the quarter-chord sweep and with $n=1$ the trailing-edge sweep. Taper makes the quarter-chord line less swept than the leading edge.

### A tapered wing

A straight-tapered wing has $b=11$ m, $c_0=2.0$ m, $c_T=1.0$ m and $\Lambda_{LE}=10^\circ$. Then $\lambda=0.5$, $s=5.5$ m and

$$
S=\frac{2.0\times11\times1.5}{2}=16.5\ \text{m}^2,\qquad\bar c=\frac{16.5}{11}=1.50\ \text{m},\qquad AR=\frac{11^2}{16.5}=7.33,
$$

$$
\bar{\bar c}=\frac23\times2.0\times\frac{1+0.5+0.25}{1.5}=1.556\ \text{m},\qquad\bar y=\frac{11}{6}\times\frac{2}{1.5}=2.444\ \text{m}.
$$

The quarter-chord sweep is $\tan\Lambda_{c/4}=\tan10^\circ-\frac{0.25\times2.0\times0.5}{5.5}=0.1763-0.0455=0.1309$, so $\Lambda_{c/4}=7.46^\circ$, and the trailing edge is almost unswept ($-0.3^\circ$). This is the wing in the figure above.

### An elliptic wing (Slides v2 p. 43)

The Supermarine Spitfire wing has an elliptical planform. The example takes a root chord $c_0=0.25$ m and a full span $b=1.1$ m, so $s=0.55$ m and

$$
c(y)=c_0\sqrt{1-\frac{y^2}{s^2}} .
$$

The area integral needs the substitution $y=s\sin\phi$, $dy=s\cos\phi\,d\phi$, with $\phi$ from 0 to $\pi/2$:

$$
\begin{aligned}
\int_0^s\sqrt{1-\frac{y^2}{s^2}}\,dy&=\int_0^{\pi/2}\cos\phi\cdot s\cos\phi\,d\phi\\
&=s\int_0^{\pi/2}\frac{1+\cos2\phi}{2}\,d\phi=\frac{\pi s}{4} .
\end{aligned}
$$

Hence

$$
S=2c_0\cdot\frac{\pi s}{4}=\frac{\pi c_0s}{2}=\frac{\pi c_0b}{4}=\frac{\pi\times0.25\times1.1}{4}=0.216\ \text{m}^2,
$$

$$
AR=\frac{b^2}{S}=\frac{4b}{\pi c_0}=\frac{1.1^2}{0.216}=5.60 .
$$

A rectangular wing with the same area and a chord equal to the elliptic root chord would have $b=S/c_0=0.216/0.25=0.864$ m and $AR=0.864^2/0.216=3.46$: the elliptic wing reaches 27% more span with the same area.

The mean chords of the elliptic wing follow in the same way. The SMC is $\bar c=S/b=\pi c_0/4=0.196$ m. For the MAC,

$$
\int_{-s}^{s}c^2\,dy=c_0^2\int_{-s}^{s}\left(1-\frac{y^2}{s^2}\right)dy=c_0^2\left[2s-\frac{2s}{3}\right]=\frac{4c_0^2s}{3},
$$

so

$$
\bar{\bar c}=\frac{4c_0^2s/3}{\pi c_0s/2}=\frac{8c_0}{3\pi}=0.212\ \text{m},\qquad\bar y=\frac{4s}{3\pi}=0.424\,s .
$$

> [!check] SMC against MAC
> For any planform the MAC is at least the SMC, with equality only for constant chord: $\int c^2dy\big/\int c\,dy\ \ge\ \int c\,dy\big/\int dy$ is the statement that the chord-weighted mean of $c$ is no less than its plain mean. For three half-wings of equal span and area, $\bar{\bar c}/\bar c$ is 1.000 (rectangular), 1.062 ($\lambda=0.4$) and 1.081 (elliptic, $32/(3\pi^2)$).

![[mof_m02_chord_distributions.png|1000]]

### Wing loading and the spanwise lift distribution

Each section of a wing can have a different aerofoil and a different angle of attack, so the lift per unit span $L'(y)$ varies along the span, and the total lift is

$$
L=\int_{-b/2}^{b/2}L'(y)\,dy
$$

(Slides v2, p. 41). Different combinations of planform, section and twist can give the same total lift with different distributions (why some are better: [[SESA2022 T5 - Finite Wing Theory]]). The total lift divided by the area, $W/S$ in level flight, is the [[Wing Loading]], the main design variable of the performance chapters.

## 5. The aerofoil (Notes §2.7, p. 10; Slides v2 pp. 36–37)

An **aerofoil** is the cross-section of a wing (a section parallel to the plane of symmetry). Its geometry is described by a few lines (Slides v2, p. 36):

- the **chord line**, the straight line joining the leading edge (LE) to the trailing edge (TE), whose length is the **chord** $c$;
- the **mean camber line**, the locus of points halfway between the upper and lower surfaces; the **camber** is its maximum distance from the chord line;
- the **thickness**, the distance between the upper and lower surfaces, with maximum value $t$ and thickness-to-chord ratio $t/c$.

For a section, the **angle of attack** is measured between the free stream and the chord line. For a whole aircraft it is measured from the body datum, which in general is not parallel to the wing chord.

### NACA four-digit sections

The NACA four-digit series codes a section as MPXX. M is the maximum camber in percent of the chord, P the position of maximum camber in tenths of the chord from the leading edge, and XX the maximum thickness in percent of the chord. A symmetric section has M = P = 0 (for example NACA 0012). The section is built from $m=\text{M}/100$, $p=\text{P}/10$ and $t=\text{XX}/100$ with the standard equations (*Aerodynamics - NACA 4-Digit Airfoil Generator.xlsx*). The camber line, with $x$ as a fraction of the chord, is

$$
y_c=\begin{cases}\dfrac{m}{p^2}\left(2px-x^2\right), & 0\le x<p,\\[2ex]\dfrac{m}{(1-p)^2}\left[(1-2p)+2px-x^2\right], & p\le x\le1,\end{cases}
$$

which rises to its maximum $y_c=m$ at $x=p$ (both branches give $m$ there, with zero slope). The half-thickness is

$$
y_t=\frac{t}{0.2}\left(0.2969\sqrt x-0.1260x-0.3516x^2+0.2843x^3-0.1015x^4\right),
$$

applied perpendicular to the camber line to give the upper and lower surfaces. The thickness is greatest at $x\approx0.30$, where $2y_t=t$, for every four-digit section, and the trailing edge is left very slightly open ($2y_t=0.021t$ at $x=1$).

**NACA 4412 with a 1 m chord** (Slides v2, p. 37): M = 4, P = 4, XX = 12, so the maximum camber is $0.04c=0.04$ m, located $0.4c=0.4$ m behind the leading edge, and the maximum thickness is $0.12c=0.12$ m.

![[mof_m02_naca4412.png|900]]

Aerofoil shape has followed speed: thin, highly cambered sections in the early 1900s, rounded subsonic sections, flatter-topped transonic (supercritical) sections and thin sharp-edged supersonic sections (Slides v2, p. 36). For how camber and thickness set the lift, see [[SESA2022 T4 - Thin Aerofoil Theory]].

## 6. Aircraft components (Notes §2.8, p. 11; Slides v2 pp. 11–14)

| Component | Function |
|---|---|
| fuselage | main body, nose to tail; carries the cockpit, passenger cabin and payload |
| wings | produce the lift; carry fuel and, on many aircraft, the engines and main undercarriage |
| winglets | small near-vertical surfaces at the wing tips that reduce induced drag |
| propulsion (engines in nacelles) | provide the thrust; tractor or pusher, propeller or jet |
| empennage (tail) | horizontal stabiliser (tailplane) and vertical stabiliser (fin), for stability and trim |
| elevator | hinged rear part of the horizontal stabiliser, controls pitch |
| rudder | hinged rear part of the fin, controls yaw |
| ailerons | outboard trailing-edge surfaces moving in opposite senses, control roll |
| flaps | inboard trailing-edge surfaces deflected together, raise $C_{L,\max}$ for take-off and landing |
| trim tab | small surface on a control surface that holds it at the trimmed position without stick force |
| undercarriage (landing gear) | supports the aircraft on the ground; a tricycle layout has nose wheels and main wheels |

The components are labelled on a twin-turboprop regional passenger aircraft with a tricycle undercarriage (Notes §2.8, p. 11). Inside the wing, spars and ribs carry the bending and torsion loads (Slides v2, p. 13).

A propeller is mounted either as a **tractor**, ahead of its engine and pulling the aircraft, or as a **pusher**, behind it (Slides v2, p. 64). A tractor propeller works in undisturbed air, and its slipstream blows over the wing roots and the tail, which helps control at low speed. A pusher leaves the air ahead of the wing and fuselage clean, but its propeller works in their wake and needs ground clearance when the aircraft rotates for take-off. Propeller layouts include a single nose-mounted tractor, wing-mounted twins and fours, a three-engine layout with a nose tractor, a twin-boom push-pull layout with a propeller at each end of the central nacelle, and wing-mounted pushers. Jet engines are hung in pods under the wing (twin- and four-engine transports), mounted on the rear fuselage (rear-mounted twin jets), combined with a third engine in the tail (tri-jets) or buried in the fuselage (single- and twin-engine fighters). Engines under the wing relieve its bending in flight, because their weight acts against the lift, and keep the engines accessible; rear-mounted engines leave the wing clean but move the centre of gravity aft. For how each kind of engine produces its thrust, and why a propeller's thrust falls with speed while a jet's does not, see [[SESA1015 M05 - Minimum Drag, Power and Performance Curves#Thrust as the rate of change of momentum]].

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| root chord $c_R$ or $c_0$ | centreline chord | notes use $c_R$, slides $c_0$ |
| standard mean chord (SMC) $\bar c$ | geometric mean chord | $S/b$ |
| mean aerodynamic chord (MAC) $\bar{\bar c}$ | aerodynamic mean chord | $\int c^2dy/\int c\,dy$; slides write $\bar{\bar c}$, some texts $\bar c$ |
| horizontal stabiliser | tailplane | |
| vertical stabiliser | fin | |
| undercarriage | landing gear | |

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Previous: [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]] · Next: [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]
- Concepts: [[Dynamic Pressure and Aerodynamic Coefficients]] · [[Wing Planform Geometry]] · [[Aerofoil Geometry and NACA Four-Digit Sections]] · [[Wing Loading]] · [[Reynolds Number]] · [[Pressure Coefficient]] · [[Newtonian Fluid and Viscosity]] · [[Buckingham Pi Theorem]] · [[Free Body Diagram and Equilibrium]]
- Builds on: [[SESA1016 T6 - Dimensional Analysis and Similarity]] · [[SESA1016 T7 - Fluid Properties and Viscosity]]
- Used in: wind-tunnel data reduction in [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions]]; the MAC and tail moment arm in [[SESA1015 M11 - Longitudinal Trim and Static Stability]]
- Later in the degree: [[SESA2022 T3 - Potential Flow]] (how pressure fields create lift) · [[SESA2022 T4 - Thin Aerofoil Theory]] (camber, lift slope, aerodynamic centre) · [[SESA2022 T5 - Finite Wing Theory]] (aspect ratio, spanwise loading, induced drag) · [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] (body and wind axes in six degrees of freedom) · [[Euler Angles and Rotation Matrices]]

## Sources

- *Mechanics of Flight Course Notes* (Prof. A. Keane, October 2020), §2.3 (flight path, relative wind, p. 8), §2.4 Aerodynamic Forces and Moments (pp. 8–9), §2.5 Geometry (pp. 9–10), §2.6 Wing Areas (p. 10), §2.7 Aerofoil (p. 10), §2.8 Aircraft Components (p. 11)
- *Mechanics of Flight Lecture Slides* version 2: pp. 11–14 (aircraft anatomy, internal wing structure), pp. 34–35 (pressure, friction, Sutherland's formula, $N'$ and $A'$), pp. 36–37 (aerofoil nomenclature, NACA 4412), pp. 38–43 (wing areas, geometric definitions, SMC and MAC, twist, lift distribution, elliptic wing example), pp. 44–48 (similarity, dimensionless coefficients, Reynolds number), p. 58 (Reynolds-number table), p. 64 (pusher and tractor configurations, propeller and jet engine layouts), pp. 69–70 (formula summary)
- *Aerodynamics - NACA 4-Digit Airfoil Generator.xlsx* (camber-line and thickness equations)
- Revision workbook: Questions 3, 9, 41, 42

## Self-study tasks

There is no lecturer-set problem list for this topic; the tasks are the slide examples and the revision-workbook questions that use the coefficients and the wing geometry.

### Core

- [ ] Gross area and aspect ratio of the elliptic (Spitfire) wing, and of the rectangular wing with the same area and root chord (Slides v2, p. 43). → [[#An elliptic wing (Slides v2 p. 43)]]
- [ ] NACA 4412 with a 1 m chord: maximum camber, its position and the maximum thickness (Slides v2, p. 37). → [[#NACA four-digit sections]]
- [ ] Revision Q9: lift-curve slope from wind-tunnel force readings, which needs $C_L=L/(qS)$. → [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 9]]
- [ ] Revision Q42: lift-to-drag ratio, with the wing area from $S=b^2/AR$. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 42]]
- [ ] Derive $S$, $\bar c$, $\bar{\bar c}$ and $\bar y$ for a straight-tapered wing and check them on the 11 m example. → [[#The straight-tapered wing]] · [[#A tapered wing]]

### Further practice

- [ ] Revision Q41: wind-tunnel load-cell capacity for a scaled model tested at a Reynolds-matched speed. → [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 41]]
- [ ] Revision Q3: wing area from span and aspect ratio as the first step of a take-off thrust calculation. → [[SESA1015 T02 - Take-off and Landing Solutions#Question 3]]
- [ ] Repeat the dimensional analysis of the lift with $\mu$ and $a$ included, choosing $\rho$, $V$, $l$ as repeating variables (suggested, not lecturer-set). → [[#Viscosity and compressibility: Reynolds and Mach numbers]]
- [ ] Cambridge 3A1 questions on coefficients and Reynolds-number scaling of models. → [[SESA1015 Cambridge Part IIA Practice]]
