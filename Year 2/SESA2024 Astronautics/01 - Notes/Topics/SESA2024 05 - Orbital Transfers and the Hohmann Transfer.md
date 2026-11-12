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

RemoveDebris, a debris-capture demonstrator built by the Surrey Space Centre and Surrey Satellite Technology Ltd, was released from the ISS by a robotic arm and pushed gently backwards, against the station's direction of travel (2025-12-02, ll. 45–130).

The push is tiny, but it is a change of velocity at one point, so the new orbit must pass through the release point; an orbit that does not intersect the ISS's is impossible. Taking speed away removes kinetic energy, so the energy equation says the new $a$ is smaller: the satellite drops into a slightly elliptical orbit whose highest point is the release point (ll. 133–265). Releasing it forwards would instead have raised it on to a larger ellipse, and many orbits later it could come back and meet the station, which is why the backwards release was chosen (ll. 265–315).

Relative to the ISS, a smaller $a$ means a shorter period by Kepler's third law, so after half an orbit the satellite is below the station and has gained on it, and each orbit it pulls further ahead, ending up ahead and below (ll. 330–395; numbers for the new orbit and the drift are in §4).

![[ast_removedebris_relative_motion.png|800]]

To catch up with a spacecraft ahead in the same orbit, the pursuer fires backwards, drops into a lower, faster orbit, and fires forwards again once it has caught up (ll. 375–445). Orbital rendezvous, which Apollo depended on, rests on this reasoning.

The linearised relative-motion equations behind the figure are outside the syllabus, and the figure shows only the shape of the motion. Its two numbers, a 177 m drop and an 833 m drift per orbit, follow from the energy equation and Kepler's third law alone (§4).

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

At apoapsis the same steps with $r_2$ in place of $r_1$ give

$$
\frac{2}{r_2}-\frac{2}{r_1+r_2}=\frac{2(r_1+r_2)-2r_2}{r_2(r_1+r_2)}=\frac{2r_1}{r_2(r_1+r_2)},
$$

so

$$
V_{Ta}=\sqrt{\frac{\mu}{r_2}}\sqrt{\frac{2r_1}{r_1+r_2}},
\qquad
\Delta V_{Ta}=\sqrt{\frac{\mu}{r_2}}\left(1-\sqrt{\frac{2r_1}{r_1+r_2}}\right).
$$

To reduce the total to one variable, write $x=r_1/r_2$ and divide every term by $V_1=\sqrt{\mu/r_1}$. The first burn becomes

$$
\frac{\Delta V_{Tp}}{V_1}=\sqrt{\frac{2r_2}{r_1+r_2}}-1=\sqrt{\frac{2}{1+x}}-1,
$$

after dividing top and bottom of the fraction by $r_2$. For the second burn, $\sqrt{\mu/r_2}/\sqrt{\mu/r_1}=\sqrt{r_1/r_2}=\sqrt x$, and $2r_1/(r_1+r_2)=2x/(1+x)$:

$$
\frac{\Delta V_{Ta}}{V_1}=\sqrt x\left(1-\sqrt{\frac{2x}{1+x}}\right)=\sqrt x-x\sqrt{\frac{2}{1+x}}.
$$

Add the two and collect the $\sqrt{2/(1+x)}$ terms:

$$
\frac{\Delta V}{V_1}=\sqrt{\frac{2}{1+x}}-1+\sqrt x-x\sqrt{\frac{2}{1+x}}
$$

$$
\frac{\Delta V}{V_1}=\left(\frac{2}{1+x}\right)^{1/2}(1-x)+x^{1/2}-1.
$$

> [!check] The LEO-to-GEO ratio
> For $r_1=6578$ km and $r_2=42\,164$ km, $x=0.1560$ and the bracket gives $\Delta V/V_1=0.5051$. Times $V_1=7.784$ km/s that is 3.932 km/s, the same as the four-speed calculation in the worked example. At $x=1$ the formula gives $0$, as it must for no transfer.

This rises with $r_2/r_1$ to a maximum of $0.536\,V_1$ at $r_2/r_1=15.58$ and then falls slowly towards $\sqrt2-1=0.414$ as $r_2\to\infty$. The second burn shrinks faster than the first grows, because the outer circular speed falls away.

![[ast_hohmann_dv_ratio.png|650]]

### Transfer time

The spacecraft travels half of the transfer ellipse, so by Kepler's third law

$$
t_T=\frac{\tau_T}{2}=\pi\sqrt{\frac{a_T^3}{\mu}}.
$$

## 3. Where the Hohmann transfer is used, and its limits

Most Earth orbits are near-circular and most upper stages are chemical, so the Hohmann transfer is the standard way to raise an orbit, and it is a very common exam question (ll. 705–715). In practice a launcher often performs the first burn, placing the spacecraft in a geostationary transfer orbit (GTO), and the spacecraft's own apogee engine performs the second (2020 Lecture 13, ll. 151–160).

