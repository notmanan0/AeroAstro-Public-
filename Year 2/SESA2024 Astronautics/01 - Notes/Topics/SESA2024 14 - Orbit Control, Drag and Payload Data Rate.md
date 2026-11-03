---
title: "SESA2024 14 - Orbit Control, Drag and Payload Data Rate"
module: "SESA2024 Astronautics"
type: topic
stream: "Remote Sensing Case Study"
order: 14
tags: [sesa2024, remote-sensing, drag, orbit-control, data-rate]
aliases: ["Orbit control cycle", "Drag make-up", "Payload data rate", "Chapter 11B"]
date: 2026-10-30
status: lectured
coverage: "Not lectured in 2025-26: the 2025-12-11 lecture stopped after the orbital elements. This note follows the workbook's Chapter 11B solutions and the equations quoted in the 2015/16 and 2017/18 papers."
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]", "[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]", "[[SESA2024 07 - Spacecraft Propulsion]]"]
next_topics: ["[[SESA2024 15 - Space Sustainability, Debris and NewSpace]]"]
key_concepts: ["[[Orbit Control Cycle]]", "[[Payload Data Rate]]", "[[Swath Width and Push-Broom Imaging]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]]"]
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf", "03 - Exams & Past Papers/SESA2024-201516-01-SESA2024W1.pdf", "03 - Exams & Past Papers/SESA2024-201718-01-SESA2024W1.pdf"]
---

# SESA2024 14 - Orbit Control, Drag and Payload Data Rate

