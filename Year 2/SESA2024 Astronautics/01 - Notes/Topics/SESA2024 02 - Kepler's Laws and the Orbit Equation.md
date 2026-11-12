---
title: "SESA2024 02 - Kepler's Laws and the Orbit Equation"
module: "SESA2024 Astronautics"
type: topic
stream: "Mission Analysis"
order: 2
tags: [sesa2024, orbital-mechanics, kepler, two-body-problem]
aliases: ["Kepler's Laws", "Orbital motion", "Chapter 5 Lectures 1-3", "Orbit equation"]
date: 2026-10-30
status: lectured
coverage: "Week 4 (2025-10-21, 2025-10-23) and Week 5 (2025-10-28, first half)"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 01 - Systems Engineering and Spacecraft Design]]"]
next_topics: ["[[SESA2024 03 - Orbital Elements and Conic Sections]]"]
key_concepts: ["[[Kepler's Laws]]", "[[Orbit Equation and Conic Sections]]", "[[Orbital Angular Momentum]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch5 - Mission Analysis Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Keplers Laws and the ellipse equation_2025-26_V5.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-21.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-23.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-28 - 1200.txt", "02 - Sources/Lectures/SESA2024 Lecture 4.txt", "02 - Sources/Lectures/SESA2024 Lecture 5.txt", "02 - Sources/Lectures/SESA2024 Lecture 6 - SESA2024 Chapter 5 - - Confirming Keplers Laws.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-11 - Quiz 2 Worked Solutions.txt"]
---

# SESA2024 02 - Kepler's Laws and the Orbit Equation

> [!abstract] Summary
> Kepler found three laws from planetary data: orbits are ellipses with the Sun at a focus, the radius line sweeps equal areas in equal times, and the period squared is proportional to the semi-major axis cubed. Newton's second law and inverse-square gravity, written in rotating radial and transverse axes, prove all three. The transverse equation gives a constant angular momentum per unit mass $h=r^2\dot\theta$ (the second law), the radial equation becomes $u''+u=\mu/h^2$ whose solution is a conic with $a(1-e^2)=h^2/\mu$ (the first law), and dividing the ellipse area by $h/2$ gives $\tau=2\pi\sqrt{a^3/\mu}$ (the third law).

