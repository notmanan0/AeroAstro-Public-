---
title: "SESA2024 12 - Sun- and Earth-Synchronous Orbits"
module: "SESA2024 Astronautics"
type: topic
stream: "Remote Sensing Case Study"
order: 12
tags: [sesa2024, remote-sensing, sun-synchronous, repeat-ground-track, j2]
aliases: ["SSO", "Sun-synchronous orbit", "Earth-synchronous orbit", "Chapter 11 Lectures 4-5"]
date: 2026-10-30
status: lectured
coverage: "Week 11 (2025-12-09; first part of 2025-12-11)"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 11 - Payload and Orbit Selection]]", "[[SESA2024 06 - Attitude Control]]"]
next_topics: ["[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]"]
key_concepts: ["[[Sun-Synchronous Orbit]]", "[[Nodal Regression (J2)]]", "[[Repeat Ground Track]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Sun and Earth synchronous orbits_V1.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-12-09.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-12-11.txt"]
---

# SESA2024 12 - Sun- and Earth-Synchronous Orbits

> [!abstract] Summary
> A Sun-synchronous orbit crosses any given latitude at the same local solar time on every pass, which needs the orbit plane to turn eastwards once a year, at 0.9856° per day. Thrusting would cost far too much propellant, but the Earth's equatorial bulge ($J_2$) makes the plane regress at a rate set by $a$ and $i$, and for 700–900 km the bulge gives exactly the right rate at an inclination of about 98–99°. An Earth-synchronous orbit repeats its ground track after $N$ orbits in $M$ days; allowing for both the Earth's rotation and the plane's regression, both conditions together require $\tau=(M/N)\times86\,400$ s.