> [!abstract] Summary
> Atmospheric drag shrinks a low orbit by $\delta a=-2\pi\rho(SC_D/m)a^2$ per orbit and shortens its period, so a repeat ground track drifts out of its tolerance band. The fix is a cycle: boost slightly above the nominal orbit, let drag carry the orbit down through it while the track error traces a parabola across the band, and boost again with a small Hohmann transfer; the cycle lasts $2k$ orbits with $k=\sqrt{2\Delta t_0/|\delta\tau|}$. The remote-sensing case ends with the payload data rate, pixels times bits times bands per line, divided by the time the ground track takes to advance one pixel.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for drag decay, the orbit-control cycle, the ΔV and propellant for drag make-up, or the data rate of a push-broom imager.
> - **Assumptions:** circular orbit; constant density over a cycle (design with the high-solar-activity value); small decay per orbit; Hohmann boosts; nadir push-broom imager.
> - **Method:** 1. $\delta a=-2\pi\rho(SC_D/m)a^2$, $\delta\tau=3\pi\delta a/V$. 2. Tolerance $\pm E_0$: $\delta\lambda=2E_0/R_E$, $\Delta t_0=\delta\lambda/\omega_E$. 3. $k=\sqrt{2\Delta t_0/|\delta\tau|}$, cycle $2k$ orbits, height lost $2k|\delta a|$. 4. $\Delta V_{cycle}\approx V\Delta a/2a$; total over the life; propellant from the rocket equation. 5. Data: $V_{gd}=VR_E/a$, $t_s=p/V_{gd}$, $R_b=N_{pix}\times b\times N_{bands}/t_s$.
> - **Common mistakes:** thinking drag slows the spacecraft (it speeds up as $a$ falls); using the orbital speed rather than the ground speed for the line time.
> - **Practise:** [[#The workbook civilian imager at 619 km]] · [[SESA2024 2019-20 Exam Solutions#B3: Drag and data rate|2019/20 B3]]

> [!note] Coverage
> No 2025-26 lecture covered this material: Dr Ryan's last Chapter 11 lecture ended with the orbital elements and pointed to the online material (2025-12-11, ll. 451–476), and no recording of an orbit-control lecture is in the vault. Everything here comes from the workbook's Chapter 11B solutions and the past papers, which have asked for it regularly.

A remote-sensing satellite at 600–900 km still flies through a thin atmosphere. Each orbit, drag removes a little energy, the orbit shrinks a little, and the period shortens. A shorter period means the satellite arrives at each equator crossing slightly early, and since the Earth turns underneath at a fixed rate, the ground track creeps eastwards relative to the reference grid. After enough orbits it leaves the tolerance band that the repeat ground track was designed to hold. Propulsion has to put the energy back, and the question is how to do it with as few, as small, burns as possible.

The case study then closes the loop with the payload: the imager's pixels, bands and ground speed set the data rate that the communications link of [[SESA2024 09 - Communications|Chapter 9]] has to carry.

## 1. Drag decay per orbit

The drag force on a spacecraft of area $S$ and drag coefficient $C_D$ moving at $V$ through density $\rho$ is $D=\tfrac12\rho V^2SC_D$. Over one circular orbit it does work $-D\times2\pi a$, which removes that much orbital energy. The orbital energy of a spacecraft of mass $m$ is $E=-\mu m/2a$, so

$$
\frac{dE}{da}=\frac{\mu m}{2a^2}
\quad\Longrightarrow\quad
\delta E=\frac{\mu m}{2a^2}\delta a.
$$

Equate the energy change to the work done by drag:

$$
\frac{\mu m}{2a^2}\delta a=-\tfrac12\rho V^2SC_D\,(2\pi a).
$$

On a circular orbit $V^2=\mu/a$:

$$
\frac{\mu m}{2a^2}\delta a=-\pi\rho\frac{\mu}{a}SC_D\,a=-\pi\rho\mu SC_D.
$$

Solve for $\delta a$:

$$
\boxed{\delta a=-2\pi\rho\frac{SC_D}{m}a^2\ \text{per orbit}}
$$

This derivation is 2019/20 B3(ii) (6 marks). The period changes too. From $\tau=2\pi a^{3/2}/\sqrt\mu$,

$$
\frac{d\tau}{da}=\frac{3\pi a^{1/2}}{\sqrt\mu}=\frac{3\pi}{V},
\qquad
\boxed{\delta\tau=\frac{3\pi}{V}\delta a}
$$

since $\sqrt{a/\mu}=1/V$. Drag makes the spacecraft faster, not slower: as $a$ falls, $V=\sqrt{\mu/a}$ rises. The density at a given altitude can change by a factor of about ten between solar minimum and maximum, so design uses the high-activity value.

The same equation shows why a drag sail works for end-of-life disposal: $\delta a\propto S$, so raising the area ninefold makes the orbit decay nine times faster (2019/20 B3(iii)). At $a=7078$ km with $\rho=10^{-14}\ \mathrm{kg/m^3}$, $C_D=2.2$ and $m=50$ kg, a 1 m² spacecraft loses 0.14 m per orbit and a 9 m² sail raises that to 1.25 m per orbit, which helps meet the 25-year (or FCC 5-year) disposal rule in [[SESA2024 15 - Space Sustainability, Debris and NewSpace|note 15]].

## 2. The orbit-control cycle

The ground track must stay within $\pm E_0$ of its nominal position at the equator. As an angle, the full window $2E_0$ is $\delta\lambda=2E_0/R_E$ radians, and since the Earth turns at $\omega_E=360^\circ/86\,164\ \mathrm s=0.004178^\circ$/s, a timing error of

$$
\Delta t_0=\frac{\delta\lambda}{\omega_E}
$$

moves the equator crossing across the whole window.

The strategy is to boost the orbit a little above nominal, by $\Delta a/2$. The period is then slightly long, the satellite arrives late at each crossing, and the track drifts west, starting from one edge of the window. Drag shortens the period by $|\delta\tau|$ every orbit. After $k$ orbits the period is nominal and the drift stops at the far edge; after $2k$ orbits the period is short by the same amount, the track has drifted back across the window, and it is time to boost again.

The accumulated timing error after $j$ orbits, starting with a period excess of $k|\delta\tau|$, is

$$
\sum_{i=1}^{j}(k-i)|\delta\tau|\approx|\delta\tau|\left(kj-\tfrac12j^2\right),
$$

a parabola in $j$, with its maximum $\tfrac12|\delta\tau|k^2$ at $j=k$. That maximum must equal the whole window:

$$
\tfrac12|\delta\tau|k^2=\Delta t_0
\quad\Longrightarrow\quad
\boxed{k=\sqrt{\frac{2\Delta t_0}{|\delta\tau|}}}
$$

The cycle lasts $2k$ orbits, during which the orbit loses $\Delta a=2k|\delta a|$ in height. The boost that restores it is a Hohmann transfer between $a-\Delta a/2$ and $a+\Delta a/2$; for such a small change both burns are nearly equal, and

$$
\Delta V_{cycle}\approx\frac{V\,\Delta a}{2a}.
$$

Over a mission of $N$ cycles the total is $N\Delta V_{cycle}$, and the propellant follows from the rocket equation. The past-paper version, "explain, with a diagram, the full orbit control strategy required to maintain a repeating ground track" (2013/14, 2016/17), wants the parabola between $\pm E_0$ and the saw-tooth of $a$ against time.

![[ast_orbit_control_cycle.png|650]]

A remote-sensing ΔV budget has three parts (2015/16 Q1(vii)): orbit acquisition, correcting the launcher's injection errors; drag make-up for ground-track maintenance; and inclination (LST) maintenance against solar perturbations, plus end-of-life disposal.

## 3. Payload data rate

The sub-satellite point moves more slowly than the spacecraft, in proportion to the radii (2013/14, 2016/17, 2017/18 papers):

$$
V_{gd}=V\frac{R_E}{a}.
$$

A push-broom imager reads one line each time the ground track advances one pixel $p$, so the line time is

$$
t_s=\frac{p}{V_{gd}},
$$

and with $N_{pix}$ pixels per line, $b$ bits per pixel and $N_{bands}$ spectral bands,

$$
\boxed{R_b=\frac{N_{pix}\times b\times N_{bands}}{t_s}}
$$

The swath and field of view follow from the detector: $d=N_{pix}\times p$ and $\beta=2\tan^{-1}(d/2h)$. Some papers read the detector elements in pairs, each pair a 16-bit word, which halves the words per line and doubles the effective pixel.

If the rate exceeds what the downlink can carry, the data must be reduced: lossless coding such as differential PCM, fewer bits per pixel (16 to 12, or 8 to 6 for a 25 % cut), summing pixels or bands at the cost of resolution, imaging only land or cloud-free areas, or storing on board and relaying through data-relay satellites (2013/14, 2014/15, 2017/18).

## Worked examples

### The workbook civilian imager at 619 km

Workbook 11B Mission 1, after its orbit has been fixed at $(N,M)=(89,6)$, $a=6997$ km, $\tau=5824.7$ s. Drag data: $\rho=5.18\times10^{-14}\ \mathrm{kg/m^3}$, $S=1$ m², $C_D=2.2$, $m=150$ kg, tolerance $E_0=0.5$ km. Recomputed in Python.

$$
\delta a=-2\pi(5.18\times10^{-14})\frac{1\times2.2}{150}(6.997\times10^6)^2=-0.234\ \mathrm{m/orbit},
$$

$$
V=\sqrt{\mu/a}=7548\ \mathrm{m/s},
\qquad
\delta\tau=\frac{3\pi(-0.234)}{7548}=-2.92\times10^{-4}\ \mathrm{s/orbit}.
$$

The window: $\delta\lambda=2\times0.5/6378=1.568\times10^{-4}$ rad $=0.00898^\circ$, so $\Delta t_0=0.00898/0.004178=2.15$ s, and

$$
k=\sqrt{\frac{2\times2.15}{2.92\times10^{-4}}}=121.4\approx121,
$$

a cycle of 242 orbits, $242\times5824.7/86\,400=16.3$ days, losing $2\times121\times0.234=56.6$ m. The boost needs

$$
\Delta V_{cycle}\approx\frac{7548\times56.6}{2\times6.997\times10^6}=0.031\ \mathrm{m/s},
$$

2.05 m/s over 67 cycles in three years, and with $I_{sp}=180$ s only 0.17 kg of propellant.

The data rate: $V_{gd}=7548\times6378/6997=6880$ m/s, $t_s=26.9/6880=3.91$ ms, and for 19 500 pixels, 8 bits and 3 bands

$$
R_b=\frac{19\,500\times8\times3}{3.91\times10^{-3}}=119.7\ \mathrm{Mbit/s}.
$$

The military imager in the same workbook, 1000 kg with 10 m² at 277 km, needs a boost every half day, 1765 m/s over three years and 632 kg of propellant: low orbits are very expensive to hold.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]
- Next: [[SESA2024 15 - Space Sustainability, Debris and NewSpace]]
- Concepts: [[Orbit Control Cycle]] · [[Payload Data Rate]] · [[Swath Width and Push-Broom Imaging]]
- Hohmann transfer: [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]] · Propellant: [[SESA2024 07 - Spacecraft Propulsion]] · Downlink: [[SESA2024 09 - Communications]]

