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

[[SESA2024 11 - Payload and Orbit Selection|The first pass]] ended with two operational requirements: the same illumination on every pass, and the same viewing geometry at regular intervals. This note turns each into a condition on the orbital elements, and then shows that both can be met at once.

The physical picture for the first is a hoop around a ball, and a student holding an inflatable Sun (2025-12-09, ll. 101–175). Carried round the Sun over a year, an unperturbed orbit plane keeps its orientation fixed in space, so at the summer solstice the Sun might be off to one side of the plane and at the equinox square on to it. The Sun angle at the ground track drifts through the year. For constant illumination the plane must instead turn with the Earth's motion round the Sun, completing one turn a year. Something has to supply the torque, and remarkably the Earth's own shape does.

## 1. Sun-synchronism

A spacecraft in a Sun-synchronous orbit arrives over a given location at the same local solar time on each pass, so the Sun stands at the same height and direction whenever a target is imaged (2025-12-09, ll. 26–75). Seasonal changes in the Sun's elevation still occur; Sun-synchronism removes the drift due to the orbit.

The condition is that the angle $\phi$ between the Earth–Sun line and the orbit plane stays constant (ll. 76–200). In terms of the right ascension of the Sun $\alpha_S$ and the RAAN $\Omega$,

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

"a little bit under one degree per day" (ll. 201–230).

## 2. Nodal regression from the Earth's oblateness

Turning the orbit plane with thrusters would be very expensive, since plane changes cost a great deal of ΔV (ll. 226–245). The alternative is a natural perturbation.

The Earth is not a sphere (ll. 245–300). Its rotation over billions of years has made it slightly oblate: the equatorial radius is about 6378 km and the polar radius about 6357 km, a difference of about 21 km. A perfectly spherical Earth pulls an orbiting spacecraft straight towards its centre. The bulge adds a tiny pull towards the equatorial plane whenever the spacecraft is above or below it, which has a small component normal to the orbit and so produces a torque on the orbit (ll. 300–375).