The same method works around the Sun, from the Earth's orbit to another planet's, but the transfer to the outer planets takes years, and the planets must be correctly phased when you leave, which defines a launch window (Workbook Ch5 Q6). It is the minimum-ΔV two-impulse transfer between coplanar circles, but it is not the fastest, and it does not handle elliptical, inclined or hyperbolic orbits, which need other manoeuvres (ll. 727–750).

## 4. How far a small burn moves the orbit

The RemoveDebris release can be put into numbers using only the energy equation and Kepler's third law. The same small-change method is used for drag make-up in [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]].

Start from the energy equation at the release radius $r$, which does not change during an impulsive burn:

$$
\frac{V^2}{2}-\frac{\mu}{r}=-\frac{\mu}{2a}.
$$

A small change $\delta V$ in speed, with $r$ fixed, changes the left side by $V\,\delta V$ and the right side by the derivative of $-\mu/2a$ with respect to $a$, times $\delta a$:

$$
V\,\delta V=\frac{\mu}{2a^2}\,\delta a.
$$

Solve for $\delta a$:

$$
\delta a=\frac{2a^2V}{\mu}\,\delta V.
$$

The ISS orbit is circular, so $\mu=aV^2$ and

$$
\delta a=\frac{2a^2V}{aV^2}\,\delta V=\frac{2a}{V}\,\delta V.
$$

For the ISS, $a=6780$ km and $V=\sqrt{398\,600/6780}=7.668$ km/s. A backwards push of $\delta V=-0.05$ m/s $=-5\times10^{-5}$ km/s gives

$$
\delta a=\frac{2(6780)}{7.668}\left(-5\times10^{-5}\right)=-0.0884\ \mathrm{km}=-88\ \mathrm m.
$$

The release point stays on the new orbit and is now its apoapsis, so $r_a=6780$ km and $r_p=2(a+\delta a)-r_a=r_a+2\,\delta a$. The perigee therefore sits $2|\delta a|=177$ m below the station's orbit, half an orbit after release.

For the drift, differentiate Kepler's third law, $\tau=2\pi a^{3/2}\mu^{-1/2}$:

$$
\frac{d\tau}{da}=\frac32\cdot2\pi a^{1/2}\mu^{-1/2}=\frac32\frac{\tau}{a},
$$

$$
\delta\tau=\frac32\,\tau\,\frac{\delta a}{a}.
$$

With $\tau=5556$ s,

$$
\delta\tau=\frac32(5556)\frac{-0.0884}{6780}=-0.109\ \mathrm s.
$$

Each time the satellite returns to the release point it arrives 0.109 s earlier than the station, which is then $V|\delta\tau|=7.668\times0.109=0.833$ km behind it. So the satellite gains 833 m per orbit. Substituting $\delta a=2a\,\delta V/V$ into $V|\delta\tau|$ gives the compact form

$$
V|\delta\tau|=V\cdot\frac32\tau\cdot\frac{2|\delta V|}{V}=3\,|\delta V|\,\tau,
$$

and $3(5\times10^{-5})(5556)=0.833$ km.

> [!check] Exact against linearised
> Solving the energy equation exactly with the reduced speed $V+\delta V$ (here $\delta V=-0.05$ m/s) gives $\delta a=-88.4$ m and $\delta\tau=-0.1087$ s, the same to three figures, so the small-change form is safe for any burn much smaller than the orbital speed. The relative-motion figure above shows the same 177 m and 833 m.

## Worked examples

Constants: $R_E=6378$ km and $\mu=398\,600\ \mathrm{km^3/s^2}$.

### 200 km parking orbit to GEO

The task is to find the ΔV and transfer time from a circular 200 km parking orbit to GEO ($r_{GEO}=42\,164$ km), and to estimate the propellant for the second burn if $V_{ex}=2.5$ km/s (Chapter 5 worked example, 2020 Lecture 13).

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

Rounded components give 1.478 and 3.933 km/s, the values on the slides. The transfer time is half the transfer orbit's period:

$$
\frac{a_T^3}{\mu}=\frac{24\,371^3}{398\,600}=3.631\times10^7\ \mathrm{s^2},
$$

$$
t_T=\pi\sqrt{3.631\times10^7}=\pi\times6026=18\,930\ \mathrm s=5.26\ \mathrm h.
$$

> [!check] Energy on each orbit
> The specific energies $-\mu/2a$ are $-30.30\ \mathrm{km^2/s^2}$ on the parking orbit, $-8.18$ on the transfer ellipse and $-4.73$ in GEO. Each prograde burn raises the energy, and the transfer ellipse sits between the two circles, as it must. Most of the energy gain comes from the first burn (22.1 against 3.5 $\mathrm{km^2/s^2}$), although its ΔV is under twice the second's, because a burn adds energy of about $V\,\delta V$ and the spacecraft is fastest at perigee.

For the second burn, write $x=m_0/m_f$:

$$
x=\exp\left(\frac{1.477}{2.5}\right)=1.806,
\qquad
\frac{m_p}{m_0}=1-\frac1x=0.446.
$$

About 45 % of the spacecraft's mass after the first burn is propellant for the circularisation alone. A 4000 kg spacecraft in GTO arrives in GEO at about 2200 kg (2020 Lecture 13, ll. 151–160).