## Sources

- Problem Sheet Workbook 2025-26, Chapter 11B solutions
- Data sheets of the 2015/16 and 2017/18 papers; 2019/20 B3 (drag sail)
- No 2025-26 lecture or transcript; see the coverage note at the top.

## Self-study tasks

Nothing was set in lectures for this material; the tasks come from the workbook and past papers.

### Core

- [ ] Derive the drag decay per orbit and the period change (2019/20 B3(ii), 6 marks). → [[#1. Drag decay per orbit]] · [[SESA2024 2019-20 Exam Solutions#B3: Drag and data rate|solution]]
- [ ] Explain with a diagram the orbit-control strategy for a repeating ground track (2013/14, 2016/17). → [[#2. The orbit-control cycle]]
- [ ] Workbook 11B Mission 1: drag decay, control cycle, ΔV, propellant and data rate. → [[#The workbook civilian imager at 619 km]] · [[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions#Mission 1: civilian multispectral imager|Workbook solution]]

### Further practice

- [ ] The drag sail for disposal (2019/20 B3(iii)). → [[#1. Drag decay per orbit]]
- [ ] Three elements of a remote-sensing ΔV budget (2015/16 Q1(vii)). → [[#2. The orbit-control cycle]]
- [ ] Ways to reduce a data volume that exceeds the downlink (2013/14, 2017/18). → [[#3. Payload data rate]]
- [ ] Workbook 11B Mission 2, the military imager. → [[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions#Mission 2: military surveillance imager|Workbook solution]]