> [!summary]- Exam use: quick path
> - **Use it when:** you need the inclination of a Sun-synchronous orbit, a repeat-track period, or the altitude for $N$ orbits in $M$ days.
> - **Assumptions:** circular orbit; only the $J_2$ perturbation; $a$ in km in the regression formula; integer, coprime $N$ and $M$.
> - **Method:** 1. Required regression $\dot\Omega=360^\circ/365.25\ \mathrm d=0.9856^\circ$/day (eastward). 2. Period from the repeat: $\tau=(M/N)\times86\,400$ s. 3. $a=[\mu(\tau/2\pi)^2]^{1/3}$, $h=a-R_E$. 4. $\cos i=0.9856/(-2.0647\times10^{14}a^{-7/2})$. 5. Check $i>90^\circ$ and $h$ in range.
> - **Common mistakes:** putting $a$ in metres into the regression formula; using the sidereal day in $\tau=(M/N)\times86\,400$, where the solar day appears because regression has already been allowed for.
> - **Practise:** [[#Inclination for 700 to 900 km]] · [[SESA2024 2024-25 Exam Solutions#Section A|2024/25 A6]]

The first pass for a remote-sensing imager ([[SESA2024 11 - Payload and Orbit Selection]]) leaves two operational requirements: the same illumination on every pass, and the same viewing geometry at regular intervals. Each becomes a condition on the orbital elements, and both can be met at once.

For illumination, the orbit plane can be treated as a hoop around a ball, carried round the Sun. Over a year an unperturbed orbit plane keeps its orientation fixed in space, so at the summer solstice the Sun might be off to one side of the plane and at the equinox square on to it. The Sun angle at the ground track drifts through the year. For constant illumination the plane must instead turn with the Earth's motion round the Sun, completing one turn a year. The torque is supplied by the Earth's own shape.

## 1. Sun-synchronism

A spacecraft in a Sun-synchronous orbit arrives over a given location at the same local solar time on each pass, so the Sun stands at the same height and direction whenever a target is imaged. Seasonal changes in the Sun's elevation still occur; Sun-synchronism removes the drift due to the orbit.

The condition is that the angle $\phi$ between the Earth–Sun line and the orbit plane stays constant. In terms of the right ascension of the Sun $\alpha_S$ and the RAAN $\Omega$,

$$
\phi=\alpha_S-\Omega=\text{constant}.
$$

Differentiate with respect to time:

$$
\dot\Omega=\dot\alpha_S.
$$

The Sun's right ascension goes once round in a year, so the orbit plane must turn eastwards at

$$
\dot\Omega=\frac{360^\circ}{365.25\ \mathrm{days}}=0.9856^\circ\ \text{per day},
$$

a little under one degree per day.

## 2. Nodal regression from the Earth's oblateness

Turning the orbit plane with thrusters would be very expensive, since plane changes cost a great deal of ΔV. The alternative is a natural perturbation.

The Earth is not a sphere. Its rotation over billions of years has made it slightly oblate: the equatorial radius is about 6378 km and the polar radius about 6357 km, a difference of about 21 km. A perfectly spherical Earth pulls an orbiting spacecraft straight towards its centre. The bulge adds a tiny pull towards the equatorial plane whenever the spacecraft is above or below it, which has a small component normal to the orbit and so produces a torque on the orbit.

The orbit, however, carries angular momentum $\mathbf h$, like a spinning bicycle wheel. A torque applied to it does not tip the plane over; it makes $\mathbf h$ precess, as a spinning wheel does under a torque ([[SESA2024 06 - Attitude Control#3. Gyroscopic precession and momentum bias|note 06 §3]]). The node, where the orbit crosses the equator, therefore moves a little on each orbit: nodal regression.

The rate for a circular orbit is

$$
\dot\Omega=-\frac32J_2\sqrt{\mu}\,R_E^2\,a^{-7/2}\cos i,
$$

with $J_2=1.0826\times10^{-3}$ the dimensionless oblateness coefficient. The full derivation needs perturbation theory beyond this module and is not examined (outline: [[#Where the regression rate comes from]]). With $a$ in km, $\mu=398\,600.4\ \mathrm{km^3/s^2}$ and $R_E=6378.1$ km, the constant in front of $a^{-7/2}\cos i$ is first evaluated in radians per second:

$$
\frac32J_2R_E^2\sqrt\mu=1.5\times1.0826\times10^{-3}\times6378.1^2\times631.35=4.1707\times10^{7}\ \mathrm{km^{7/2}\,rad/s}.
$$

Multiply by 86 400 s per day and by $180/\pi$ degrees per radian:

$$
4.1707\times10^{7}\times86\,400\times\frac{180}{\pi}=2.0647\times10^{14},
$$

so

$$
\boxed{\dot\Omega=-2.0647\times10^{14}\,a^{-7/2}\cos i\quad(\text{deg/day},\ a\text{ in km})}
$$

The constant only works with $a$ in kilometres.

### Where the regression rate comes from

Write the Earth's gravitational potential per unit mass as $U=\mu/r+\mathcal R$, with the force per unit mass equal to $\nabla U$. The bulge contributes the $J_2$ term

$$
\mathcal R=-\frac{\mu J_2R_E^2}{2r^3}\left(3\sin^2\delta-1\right),
$$

where $\delta$ is the spacecraft's latitude. Over the equator ($\delta=0$) $\mathcal R$ is positive, an extra pull from the extra mass there; over the poles it is negative.

The latitude follows from the orbital elements. In the spherical triangle formed by the ascending node, the spacecraft and the point on the equator below it, the angle at the node is $i$ and the arc from the node to the spacecraft is the argument of latitude $u=\omega+\theta$, so

$$
\sin\delta=\sin i\sin u.
$$

Substitute into $\mathcal R$:

$$
\mathcal R=-\frac{\mu J_2R_E^2}{2r^3}\left(3\sin^2i\,\sin^2u-1\right).
$$

The node moves by a tiny amount per orbit, so only the average of $\mathcal R$ over one orbit matters. On a circular orbit $r=a$ and $u$ grows at a constant rate, so the average of $\sin^2u$ over a revolution is $\tfrac12$:

$$
\langle\mathcal R\rangle=-\frac{\mu J_2R_E^2}{2a^3}\left(\frac32\sin^2i-1\right).
$$

Take the minus sign inside the bracket:

$$
\langle\mathcal R\rangle=\frac{\mu J_2R_E^2}{4a^3}\left(2-3\sin^2i\right).
$$

Lagrange's planetary equation for the node, taken from perturbation theory (Fortescue, Stark and Swinerd, Ch. 5), is

$$
\dot\Omega=\frac{1}{na^2\sqrt{1-e^2}\,\sin i}\,\frac{\partial\langle\mathcal R\rangle}{\partial i}.
$$

Set $e=0$ for the circular orbit:

$$
\dot\Omega=\frac{1}{na^2\sin i}\,\frac{\partial\langle\mathcal R\rangle}{\partial i}.
$$

Differentiate the averaged potential with respect to $i$, using $\dfrac{d}{di}\sin^2i=2\sin i\cos i$:

$$
\frac{\partial\langle\mathcal R\rangle}{\partial i}=\frac{\mu J_2R_E^2}{4a^3}\left(-6\sin i\cos i\right)=-\frac{3\mu J_2R_E^2}{2a^3}\sin i\cos i.
$$

Substitute; the $\sin i$ cancels:

$$
\dot\Omega=-\frac{3\mu J_2R_E^2}{2na^5}\cos i.
$$

The mean motion is $n=\sqrt{\mu/a^3}$, so $\mu/n=\sqrt\mu\,a^{3/2}$:

$$
\dot\Omega=-\frac32J_2\sqrt\mu\,R_E^2\,a^{3/2}a^{-5}\cos i.
$$

Collect the powers of $a$:

$$
\dot\Omega=-\frac32J_2\sqrt\mu\,R_E^2\,a^{-7/2}\cos i,
$$

the rate above, in radians per second when $\mu$, $R_E$ and $a$ share one length unit. The same expression is often written $\dot\Omega=-\tfrac32nJ_2(R_E/a)^2\cos i$, since $\sqrt\mu\,a^{-7/2}=n/a^2$. The surviving $\cos i$ sets the sign of the regression.

> [!check] An 800 km Sun-synchronous orbit from the radian form
> At $a=7178$ km, $n=\sqrt{398\,600.4/7178^3}=1.0382\times10^{-3}$ rad/s and $(R_E/a)^2=(6378.1/7178)^2=0.78954$, so $\tfrac32nJ_2(R_E/a)^2=1.5\times1.0382\times10^{-3}\times1.0826\times10^{-3}\times0.78954=1.3311\times10^{-6}$ rad/s. The required rate is $2\pi/(365.25\times86\,400)=1.9910\times10^{-7}$ rad/s, so $\cos i=-1.9910\times10^{-7}/(1.3311\times10^{-6})=-0.14958$ and $i=98.60^\circ$. The degrees-per-day constant gives the same: $a^{-7/2}=3.1914\times10^{-14}$, $\cos i=0.9856/(-2.0647\times10^{14}\times3.1914\times10^{-14})=-0.14957$, $i=98.60^\circ$, as in the table in [[#Inclination for 700 to 900 km]].

### Which inclination

The sign of $\dot\Omega$ is set by $\cos i$:

- $0\le i<90^\circ$: $\cos i>0$, $\dot\Omega<0$, the node moves west, the wrong way;
- $i=90^\circ$: $\cos i=0$, no regression; a polar orbit feels no net torque from the bulge;
- $90^\circ<i\le180^\circ$: $\cos i<0$, $\dot\Omega>0$, the node moves east, as required.

So a Sun-synchronous orbit is retrograde, tipped a little past the pole. Setting $\dot\Omega=0.9856$ and solving,

$$
\cos i=\frac{0.9856}{-2.0647\times10^{14}\,a^{-7/2}}.
$$

For altitudes of 200–1000 km this gives $96^\circ$ to $99.5^\circ$, and for the first-pass 700–900 km about $98^\circ$ to $99^\circ$. That inclination still covers almost the whole globe, so a Sun-synchronous orbit gives near-global coverage as a bonus.

![[ast_sso_inclination.png|700]]

## 3. Earth-synchronism

An Earth-synchronous orbit's ground track repeats precisely after a certain number of orbits $N$ in a certain number of days $M$. Once the track repeats, the spacecraft returns over any target, a fire in California or a single ground station, with the same geometry every $M$ days. The track grows orbit by orbit until it meets its own start.

Define the longitude displacement $\Delta\lambda$ between successive equator crossings. The condition is that $N$ displacements add up to exactly $M$ full turns:

$$
N\,\Delta\lambda=M\times360^\circ.
$$

Examples include a track at $63^\circ$ inclination repeating after 77 orbits in 5 days, and one at about $70^\circ$ repeating after 15 orbits in 1 day, both Earth-synchronous but not Sun-synchronous; and one at $96^\circ$ repeating after 14 orbits in 1 day, which is both.

## 4. Both at once

The displacement per orbit has two parts. The Earth rotates eastwards under the orbit, which shifts the track westwards by

$$
\Delta\lambda_{rot}=360^\circ\,\frac{\tau}{T_{sid}},
$$

where $T_{sid}=86\,164.1$ s is the sidereal day, the Earth's rotation period relative to the stars. Meanwhile the Sun-synchronous orbit plane turns eastwards by $360^\circ$ per year, which reduces the westward shift by

$$
\Delta\lambda_{reg}=360^\circ\,\frac{\tau}{T_{yr}},
$$

with $T_{yr}=365.25\times86\,400=31\,557\,600$ s. The net displacement is

$$
\Delta\lambda=360^\circ\,\tau\left(\frac{1}{T_{sid}}-\frac{1}{T_{yr}}\right).
$$

Put this into the Earth-synchronism condition:

$$
N\times360^\circ\,\tau\left(\frac{1}{T_{sid}}-\frac{1}{T_{yr}}\right)=M\times360^\circ.
$$

Cancel the $360^\circ$ and solve for $\tau$:

$$
\tau=\frac MN\cdot\frac{1}{1/T_{sid}-1/T_{yr}}.
$$

Insert the numbers:

$$
\frac{1}{86\,164.1}-\frac{1}{31\,557\,600}=1.160575\times10^{-5}-0.003169\times10^{-5}=1.157407\times10^{-5}\ \mathrm{s^{-1}},
$$

$$
\frac{1}{1.157407\times10^{-5}}=86\,400.0\ \mathrm s.
$$

$$
\boxed{\tau=\frac MN\times86\,400\ \mathrm s}
$$

This is the mean solar day: a Sun-synchronous plane keeps pace with the Sun, so relative to it the Earth turns once per solar day, not per sidereal day. The number of days and orbits are $M$ and $N$ here (also written $m$ and $n$).

With $\tau$ known, Kepler's third law gives $a$, and the regression condition gives $i$. Because $N$ and $M$ must be integers, only a discrete set of orbits is both Sun- and Earth-synchronous (see [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]).

![[ast_repeat_groundtrack_solutions.png|700]]

## Worked examples

Constants: $R_E=6378$ km, $\mu=398\,600\ \mathrm{km^3/s^2}$ and the regression constant $2.0647\times10^{14}$.

### Inclination for 700 to 900 km

| Altitude | $a$ (km) | Sun-synchronous $i$ |
|---|---|---|
| 700 km | 7078 | 98.19° |
| 800 km | 7178 | 98.60° |
| 900 km | 7278 | 99.03° |

So 700–900 km means $98^\circ$–$99^\circ$, as read off the chart.

### Sixteen orbits a day (2024/25 A6)

A Sun-synchronous orbit repeating after 16 orbits in 1 day has

$$
\tau=\frac{1}{16}\times86\,400=5400\ \mathrm s.
$$

Kepler's third law, inverted:

$$
a=\left[398\,600\left(\frac{5400}{2\pi}\right)^2\right]^{1/3}=\left[398\,600\times859.4^2\right]^{1/3}=\left(2.944\times10^{11}\right)^{1/3}=6652.6\ \mathrm{km},
$$

an altitude of $6652.6-6378=274.6$ km. For the inclination, $a^{-3.5}=6652.6^{-3.5}=4.164\times10^{-14}$, so

$$
\cos i=\frac{0.9856}{-2.0647\times10^{14}\times4.164\times10^{-14}}=\frac{0.9856}{-8.598}=-0.1146,
$$

$$
i=\cos^{-1}(-0.1146)=96.58^\circ.
$$

> [!check] Check against the curve
> At 274.6 km the Sun-synchronous curve gives just under $96.6^\circ$, and the inclination falls towards $96^\circ$ as the altitude falls, so the answer sits where it should. The orbit is too low for a long mission, since drag at 275 km would need near-continuous make-up.

### Fourteen orbits a day

For the example with $M=1$, $N=14$: $\tau=86\,400/14=6171.4$ s, $a=7271.9$ km, altitude 893.9 km, $a^{-3.5}=3.049\times10^{-14}$, $\cos i=-0.1565$ and $i=99.01^\circ$.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 11 - Payload and Orbit Selection]]
- Next: [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]
- Concepts: [[Sun-Synchronous Orbit]] · [[Nodal Regression (J2)]] · [[Repeat Ground Track]] · [[Local Solar Time and RAAN]]
- Precession of angular momentum: [[SESA2024 06 - Attitude Control]] · [[Momentum Bias and Gyroscopic Rigidity]]

## Sources

- `Chapter 11_Sun and Earth synchronous orbits_V1.pdf` (Dr C. Ryan, after Prof H. Lewis) with transcripts `SESA2024 Lecture 2025-12-09.txt` and `SESA2024 Lecture 2025-12-11.txt`, ll. 1–130
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 5 (perturbations and Sun-synchronous orbits)
- Figures: `generate_ast_ch12_sso_figures.py` (`ast_sso_inclination`, `ast_repeat_groundtrack_solutions`; regenerated in the shared style on 5 Nov 2026, with the $(98,7)=(14,1)$ point marked). Numbers recomputed in Python.

## Self-study tasks

### Core

- [ ] Explain, with the Earth–Sun geometry, why a Sun-synchronous plane must turn at 0.9856° per day (2025-12-09, ll. 76–230). → [[#1. Sun-synchronism]]
- [ ] Explain how the Earth's oblateness makes the node regress, and why the inclination must exceed 90° (ll. 245–525). → [[#2. Nodal regression from the Earth's oblateness]] · [[#Which inclination]]
- [ ] Derive $\tau=(M/N)\times86\,400$ s for a simultaneously Sun- and Earth-synchronous orbit (2025-12-11, ll. 26–125). → [[#4. Both at once]]
- [ ] 2024/25 A6: altitude and inclination for 16 orbits per day. Targets 274.6 km and 96.58°. → [[#Sixteen orbits a day (2024/25 A6)]] · [[SESA2024 2024-25 Exam Solutions#Section A|solution]]

### Further practice

- [ ] Watch the MIT bicycle-wheel precession video and the Sun- and Earth-synchronous orbit videos on Blackboard (2025-12-09, ll. 600–625).
- [ ] Find the Sun-synchronous inclination at 700, 800 and 900 km. → [[#Inclination for 700 to 900 km]]
- [ ] Check that $1/(1/T_{sid}-1/T_{yr})=86\,400$ s and explain why the solar day appears. → [[#4. Both at once]]

## Transcript and slide slips

> [!warning] Transcript slip (2025-12-09, l. 775)
> Where: [[#3. Earth-synchronism]].
>
> Southampton is put at "53 or something" degrees latitude. It is at about $50.9^\circ$ N.

> [!warning] Slide table difference
> Where: [[#Fourteen orbits a day]].
>
> The slide table lists 888.3 km and $98.98^\circ$ for $M=1$, $N=14$, against 893.9 km and $99.01^\circ$ here. The difference of about 6 km presumably comes from different constants or a $J_2$-corrected period in the table.
