---
title: "SESA2024 04 - Orbital Energy and the Vis-Viva Equation"
module: "SESA2024 Astronautics"
type: topic
stream: "Mission Analysis"
order: 4
tags: [sesa2024, orbital-mechanics, orbital-energy, vis-viva]
aliases: ["Orbital energy equation", "Vis-viva", "Chapter 5 Lectures 9-10"]
date: 2026-10-30
status: lectured
coverage: "Week 9 (2025-11-27)"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]", "[[SESA2024 03 - Orbital Elements and Conic Sections]]"]
next_topics: ["[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]"]
key_concepts: ["[[Vis-Viva Equation]]", "[[Orbital Angular Momentum]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch5 - Mission Analysis Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Orbital energy_V1.pdf", "02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Orbital energy worked example_V1.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-27.txt"]
---

# SESA2024 04 - Orbital Energy and the Vis-Viva Equation

> [!abstract] Summary
> Gravity is a conservative force, so the specific orbital energy $\varepsilon=V^2/2-\mu/r$ is the same at every point of an orbit. Evaluating it at periapsis and apoapsis, where $r_pV_p=r_aV_a$, gives $\varepsilon=-\mu/2a$, which leads to the orbital energy (vis-viva) equation $V^2/2-\mu/r=-\mu/2a$. It gives the speed anywhere on any conic from $r$ and $a$ alone, and every ΔV calculation in the module starts from it.

