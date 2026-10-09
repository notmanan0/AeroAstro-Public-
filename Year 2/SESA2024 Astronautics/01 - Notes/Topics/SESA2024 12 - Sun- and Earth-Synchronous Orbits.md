---
title: "SESA2024 12 - Sun- and Earth-Synchronous Orbits"
module: "SESA2024 Astronautics"
type: topic
stream: "Remote Sensing Case Study"
order: 12
tags:
  - sesa2024
  - remote-sensing
  - sun-synchronous
  - repeat-ground-track
  - j2
aliases: ["SSO", "Earth-synchronous", "Repeat ground track", "Nodal regression"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 11 - Payload and Orbit Selection]]"]
next_topics: ["[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]"]
key_concepts: ["[[Sun-Synchronous Orbit]]", "[[Nodal Regression (J2)]]", "[[Repeat Ground Track]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Sun and Earth synchronous orbits_V1.pdf", "02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_ground track visualisation.pdf"]
---

# SESA2024 12 - Sun- and Earth-Synchronous Orbits

> [!abstract] Summary
> - **Sun-synchronous**: the orbit plane keeps a fixed angle $\phi = \alpha_S-\Omega$ to the Sun, so the node must precess **East at 0.986°/day** (360°/365.25 d). Propulsion cannot afford this, but **Earth oblateness ($J_2$)** can: $\dot\Omega = -2.0647\times10^{14}a^{-3.5}\cos i$ °/day. A positive $\dot\Omega$ needs $\cos i<0$, so **$i\approx98$–99° at 700–900 km**.
> - **Earth-synchronous** (repeat ground track): after $n$ orbits in $m$ days the track has shifted exactly $m\times360^\circ$.
> - Combining the Earth's rotation beneath the orbit with Sun-synchronous nodal drift gives the design condition
> $$\boxed{\tau = \frac{m}{n}\,86\,400\ \text{s}}$$
> i.e. $m$ **solar** days for $n$ orbits.

## Key Concepts
- [[Sun-Synchronous Orbit]] · [[Nodal Regression (J2)]] · [[Repeat Ground Track]]

---

## 1. What is Sun-synchronism?
- The spacecraft arrives over a location at the **same local solar time (LST)** on each pass. The Sun is in the same place in the sky, so shadow lengths and directions are unchanged (apart from seasonal variation).
- Geometrically, the angle between the orbit plane and the Earth–Sun vector is constant:

$$
\phi = \alpha_S-\Omega = \text{constant}
$$

  where $\alpha_S$ is the **right ascension of the Sun**.
- Differentiating: $\dot\phi = \dot\alpha_S-\dot\Omega = 0$, so

$$
\dot\Omega = \dot\alpha_S = \frac{360^\circ}{365.25\ \text{days}}\approx\mathbf{0.986^\circ/\text{day, eastward}}
$$

  The plane rotates once a year in inertial space.

## 2. How: Earth oblateness
Option 1, propulsive rotation of the plane, is **not feasible**: the fuel mass would be excessive.

Option 2 uses a natural perturbation.
- The Earth is an **oblate spheroid**: its equatorial radius exceeds its polar radius by about 21 km, out of 6378 km.
- The equatorial bulge means gravity does **not point at the Earth's centre**. Its tangential components produce a **torque on the orbit**.
- Like a bicycle wheel or gyroscope (Ch 6), the torque **precesses the orbital angular momentum vector**. The net effect is that the **node regresses** along the equator.

Nodal regression for a circular orbit ($a$ in km, positive East, inertial frame):

$$
\dot\Omega = -2.0647\times10^{14}\,a^{-3.5}\cos i\quad(^\circ/\text{day})
$$

This is the $J_2$ result $\dot\Omega = -\tfrac32J_2(R_E/a)^2\sqrt{\mu/a^3}\cos i$ with numbers inserted. It checks to 0.003 %. See [[Nodal Regression (J2)]].

| Inclination | Node motion |
|---|---|
| $0^\circ<i<90^\circ$ (prograde) | moves **West** |
| $i = 90^\circ$ | stationary |
| $i>90^\circ$ (retrograde) | moves **East** ✔ |

