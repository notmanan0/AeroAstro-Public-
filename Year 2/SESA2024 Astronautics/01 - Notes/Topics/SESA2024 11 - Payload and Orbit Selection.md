---
title: "SESA2024 11 - Payload and Orbit Selection"
module: "SESA2024 Astronautics"
type: topic
stream: "Remote Sensing Case Study"
order: 11
tags: [sesa2024, remote-sensing, orbit-selection, mission-analysis]
aliases: ["Orbit selection first pass", "Chapter 11 Lectures 1-3", "Remote sensing orbit selection"]
date: 2026-10-30
status: lectured
coverage: "Week 10 (2025-12-04)"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 03 - Orbital Elements and Conic Sections]]", "[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]"]
next_topics: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]"]
key_concepts: ["[[Swath Width and Push-Broom Imaging]]", "[[Keplerian Orbital Elements]]", "[[Sun-Synchronous Orbit]]", "[[Repeat Ground Track]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Orbit Selection First Pass_V1.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-12-04.txt"]
---

# SESA2024 11 - Payload and Orbit Selection

> [!abstract] Summary
> In an Earth-observation satellite the payload drives every choice, which makes it a clear case of mission analysis. A first pass for a push-broom imager of about 10 m resolution and a life of years gives a near-polar inclination for global coverage, a near-circular orbit for constant resolution, and an altitude of about 700–900 km as the trade between resolution and drag. The payload's operational needs then add two conditions, the same illumination on every pass and the same viewing geometry at regular intervals, which lead to Sun-synchronous and Earth-synchronous orbits.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for first-pass values of $i$, $e$ and $a$ for a remote-sensing mission, or why a mission needs Sun- or Earth-synchronism.
> - **Assumptions:** a nadir-pointing, visible-wavelength push-broom imager; a civil mission lasting years; drag the main constraint on low altitude.
> - **Method:** 1. Inclination: near-polar for global coverage. 2. Eccentricity: near zero for constant range and pixel size. 3. Altitude: 700–900 km ($a$ = 7078–7278 km), balancing resolution against drag make-up. 4. Illumination: sunlit target at a moderate Sun angle, invariant from pass to pass, so Sun-synchronous. 5. Geometry: the same view at regular intervals, so Earth-synchronous (repeat ground track).
> - **Common mistakes:** choosing 200 km "for resolution" without the drag penalty; choosing noon passes, which bring sun glint off water.
> - **Practise:** [[#3. The first pass for a 10 m imager]] · [[#4. A spy satellite with the same method]]

A scientist's objective, say counting trees to track climate change, leads to a payload with a ground resolution, a wavelength and a field of view. The payload's requirements lead to an orbit, and the orbit leads to a spacecraft concept, which is traded and iterated, sometimes all the way back to the objectives. Mission analysis sits between payload selection and spacecraft design, and much of what decides it is practical: a small budget limits the propulsion, which limits the ΔV, which limits the orbit.

The case study is civil remote sensing: environmental monitoring, climate, weather, forests and agriculture, cartography, ships, fires and volcanoes. Every element of the orbit in this case can be traced back to something the payload needs.

## 1. Orbits follow from objectives

Examples of objective leading to orbit:

| Objective | Orbit |
|---|---|
| Global environmental monitoring at high resolution | LEO, near-polar |
| Global communications through large fixed ground stations | GEO |
| Global communications to small mobile terminals | LEO constellation (Starlink) |
| Astronomical imaging | LEO, HEO or GEO, away from atmospheric and orbital disturbances |

There is rarely a single right answer; the choice is a trade.

## 2. The push-broom imager

The simplest remote-sensing instrument is the push-broom imager, a line of detectors (CCD elements) laid across the ground track. The spacecraft's motion sweeps the line along the track, recording one strip of the Earth per pixel of travel, like a broom pushed steadily forward without the back-and-forth of sweeping. Strips from successive orbits, displaced as the Earth turns, are joined into a map.

The strip has a width on the ground, the swath width $d$. For a nadir-pointing instrument with field of view $\beta$ at altitude $h$, the nadir line splits the field of view into two right-angled triangles, each with angle $\beta/2$ at the spacecraft, height $h$ and base $d/2$. The ground is treated as flat across the swath, which is reasonable while $d$ is a few hundred kilometres against an Earth radius of 6378 km.

![[ast_swath_geometry.png|640]]

In one triangle the side opposite $\beta/2$ is $d/2$ and the side adjacent is $h$:

$$
\tan\frac{\beta}{2}=\frac{d/2}{h}.
$$

Multiply both sides by $2h$:

$$
d=2h\tan\frac{\beta}{2}.
$$

For a fixed field of view the swath grows in proportion to altitude, and so does the ground size of one pixel, since each detector element sees a fixed small angle. The orbit therefore decides how much ground is sampled, how quickly, and at what resolution. The swath is used in [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]] to fix the repeat ground track.

## 3. The first pass for a 10 m imager

The requirements: view as much of the Earth as possible at about 10 m resolution, for a lifetime of years, since such satellites cost hundreds of millions. The six elements divide into three in-plane ones (size $a$, shape $e$, position $\theta$, the last irrelevant for coverage) and three that orient the orbit ($i$, $\Omega$, $\omega$).

Inclination: the options are about $0^\circ$, about $50^\circ$ or about $90^\circ$. The highest latitude a ground track reaches equals the inclination for $i\le90^\circ$, and $180^\circ-i$ for a retrograde orbit, because that is the greatest angle the orbit plane makes with the equator. A $50^\circ$ orbit therefore reaches $50^\circ$ N and S and sees only the southern edge of the UK (about $50$–$61^\circ$ N), and none of Sweden or Iceland; a nadir imager with a swath of a few hundred kilometres adds only a couple of degrees beyond that. For global coverage the inclination must be near-polar. A Sun-synchronous orbit at $98^\circ$ reaches $180^\circ-98^\circ=82^\circ$, so only small caps around the poles are missed.

Eccentricity: about 0, about 0.1 or about 0.4. A high eccentricity would let the spacecraft dwell over a region of interest, which is what Molniya orbits do. For global mapping, though, the instrument should be at the same range everywhere, so that a pixel in Canada and a pixel in Argentina cover the same ground area. That calls for a near-circular orbit.

> [!check] What the eccentricity options mean in low orbit
> At $a=7178$ km (800 km mean altitude), $r_p=a(1-e)$ and $r_a=a(1+e)$ give, after subtracting $R_E=6378$ km, apsis altitudes of 728 and 872 km for $e=0.01$, a range ratio of 1.2. For $e=0.1$ they are 82 km and 1518 km: perigee is deep in the atmosphere, and pixel size would vary eighteen-fold round the orbit. For $e=0.4$, $r_p$ is 2071 km below the surface. In low orbit only a near-zero eccentricity is even possible; the larger values belong to orbits with much larger $a$.

Altitude: 200 km, 700 km or 1200 km. At 200 km the resolution would be excellent, but drag would bring the satellite down quickly unless it thrusts continuously. At 1200 km drag is negligible (OneWeb flies near there), but the resolution suffers. A middle altitude gives decent images with drag that can be made up over a life of years:

$$
h=700\text{–}900\ \mathrm{km},
\qquad
a=R_E+h=7078\text{–}7278\ \mathrm{km}.
$$

Altitude also sets the period and so how soon the satellite returns over an event such as a hurricane, which is becoming a requirement in its own right.

The first-pass result, which is also the answer to the 3–4 mark past-paper question on first-pass values of $i$, $e$ and $a$ (2013/14, 2018/19, 2019/20):

| Element | Choice | Reason |
|---|---|---|
| $i$ | near-polar | global coverage |
| $e$ | near 0 | constant range, so constant pixel size |
| $a$ | 7078–7278 km (700–900 km altitude) | resolution against drag over a long life |

NASA's Aqua, launched in 2002 at about 705 km, is a real example. Even at that altitude it had to boost its orbit every few years against drag; its last boost was in 2021, it has since run out of propellant and is slowly descending, still working, towards re-entry.

## 4. A spy satellite with the same method

If the resolution requirement changes from 10 m to 0.1 m with everything else the same, global coverage still points to a high inclination. But 0.1 m resolution needs the spacecraft very close to the ground, and staying at 200 km for years is impossible because of drag. A highly eccentric orbit with a very low perigee over the target region and a high apogee resolves this: the spacecraft dives through the dense atmosphere quickly, takes its images, and coasts up and out, so it survives. The result is a large, eccentric orbit, almost the opposite of the civil one. A constant-resolution argument would favour a circular orbit for spy satellites too, but the resolution requirement outweighs it, so one changed requirement changes the orbit completely.

## 5. Illumination and viewing geometry

The orbital elements are not the only consideration; conditions on the ground matter too.

Illumination. A visible-wavelength imager needs the target in sunlight. The Sun angle matters as well. A low Sun throws long shadows. A Sun directly behind the spacecraft eliminates shadows but produces sun glint: in an image of South-East Asia, a glare off the sea stretches thousands of kilometres. A moderate Sun angle is the compromise.

Invariance. Remote sensing is about change: before-and-after images of a fire, a volcano or a forest. If the Sun angle drifts from day 1 to day 10 to day 20, the shadows change length and direction and the images cannot be compared. The useful images are the ones with the same moderate Sun angle every time. That requires the target to be imaged at the same local solar time on every pass, which is Sun-synchronism.

Viewing geometry. An oblique view shows building heights (artificial islands off Dubai, for example), a vertical view gives clean geometry. Either can be useful, but the same target should be seen with the same geometry at regular intervals so that images can be compared. That requires the ground track to repeat, which is Earth-synchronism.

The final first-pass requirements for a 10 m imager are therefore: near-polar, near-circular, 700–900 km; target in sunlight at a moderate Sun angle; invariant illumination; invariant, repeating viewing geometry. That describes a Sun- and Earth-synchronous orbit ([[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]).

## 6. What the payload asks of the rest of the spacecraft

The orbit choice also sets the attitude requirement. A past-paper question (2018/19 Q1(vii)) asks for three basic orbit requirements and one attitude requirement for such a mission: near-polar (Sun-synchronous, about $98^\circ$), circular, 700–900 km with a repeat ground track, and nadir pointing from a three-axis-stabilised platform with the required accuracy and stability. The general effect of the payload on the other subsystems is set out in [[SESA2024 01 - Systems Engineering and Spacecraft Design#7. How the payload drives the design|note 01 §7]].

## Worked example

### Swath width and altitude range

*(Suggested, not lecturer-set; the instrument is the one in [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]].)* An imager with a $28.96^\circ$ field of view has $\beta/2=14.48^\circ$ and $\tan14.48^\circ=0.2582$, so $d=2\times0.2582\,h=0.5165\,h$. At the ends and middle of the first-pass range:

$$
h=700\ \mathrm{km}\Rightarrow d=362\ \mathrm{km},
\qquad
h=800\ \mathrm{km}\Rightarrow d=413\ \mathrm{km},
\qquad
h=900\ \mathrm{km}\Rightarrow d=465\ \mathrm{km}.
$$

The periods follow from Kepler's third law with $R_E=6378$ km. At 800 km, $a=7178$ km and

$$
\tau=2\pi\sqrt{\frac{7178^3}{398\,600}}=2\pi\sqrt{9.278\times10^5}=2\pi\times963.2=6052\ \mathrm s.
$$

The same calculation at 700 and 900 km gives 5926 s and 6179 s, the 6050 ± 120 s used in [[SESA2024 12 - Sun- and Earth-Synchronous Orbits]] and [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]].

> [!check] Ground covered per orbit
> At 800 km the swath of 413 km is 1.0 % of the equator's 40 075 km circumference per pass, and the satellite makes $86\,400/6052=14.3$ orbits a day. Counting both the ascending and descending passes (a visible-light imager can use only the sunlit ones, which halves this), one day covers $2\times14.3\times413=11\,800$ km, about 29 % of the equator, which is why the ground track has to be planned to fill the gaps over several days (the repeat-ground-track problem of [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission|note 13]]).

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]
- Next: [[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]
- Concepts: [[Swath Width and Push-Broom Imaging]] · [[Keplerian Orbital Elements]] · [[Sun-Synchronous Orbit]] · [[Repeat Ground Track]]
- Payload impact: [[SESA2024 01 - Systems Engineering and Spacecraft Design]]
- Commercial trade-offs between spatial, spectral and temporal resolution: [[SESA2024 15 - Space Sustainability, Debris and NewSpace]]

## Sources

- `Chapter 11_Orbit Selection First Pass_V1.pdf` (Dr C. Ryan, after Prof H. Lewis) with transcript `SESA2024 Lecture 2025-12-04.txt`
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 5 (mission analysis)
- Figures: `generate_ast_ch11_payload_figures.py` (`ast_swath_geometry`). Numbers recomputed in Python.

## Self-study tasks

### Core

- [ ] First-pass values of $i$, $e$ and $a$ for a remote-sensing mission, with a reason for each (worked with the class, 2025-12-04, ll. 260–400; 2013/14, 2018/19, 2019/20). → [[#3. The first pass for a 10 m imager]]
- [ ] Repeat the first pass for a 0.1 m spy satellite (ll. 401–475). → [[#4. A spy satellite with the same method]]
- [ ] Explain why change detection needs Sun-synchronism and Earth-synchronism (class discussion, ll. 551–625). → [[#5. Illumination and viewing geometry]]

### Further practice

- [ ] Three orbit requirements and one attitude requirement for a remote-sensing imager (2018/19 Q1(vii)). → [[#6. What the payload asks of the rest of the spacecraft]]
- [ ] Advantage of push-broom over whisk-broom imaging (2017/18 Q1(vii)). → [[#2. The push-broom imager]] · [[SESA2024 06 - Attitude Control#Type 1: spinner|whisk-broom on a spinner]]
- [ ] Swath width and period at 700, 800 and 900 km for a 28.96° field of view. → [[#Swath width and altitude range]]

## Transcript and slide slips

> [!warning] Transcript slip (2025-12-04, ll. 345–355)
> Where: [[#3. The first pass for a 10 m imager]].
>
> ESA's GOCE gravity mission is described as flying at 200 km until its ion thruster "failed" and it fell out of the sky. GOCE flew at about 255 km (later lowered to about 224 km), and it re-entered in 2013 after its xenon propellant ran out, not because the thruster failed.
