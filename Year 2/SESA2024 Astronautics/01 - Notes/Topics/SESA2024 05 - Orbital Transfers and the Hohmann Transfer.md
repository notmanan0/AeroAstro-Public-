---
title: "SESA2024 05 - Orbital Transfers and the Hohmann Transfer"
module: "SESA2024 Astronautics"
type: topic
stream: "Mission Analysis"
order: 5
tags: [sesa2024, orbital-mechanics, orbital-transfer, hohmann-transfer, delta-v]
aliases: ["Hohmann transfer", "Orbital transfers", "Chapter 5 Lectures 11-13"]
date: 2026-10-30
status: lectured
coverage: "Week 10 (2025-12-02)"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]", "[[SESA2024 07 - Spacecraft Propulsion]]"]
next_topics: ["[[SESA2024 11 - Payload and Orbit Selection]]"]
key_concepts: ["[[Hohmann Transfer]]", "[[Vis-Viva Equation]]", "[[Tsiolkovsky Rocket Equation]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch5 - Mission Analysis Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Hohman transfers_V2.pdf", "02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Hohman transfers worked example_V1.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-12-02.txt", "02 - Sources/Lectures/SESA2024 Lecture 12.txt", "02 - Sources/Lectures/SESA2024 Lecture 13.txt"]
---

# SESA2024 05 - Orbital Transfers and the Hohmann Transfer

> [!abstract] Summary
> An impulsive burn changes a spacecraft's speed at one point, so the new orbit always passes through the point where the burn happened. Moving between two circular coplanar orbits therefore takes at least two burns, and the Hohmann transfer does it with a half-ellipse tangent to both circles: a prograde burn at the inner circle puts the spacecraft on the ellipse, and a second prograde burn at apoapsis circularises it. Each ΔV is a difference of two speeds from the energy equation, the transfer time is half the ellipse's period, and the rocket equation turns ΔV into propellant.