> [!summary]- Exam use: quick path
> - **Use it when:** you need the speed at a point on an orbit, $a$ from a measured $(r,V)$, or whether an object is bound, escaping or will hit the Earth.
> - **Assumptions:** two-body, no drag or thrust between the two points; $r$ is measured from the centre of the central body, not the surface.
> - **Method:** 1. Convert altitudes to radii, $r=R_E+h$. 2. Get $a$: $(r_p+r_a)/2$, or $a=r$ for a circle, or $1/a=2/r-V^2/\mu$ from a measured pair. 3. $V=\sqrt{\mu(2/r-1/a)}$. 4. If you need $e$: $e=r_a/a-1$ or $1-r_p/a$. 5. Check $r_pV_p=r_aV_a$.
> - **Common mistakes:** using altitude for $r$; forgetting that $a<0$ for a hyperbola, so $-\mu/2a>0$.
> - **Practise:** [[#The 200 km circle and the 200 by 40 000 km ellipse]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q4. Unidentified object with apogee height 1000 km and speed 5.589 km/s|Workbook Q4]]

An orbit is a continuous exchange between kinetic and potential energy. A spacecraft climbing from periapsis towards apoapsis slows down, trading speed for height; on the way back down it speeds up again. Nothing is lost, because gravity is conservative: the work it does between two points does not depend on the path taken (2025-11-27, ll. 67–88). So the total energy is a constant of the orbit, like the angular momentum, and fixing its value turns out to need only the semi-major axis.

Dr Ryan called the result "probably the most important equation that you're going to see" in the orbital mechanics, alongside the rocket equation (ll. 23–30, 265–285). It works the same for circles, ellipses, parabolas and hyperbolas.

## 1. Kinetic and potential energy

Kinetic energy is $\tfrac12mV^2$, with $m$ the mass of the spacecraft. Gravitational potential energy needs a reference, and the natural one is a point infinitely far from the central body, where the gravitational force has vanished (ll. 89–110). The potential energy at radius $r$ is the work done by gravity in bringing the spacecraft in from infinity, which is negative:

$$
PE=-\int_\infty^r\frac{\mu m}{r'^2}\,dr'.
$$

Integrate:

$$
PE=-\mu m\left[-\frac1{r'}\right]_\infty^r=-\frac{\mu m}{r}.
$$

> [!warning] Transcript slip (2025-11-27, ll. 105–110)
> The force is described as "mu ... times by m, the mass of the earth". In $\mu m/r^2$ the $m$ is the spacecraft's mass; the Earth's mass is already inside $\mu=GM$.

Energy conservation then says $KE+PE$ is constant. Divide by $m$ to work per unit mass and call the constant $\varepsilon$, the specific orbital energy (ll. 111–150):

$$
\frac{V^2}{2}-\frac{\mu}{r}=\varepsilon.
$$

The potential term is negative everywhere, so a spacecraft can have negative total energy, and it does whenever it is bound.

## 2. The value of ε

The lecture said the slide's derivation was hard to follow and did it differently on the board (ll. 199–265); this is his version with every step. Start from angular momentum. At periapsis and apoapsis the velocity is perpendicular to the radius, so $h=r_pV_p=r_aV_a$ and

$$
\frac{V_p}{V_a}=\frac{r_a}{r_p}.
$$

Square it:

$$
\frac{V_p^2}{V_a^2}=\frac{r_a^2}{r_p^2}.
$$

The energy equation at each apsis gives $V_p^2=2(\varepsilon+\mu/r_p)$ and $V_a^2=2(\varepsilon+\mu/r_a)$. Substitute; the factors of 2 cancel:

$$
\frac{\varepsilon+\mu/r_p}{\varepsilon+\mu/r_a}=\frac{r_a^2}{r_p^2}.
$$

Cross-multiply:

$$
r_p^2\left(\varepsilon+\frac{\mu}{r_p}\right)=r_a^2\left(\varepsilon+\frac{\mu}{r_a}\right).
$$

Expand:

$$
\varepsilon r_p^2+\mu r_p=\varepsilon r_a^2+\mu r_a.
$$

Collect $\varepsilon$ on one side:

$$
\varepsilon\left(r_p^2-r_a^2\right)=\mu\left(r_a-r_p\right).
$$

Factorise the difference of two squares, $r_p^2-r_a^2=(r_p+r_a)(r_p-r_a)$:

$$
\varepsilon=\frac{\mu(r_a-r_p)}{(r_p+r_a)(r_p-r_a)}=-\frac{\mu}{r_p+r_a}.
$$

The major axis is $r_p+r_a=2a$, so

$$
\boxed{\varepsilon=-\frac{\mu}{2a}}
$$

The energy depends only on $a$, just as the period does. Substituting back gives the orbital energy equation:

$$
\boxed{\frac{V^2}{2}-\frac{\mu}{r}=-\frac{\mu}{2a}}
\qquad\Longleftrightarrow\qquad
\boxed{V=\sqrt{\mu\left(\frac2r-\frac1a\right)}}
$$

The course calls it the energy equation or orbital energy equation; "vis-viva" is the textbook name. The derivation used an ellipse, but the result holds for every conic: a parabola has $a\to\infty$ and $\varepsilon=0$, a hyperbola has $a<0$ and $\varepsilon>0$ (ll. 285–295).

| Orbit | $a$ | $\varepsilon$ |
|---|---|---|
| circle, ellipse | $>0$ | $<0$, bound |
| parabola | $\infty$ | $0$, just escapes |
| hyperbola | $<0$ | $>0$, escapes with speed to spare |

![[ast_visviva_speed.png|760]]

## 3. Special cases

Circular orbit (ll. 295–310). With $r=a$:

$$
\frac{V^2}{2}=\frac{\mu}{r}-\frac{\mu}{2r}=\frac{\mu}{2r}
\quad\Longrightarrow\quad
\boxed{V_c=\sqrt{\frac{\mu}{r}}}
$$

the same result as the force balance in [[SESA2024 02 - Kepler's Laws and the Orbit Equation#7. The circular-orbit special case|note 02 §7]]. A lower orbit is faster: to overtake a spacecraft ahead of you in the same orbit you drop to a lower orbit, go round faster, then climb back (ll. 353–370).

> [!warning] Transcript slip (2025-11-27, l. 309)
> The ISS is said to take "45 minutes to orbit at 400 kilometres altitude". Its period is about 92 minutes ([[SESA2024 02 - Kepler's Laws and the Orbit Equation#ISS orbits per day|note 02]]); 45 minutes is roughly the time it spends in sunlight or in shadow on each orbit.

Escape speed. Let $a\to\infty$, so $1/a\to0$:

$$
V_{esc}=\sqrt{\frac{2\mu}{r}}=\sqrt2\,V_c.
$$

Speeds at the apses. Put $r_p=a(1-e)$ into the energy equation:

$$
V_p^2=\mu\left(\frac{2}{a(1-e)}-\frac1a\right)=\frac{\mu}{a}\cdot\frac{2-(1-e)}{1-e}=\frac{\mu}{a}\cdot\frac{1+e}{1-e}.
$$

By the same steps with $r_a=a(1+e)$, $V_a^2=(\mu/a)(1-e)/(1+e)$. Their ratio is $(1+e)/(1-e)=r_a/r_p$, as angular momentum requires. In terms of the two radii, using $a=(r_p+r_a)/2$,

$$
V_p=\sqrt{\frac{2\mu r_a}{r_p(r_p+r_a)}},\qquad V_a=\sqrt{\frac{2\mu r_p}{r_a(r_p+r_a)}}.
$$

These two are the building blocks of the Hohmann transfer in [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer|the next note]].

## 4. Which satellite is fastest?

The lecture's poll question (ll. 309–415): at the marked points, which is fastest, a satellite on a high circular orbit A, one on a lower circular orbit B, or one at the low point of an elliptical orbit C whose periapsis is at about the same radius as B?

A is slower than B because $V_c=\sqrt{\mu/r}$ falls with radius. For C, the radius is about $r_B$, but the semi-major axis looks roughly twice that, $a\approx2r_C$. Then

$$
V_C^2=\mu\left(\frac{2}{r_C}-\frac{1}{2r_C}\right)=\frac{3\mu}{2r_C},
\qquad
V_C=\sqrt{\frac32}\,V_{c}=1.22\,V_c.
$$

So C is fastest. The intuition: at its low point, C needs extra kinetic energy to climb to its high apoapsis. At any shared point, the orbit with the larger $a$ (higher energy) has the higher speed. That is why a forward burn at one point raises the opposite side of the orbit.

## 5. Identifying an orbit from one measurement

Rearranging the energy equation for $a$ turns a single measured position and speed into the orbit's size:

$$
\frac1a=\frac2r-\frac{V^2}{\mu}.
$$

If the measurement is at an apsis, the other apsis follows from $r_p+r_a=2a$. Workbook Ch5 Q4 is the classic: an object at apogee, 1000 km up ($r_a=7378$ km), moving at 5.589 km/s. Then $1/a=2/7378-5.589^2/398\,600$, so $a=5189$ km and $r_p=2a-r_a=3000$ km. That is inside the Earth, so the object is on a suborbital trajectory: a ballistic missile, not a satellite. 2023/24 B1 does the same for Starship's second test flight at apogee.

## Worked examples

Constants: $R_E=6378$ km, $\mu=398\,600\ \mathrm{km^3/s^2}$. All numbers recomputed in Python.

### The 200 km circle and the 200 by 40 000 km ellipse

This is the Chapter 5 worked example (`Orbital energy worked example_V1.pdf`, Lecture 10). Find the speed (i) in a circular orbit at 200 km altitude and (ii) at the perigee and apogee of an ellipse with perigee 200 km and apogee 40 000 km.

For the circle, $r_1=6378+200=6578$ km:

$$
V_1=\sqrt{\frac{398\,600}{6578}}=7.784\ \mathrm{km/s}.
$$

For the ellipse, $r_p=6578$ km and $r_a=6378+40\,000=46\,378$ km, so

$$
a=\frac{6578+46\,378}{2}=26\,478\ \mathrm{km},
\qquad
e=\frac{46\,378-6578}{46\,378+6578}=0.752.
$$

At perigee:

$$
V_p=\sqrt{398\,600\left(\frac{2}{6578}-\frac{1}{26\,478}\right)}=10.302\ \mathrm{km/s}.
$$

At apogee:

$$
V_a=\sqrt{398\,600\left(\frac{2}{46\,378}-\frac{1}{26\,478}\right)}=1.461\ \mathrm{km/s}.
$$

> [!check] Angular momentum
> $r_pV_p=6578\times10.302=67\,770$ and $r_aV_a=46\,378\times1.461=67\,770\ \mathrm{km^2/s}$, equal as they must be. The ellipse's specific energy is $-\mu/2a=-7.53\ \mathrm{km^2/s^2}$, and the escape speed at 200 km would be $\sqrt2\times7.784=11.01$ km/s, so the ellipse's 10.30 km/s is bound, as its positive $a$ says.

Going from the circle to the ellipse at perigee needs $10.302-7.784=2.518$ km/s, which is the first burn of the transfer in the next note.

### A Molniya orbit from Heavens-Above

Activity 1 (ll. 419–600) took the elements of the Molniya-1T satellite from Heavens-Above, which lists perigee and apogee heights of 1516 km and 24 738 km, $e=0.59$, $i=64.4^\circ$ and $\Omega=245^\circ$, and entered them in Prof Lewis's Excel orbit visualiser. The spreadsheet needs $a$, so the heights must first become radii. The lecture used $R_E=6371$ km:

$$
r_p=6371+1516=7887\ \mathrm{km},\qquad r_a=6371+24\,738=31\,109\ \mathrm{km},
$$

$$
a=\frac{7887+31\,109}{2}=19\,498\ \mathrm{km},\qquad e=\frac{31\,109-7887}{31\,109+7887}=0.595.
$$

The energy equation then gives

$$
V_p=\sqrt{398\,600\left(\frac{2}{7887}-\frac{1}{19\,498}\right)}=8.98\ \mathrm{km/s},
\qquad
V_a=\sqrt{398\,600\left(\frac{2}{31\,109}-\frac{1}{19\,498}\right)}=2.28\ \mathrm{km/s},
$$

matching the 8.9 and 2.3 km/s the spreadsheet showed as the satellite was stepped round (ll. 595–600). The period is $2\pi\sqrt{a^3/\mu}=7.53$ h, and most of it is spent slowly near apogee over the northern hemisphere, which is the point of the orbit.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 03 - Orbital Elements and Conic Sections]]
- Next: [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]
- Concepts: [[Vis-Viva Equation]] · [[Orbital Angular Momentum]]
- Formula sheet: [[SESA2024 Formula Sheet]]
- Year 1: gravitational potential energy $-GMm/r$ in [[FEEG1002 D3 - Work, Energy and Power]]; the perigee–apogee problem combining energy and angular momentum in [[FEEG1002 D5 - Angular Impulse and Momentum]]

## Sources

- `Chapter 5_Orbital energy_V1.pdf` and `Chapter 5_Orbital energy worked example_V1.pdf` (Dr C. Ryan, after Prof H. Lewis)
- Transcript `SESA2024 Lecture 2025-11-27.txt`
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 4

## Self-study tasks

### Core

- [ ] Show that $\varepsilon=-\mu/2a$ from energy conservation and $r_pV_p=r_aV_a$ (done on the board, 2025-11-27, ll. 199–265; Workbook Ch5 Q2). → [[#2. The value of ε]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q2. Show that the specific energy is -mu over 2a|Workbook solution]]
- [ ] The worked example: speeds on a 200 km circle and at perigee and apogee of a 200 by 40 000 km ellipse (left for the class, ll. 419–425). Targets 7.784, 10.302 and 1.461 km/s. → [[#The 200 km circle and the 200 by 40 000 km ellipse]]
- [ ] Which satellite has the greatest speed? (lecture poll, ll. 309–415) → [[#4. Which satellite is fastest?]]
- [ ] Identify an object at 1000 km apogee moving at 5.589 km/s (Workbook Ch5 Q4). → [[#5. Identifying an orbit from one measurement]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q4. Unidentified object with apogee height 1000 km and speed 5.589 km/s|Workbook solution]]

### Further practice

- [ ] Activity 1: find Molniya-1T on Heavens-Above, convert its perigee and apogee heights to $a$, and enter the elements in the Excel visualiser (ll. 419–600). → [[#A Molniya orbit from Heavens-Above]]
- [ ] Activity 2: use the ΔV spreadsheet to see how a tangential burn changes the orbit, and find the ΔV at which it escapes (ll. 600–645). The spreadsheet is on Blackboard, not in the vault.
- [ ] Derive $V_p$ and $V_a$ in terms of $a$ and $e$, and the escape speed. → [[#3. Special cases]]
- [ ] Starship at apogee: find $a$, $e$ and whether perigee is inside the Earth (2023/24 B1). → [[SESA2024 2023-24 Exam Solutions]]
