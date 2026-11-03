---
title: "SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission"
module: "SESA2024 Astronautics"
type: topic
stream: "Remote Sensing Case Study"
order: 13
tags: [sesa2024, remote-sensing, repeat-ground-track, local-solar-time, raan, eclipse]
aliases: ["Calculating orbital elements", "Chapter 11 Lectures 7-9", "n m iteration"]
date: 2026-10-30
status: lectured
coverage: "Week 11 (2025-12-11, ll. 125–480) plus Prof Lewis's 2020 recordings L6, L8 and L9"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]"]
next_topics: ["[[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]"]
key_concepts: ["[[Repeat Ground Track]]", "[[Swath Width and Push-Broom Imaging]]", "[[Local Solar Time and RAAN]]", "[[Eclipse Duration]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Calculating Orbital Elements_V1.pdf", "02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Calculating Orbital Elements_Part 2_V1.pdf", "02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Calculating Orbital Elements_worked example_V1.pdf", "02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_ground track visualisation.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-12-11.txt", "02 - Sources/Lectures/SESA2024 Lecture 6 - Chapter 11 - L6 - Ground Track Visualisation Activity.txt", "02 - Sources/Lectures/SESA2024 Lecture 8.txt", "02 - Sources/Lectures/SESA2024 Lecture 9.txt"]
---

# SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission

> [!abstract] Summary
> The instrument's field of view sets the swath, and for full coverage the swath must span the gap between adjacent ground tracks at the equator, $2\pi R_E/N$. Combined with the Sun- and Earth-synchronous period $\tau=(M/N)\times86\,400$ s, that turns orbit design into a short iteration over integers $N$ and $M$, after which $a$ comes from Kepler's third law and $i$ from the regression condition. The remaining elements follow from the payload too: $e\approx0$, $\omega$ arbitrary, and $\Omega$ set by the local solar time of the node, which also fixes the eclipse and so the power and thermal design.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives an instrument field of view (or pixels and pixel size) and asks for the repeat parameters, $a$, $i$, an LST or the RAAN.
> - **Assumptions:** circular, Sun- and Earth-synchronous; nadir-pointing imager; altitude roughly 700–900 km unless the mission says otherwise; swaths just touching at the equator.
> - **Method:** 1. Guess $h$; $d=2h\tan(\beta/2)$, $\tau$ from Kepler 3. 2. $N=\mathrm{int}(2\pi R_E/d)$, $M=\mathrm{int}(N\tau/86\,400)$, with $N$ and $M$ coprime. 3. $\tau=(M/N)86\,400$; if outside the target range, step $N$ (or $M$) and repeat. 4. $a$ from Kepler 3, then $\cos i=0.9856/(-2.0647\times10^{14}a^{-3.5})$. 5. Check the swath at the new $h$ covers $2\pi R_E/N$; choose the LST and set $\Omega=\alpha_S\pm$ the node angle.
> - **Common mistakes:** a pair $N$, $M$ with a common factor (98 and 7), which repeats sooner than intended and leaves gaps; forgetting to recheck the swath after the altitude changes.
> - **Practise:** [[#The 28.96 degree imager (2020 Lecture 9)]] · [[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions#Mission 1: civilian multispectral imager|Workbook 11B Mission 1]]

By the end of [[SESA2024 12 - Sun- and Earth-Synchronous Orbits|the previous note]], the orbit is constrained to be Sun- and Earth-synchronous, with $\tau=(M/N)\times86\,400$ s. That still leaves a family of orbits. What picks one is the payload, and in particular the camera's field of view, which "the payload guys" hand to the mission analyst as a fixed number (2025-12-11, ll. 126–175). The only thing the analyst can change is the altitude.

Each pass of the push-broom imager covers a stripe of width $d$ along the ground track. Adjacent ground tracks are farthest apart at the equator and converge towards the poles, so if the stripes touch at the equator, the whole Earth between the latitude limits is covered (ll. 176–225). That fixes how many distinct tracks are needed, and through the repeat condition, the period and the altitude.

## 1. The coverage condition

For a nadir-pointing imager with field of view $\beta$ at altitude $h$, the swath width is

$$
d=2h\tan\frac{\beta}{2}.
$$

The track spacing at the equator, with $N$ distinct tracks in one repeat cycle, is the equator's circumference divided by $N$. Setting the swath equal to the spacing (ll. 201–250):

$$
d=\frac{2\pi R_E}{N}
\quad\Longrightarrow\quad
N=\mathrm{int}\left(\frac{2\pi R_E}{2h\tan(\beta/2)}\right).
$$

"int" means a nearby integer, not necessarily rounding down; the ground track can only close on itself after a whole number of orbits (2020 Lecture 9, ll. 91–120). Too low an orbit leaves gaps between the stripes, while the optimum altitude makes them just touch (2025-12-11, ll. 176–200).

Rearranging the repeat condition gives the number of days:

$$
M=\mathrm{int}\left(\frac{N\tau}{86\,400}\right).
$$

## 2. The iteration

The difficulty is circular (2025-12-11, ll. 276–400). The swath and the period both depend on $h$, but rounding $N$ and $M$ to integers changes the period, and with it $h$. So the procedure is a short loop, which the slides draw as a flowchart:

1. Choose an altitude in the first-pass range (700–900 km, so $\tau\approx6050\pm120$ s).
2. Swath $d=2h\tan(\beta/2)$.
3. Period $\tau=2\pi\sqrt{(R_E+h)^3/\mu}$.
4. $N=\mathrm{int}(2\pi R_E/d)$.
5. $M=\mathrm{int}(N\tau/86\,400)$.
6. Recompute the period from the integers, $\tau=(M/N)\times86\,400$.
7. If $\tau$ is outside the allowed range, change $N$ by one (or $M$) and go back to 6; otherwise stop.

Then $a=[\mu(\tau/2\pi)^2]^{1/3}$, $h=a-R_E$, and $i$ from the regression condition. Since $\tau\propto1/N$, increasing $N$ shortens the period and lowers the orbit (2020 Lecture 9, ll. 151–165). Changing $M$ makes a bigger jump, because $M$ is the smaller number.

Because $N$ and $M$ must be integers, only a handful of orbits in the 700–900 km band are both Sun- and Earth-synchronous; the slide table lists $(M,N)=(1,14)$ at 888 km and $98.98^\circ$, $(6,85)$, $(5,68)$ and others (2025-12-11, ll. 401–450).

> [!warning] Transcript slip (2025-12-11, ll. 420–450)
> The chosen option is first called "six days and 83 orbits", then "6 and 85". $(6,83)$ gives 952 km, outside the 700–900 km band; $(6,85)$ gives 837 km and $i=98.76^\circ$, inside it. 85 is the one meant.

### N and M must have no common factor

If $N$ and $M$ share a factor, the track repeats sooner than intended. $(98,7)$ has $\tau=(7/98)\times86\,400=6171$ s, exactly the same as $(14,1)$: the track closes after 14 orbits in one day and then simply retraces itself. There are then only 14 distinct tracks, $2\pi R_E/14=2862$ km apart at the equator, not 98. A pair such as $(97,7)$ or $(99,7)$ gives 97 or 99 distinct tracks.

## 3. The remaining elements

Prof Lewis's 2020 Lecture 8 completes the set (ll. 1–180; slides `Calculating Orbital Elements_Part 2`).

Eccentricity: close to zero, from the first pass, so the range and pixel size are constant.

Argument of perigee: undefined for a circular orbit, so arbitrary. Some missions use frozen orbits, in which $e$ and $\omega$ stay locked at chosen small values, but the course does not cover them.

Right ascension of the ascending node: not arbitrary. Sun-synchronism keeps $\phi=\alpha_S-\Omega$ constant, and that constant decides where the Sun is in the sky when the spacecraft crosses the equator, that is, the local solar time (LST) of the nodes. Choosing $\Omega$ really means choosing the LST, from the payload's illumination needs. Then, knowing the Sun's right ascension on the launch date,

$$
\Omega=\alpha_S-\phi\quad\text{at launch}.
$$

The Earth turns $15^\circ$ per hour, so an LST of $t$ hours at the node corresponds to an angle $15^\circ(12-t)$ from the Sun direction:

| Orbit | Node LST | $\phi$ | $\Omega$ at launch |
|---|---|---|---|
| Noon–midnight | 12:00 / 00:00 | $0^\circ$ or $180^\circ$ | $\alpha_S$ |
| Dawn–dusk | 06:00 / 18:00 | $90^\circ$ or $270^\circ$ | $\alpha_S-90^\circ$ |
| Mid-morning | 10:30 | $22.5^\circ$ | $\alpha_S-22.5^\circ$ |

Most European remote-sensing satellites fly a "northern-hemisphere morning" orbit with a descending node at about 10:30 LST. They reach Europe around 10:30–11:00, with good illumination and moderate shadows, before afternoon convective cloud builds up over land (2020 Lecture 8, ll. 91–120). Prof Lewis admits he was inconsistent about the direction in which $\phi$ is measured; measure it consistently, clockwise from the Earth–Sun line (ll. 61–90).

## 4. The LST sets the eclipse

The LST of the node decides how the orbit sits relative to the terminator, and so how much of each orbit is in shadow (2020 Lecture 8, ll. 91–180). A noon–midnight orbit at the equinox spends roughly half of each orbit in eclipse (about 3000 s of a 6000 s orbit). A dawn–dusk orbit rides the terminator and is in sunlight all year except for short eclipses of 15–20 minutes in the northern winter, because at $98^\circ$ it does not follow the terminator exactly. A 10 a.m. orbit spends about a third of each orbit in eclipse, around 33 minutes on average.

That chain, from a payload illumination requirement through the LST to the eclipse, then reaches the other subsystems: the battery mass and array size ([[SESA2024 08 - Electrical Power Subsystem]]), the array articulation (a Sun-synchronous orbit removes one degree of freedom, and a dawn–dusk orbit lets the array stay fixed), and the heaters and radiators needed for the hot and cold phases ([[SESA2024 10 - Thermal Control]]). It is the systems-engineering message of [[SESA2024 01 - Systems Engineering and Spacecraft Design|note 01]] in action.

## 5. Visualising ground tracks

Prof Lewis's 2020 Lecture 6 introduces a ground-track version of the Excel visualiser: enter the elements and the date and time, and it plots the track including both the Earth's rotation and the $J_2$ regression (for circular orbits only). The activity compares its tracks for the ISS, Hubble and Envisat with those on Heavens-Above and explores how the date and elements change the equator-crossing angle, the maximum latitude and the longitude step per orbit (ll. 1–80).

![[ast_sso_ground_track.png|760]]

## Worked examples

All values recomputed in Python with $R_E=6378$ km, $\mu=398\,600\ \mathrm{km^3/s^2}$.

### The 28.96 degree imager (2020 Lecture 9)

A civil mission maps roads and buildings at high resolution for about ten years with a visible imager of field of view $28.96^\circ$. Find $N$, $M$, $a$ and $i$, suggest a descending-node LST, and find the RAAN for a launch at the spring equinox (2020 Lecture 9, ll. 1–240).

High resolution with a long life gives the same trade as the first pass, so 700–900 km. Start at 800 km:

$$
d=2\times800\tan14.48^\circ=413.2\ \mathrm{km},
\qquad
\tau=2\pi\sqrt{\frac{7178^3}{398\,600}}=6052\ \mathrm s,
$$

$$
N=\mathrm{int}\left(\frac{2\pi\times6378}{413.2}\right)=\mathrm{int}(96.99)=97,
\qquad
M=\mathrm{int}\left(\frac{97\times6052}{86\,400}\right)=\mathrm{int}(6.79)=7.
$$

Then $\tau=(7/97)\times86\,400=6235$ s, which is above the 6050 ± 120 s range, so the orbit is too high (944 km). To shorten the period, increase $N$.

The recording takes $N=98$, giving $\tau=6171$ s, $a=7271.9$ km, $h=893.9$ km and $i=99.01^\circ$.

> [!warning] Source problem in the worked example (2020 Lecture 9, ll. 151–215)
> $(98,7)$ has a common factor of 7, so it is the $(14,1)$ orbit: the ground track repeats every day after 14 orbits, with tracks 2862 km apart at the equator. A 409–413 km swath leaves large gaps, so the mission would not map the whole globe. The recording skips the final swath check that would reveal it ("I'm not doing that in the worked example", l. 225).
>
> Taking $N=99$ instead, which is coprime with 7, gives $\tau=(7/99)\times86\,400=6109$ s, $a=7222.9$ km, $h=844.9$ km and $i=98.79^\circ$. The track spacing is $2\pi\times6378/99=404.8$ km, and the swath at 844.9 km is $2\times844.9\tan14.48^\circ=436.4$ km, so adjacent swaths overlap slightly and the globe is covered. $(97,7)$ also covers the globe, at 944 km.

For the LST, a European mapping mission wants mid-morning passes with good light and little convective cloud, so a descending node at 10:30. At the spring equinox the Sun's right ascension is $0^\circ$. A 10:30 node is $1.5\ \mathrm h\times15^\circ/\mathrm h=22.5^\circ$ from the Sun direction, so an ascending node at 10:30 would need $\Omega=0-22.5^\circ=337.5^\circ$. With the descending node at 10:30, the ascending node is at 22:30 on the other side of the Earth, $180^\circ$ round:

$$
\Omega=337.5^\circ-180^\circ=157.5^\circ\ \text{at launch}.
$$

Finally $e=0$ and $\omega$ is arbitrary.

### Workbook Mission 1: a civilian multispectral imager

Workbook 11B Mission 1 runs the same loop for a 19 500-pixel, three-band imager at 20–30 m resolution and arrives at $(N,M)=(89,6)$: $\tau=5824.7$ s, $h=619.0$ km, $i=97.86^\circ$, a 524.8 km swath and 26.9 m pixels. 89 and 6 are coprime, so the 89 tracks are distinct and the swath (524.8 km) exceeds the spacing (450.3 km). The full working, including the trial table and the drag and data-rate follow-ups, is in [[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions#Mission 1: civilian multispectral imager|the workbook solution]].

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]
- Next: [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]
- Concepts: [[Repeat Ground Track]] · [[Swath Width and Push-Broom Imaging]] · [[Local Solar Time and RAAN]] · [[Eclipse Duration]]
- Workbook: [[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]]

## Sources

- `Chapter 11_Calculating Orbital Elements_V1.pdf` with transcript `SESA2024 Lecture 2025-12-11.txt`, ll. 125–480 (Dr C. Ryan)
- Prof Lewis's 2020 recordings: `SESA2024 Lecture 8.txt` (the remaining elements, LST and RAAN, eclipse) with `Chapter 11_Calculating Orbital Elements_Part 2_V1.pdf`; `SESA2024 Lecture 9.txt` (worked example) with `Chapter 11_Calculating Orbital Elements_worked example_V1.pdf`; `SESA2024 Lecture 6 - Chapter 11 - L6 - Ground Track Visualisation Activity.txt` with `Chapter 11_ground track visualisation.pdf`
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 5

## Self-study tasks

### Core

- [ ] The 28.96° imager: $N$, $M$, $a$, $i$, a descending-node LST and the RAAN at a spring-equinox launch (2020 Lecture 9, "pause the recording... attempt the question yourself", ll. 1–30). Check the swath at the final altitude. → [[#The 28.96 degree imager (2020 Lecture 9)]]
- [ ] Explain why the swath condition is applied at the equator (asked of the class, 2025-12-11, ll. 201–225). → [[#1. The coverage condition]]
- [ ] Workbook 11B Mission 1, the civilian multispectral imager. → [[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions#Mission 1: civilian multispectral imager|Workbook solution]]
- [ ] Find the RAAN at launch for noon–midnight, dawn–dusk and 10:30 orbits, and say what each LST does to the eclipse (2020 Lecture 8). → [[#3. The remaining elements]] · [[#4. The LST sets the eclipse]]

### Further practice

- [ ] The ground-track activity: compare the Excel ground tracks for the ISS, Hubble and Envisat with Heavens-Above (2020 Lecture 6, ll. 41–80). → [[#5. Visualising ground tracks]]
- [ ] Workbook 11B Mission 2, the military surveillance imager. → [[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions#Mission 2: military surveillance imager|Workbook solution]]
- [ ] Show that $(98,7)$ is the same orbit as $(14,1)$ and find a coprime alternative. → [[#N and M must have no common factor]]
- [ ] LST of the nodes for a Sun-synchronous orbit (2024/25 A7: a 10:00 node stays at 10:00). → [[SESA2024 2024-25 Exam Solutions#Section A|2024/25 A7]]