> [!summary]- Exam use: quick path
> - **Use it when:** a question moves a spacecraft between two circular orbits in the same plane (LEO to GEO, Earth's orbit to another planet's), asks for the transfer time, or asks for the propellant for a burn.
> - **Assumptions:** impulsive burns (high thrust, short duration), fired along the velocity at the apses so there is no gravity loss; coplanar circular start and end orbits; no drag.
> - **Method:** 1. Radii: $r_1=R+h_1$, $r_2=R+h_2$; transfer $a_T=(r_1+r_2)/2$. 2. Circular speeds $V_{1,2}=\sqrt{\mu/r_{1,2}}$. 3. Transfer speeds $V_{Tp},V_{Ta}=\sqrt{\mu(2/r-1/a_T)}$ at $r_1$ and $r_2$. 4. $\Delta V=(V_{Tp}-V_1)+(V_2-V_{Ta})$; time $=\pi\sqrt{a_T^3/\mu}$. 5. Propellant: $m_0/m_f=e^{\Delta V/V_{ex}}$, fraction $1-m_f/m_0$.
> - **Common mistakes:** adding the Earth's radius to a radius that was already given as a radius (the GEO 42 164 km); taking the full period instead of half for the transfer time.
> - **Practise:** [[#200 km parking orbit to GEO]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q7. From a 300 km equatorial orbit to GEO with staged masses|Workbook Q7]]

The lecture started with a video, filmed from the ISS, of the RemoveDebris satellite being released by a robotic arm (2025-12-02, ll. 45–130). RemoveDebris, built by the Surrey Space Centre and Surrey Satellite Technology Ltd to demonstrate debris-capture techniques, was pushed gently backwards, against the station's direction of travel. Two quiz questions followed, and they carry the whole idea of this note.

First, which orbit does it end up on? The push is tiny, but it is a change of velocity at one point, so the new orbit must pass through the release point; an orbit that does not intersect the ISS's is impossible. Taking speed away removes kinetic energy, so the energy equation says the new $a$ is smaller: the satellite drops into a slightly elliptical orbit whose highest point is the release point (ll. 133–265). Releasing it forwards would instead have raised it on to a larger ellipse, and many orbits later it could come back and meet the station, which is why the backwards release was chosen (ll. 265–315).

Second, where does it go relative to the ISS? A smaller $a$ means a shorter period by Kepler's third law, so after half an orbit the satellite is below the station and has gained on it, and each orbit it pulls further ahead (ll. 330–395). The answer to the poll was "ahead and below".

![[ast_removedebris_relative_motion.png|800]]

This is counter-intuitive enough that Dr Ryan dwelt on it: to catch up with a spacecraft ahead of you in the same orbit, you fire backwards, drop into a lower, faster orbit, and fire forwards again when you have caught up (ll. 375–445). Buzz Aldrin wrote his MIT doctorate on orbital rendezvous, which his fellow astronauts teased him for until Apollo needed it ("Dr Rendezvous").

The figure uses the linearised relative-motion equations for a circular reference orbit, which the course does not cover; it is there only to show the shape. For a 5 cm/s backwards push at the ISS's altitude, the satellite drops about 177 m below and drifts $3\,\Delta V\,\tau\approx830$ m ahead each orbit.

> [!warning] Transcript slips (2025-12-02, ll. 60–70 and 125–135)
> RemoveDebris is described as a "large CubeSat" about 30 cm across. It was a microsatellite of about 100 kg, built to CubeSat-style standards but much larger, and it carried two CubeSats of its own as targets. The ISS is again given an orbital period of "about 45 minutes"; it is about 92 minutes.

## 1. Assumptions for orbital transfers

The analysis rests on two assumptions (2025-12-02, ll. 463–530; slides).

The burns are impulsive. A high-thrust engine fires for a time much shorter than the orbital period, so the change of velocity happens at a single point and the position does not change during it. That means a chemical engine. An ion thruster firing for weeks spirals out gradually instead, and this analysis does not apply to it (ll. 715–730).

The burns are along the velocity, with a small flight-path angle $\gamma$ between the velocity and the local horizontal. If the thrust has a component along the radius, part of the work goes into fighting gravity rather than changing the orbit, a gravity loss. At periapsis and apoapsis the velocity is exactly perpendicular to the radius, $\gamma=0$, so burns there have no gravity loss (ll. 485–520). With both assumptions the rocket equation applies with no loss terms:

$$
\Delta V=V_{ex}\ln\frac{m_0}{m_f},
$$

where $V_{ex}$ is the exhaust velocity and $m_0$ and $m_f$ the masses before and after the burn (see [[SESA2024 07 - Spacecraft Propulsion]]).

Because an impulsive burn leaves the position unchanged, the orbits before and after a burn always share the burn point. Two circular orbits of different radii never meet, so going from one to the other needs at least two burns: one to leave the first circle on an orbit that reaches the second, and another to stay on the second (ll. 529–545).

## 2. The Hohmann transfer

The Hohmann transfer is the two-burn transfer between coplanar circular orbits that uses a transfer ellipse tangent to both circles (2025-12-02, ll. 551–715). Its periapsis touches the inner circle of radius $r_1$ and its apoapsis touches the outer circle of radius $r_2$. Both burns are therefore at apses and along the velocity, with no gravity loss.

![[ast_hohmann_leo_geo.png|700]]

The transfer ellipse's major axis runs from $r_1$ on one side of the planet to $r_2$ on the other, so

$$
a_T=\frac{r_1+r_2}{2}.
$$

The speed on the inner circle is $V_1=\sqrt{\mu/r_1}$. At the transfer orbit's periapsis, the energy equation with $r=r_1$ and $a=a_T$ gives

$$
V_{Tp}=\sqrt{\mu\left(\frac{2}{r_1}-\frac{1}{a_T}\right)}.
$$

The first burn adds the difference:

$$
\Delta V_{Tp}=V_{Tp}-V_1.
$$

The spacecraft then coasts half an orbit to apoapsis at $r_2$, where its speed is

$$
V_{Ta}=\sqrt{\mu\left(\frac{2}{r_2}-\frac{1}{a_T}\right)}.
$$

That is less than the circular speed $V_2=\sqrt{\mu/r_2}$ at that radius, so without a second burn it would fall back down to $r_1$. The second burn circularises:

$$
\Delta V_{Ta}=V_2-V_{Ta},
\qquad
\Delta V=\Delta V_{Tp}+\Delta V_{Ta}.
$$

Both burns are prograde, so only the magnitudes matter and the order of subtraction does not (2020 Lecture 13, ll. 91–100).

### The ΔV in closed form

Substituting $a_T=(r_1+r_2)/2$ gives the closed forms used in Workbook Ch5 Q3. At periapsis,

$$
\frac{2}{r_1}-\frac{2}{r_1+r_2}=\frac{2(r_1+r_2)-2r_1}{r_1(r_1+r_2)}=\frac{2r_2}{r_1(r_1+r_2)},
$$

so

$$
V_{Tp}=\sqrt{\frac{\mu}{r_1}}\sqrt{\frac{2r_2}{r_1+r_2}},
\qquad
\Delta V_{Tp}=\sqrt{\frac{\mu}{r_1}}\left(\sqrt{\frac{2r_2}{r_1+r_2}}-1\right).
$$

By the same steps at apoapsis,

$$
V_{Ta}=\sqrt{\frac{\mu}{r_2}}\sqrt{\frac{2r_1}{r_1+r_2}},
\qquad
\Delta V_{Ta}=\sqrt{\frac{\mu}{r_2}}\left(1-\sqrt{\frac{2r_1}{r_1+r_2}}\right).
$$

Writing $x=r_1/r_2$ and dividing by $V_1$ gives the total as a function of the radius ratio only:

$$
\frac{\Delta V}{V_1}=\left(\frac{2}{1+x}\right)^{1/2}(1-x)+x^{1/2}-1.
$$

This rises with $r_2/r_1$ to a maximum of $0.536\,V_1$ at $r_2/r_1=15.58$ and then falls slowly towards $\sqrt2-1=0.414$ as $r_2\to\infty$. The second burn shrinks faster than the first grows, because the outer circular speed falls away.

![[ast_hohmann_dv_ratio.png|650]]

### Transfer time

The spacecraft travels half of the transfer ellipse, so by Kepler's third law

$$
t_T=\frac{\tau_T}{2}=\pi\sqrt{\frac{a_T^3}{\mu}}.
$$

## 3. Where the Hohmann transfer is used, and its limits

Most Earth orbits are near-circular and most upper stages are chemical, so the Hohmann transfer is the standard way to raise an orbit, and Dr Ryan flagged it as "a very, very, very common exam question" (ll. 705–715). In practice a launcher often performs the first burn, placing the spacecraft in a geostationary transfer orbit (GTO), and the spacecraft's own apogee engine performs the second (2020 Lecture 13, ll. 151–160).

The same method works around the Sun, from the Earth's orbit to another planet's, but the transfer to the outer planets takes years, and the planets must be correctly phased when you leave, which defines a launch window (Workbook Ch5 Q6). It is the minimum-ΔV two-impulse transfer between coplanar circles, but it is not the fastest, and it does not handle elliptical, inclined or hyperbolic orbits, which need other manoeuvres (ll. 727–750).

## Worked examples

All numbers recomputed in Python with $R_E=6378$ km and $\mu=398\,600\ \mathrm{km^3/s^2}$.

### 200 km parking orbit to GEO

The Chapter 5 worked example (`Hohman transfers worked example_V1.pdf`; 2020 Lecture 13): find the ΔV and transfer time from a circular 200 km parking orbit to GEO ($r_{GEO}=42\,164$ km), and estimate the propellant for the second burn if $V_{ex}=2.5$ km/s.

The parking-orbit radius is $r_1=6378+200=6578$ km, which is also the transfer orbit's perigee. The GEO radius is given as a radius, so nothing is added to it (2020 Lecture 13, ll. 31–45). Then

$$
a_T=\frac{6578+42\,164}{2}=24\,371\ \mathrm{km}.
$$

The four speeds:

$$
V_1=\sqrt{\frac{398\,600}{6578}}=7.784\ \mathrm{km/s},
\qquad
V_{Tp}=\sqrt{398\,600\left(\frac{2}{6578}-\frac{1}{24\,371}\right)}=10.239\ \mathrm{km/s},
$$

$$
V_{Ta}=\sqrt{398\,600\left(\frac{2}{42\,164}-\frac{1}{24\,371}\right)}=1.597\ \mathrm{km/s},
\qquad
V_{GEO}=\sqrt{\frac{398\,600}{42\,164}}=3.075\ \mathrm{km/s}.
$$

The burns:

$$
\Delta V_{Tp}=10.239-7.784=2.455\ \mathrm{km/s},
\qquad
\Delta V_{Ta}=3.075-1.597=1.477\ \mathrm{km/s},
$$

$$
\Delta V=3.932\ \mathrm{km/s}.
$$

The slides add rounded components and quote 1.478 and 3.933 km/s. The transfer time is

$$
t_T=\pi\sqrt{\frac{24\,371^3}{398\,600}}=18\,930\ \mathrm s=5.26\ \mathrm h.
$$

For the second burn, write $x=m_0/m_f$:

$$
x=\exp\left(\frac{1.477}{2.5}\right)=1.806,
\qquad
\frac{m_p}{m_0}=1-\frac1x=0.446.
$$

About 45 % of the spacecraft's mass after the first burn is propellant for the circularisation alone. A 4000 kg spacecraft in GTO arrives in GEO at about 2200 kg (2020 Lecture 13, ll. 151–160).

> [!check] Is the second burn's propellant plausible?
> Yes. Real GEO communications satellites launched into GTO typically carry roughly half their launch mass as propellant, most of it for apogee raising, which matches this estimate.

### 400 km to GEO with the Excel tool

In the lecture the Hohmann spreadsheet was set to a 6758 km original orbit (about 380 km up) and a 42 164 km target, and the burns were adjusted by hand until the final orbit matched (2025-12-02, ll. 771–880). The exact Hohmann values for that pair of radii are

$$
\Delta V_{Tp}=2.403\ \mathrm{km/s},\qquad\Delta V_{Ta}=1.459\ \mathrm{km/s},\qquad\Delta V=3.862\ \mathrm{km/s},
$$

with a transfer time of 5.29 h. The lecture read off "3.7 km/s" while the final orbit was still being tuned; the remaining "orbital error" shown by the tool goes to zero as the sum approaches 3.86 km/s. Raising the parking orbit from 200 to 380 km saves about 70 m/s.

> [!warning] Transcript slip (2025-12-02, ll. 815–835)
> The class was asked for the altitude of a "geostationary transfer orbit" and the answer given was 36 000 km. That is the altitude of the geostationary orbit itself. The transfer orbit (GTO) is the ellipse between the parking orbit and GEO, with its perigee at a few hundred kilometres and its apogee at GEO height.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]
- Next: [[SESA2024 11 - Payload and Orbit Selection]] (the next lecture, 2025-12-04); the Hohmann make-up manoeuvre returns in [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]
- Concepts: [[Hohmann Transfer]] · [[Vis-Viva Equation]] · [[Tsiolkovsky Rocket Equation]] (SESA2023)
- Propulsion: [[SESA2024 07 - Spacecraft Propulsion]] · [[SESA2023 Propulsion Hub]]

## Sources

- `Chapter 5_Hohman transfers_V2.pdf` and `Chapter 5_Hohman transfers worked example_V1.pdf` (Dr C. Ryan, after Prof H. Lewis)
- Transcript `SESA2024 Lecture 2025-12-02.txt`
- Prof Lewis's 2020 recordings: `SESA2024 Lecture 12.txt` (Hohmann visualisation activity) and `SESA2024 Lecture 13.txt` (the worked example)
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 5

## Self-study tasks

### Core

- [ ] The worked example: ΔV, transfer time and second-burn propellant fraction from a 200 km parking orbit to GEO with $V_{ex}=2.5$ km/s ("please go have a look at that", 2025-12-02, ll. 705–715). Targets 3.93 km/s, 5.26 h, 45 %. → [[#200 km parking orbit to GEO]]
- [ ] RemoveDebris poll questions: which orbit after a backwards release, and where it goes relative to the ISS (ll. 133–395). → [[#SESA2024 05 - Orbital Transfers and the Hohmann Transfer|opening section]]
- [ ] 300 km equatorial orbit to GEO, with the staged masses (Workbook Ch5 Q7). Target 3.893 km/s, about 600 kg in GEO. → [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q7. From a 300 km equatorial orbit to GEO with staged masses|Workbook solution]]
- [ ] Express the Hohmann ΔV in terms of $x=r_1/r_2$ (Workbook Ch5 Q3). → [[#The ΔV in closed form]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q3. Hohmann total delta-V in terms of x = r1 over r2|Workbook solution]]

### Further practice

- [ ] The Hohmann visualisation activity: set a LEO original orbit and a GEO target in the Excel tool, and adjust $\Delta V_1$ and $\Delta V_2$ until the orbital error is near zero (2020 Lecture 12; 2025-12-02, ll. 750–880). → [[#400 km to GEO with the Excel tool]]
- [ ] Advantages and disadvantages of the Hohmann transfer for interplanetary missions (Workbook Ch5 Q6). → [[#3. Where the Hohmann transfer is used, and its limits]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q6. Hohmann transfer for interplanetary missions|Workbook solution]]
- [ ] Comet intercept by a heliocentric Hohmann transfer (Workbook Ch5 Q8). → [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q8. Comet intercept by heliocentric Hohmann transfer|Workbook solution]]
- [ ] Explain why the burns are placed at the apses (2025-12-02, ll. 485–520). → [[#1. Assumptions for orbital transfers]]