> [!summary]- Exam use: quick path
> - **Use it when:** you need an orbital period, a semi-major axis from a period, $e$ from periapsis and apoapsis radii, or a speed ratio between two points on one orbit.
> - **Assumptions:** two-body problem; the orbiting mass is negligible against the central mass, so $\mu=GM$ of the central body only; no drag, no thrust, no other bodies.
> - **Method:** 1. Pick the right $\mu$ (Earth $398\,600\ \mathrm{km^3/s^2}$, Sun $1.327\times10^{11}\ \mathrm{km^3/s^2}$). 2. Get $a$: for a circle $a=R_E+h_{\text{alt}}$; otherwise $a=(r_p+r_a)/2$. 3. Period $\tau=2\pi\sqrt{a^3/\mu}$, or invert, $a=[\mu(\tau/2\pi)^2]^{1/3}$. 4. Shape: $e=(r_a-r_p)/(r_a+r_p)$. 5. Speed ratio from $h$: $r_pV_p=r_aV_a$.
> - **Common mistakes:** using $\mu_E$ for a heliocentric orbit (or the reverse); mixing metres with $\mathrm{km^3/s^2}$, which is out by a factor of $10^{9/2}$ in the period.
> - **Practise:** [[#Worked examples]] · [[#Self-study tasks|Quiz 2 questions below]]

Kepler worked from data, not theory. He took Tycho Brahe's naked-eye measurements of planetary positions, made with a sextant rather than a telescope, and fitted three laws to them (2025-10-21, ll. 61–100, 261–290). They describe the shape of an orbit, how the speed varies around it, and how long one revolution takes. All three follow from Newton's second law and his inverse-square law of gravitation, which he proved about seventy years later using the calculus he had just invented.

Gravity always points at the central body, so it can change the spacecraft's speed and direction but never its angular momentum about that body. That one fact gives the second law directly. The radial balance between gravity and the "centrifugal" term $r\dot\theta^2$ then decides how far the orbit swings in and out, which gives a conic section: a circle or ellipse if the spacecraft is bound, a parabola or hyperbola if it is not (some comets follow hyperbolic paths).

The derivations are for understanding, not recall, and are not examined (2025-10-21, l. 321; also 2025-10-23, ll. 21–30). The results are used everywhere, so the derivation is given in full (the intermediate steps are in 2020 Lectures 4–6).

## 1. Kepler's three laws

Kepler's laws are:

1. The orbit of each planet is an ellipse with the Sun at one focus (1609).
2. The line joining the planet to the Sun sweeps out equal areas in equal times (1609).
3. The square of the period of the planet is proportional to the cube of its mean distance from the Sun (1619).

They hold just as well for a satellite around the Earth, with the Earth at the focus. The "mean distance" in the third law is the semi-major axis $a$, half the longest diameter of the ellipse, and the period is written $\tau$ (2025-10-21, ll. 211–250).

The second law has a consequence you can see without any maths. Equal areas in equal times means the thin wedge swept near periapsis, close to the focus, must be short and wide, while the wedge near apoapsis is long and thin. The arc covered near periapsis in the same time is therefore longer, so the body moves fastest when it is closest (2025-10-28, ll. 241–290).

![[ast_kepler_equal_areas.png|800]]

## 2. The ellipse in polar form

An ellipse centred on the origin is

$$
\frac{x^2}{a^2}+\frac{y^2}{b^2}=1,
$$

with semi-major axis $a$ and semi-minor axis $b$. The eccentricity $e$ ($0\le e<1$) measures how squashed it is, and each focus sits a distance $ae$ from the centre. Pythagoras on the triangle from the focus to the end of the minor axis, whose hypotenuse is $a$, gives

$$
a^2=b^2+(ae)^2
\quad\Longrightarrow\quad
b^2=a^2(1-e^2).
$$

For orbits the curve has to be described from the focus, by the distance $r$ and angle $\theta$ of the orbiting body, because that is how the motion comes out of Newton's laws. The construction puts the focus $F$ at $x=-ae$, the point $P$ on the ellipse, and a line of length $h$ from the centre $C$ to $P$ at angle $\alpha$. (This $h$ is only a construction length; it is not the angular momentum of §4.)

![[ast_ellipse_polar_geometry.png|800]]

From the small triangle at the centre,

$$
x=h\cos\alpha,\qquad y=h\sin\alpha.
$$

From the larger triangle at the focus, which shares the same height $y$,

$$
r\cos\theta=x+ae,\qquad r\sin\theta=y.
$$

So $x=r\cos\theta-ae$ and $y=r\sin\theta$. Substitute these into the Cartesian equation:

$$
\frac{(r\cos\theta-ae)^2}{a^2}+\frac{r^2\sin^2\theta}{b^2}=1.
$$

Multiply through by $a^2b^2$:

$$
b^2(r\cos\theta-ae)^2+a^2r^2\sin^2\theta=a^2b^2.
$$

Expand the bracket:

$$
b^2r^2\cos^2\theta-2ab^2e\,r\cos\theta+a^2b^2e^2+a^2r^2\sin^2\theta=a^2b^2.
$$

Replace every $b^2$ by $a^2(1-e^2)$ and divide by $a^2$:

$$
(1-e^2)r^2\cos^2\theta-2ae(1-e^2)\,r\cos\theta+a^2e^2(1-e^2)+r^2\sin^2\theta=a^2(1-e^2).
$$

Collect the $r^2$ terms, using $\cos^2\theta+\sin^2\theta=1$:

$$
(1-e^2\cos^2\theta)\,r^2-2ae(1-e^2)\cos\theta\;r-a^2(1-e^2)^2=0,
$$

where the constant term is $a^2(1-e^2)(e^2-1)=-a^2(1-e^2)^2$. This is a quadratic $Ar^2+Br+C=0$ in $r$, solved with the quadratic formula. The discriminant is

$$
B^2-4AC=4a^2e^2(1-e^2)^2\cos^2\theta+4(1-e^2\cos^2\theta)\,a^2(1-e^2)^2.
$$

Take out the common factor:

$$
B^2-4AC=4a^2(1-e^2)^2\left[e^2\cos^2\theta+1-e^2\cos^2\theta\right]=4a^2(1-e^2)^2.
$$

So the square root is $2a(1-e^2)$, and

$$
r=\frac{2ae(1-e^2)\cos\theta\pm2a(1-e^2)}{2(1-e^2\cos^2\theta)}=\frac{a(1-e^2)(e\cos\theta\pm1)}{(1-e\cos\theta)(1+e\cos\theta)}.
$$

The minus sign gives a negative $r$, so take the plus sign, and the factor $(1+e\cos\theta)$ cancels:

$$
r=\frac{a(1-e^2)}{1-e\cos\theta}.
$$

In this construction $\theta$ is measured from the direction pointing away from the nearest vertex, so $\theta=0$ is apoapsis. Orbit problems measure $\theta$ from periapsis instead, which means replacing $\theta$ by $\theta+180^\circ$, and $\cos(\theta+180^\circ)=-\cos\theta$ (2025-10-21, ll. 661–680):

$$
\boxed{r=\frac{a(1-e^2)}{1+e\cos\theta}}
$$

Two special points follow straight away. At periapsis ($\theta=0$) and apoapsis ($\theta=180^\circ$),

$$
r_p=\frac{a(1-e^2)}{1+e}=a(1-e),\qquad r_a=\frac{a(1-e^2)}{1-e}=a(1+e).
$$

Adding them gives

$$
r_p+r_a=a(1-e)+a(1+e)=2a.
$$

Subtracting them gives

$$
r_a-r_p=a(1+e)-a(1-e)=2ae.
$$

Divide the second by the first and the $2a$ cancels:

$$
e=\frac{r_a-r_p}{r_a+r_p}.
$$

> [!check] A point on the ellipse
> Take $a=7000$ km, $e=0.1$ and $\theta=60^\circ$. The boxed equation gives $r=7000(0.99)/(1+0.05)=6600$ km. With the focus at $(ae,0)=(700,0)$ km and periapsis on the $+x$ axis, the point is $x=700+6600\cos60^\circ=4000$ km, $y=6600\sin60^\circ=5716$ km, and $x^2/a^2+y^2/b^2$ with $b^2=a^2(1-e^2)$ comes to 1.000 (checked in Python). At $\theta=90^\circ$ the same equation gives $r=a(1-e^2)=6930$ km, the semi-latus rectum $p$ that reappears in §4.

## 3. Acceleration in rotating radial and transverse axes

$F=ma$ needs the acceleration in the same polar description, which is built from first principles here (2020 Lecture 4). Let $\mathbf i$ be the unit vector pointing radially outwards from the Sun $S$ and $\mathbf j$ the unit vector perpendicular to it in the direction of motion (transverse). These axes rotate with the planet, which is what makes the derivation more than just differentiating components.

At $P$ the velocity has a radial component $\dot r$ and a transverse component $r\dot\theta$. A short time $\delta t$ later the planet is at $Q$, having turned through $\delta\theta$, and its components along the new axes are $\dot r+\delta\dot r$ and $(r+\delta r)(\dot\theta+\delta\dot\theta)$.

![[ast_radial_transverse_axes.png|700]]

The change in velocity has to be measured in one set of axes, so resolve the velocity at $Q$ back along the directions $\mathbf i$ and $\mathbf j$ at $P$. The axes at $Q$ are rotated by $\delta\theta$, so the radial velocity at $Q$ contributes $(\dot r+\delta\dot r)\cos\delta\theta$ along $\mathbf i$ and $(\dot r+\delta\dot r)\sin\delta\theta$ along $\mathbf j$, and the transverse velocity at $Q$ contributes $-(r+\delta r)(\dot\theta+\delta\dot\theta)\sin\delta\theta$ along $\mathbf i$ and $(r+\delta r)(\dot\theta+\delta\dot\theta)\cos\delta\theta$ along $\mathbf j$.

For a small angle, $\sin\delta\theta\approx\delta\theta$ and $\cos\delta\theta\approx1$. The radial change in velocity is then

$$
\delta v_r=(\dot r+\delta\dot r)-\dot r-(r+\delta r)(\dot\theta+\delta\dot\theta)\,\delta\theta.
$$

Drop the products of two small quantities, such as $\delta r\,\delta\theta$:

$$
\delta v_r\approx\delta\dot r-r\dot\theta\,\delta\theta.
$$

The transverse change is

$$
\delta v_\theta=(\dot r+\delta\dot r)\,\delta\theta+(r+\delta r)(\dot\theta+\delta\dot\theta)-r\dot\theta.
$$

Expand the product and drop second-order terms:

$$
\delta v_\theta\approx\dot r\,\delta\theta+r\,\delta\dot\theta+\delta r\,\dot\theta.
$$

The change has two radial terms ($\delta\dot r$ and $-r\dot\theta\,\delta\theta$) and three transverse terms, which come from two vector diagrams (2025-10-23, ll. 281–300). Divide by $\delta t$ and let $\delta t\to0$, so that $\delta\dot r/\delta t\to\ddot r$, $\delta\theta/\delta t\to\dot\theta$, $\delta\dot\theta/\delta t\to\ddot\theta$ and $\delta r/\delta t\to\dot r$:

$$
a_r=\ddot r-r\dot\theta^2,
$$

$$
a_\theta=\dot r\dot\theta+r\ddot\theta+\dot r\dot\theta=2\dot r\dot\theta+r\ddot\theta.
$$

The $-r\dot\theta^2$ term is the centripetal acceleration of the rotating radius, and $2\dot r\dot\theta$ is the Coriolis-type term that appears because the axes rotate while $r$ changes.

## 4. Equations of motion

Gravity is the only force (two-body problem, no drag or thrust). It acts along $-\mathbf i$ with magnitude $GMm/r^2$, where $M$ is the mass of the central body and $m$ the mass of the planet or spacecraft. In vector form, with the unit vector $\mathbf r/r$ (2025-10-23, ll. 341–380):

$$
-\frac{GMm}{r^2}\frac{\mathbf r}{r}=m\mathbf a.
$$

Resolving, with $\mu=GM$ and $m$ cancelled:

$$
\text{radial:}\quad -\frac{\mu}{r^2}=\ddot r-r\dot\theta^2,
\qquad
\text{transverse:}\quad 0=2\dot r\dot\theta+r\ddot\theta.
$$

$\mu$ is the gravitational parameter of the central body: the Sun's for a planet, the Earth's for an Earth satellite.

### Transverse equation: angular momentum is conserved

The transverse acceleration is the product-rule derivative of $r^2\dot\theta$ divided by $r$. Differentiate $r^2\dot\theta$:

$$
\frac{d}{dt}\left(r^2\dot\theta\right)=2r\dot r\dot\theta+r^2\ddot\theta=r\left(2\dot r\dot\theta+r\ddot\theta\right).
$$

So

$$
a_\theta=\frac1r\frac{d}{dt}\left(r^2\dot\theta\right)=0.
$$

Multiply by $r$; a quantity whose time derivative is zero is constant:

$$
\boxed{h=r^2\dot\theta=\text{constant}}
$$

$h$ is the orbital moment of momentum per unit mass (the specific angular momentum). Writing $r^2\dot\theta=r\,(r\dot\theta)$ and noting that $r\dot\theta$ is the transverse velocity $V\sin\alpha$, with $\alpha$ the angle between $\mathbf r$ and $\mathbf V$,

$$
h=rV\sin\alpha=|\mathbf r\times\mathbf V|.
$$

As a vector, $\mathbf h=\mathbf r\times\mathbf V$ points out of the orbit plane by the right-hand rule. Because it is constant in direction as well as size, the orbit plane is fixed in space (2025-10-23, ll. 481–510). At periapsis and apoapsis the velocity is perpendicular to the radius ($\alpha=90^\circ$), so

$$
h=r_pV_p=r_aV_a.
$$

### Radial equation: the orbit equation

The radial equation $\ddot r-r\dot\theta^2=-\mu/r^2$ contains time derivatives, but the orbit equation needs $r$ as a function of $\theta$. Two substitutions do it. Put $u=1/r$, and use $\dot\theta=h/r^2=hu^2$ to swap time derivatives for $\theta$ derivatives with the chain rule (2025-10-23, ll. 521–560; 2020 Lecture 5, ll. 176–300):

$$
\dot r=\frac{d}{dt}\left(\frac1u\right)=-\frac{1}{u^2}\frac{du}{dt}=-\frac{1}{u^2}\frac{du}{d\theta}\dot\theta.
$$

Since $\dot\theta/u^2=r^2\dot\theta=h$,

$$
\dot r=-h\frac{du}{d\theta}.
$$

Differentiate again. $h$ is constant, so

$$
\ddot r=-h\frac{d}{dt}\left(\frac{du}{d\theta}\right)=-h\frac{d^2u}{d\theta^2}\dot\theta.
$$

Substitute $\dot\theta=hu^2$:

$$
\ddot r=-h^2u^2\frac{d^2u}{d\theta^2}.
$$

The centripetal term becomes

$$
r\dot\theta^2=\frac1u\left(hu^2\right)^2=h^2u^3.
$$

Put both into the radial equation, with $\mu/r^2=\mu u^2$:

$$
-h^2u^2\frac{d^2u}{d\theta^2}-h^2u^3=-\mu u^2.
$$

Divide by $-h^2u^2$:

$$
\boxed{\frac{d^2u}{d\theta^2}+u=\frac{\mu}{h^2}}
$$

This is a constant-coefficient linear ODE, the forced simple-harmonic equation from MATH2048. Its general solution is a complementary function plus a particular integral:

$$
u=A\cos\theta+B\sin\theta+\frac{\mu}{h^2}.
$$

Measure $\theta$ from periapsis. There $r$ is a minimum, so $u$ is a maximum and $du/d\theta=0$ at $\theta=0$:

$$
\left.\frac{du}{d\theta}\right|_{\theta=0}=-A\sin0+B\cos0=B=0.
$$

So $u=A\cos\theta+\mu/h^2$. Name the remaining constant through $e=Ah^2/\mu$:

$$
u=\frac{\mu}{h^2}\left(1+e\cos\theta\right).
$$

Invert:

$$
\boxed{r=\frac{h^2/\mu}{1+e\cos\theta}}
$$

> [!check] Substituting back
> With $u=(\mu/h^2)(1+e\cos\theta)$, $u''=-(\mu/h^2)e\cos\theta$, so $u''+u=\mu/h^2$ for every $e$ (confirmed symbolically with SymPy). The ODE fixes the constant term; $e$ is the free constant, set by the speed at periapsis.

### Comparing the two equations: Kepler's first law

This has the same form as the polar ellipse of §2. Both describe the same curve if

$$
\boxed{a(1-e^2)=\frac{h^2}{\mu}=p}
$$

where $p$ is the semi-latus rectum, the radius at $\theta=90^\circ$. Everything on both sides is a constant of the orbit, so orbits are ellipses with the central body at the focus, which is Kepler's first law (2025-10-23, ll. 575–605). More generally the solution is a conic: $e=0$ gives a circle, $0<e<1$ an ellipse, $e=1$ a parabola and $e>1$ a hyperbola (see [[SESA2024 03 - Orbital Elements and Conic Sections]]).

## 5. Kepler's second law

Over a short time the radius sweeps a thin triangle $SPQ$ (2025-10-28, ll. 161–220). Approximate it by the right-angled triangle with height $r$ and base $r\,\delta\theta$, ignoring the sliver between the chord and the arc, which is second order:

$$
\delta A\approx\tfrac12\,r\cdot r\,\delta\theta=\tfrac12r^2\,\delta\theta.
$$

Divide by $\delta t$ and take the limit:

$$
\dot A=\frac{dA}{dt}=\tfrac12r^2\dot\theta=\tfrac12h.
$$

Since $h$ is constant, so is the rate at which area is swept: equal areas in equal times. Kepler's second law is therefore conservation of angular momentum under a central force, and the speed at the two apses follows from $r_pV_p=r_aV_a$.

## 6. Kepler's third law and the period

The period is the time to sweep the whole ellipse (2025-10-28, ll. 291–400):

$$
\tau=\frac{\text{area}}{\dot A}=\frac{\pi ab}{h/2}.
$$

Replace $b$ by $a\sqrt{1-e^2}$:

$$
\tau=\frac{2\pi a^2\sqrt{1-e^2}}{h}.
$$

From the comparison in §4, $h=\sqrt{\mu a(1-e^2)}$:

$$
\tau=\frac{2\pi a^2\sqrt{1-e^2}}{\sqrt{\mu a}\,\sqrt{1-e^2}}.
$$

The $\sqrt{1-e^2}$ cancels and $a^2/\sqrt a=a^{3/2}$:

$$
\boxed{\tau=2\pi\sqrt{\frac{a^3}{\mu}}}
\qquad\Longleftrightarrow\qquad
\boxed{\tau^2=\frac{4\pi^2}{\mu}a^3}
$$

This is the third law with the constant of proportionality found. The period depends on the semi-major axis and the central body only. Two orbits with the same $a$ have the same period however different their eccentricities, which is why a transfer ellipse's half-period follows from its $a$ alone in [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]].

Kepler's third law also gives the mean motion (2020 Lecture 6, ll. 101–125):

$$
n=\frac{2\pi}{\tau}=\sqrt{\frac{\mu}{a^3}},
$$

the constant angular rate at which a point would go round the auxiliary circle of radius $a$. It is constant for a given $a$ even though the real angular rate $\dot\theta$ varies around an ellipse. The number of orbits per day in the ground-track problems of [[SESA2024 12 - Sun- and Earth-Synchronous Orbits]] is a different quantity, written $N$.

### Big G and μ

$G=6.674\times10^{-11}\ \mathrm{m^3\,kg^{-1}\,s^{-2}}$ is tiny, which is why it took more than a century after the *Principia* to measure (2025-10-28, ll. 421–495). Henry Cavendish did it in 1798 with a torsion balance: two small lead balls on a rod hung from a fine wire, attracted by two large lead spheres, the twist of the wire giving the force. His result corresponds to $6.74\times10^{-11}$, about 1 % high. In practice $G$ and $M$ are never used separately, because $\mu=GM$ is known far more precisely from spacecraft tracking than either factor:

| Body | $\mu$ |
|---|---|
| Earth | $3.986\times10^{14}\ \mathrm{m^3/s^2}=398\,600\ \mathrm{km^3/s^2}$ |
| Sun | $1.327\times10^{20}\ \mathrm{m^3/s^2}=1.327\times10^{11}\ \mathrm{km^3/s^2}$ |

## 7. The circular-orbit special case

The same derivation for a circle is shorter, and 2019/20 B1 asks for it (2025-10-23, ll. 321–340). On a circle $r$ is constant, so $\dot r=\ddot r=0$, and the accelerations reduce to

$$
a_r=-r\dot\theta^2,\qquad a_\theta=r\ddot\theta.
$$

The transverse equation gives $\ddot\theta=0$, so the angular rate $\omega=\dot\theta$ is constant. The radial equation gives

$$
\frac{\mu}{r^2}=r\omega^2.
$$

With the orbital speed $V=r\omega$,

$$
\frac{\mu}{r^2}=\frac{V^2}{r}
\quad\Longrightarrow\quad
V_{\text{circ}}=\sqrt{\frac{\mu}{r}}.
$$

The period is the circumference divided by the speed:

$$
\tau=\frac{2\pi r}{V}=2\pi\sqrt{\frac{r^3}{\mu}},
$$

which is the third law with $a=r$.

> [!check] Geostationary and ISS numbers
> At $r=42\,164$ km, $V_{\text{circ}}=\sqrt{398\,600/42\,164}=3.075$ km/s, and $2\pi r/V=86\,164$ s, the sidereal day used in the worked example below. The ISS at $r=6780$ km moves at 7.668 km/s with $h=rV=51\,986\ \mathrm{km^2/s}$.

## Worked examples

The values below use $\mu_E=398\,600.44\ \mathrm{km^3/s^2}$, $\mu_S=1.327\,12\times10^{11}\ \mathrm{km^3/s^2}$, $R_E=6378\ \mathrm{km}$ and $1\ \mathrm{AU}=1.496\times10^{8}\ \mathrm{km}$.

### Geostationary radius from the sidereal day

The orbit whose period matches the Earth's rotation relative to the stars, 23 h 56 min 4 s $=86\,164\ \mathrm s$, has a radius found by inverting the period equation (2020 Lecture 6, ll. 126–150):

$$
a=\left[\mu\left(\frac{\tau}{2\pi}\right)^2\right]^{1/3}=\left[398\,600\left(\frac{86\,164}{2\pi}\right)^2\right]^{1/3}=42\,164\ \mathrm{km}.
$$

That is $6.61R_E$, an altitude of $42\,164-6378=35\,786\ \mathrm{km}$, the rounded 36 000 km usually quoted. Using 24 h instead of the sidereal day gives 42 241 km, 77 km too high.

### ISS orbits per day

With $a=6780\ \mathrm{km}$,

$$
\tau=2\pi\sqrt{\frac{6780^3}{398\,600}}=5556\ \mathrm s=92.6\ \mathrm{min},
\qquad
\frac{86\,400}{5556}=15.55\ \text{orbits per day}.
$$

### Length of the year for Earth, Mars and Pluto

Around the Sun, with $a$ in AU converted to km:

| Planet | $a$ (AU) | $\tau$ (days) | $\tau$ (years) |
|---|---|---|---|
| Earth | 1.000 | 365.26 | 1.000 |
| Mars | 1.524 | 687.0 | 1.881 |
| Pluto | 39.48 | 90 600 | 248.1 |

Inverting for $\tau=365.25\ \mathrm d$ gives $a=0.99999\ \mathrm{AU}$, so a year of 365 days is what an orbit of radius 1 AU requires (2025-10-28, ll. 501–520).

> [!check] Units
> Keep $a$ in km whenever $\mu$ is in $\mathrm{km^3/s^2}$. Converting $\mu$ to metres means multiplying by $10^9$, not $10^3$, because it is cubic; a factor of a thousand wrong shows up as an obviously absurd answer such as 0.0 revolutions a day.

### Quiz 2 numerical questions

A circular orbit at 300 km altitude: $a=6378+300=6678\ \mathrm{km}$, so

$$
\tau=2\pi\sqrt{\frac{6678^3}{398\,600}}=5431\ \mathrm s,
\qquad
\frac{86\,400}{5431}=15.909\ \text{orbits per day}.
$$

Low Earth orbits make about sixteen revolutions a day, so an answer of 400 or 4 means a units error (ll. 21–40).

An asteroid completes one orbit of the Sun while the Earth completes five. Then $\tau_A=5\tau_E$, and taking the ratio of the third law for the two bodies cancels $\mu_S$:

$$
\frac{a_A}{a_E}=\left(\frac{\tau_A}{\tau_E}\right)^{2/3}=5^{2/3}=2.924,
$$

so $a_A=2.92\ \mathrm{AU}$, inside the expected range of two to three AU. The trap is using $\mu_E$; the asteroid orbits the Sun (ll. 55–80). 2024/25 B1 uses the same idea with six asteroid orbits to five Earth orbits, giving $a=(5/6)^{2/3}=0.886\ \mathrm{AU}$.

An orbit whose apoapsis radius is three times its periapsis radius:

$$
e=\frac{r_a-r_p}{r_a+r_p}=\frac{3r_p-r_p}{3r_p+r_p}=\frac{2}{4}=0.5,
$$

independent of $a$ (ll. 121–140).

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 01 - Systems Engineering and Spacecraft Design]]
- Next: [[SESA2024 03 - Orbital Elements and Conic Sections]]- Concepts: [[Kepler's Laws]] · [[Orbit Equation and Conic Sections]] · [[Orbital Angular Momentum]]
- Workbook: [[SESA2024 Workbook Ch5 - Mission Analysis Solutions]]
- Year 1: conservation of angular momentum under a central force, [[FEEG1002 D5 - Angular Impulse and Momentum]]; centripetal acceleration $v^2/r$, [[FEEG1002 D2 - Curvilinear Motion]]
- Maths: the solution of $u''+u=\text{const}$ is the MATH2048 second-order constant-coefficient ODE

## Sources

- `Chapter 5_Keplers Laws and the ellipse equation_2025-26_V5.pdf` (Dr C. Ryan, slides originally by Prof H. Lewis)
- Transcripts `SESA2024 Lecture 2025-10-21.txt` (laws and polar ellipse), `SESA2024 Lecture 2025-10-23.txt` (accelerations, equations of motion, $h$, orbit equation) and `SESA2024 Lecture 2025-10-28 - 1200.txt`, ll. 1–520 (Kepler 2 and 3, $G$)
- Prof Lewis's 2020 recordings, which the 2025 lecture points to for the skipped steps: `SESA2024 Lecture 4.txt` (accelerations), `SESA2024 Lecture 5.txt` (equation of motion) and `SESA2024 Lecture 6 - SESA2024 Chapter 5 - - Confirming Keplers Laws.txt` (Kepler 2, 3, mean motion, activities)
- `SESA2024 Lecture 2025-11-11 - Quiz 2 Worked Solutions.txt`
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 4 (celestial mechanics) and Ch. 5

## Self-study tasks

### Core

- [ ] Quiz 2: orbital period and orbits per day for a circular orbit at 300 km (Quiz 2 walk-through, ll. 15–40). Target 5431 s and 15.909. → [[#Quiz 2 numerical questions]]
- [ ] Quiz 2: semi-major axis of an asteroid that orbits once while the Earth orbits five times, in AU (ll. 55–80). Target 2.92 AU. → [[#Quiz 2 numerical questions]]
- [ ] Quiz 2: eccentricity when $r_a=3r_p$ (ll. 121–140). Target 0.5. → [[#Quiz 2 numerical questions]]
- [ ] Kepler 3 activity: the year for Mars and Pluto, Earth's $a$ from 365.25 days, ISS orbits per day, and the GEO radius from 23 h 56 min (2020 Lecture 6, ll. 126–150; 2025-10-28, ll. 501–520). → [[#Worked examples]]
- [ ] State Kepler's three laws and say which conservation law the second one expresses (2015/16 Q2(i); 2018/19 Q2(i)). → [[#1. Kepler's three laws]] · [[#5. Kepler's second law]]
- [ ] Show that the orbit plane is fixed and that $r_pV_p=r_aV_a$ (Workbook Ch5 Q1). → [[#Transverse equation: angular momentum is conserved]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q1. Invariant plane and the periapsis-apoapsis speed relation|Workbook solution]]
- [ ] Prove $r_a=a(1+e)$ (Workbook Ch5 Q5). → [[#2. The ellipse in polar form]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q5. Prove that the apoapsis radius is a(1+e)|Workbook solution]]

### Further practice

- [ ] Repeat the derivation for a circular orbit to get $V=\sqrt{\mu/r}$ and $\tau=2\pi\sqrt{r^3/\mu}$ ("if you wanted to, you can do your own", 2025-10-23, ll. 321–340; 2019/20 B1). → [[#7. The circular-orbit special case]] · [[SESA2024 2019-20 Exam Solutions#B1: GEO|2019/20 B1]]
- [ ] Finish the polar-ellipse algebra the lecture skipped, from the quadratic in $r$ (2025-10-21, ll. 581–660). → [[#2. The ellipse in polar form]]
- [ ] Apply the boundary condition at periapsis to the general solution of $u''+u=\mu/h^2$ (left for a tutorial, 2025-10-23, l. 575). → [[#Radial equation: the orbit equation]]
- [ ] Check the solution of $u''+u=\mu/h^2$ on Wolfram Alpha (2020 Lecture 5, ll. 351–360; 2025-10-23, ll. 541–570).
- [ ] Use Kepler 3 as a ratio for an asteroid in a 6:5 resonance with the Earth (2024/25 B1). → [[#Quiz 2 numerical questions]] · [[SESA2024 2024-25 Exam Solutions#B1: Asteroid deflection|2024/25 B1]]
- [ ] Read Fortescue, Stark and Swinerd Ch. 5 up to and including the mission-analysis section (2020 Lecture 6, ll. 150–155).

## Transcript and slide slips

> [!warning] Transcript slip (2025-10-28, ll. 401–420)
> Where: [[#4. Equations of motion]].
>
> The lecture says that for a satellite going around the Earth, $\mu$ "is just the mass of the satellite". It is $GM$ with $M$ the mass of the Earth. The satellite's mass cancels out of the equations, which is why a 1 kg CubeSat and the ISS at the same height have the same period.

> [!warning] Transcript slip (2025-10-23, ll. 541–545)
> Where: [[#Radial equation: the orbit equation]].
>
> The lecture reads this equation out as "d squared u by d theta squared plus 1 over r is equal to mu over h". The right-hand side is $\mu/h^2$; the $1/r$ is $u$, so that part is consistent. The slide has it right.

> [!warning] Transcript slip (2025-10-28, ll. 190–200)
> Where: [[#5. Kepler's second law]].
>
> The lecture first says $\tfrac12r^2\,d\theta/dt$ "is equal to h", then corrects it a few lines later to "half that magnitude". The rate of sweeping is $\dot A=h/2$, and that factor of one half is needed for the period below.

> [!warning] Transcript slips (2025-10-28, ll. 461–480)
> Where: [[#Big G and μ]].
>
> The lecture describes Cavendish's large spheres as "about 300 kilograms each"; they were about 158 kg (348 lb). It also puts the experiment "120 years after Newton"; the *Principia* was 1687, so it was 111 years.