**Sun-synchronous condition**:

$$
-2.0647\times10^{14}a^{-3.5}\cos i = +0.986\ \Rightarrow\ \boxed{i = \cos^{-1}\left(\frac{0.986}{-2.0647\times10^{14}a^{-3.5}}\right)}
$$

At 700 / 800 / 900 km, $i$ = 98.19° / 98.61° / 99.04°.

![[ast_sso_inclination.png|600]]

> [!warning] Units
> - Keep 0.986 in **degrees per day**; do *not* convert it to radians.
> - $a$ is in **km**.
> - Your calculator's $\cos^{-1}$ may return radians. The lecture flags this explicitly.

(The same logic applies at other planets with their own constants: Mars in 2021/22 B3 and Jupiter in 2023/24 B3.)

## 3. What is Earth-synchronism?
- The ground track **repeats exactly with respect to geography** after an integer number of orbits $n$ and days $m$. Target revisit frequency can then be specified and controlled.
- Requirement: $n\,\Delta\lambda = m\times360^\circ$, where $\Delta\lambda$ is the westward shift of the track per orbit.
- Examples: $(m:n) = (1:15)$ repeats daily; $(1:14)$ can be both Sun- and Earth-synchronous.

## 4. Deriving $\tau = (m/n)86\,400$ s
The track shift per orbit has two parts ($\tau$ = nodal period, taken equal to the orbit period):

1. **Earth rotation** beneath the plane moves the track **West**:
$$
\Delta\lambda_{ROT} = 360^\circ\frac{\tau}{\tau_E},\qquad \tau_E = 86\,164\ \text{s (sidereal day)}
$$
2. **Nodal regression** (Sun-synchronous) moves it **East**. $360^\circ\,\tau_E/\tau_Y$ per day becomes, per orbit,
$$
\Delta\lambda_{REG} = 360^\circ\frac{\tau}{\tau_Y},\qquad \tau_Y = 3.155815\times10^7\ \text{s}
$$

Net westward shift: $\Delta\lambda = 360^\circ\left(\dfrac{\tau}{\tau_E}-\dfrac{\tau}{\tau_Y}\right)$. Setting $n\Delta\lambda = m\cdot360^\circ$:

$$
n\tau\left(1-\frac{\tau_E}{\tau_Y}\right) = m\tau_E\ \Rightarrow\ \tau = \frac{m}{n}\cdot\frac{86\,164}{1-86\,164/3.155815\times10^7} = \frac{m}{n}\,86\,400\ \text{s}
$$

> [!tip] Why 86 400 and not 86 164?
> A Sun-synchronous plane rotates with the Sun. Relative to the plane, the Earth therefore turns once per **solar** day (86 400 s), not once per sidereal day. (For Mars, 2021/22 B3(i) asks you to derive the analogue, 88 509.62 s. For Jupiter, 2023/24 B3 gives 35 733 s.)

## 5. Ground track
![[ast_sso_ground_track.png|760]]

- Per orbit the track shifts West by $\Delta\lambda = 360^\circ(\tau/\tau_E-\tau/\tau_Y)$. For (98,7), $\tau$ = 6171 s, so **25.7°**.
- Maximum latitude reached is $180^\circ-i$ for retrograde orbits; 81° at $i$ = 99°.
- **Sketching a ground track (exam)**:
  - mark the ascending and descending nodes 180° apart in longitude, minus the half-orbit westward shift;
  - peak latitude ±$(180^\circ-i)$;
  - a sinusoid-like curve, shifted West for successive orbits;
  - mark **eclipse entry and exit**: in an SSO, the nightside half is centred on the node at the midnight LST.
  - (Asked in 2020/21 Q2(iv), 2021/22 B1(v), 2022/23 B3(iii) and 2023/24 B1(vi).)

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 11 - Payload and Orbit Selection]] · Next: [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]
- Precession analogy: [[SESA2024 06 - Attitude Control]]

## Sources
- Chapter 11 "Sun- and Earth-synchronous orbits" and "ground track visualisation" (C. Ryan, after H. Lewis)