The orbit, however, carries angular momentum $\mathbf h$, like a spinning bicycle wheel. A torque applied to it does not tip the plane over; it makes $\mathbf h$ precess, exactly as the wheel did in the attitude-control demonstrations ([[SESA2024 06 - Attitude Control#3. Gyroscopic precession and momentum bias|note 06 §3]]). The node, where the orbit crosses the equator, therefore moves a little on each orbit: nodal regression (ll. 376–425).

The rate for a circular orbit, quoted on the slides without derivation ("a really complicated analysis", ll. 426–450), is

$$
\dot\Omega=-\frac32J_2\sqrt{\mu}\,R_E^2\,a^{-7/2}\cos i,
$$

with $J_2=1.0826\times10^{-3}$. Converting radians per second to degrees per day, with $a$ in km and $\mu=398\,600.4\ \mathrm{km^3/s^2}$, $R_E=6378.1$ km:

$$
\frac32\times1.0826\times10^{-3}\times6378.1^2\times\sqrt{398\,600.4}\times86\,400\times\frac{180}{\pi}=2.0647\times10^{14},
$$

so

$$
\boxed{\dot\Omega=-2.0647\times10^{14}\,a^{-7/2}\cos i\quad(\text{deg/day},\ a\text{ in km})}
$$

The constant only works with $a$ in kilometres (2020 Lecture 9, ll. 181–200).

### Which inclination

The sign of $\dot\Omega$ is set by $\cos i$ (2025-12-09, ll. 451–525):

- $0\le i<90^\circ$: $\cos i>0$, $\dot\Omega<0$, the node moves west, the wrong way;
- $i=90^\circ$: $\cos i=0$, no regression; a polar orbit feels no net torque from the bulge;
- $90^\circ<i\le180^\circ$: $\cos i<0$, $\dot\Omega>0$, the node moves east, as required.

So a Sun-synchronous orbit is retrograde, tipped a little past the pole. Setting $\dot\Omega=0.9856$ and solving,

$$
\cos i=\frac{0.9856}{-2.0647\times10^{14}\,a^{-7/2}}.
$$

For altitudes of 200–1000 km this gives $96^\circ$ to $99.5^\circ$, and for the first-pass 700–900 km about $98^\circ$ to $99^\circ$ (ll. 526–600). That inclination still covers almost the whole globe, which Dr Ryan called "a beautiful natural trick" (l. 598).

![[ast_sso_inclination.png|700]]

## 3. Earth-synchronism

An Earth-synchronous orbit's ground track repeats precisely after a certain number of orbits $N$ in a certain number of days $M$ (ll. 626–700). Once the track repeats, the spacecraft returns over any target, a fire in California or a single ground station, with the same geometry every $M$ days. Dr Ryan's analogy is the old game Snake: the track grows longer orbit by orbit until the snake eats its own tail (2025-12-09, ll. 776–800).

Define the longitude displacement $\Delta\lambda$ between successive equator crossings. The condition is that $N$ displacements add up to exactly $M$ full turns:

$$
N\,\Delta\lambda=M\times360^\circ.
$$

The slides' examples (ll. 726–826): a track at $63^\circ$ inclination repeating after 77 orbits in 5 days, and one at about $70^\circ$ repeating after 15 orbits in 1 day, both Earth-synchronous but not Sun-synchronous; and one at $96^\circ$ repeating after 14 orbits in 1 day, which is both.

> [!warning] Transcript slip (2025-12-09, l. 775)
> Southampton is put at "53 or something" degrees latitude. It is at about $50.9^\circ$ N.

## 4. Both at once

The displacement per orbit has two parts (2025-12-09, ll. 826–855; 2025-12-11, ll. 26–125). The Earth rotates eastwards under the orbit, which shifts the track westwards by

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
\frac{1}{1/86\,164.1-1/31\,557\,600}=86\,400.0\ \mathrm s.
$$

$$
\boxed{\tau=\frac MN\times86\,400\ \mathrm s}
$$

This is just the mean solar day, and it makes sense: a Sun-synchronous plane keeps pace with the Sun, so relative to it the Earth turns once per solar day, not per sidereal day. "Does anyone know what 86,400 seconds is? ... A day" (2025-12-11, ll. 120–126). The slides remember the symbols as $m$ for days and $n$ for orbits.

With $\tau$ known, Kepler's third law gives $a$, and the regression condition gives $i$. Because $N$ and $M$ must be integers, only a discrete set of orbits is both Sun- and Earth-synchronous, as the next note shows.

![[ast_repeat_groundtrack_solutions.png|700]]

## Worked examples

All values recomputed in Python with $R_E=6378$ km, $\mu=398\,600\ \mathrm{km^3/s^2}$ and the regression constant $2.0647\times10^{14}$.

### Inclination for 700 to 900 km

| Altitude | $a$ (km) | Sun-synchronous $i$ |
|---|---|---|
| 700 km | 7078 | 98.19° |
| 800 km | 7178 | 98.60° |
| 900 km | 7278 | 99.03° |

So 700–900 km means $98^\circ$–$99^\circ$, as read off the chart in the lecture (2025-12-09, ll. 526–600).

### Sixteen orbits a day (2024/25 A6)

A Sun-synchronous orbit repeating after 16 orbits in 1 day has

$$
\tau=\frac{1}{16}\times86\,400=5400\ \mathrm s,
\qquad
a=\left[398\,600\left(\frac{5400}{2\pi}\right)^2\right]^{1/3}=6652.6\ \mathrm{km},
$$

an altitude of 274.6 km, and

$$
\cos i=\frac{0.9856}{-2.0647\times10^{14}\times6652.6^{-3.5}}
\quad\Longrightarrow\quad
i=96.58^\circ.
$$

### Fourteen orbits a day

The slide example with $M=1$, $N=14$ (2025-12-11, ll. 401–420): $\tau=6171.4$ s, $a=7271.9$ km, altitude 893.9 km, $i=99.01^\circ$. The slide table lists 888.3 km and $98.98^\circ$; the difference of about 6 km presumably comes from different constants or a $J_2$-corrected period in the table, and is not explained in the lecture.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 11 - Payload and Orbit Selection]]
- Next: [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]
- Concepts: [[Sun-Synchronous Orbit]] · [[Nodal Regression (J2)]] · [[Repeat Ground Track]] · [[Local Solar Time and RAAN]]
- Precession of angular momentum: [[SESA2024 06 - Attitude Control]] · [[Momentum Bias and Gyroscopic Rigidity]]

## Sources

- `Chapter 11_Sun and Earth synchronous orbits_V1.pdf` (Dr C. Ryan, after Prof H. Lewis) with transcripts `SESA2024 Lecture 2025-12-09.txt` and `SESA2024 Lecture 2025-12-11.txt`, ll. 1–130
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 5 (perturbations and Sun-synchronous orbits)

## Self-study tasks

### Core

- [ ] Explain, with the Earth–Sun geometry, why a Sun-synchronous plane must turn at 0.9856° per day (2025-12-09, ll. 76–230). → [[#1. Sun-synchronism]]
- [ ] Explain how the Earth's oblateness makes the node regress, and why the inclination must exceed 90° (ll. 245–525). → [[#2. Nodal regression from the Earth's oblateness]] · [[#Which inclination]]
- [ ] Derive $\tau=(M/N)\times86\,400$ s for a simultaneously Sun- and Earth-synchronous orbit (2025-12-11, ll. 26–125). → [[#4. Both at once]]
- [ ] 2024/25 A6: altitude and inclination for 16 orbits per day. Targets 274.6 km and 96.59°. → [[#Sixteen orbits a day (2024/25 A6)]] · [[SESA2024 2024-25 Exam Solutions#Section A|solution]]

### Further practice

- [ ] Watch the MIT bicycle-wheel precession video and the Sun- and Earth-synchronous orbit videos on Blackboard (2025-12-09, ll. 600–625).
- [ ] Find the Sun-synchronous inclination at 700, 800 and 900 km. → [[#Inclination for 700 to 900 km]]
- [ ] Check that $1/(1/T_{sid}-1/T_{yr})=86\,400$ s and explain why the solar day appears. → [[#4. Both at once]]
