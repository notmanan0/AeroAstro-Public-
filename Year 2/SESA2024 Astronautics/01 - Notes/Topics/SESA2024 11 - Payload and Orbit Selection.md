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
> Chapter 11 applies the module to one case: an Earth-observation satellite whose payload drives every choice. A first pass for a push-broom imager of about 10 m resolution and a life of years gives a near-polar inclination for global coverage, a near-circular orbit for constant resolution, and an altitude of about 700–900 km as the trade between resolution and drag. The payload's operational needs then add two conditions, the same illumination on every pass and the same viewing geometry at regular intervals, which lead to Sun-synchronous and Earth-synchronous orbits.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for first-pass values of $i$, $e$ and $a$ for a remote-sensing mission, or why a mission needs Sun- or Earth-synchronism.
> - **Assumptions:** a nadir-pointing, visible-wavelength push-broom imager; a civil mission lasting years; drag the main constraint on low altitude.
> - **Method:** 1. Inclination: near-polar for global coverage. 2. Eccentricity: near zero for constant range and pixel size. 3. Altitude: 700–900 km ($a$ = 7078–7278 km), balancing resolution against drag make-up. 4. Illumination: sunlit target at a moderate Sun angle, invariant from pass to pass, so Sun-synchronous. 5. Geometry: the same view at regular intervals, so Earth-synchronous (repeat ground track).
> - **Common mistakes:** choosing 200 km "for resolution" without the drag penalty; choosing noon passes, which bring sun glint off water.
> - **Practise:** [[#3. The first pass for a 10 m imager]] · [[#4. A spy satellite with the same method]]

Dr Ryan put mission analysis back in its place in the design process at the start of this block (2025-12-04, ll. 26–150). A scientist's objective, say counting trees to track climate change, leads to a payload with a ground resolution, a wavelength and a field of view. The payload's requirements lead to an orbit, and the orbit leads to a spacecraft concept, which is traded and iterated, sometimes all the way back to the objectives. Mission analysis sits between payload selection and spacecraft design, and much of what decides it is practical: a small budget limits the propulsion, which limits the ΔV, which limits the orbit.

The case study is civil remote sensing: environmental monitoring, climate, weather, forests and agriculture, cartography, ships, fires and volcanoes (ll. 151–175). It is a good teaching case because every element of the orbit can be traced back to something the payload needs.

## 1. Orbits follow from objectives

The slides give a few examples of objective leading to orbit (ll. 76–125):

| Objective | Orbit |
|---|---|
| Global environmental monitoring at high resolution | LEO, near-polar |
| Global communications through large fixed ground stations | GEO |
| Global communications to small mobile terminals | LEO constellation (Starlink) |
| Astronomical imaging | LEO, HEO or GEO, away from atmospheric and orbital disturbances |

There is rarely a single right answer; the choice is a trade.

## 2. The push-broom imager

The lecture used the simplest remote-sensing instrument (ll. 151–200). A push-broom imager is a line of detectors (CCD elements) laid across the ground track. The spacecraft's motion sweeps the line along the track, recording one strip of the Earth per pixel of travel, like a broom pushed steadily forward without the back-and-forth of sweeping. Strips from successive orbits, displaced as the Earth turns, are joined into a map.

The strip has a width on the ground, the swath width $d$. For a nadir-pointing instrument with field of view $\beta$ at altitude $h$, two right-angled triangles give

$$
\tan\frac{\beta}{2}=\frac{d/2}{h}
\quad\Longrightarrow\quad
d=2h\tan\frac{\beta}{2}.
$$

The orbit therefore decides how much ground is sampled and how quickly. The swath is used in [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]] to fix the repeat ground track.

## 3. The first pass for a 10 m imager

The requirements: view as much of the Earth as possible at about 10 m resolution, for a lifetime of years, since such satellites cost hundreds of millions (ll. 226–260). The six elements divide into three in-plane ones (size $a$, shape $e$, position $\theta$, the last irrelevant for coverage) and three that orient the orbit ($i$, $\Omega$, $\omega$).

Inclination: the options on the slide are about $0^\circ$, about $50^\circ$, or about $90^\circ$ (ll. 260–285). The ground track only reaches latitudes up to the inclination, so a $50^\circ$ orbit would see the UK (about $51^\circ$ N) but not Sweden or Iceland. For global coverage the inclination must be near-polar.

Eccentricity: about 0, about 0.1 or about 0.4 (ll. 285–325). A student suggested a high eccentricity to dwell over a region of interest, which is what Molniya orbits do. For global mapping, though, the instrument should be at the same range everywhere, so that a pixel in Canada and a pixel in Argentina cover the same ground area. That calls for a near-circular orbit.

Altitude: 200 km, 700 km or 1200 km (ll. 326–400). At 200 km the resolution would be excellent, but drag would bring the satellite down quickly unless it thrusts continuously. At 1200 km drag is negligible (OneWeb flies near there), but the resolution suffers. A middle altitude gives decent images with drag that can be made up over a life of years:

$$
h=700\text{–}900\ \mathrm{km},
\qquad
a=R_E+h=7078\text{–}7278\ \mathrm{km}.
$$

A student also pointed out that altitude sets the period and so how soon the satellite returns over an event such as a hurricane, which is becoming a requirement in its own right (ll. 376–390).

> [!warning] Transcript slip (2025-12-04, ll. 345–355)
> ESA's GOCE gravity mission is described as flying at 200 km until its ion thruster "failed" and it fell out of the sky. GOCE flew at about 255 km (later lowered to about 224 km), and it re-entered in 2013 after its xenon propellant ran out, not because the thruster failed.

The first-pass result, which is also the answer to the 3–4 mark past-paper question on first-pass values of $i$, $e$ and $a$ (2013/14, 2018/19, 2019/20):

| Element | Choice | Reason |
|---|---|---|
| $i$ | near-polar | global coverage |
| $e$ | near 0 | constant range, so constant pixel size |
| $a$ | 7078–7278 km (700–900 km altitude) | resolution against drag over a long life |

NASA's Aqua, launched in 2002 at about 705 km, is a real example (ll. 476–505). Even at that altitude it had to boost its orbit every few years against drag; its last boost was in 2021, it has since run out of propellant and is slowly descending, still working, towards re-entry.

## 4. A spy satellite with the same method

Change one requirement: the resolution goes from 10 m to 0.1 m, everything else the same (ll. 401–475). Global coverage still points to a high inclination. But 0.1 m resolution needs the spacecraft very close to the ground, and staying at 200 km for years is impossible because of drag. The answer is a highly eccentric orbit with a very low perigee over the target region and a high apogee: the spacecraft dives through the dense atmosphere quickly, takes its images, and coasts up and out, so it survives. The result is a large, eccentric orbit, almost the opposite of the civil one. Dr Ryan conceded that a constant-resolution argument could be made for spy satellites too; the point is that one changed requirement changes the orbit completely.

## 5. Illumination and viewing geometry

Orbital elements are not the whole story; conditions on the ground matter too (ll. 505–650).

Illumination. A visible-wavelength imager needs the target in sunlight. The Sun angle matters as well. A low Sun throws long shadows. A Sun directly behind the spacecraft eliminates shadows but produces sun glint: the slide's image of South-East Asia shows a glare off the sea stretching thousands of kilometres. A moderate Sun angle is the compromise.

Invariance. Remote sensing is about change: before-and-after images of a fire, a volcano or a forest. If the Sun angle drifts from day 1 to day 10 to day 20, the shadows change length and direction and the images cannot be compared. The class chose the row of images with the same moderate Sun angle every time. That requires the target to be imaged at the same local solar time on every pass, which is Sun-synchronism.

Viewing geometry. An oblique view shows building heights (the lecture's example was artificial islands off Dubai), a vertical view gives clean geometry. Either can be useful, but the same target should be seen with the same geometry at regular intervals so that images can be compared. That requires the ground track to repeat, which is Earth-synchronism.

The final first-pass requirements for a 10 m imager are therefore: near-polar, near-circular, 700–900 km; target in sunlight at a moderate Sun angle; invariant illumination; invariant, repeating viewing geometry. In other words, a Sun- and Earth-synchronous orbit, the subject of [[SESA2024 12 - Sun- and Earth-Synchronous Orbits|the next note]].

## 6. What the payload asks of the rest of the spacecraft

The orbit choice also sets the attitude requirement. A past-paper question (2018/19 Q1(vii)) asks for three basic orbit requirements and one attitude requirement for such a mission: near-polar (Sun-synchronous, about $98^\circ$), circular, 700–900 km with a repeat ground track, and nadir pointing from a three-axis-stabilised platform with the required accuracy and stability. How the payload drives the other subsystems in general is the Chapter 4 material in [[SESA2024 01 - Systems Engineering and Spacecraft Design#7. How the payload drives the design (Chapter 4)|note 01 §7]].

## Worked example

### Swath width and altitude range

*(Suggested, not lecturer-set; it uses the instrument of the Chapter 11 worked example.)* An imager with a $28.96^\circ$ field of view at the ends and middle of the first-pass range:

$$
d=2h\tan14.48^\circ:\qquad
h=700\ \mathrm{km}\Rightarrow d=362\ \mathrm{km},
\quad
h=800\ \mathrm{km}\Rightarrow d=413\ \mathrm{km},
\quad
h=900\ \mathrm{km}\Rightarrow d=465\ \mathrm{km}.
$$

The corresponding periods, from Kepler's third law with $R_E=6378$ km, are 5926 s, 6052 s and 6179 s, the "6050 ± 120 s" used in the next two notes.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]] (previous lecture)
- Next: [[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]
- Concepts: [[Swath Width and Push-Broom Imaging]] · [[Keplerian Orbital Elements]] · [[Sun-Synchronous Orbit]] · [[Repeat Ground Track]]
- Payload impact: [[SESA2024 01 - Systems Engineering and Spacecraft Design]]
- Commercial trade-offs between spatial, spectral and temporal resolution: [[SESA2024 15 - Space Sustainability, Debris and NewSpace]]

## Sources

- `Chapter 11_Orbit Selection First Pass_V1.pdf` (Dr C. Ryan, after Prof H. Lewis) with transcript `SESA2024 Lecture 2025-12-04.txt`
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 5 (mission analysis)

## Self-study tasks

### Core

- [ ] First-pass values of $i$, $e$ and $a$ for a remote-sensing mission, with a reason for each (worked with the class, 2025-12-04, ll. 260–400; 2013/14, 2018/19, 2019/20). → [[#3. The first pass for a 10 m imager]]
- [ ] Repeat the first pass for a 0.1 m spy satellite (ll. 401–475). → [[#4. A spy satellite with the same method]]
- [ ] Explain why change detection needs Sun-synchronism and Earth-synchronism (class discussion, ll. 551–625). → [[#5. Illumination and viewing geometry]]

### Further practice

- [ ] Three orbit requirements and one attitude requirement for a remote-sensing imager (2018/19 Q1(vii)). → [[#6. What the payload asks of the rest of the spacecraft]]
- [ ] Advantage of push-broom over whisk-broom imaging (2017/18 Q1(vii)). → [[#2. The push-broom imager]] · [[SESA2024 06 - Attitude Control#Type 1: spinner|whisk-broom on a spinner]]
- [ ] Swath width and period at 700, 800 and 900 km for a 28.96° field of view. → [[#Swath width and altitude range]]