> [!check] Plausibility of the second burn's propellant
> Real GEO communications satellites launched into GTO typically carry roughly half their launch mass as propellant, most of it for apogee raising, which matches this estimate.

### 400 km to GEO with the Excel tool

In the Hohmann spreadsheet, an original orbit of 6758 km (about 380 km up) and a target of 42 164 km are matched by adjusting the burns by hand until the final orbit agrees. The exact Hohmann values for that pair of radii are

$$
\Delta V_{Tp}=2.403\ \mathrm{km/s},\qquad\Delta V_{Ta}=1.459\ \mathrm{km/s},\qquad\Delta V=3.862\ \mathrm{km/s},
$$

with a transfer time of 5.29 h. Reading the sum off while the orbit is still being tuned gives about 3.7 km/s; the remaining "orbital error" shown by the tool goes to zero as the sum approaches 3.86 km/s. Raising the parking orbit from 200 to 380 km saves about 70 m/s.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]
- Next: [[SESA2024 11 - Payload and Orbit Selection]] (2025-12-04); the Hohmann make-up manoeuvre is applied in [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]
- Concepts: [[Hohmann Transfer]] · [[Vis-Viva Equation]] · [[Tsiolkovsky Rocket Equation]] (SESA2023)
- Propulsion: [[SESA2024 07 - Spacecraft Propulsion]] · [[SESA2023 Propulsion Hub]]

## Sources

- `Chapter 5_Hohman transfers_V2.pdf` and `Chapter 5_Hohman transfers worked example_V1.pdf` (Dr C. Ryan, after Prof H. Lewis)
- Transcript `SESA2024 Lecture 2025-12-02.txt`
- Prof Lewis's 2020 recordings: `SESA2024 Lecture 12.txt` (Hohmann visualisation activity) and `SESA2024 Lecture 13.txt` (the worked example)
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 5
- Figures: `ast_hohmann_leo_geo`, `ast_hohmann_dv_ratio` (`generate_ast_extra_figures.py`) and `ast_removedebris_relative_motion` (`generate_ast_ch5_transfer_figures.py`). All numbers recomputed in Python, including the exact (non-linearised) RemoveDebris orbit.

## Self-study tasks

### Core

- [ ] The worked example: ΔV, transfer time and second-burn propellant fraction from a 200 km parking orbit to GEO with $V_{ex}=2.5$ km/s ("please go have a look at that", 2025-12-02, ll. 705–715). Targets 3.93 km/s, 5.26 h, 45 %. → [[#200 km parking orbit to GEO]]
- [ ] RemoveDebris poll questions: which orbit after a backwards release, and where it goes relative to the ISS (ll. 133–395). → [[#SESA2024 05 - Orbital Transfers and the Hohmann Transfer|opening section]] · [[#4. How far a small burn moves the orbit]]
- [ ] 300 km equatorial orbit to GEO, with the staged masses (Workbook Ch5 Q7). Target 3.893 km/s, about 600 kg in GEO. → [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q7. From a 300 km equatorial orbit to GEO with staged masses|Workbook solution]]
- [ ] Express the Hohmann ΔV in terms of $x=r_1/r_2$ (Workbook Ch5 Q3). → [[#The ΔV in closed form]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q3. Hohmann total delta-V in terms of x = r1 over r2|Workbook solution]]

### Further practice

- [ ] The Hohmann visualisation activity: set a LEO original orbit and a GEO target in the Excel tool, and adjust $\Delta V_1$ and $\Delta V_2$ until the orbital error is near zero (2020 Lecture 12; 2025-12-02, ll. 750–880). → [[#400 km to GEO with the Excel tool]]
- [ ] Advantages and disadvantages of the Hohmann transfer for interplanetary missions (Workbook Ch5 Q6). → [[#3. Where the Hohmann transfer is used, and its limits]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q6. Hohmann transfer for interplanetary missions|Workbook solution]]
- [ ] Comet intercept by a heliocentric Hohmann transfer (Workbook Ch5 Q8). → [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q8. Comet intercept by heliocentric Hohmann transfer|Workbook solution]]
- [ ] Explain why the burns are placed at the apses (2025-12-02, ll. 485–520). → [[#1. Assumptions for orbital transfers]]

## Transcript and slide slips

> [!warning] Transcript slips (2025-12-02, ll. 60–70 and 125–135)
> Where: [[#SESA2024 05 - Orbital Transfers and the Hohmann Transfer]].
>
> RemoveDebris is described as a "large CubeSat" about 30 cm across. It was a microsatellite of about 100 kg, built to CubeSat-style standards but much larger, and it carried two CubeSats of its own as targets. The ISS is again given an orbital period of "about 45 minutes"; it is about 92 minutes.

> [!warning] Transcript slip (2025-12-02, ll. 815–835)
> Where: [[#400 km to GEO with the Excel tool]].
>
> The class was asked for the altitude of a "geostationary transfer orbit" and the answer given was 36 000 km. That is the altitude of the geostationary orbit itself. The transfer orbit (GTO) is the ellipse between the parking orbit and GEO, with its perigee at a few hundred kilometres and its apogee at GEO height.
