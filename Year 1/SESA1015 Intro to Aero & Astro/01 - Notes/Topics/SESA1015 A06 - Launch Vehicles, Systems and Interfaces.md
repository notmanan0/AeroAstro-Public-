---
title: "SESA1015 A06 - Launch Vehicles, Systems and Interfaces"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 18
tags:
  - sesa1015
  - astronautics
  - launch-vehicle
  - interfaces
aliases: ["SESA1015 Astronautics 6", "Launch Systems and Interfaces"]
date: 2026-09-27
status: lectured
coverage: "Astronautics Part 3 (Launch Vehicles) pp. 28–56: the typical launch system fairing and its interfaces, impacts of launcher selection on the spacecraft, launch system characteristics (Ariane 5, Space Shuttle, Delta II, Titan III, Atlas V, Proton, Energia, Soyuz, Pegasus, Falcon 9, Falcon Heavy), air launch, reusable vehicles, single stage to orbit and Skylon. Earth-rotation benefit of the launch site, GTO penalty and propellant families added as background."
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 A05 - Staging and Payload Fraction]]"]
next_topics: []
key_concepts: ["[[Launch Vehicle Interfaces]]", "[[Multistage Rocket Performance]]", "[[Space Mission Architecture]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf (pp. 28–58)"]
---

# SESA1015 A06 - Launch Vehicles, Systems and Interfaces

> [!abstract] Summary
> The launch vehicle, the spacecraft and the ground facilities form one system, joined by mechanical, electrical and environmental interfaces. The payload fairing is the most visible interface: the spacecraft must fit inside its usable diameter and dynamic envelope, accept its air conditioning and access arrangements, and survive aeroheating and electromagnetic interference. Choosing the launcher is the main input to spacecraft structural design and sets the spacecraft's mass, volume, stowed shape, centre-of-mass position and deployment mechanisms. Launchers are compared by payload to LEO, polar LEO and GTO and by fairing size, and development is moving towards reuse, air launch and air-breathing propulsion.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks how a spacecraft is accommodated on a launcher, what the fairing interfaces are, how launcher choice constrains the spacecraft, or how launchers compare.
> - **Assumptions:** payload figures are approximate and conditional on the orbit (LEO, polar LEO, GTO), the launch site and, for reusable vehicles, whether the booster is recovered.
> - **Method:** 1. Fix the target orbit and the spacecraft mass. 2. Shortlist launchers from the payload column for that orbit. 3. Check the spacecraft fits the usable diameter and length in its stowed configuration. 4. Check the centre-of-mass position and the launch loads ([[SESA1015 A03 - Launch Environment|A03]]). 5. Close the launch-site mechanical, electrical and air-conditioning interfaces.
> - **Common mistakes:** quoting a LEO payload for a GTO or polar mission; comparing the spacecraft with the outer fairing diameter instead of the usable diameter.
> - **Practise:** [[#Centre of mass and interface bending moment]] · [[#Why GTO and polar payloads are smaller]]

A spacecraft spends minutes on its launcher and years in orbit, yet the launch usually decides more of its structural design than the orbit does. It has to fit inside a fairing a few metres across, be bolted to an adapter that carries all its loads, sit with its centre of mass close enough to that adapter to keep the bending moments acceptable, and survive the noise, vibration and acceleration of the climb with its solar arrays and antennas folded away. Once in orbit it has to unfold them, so its deployment mechanisms are designed around the stowed configuration the launcher allows.

The launcher in turn is part of a larger system. The spacecraft is prepared, checked out, fuelled and kept clean and cool at the launch site; the launcher supplies power and data links to it until lift-off; and the fairing and adapter are the physical boundary between the two. Each boundary is an interface, defined by an agreement on what crosses it: loads, signals, air, heat.

Different launchers offer different combinations of payload, orbit and fairing size. Heavy expendable launchers such as Ariane 5 and Atlas V cover most commercial and scientific missions, small air-launched rockets serve small satellites, and reusable boosters have changed the cost of reaching orbit since 2015.

---

## 1. The launch system: vehicle, payload and ground

Three elements make up a launch: the spacecraft (the payload), the launch vehicle, and the ground segment at the launch site. Each pair is joined by interfaces.

![[astro_a06_system_interfaces.png|900]]

Between the spacecraft and the launch vehicle the interface is mechanical (the adapter and separation system that carry the loads and release the spacecraft, and the fairing that encloses it) and electrical (signals passed through the vehicle before lift-off, separation commands, and electromagnetic compatibility). Between the launch vehicle and the ground it covers propellant loading, the launch-site mechanical and electrical interface at the pad, and the countdown. Between the spacecraft and the ground it covers transport, integration, checkout and battery charging, and cleanliness. The fairing sits at the centre of all three.

## 2. The payload fairing and its interfaces

The typical launch system fairing (Part 3, p. 28) is a streamlined shroud, split into halves that are jettisoned once the vehicle is high enough for aerodynamic heating and pressure to no longer matter, usually above about 100 km.

![[astro_a06_fairing_interface.png|900]]

Each feature is an interface the spacecraft designer has to satisfy:

- The **fairing diameter** is the outside size of the shroud; the **usable diameter** inside it is smaller, because the fairing structure, acoustic blankets and clearance for the fairing's own deflection take up space.
- The **dynamic envelope** (dashed) is the volume the spacecraft may occupy, including its own vibration and deflection under launch loads. A spacecraft that fits the static space but swings outside the dynamic envelope could strike the fairing.
- **Air conditioning** blows filtered, temperature- and humidity-controlled air through the fairing on the pad, keeping the spacecraft clean and cool until lift-off.
- **Access panels** (doors) allow late access to the spacecraft on the pad, for example to remove protective covers or arm devices.
- The **launch-site mechanical and electrical interface** is where umbilical connections reach the spacecraft through the vehicle before lift-off.
- **Electromagnetic interference** between the launcher's systems, the range radars and the spacecraft must be kept within agreed limits; the spacecraft is usually switched off or in a quiet mode during ascent.
- **Aeroheating** of the nose during the atmospheric part of the climb heats the fairing, which shields the spacecraft from it.
- The **booster adapter** at the base joins the spacecraft (or its own adapter cone) to the launcher's upper stage and carries all its loads.

For the acoustic, vibration and shock loads inside the fairing, see [[SESA1015 A03 - Launch Environment]].

## 3. Impacts of launcher selection on the spacecraft

Launcher selection (Part 3, p. 29) is the main input to spacecraft structural design, because the launch loads are usually the largest the structure will see. It has a major impact on:

- the spacecraft mass, which must not exceed the launcher's capacity to the target orbit;
- the spacecraft volume, set by the usable diameter and length of the fairing;
- the stowed configuration, the folded shape in which solar arrays, antennas and booms ride inside the fairing;
- the mass distribution, through a constraint on the centre-of-mass position;

and it is an input to the design of the spacecraft's deployment mechanisms, which must unfold everything that was stowed to fit.

### Centre of mass and interface bending moment

The centre-of-mass constraint follows from statics. Treat the spacecraft as a rigid body of mass $m$ with its centre of mass a height $h$ above the separation plane, and let the launcher impose a quasi-static lateral acceleration of $n_{lat}$ times $g$. The inertia force $m\,n_{lat}\,g$ acts at the centre of mass, so the moment it produces about the separation plane, which the adapter must react, is

$$
M_{int}=m\,n_{lat}\,g\,h .
$$

The moment is proportional to $h$, so the launcher's user's guide limits $h$ (and the lateral offset of the centre of mass from the axis) for a given mass. For a 2000 kg spacecraft with $h=1.5$ m and an assumed $n_{lat}=1.5$,

$$
M_{int}=2000\times1.5\times9.807\times1.5=44.1\ \mathrm{kN\,m}.
$$

Raising the centre of mass to 2.0 m raises this to 58.8 kN m; the spacecraft designer keeps heavy items (propellant tanks, batteries) low and central. Axial loads follow the same way from the axial acceleration, which peaks at stage burnout (about $4g_0$ for Ariane 5, Part 2, p. 39).

## 4. Launch system characteristics

### Launch vehicle characteristics table

Approximate payload into three reference orbits and the fairing size compare as follows (Part 3, p. 46, with Falcon 9 and Falcon Heavy from pp. 48 and 50):

| Launcher | LEO (kg) | LEO polar (kg) | GTO (kg) | Fairing diam. (m) | Fairing length (m) |
|---|---|---|---|---|---|
| Ariane 5 G (generic) | 21,000 | 9,500 | 6,600 | 4.6 | ~8.5 to ~13.0 |
| Ariane 5 ECA (evolution) | 21,000 | 9,500 | 10,000 | 4.6 | ~8.5 to ~13.0 |
| Shuttle | 24,400 | — | 5,900 | 4.5 | 18.0 |
| Delta II | 5,000 | 3,000 | 2,000 | 2.5 | 4.8 |
| Titan III | 11,000 | — | 5,000 | 3.6 | 12.4 |
| Atlas V | 20,500 | 17,300 | 8,700 | 4.2 | 12.2 |
| Proton | 20,000 | — | 5,500 | 3.3 | 7.5 |
| Energia | 90,000 | 72,000 | — | 5.5 | 37 |
| Soyuz | 4,850 | 4,400 | 3,250 | 3.7 | 6.5 |
| Pegasus (air launched) | 455 | 265 | 125 | 1.2 | 1.9 |
| Falcon 9 | 22,800 | — | 8,300 | 4.6 | ~6.6 to ~11.4 |
| Falcon Heavy | 63,800 | — | 26,700 | — | — |

![[astro_a06_payload_capability.png|850]]

The launcher families are:

- **Ariane 5** (Europe, launched from Kourou): a cryogenic core stage with two large solid boosters strapped on; the ECA version's improved cryogenic upper stage raises the GTO payload from 6.6 to 10 t with the same LEO figure.
- **Space Shuttle** (USA): a partly reusable system of a winged orbiter with three hydrogen–oxygen engines, an expendable external tank and two recovered solid boosters. The orbiter itself only reached LEO; its GTO figure needs an extra upper stage carried in the payload bay. Its 18 m payload bay is by far the longest volume in the table.
- **US expendable launch vehicles** (ELVs): Delta II, Titan III and Atlas V, each a liquid core with optional solid strap-ons.
- **Russian ELVs**: Proton (storable propellants, a heavy GTO launcher), Energia (a 90 t to LEO heavy lifter, built for the Buran orbiter), and Soyuz (four strap-on boosters around a core, in service since the 1960s and the crew launcher to the ISS).
- **Air launch**: Pegasus, a three-stage solid rocket dropped from a Lockheed L-1011 TriStar aircraft.
- **SpaceX**: Falcon 9 and Falcon Heavy (three Falcon 9 first stages side by side), whose first stages land and are flown again.

The propellant families named here (cryogenic hydrogen–oxygen, kerosene–oxygen, storable and solid) are described in [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]].

### Why GTO and polar payloads are smaller

Every launcher in the table delivers much less to GTO than to LEO, and less to polar LEO than to LEO. Both follow from the rocket equation of [[SESA1015 A04 - Rocket Equation and Launch Performance|A04]] (background derivation using the vis-viva equation, [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation|SESA2024]]).

A geostationary transfer orbit has its perigee in LEO, say $r_p=6578$ km, and its apogee at geostationary radius, $r_a=42\,164$ km (Part 1, p. 10), so its semi-major axis is

$$
a=\frac{r_p+r_a}{2}=\frac{6578+42\,164}{2}=24\,371\ \mathrm{km}.
$$

The vis-viva equation $V^2=\mu\left(\frac2r-\frac1a\right)$ at perigee gives

$$
V_p=\sqrt{3.986\times10^{5}\left(\frac{2}{6578}-\frac{1}{24\,371}\right)}=10.24\ \mathrm{km/s},
$$

against 7.78 km/s for the circular orbit at the same radius. GTO needs about 2.45 km/s more. For an upper stage with $V_{ex}=4.4$ km/s that extra burn needs a mass ratio of $e^{2.45/4.4}=1.75$, so at most $1/1.75=57$ % of the mass that could be placed in LEO arrives in GTO, and less once the extra stage structure is counted. The table's GTO/LEO ratios of 0.3–0.5 for most vehicles reflect this.

A polar orbit cannot use the Earth's rotation. A point on the equator moves eastwards at $\omega R_E=7.292\times10^{-5}\times6378=0.465$ km/s, and a site at latitude $\phi$ at $0.465\cos\phi$ km/s:

| Launch site | Latitude | Eastward speed (km/s) |
|---|---|---|
| Kourou | 5.2° N | 0.463 |
| Cape Canaveral | 28.5° N | 0.409 |
| Baikonur | 45.6° N | 0.325 |

An eastward launch starts with this speed already in hand; a polar launch heads north or south and gains nothing from it (and must cancel it to reach an exactly polar orbit). This is why sites are placed near the equator with open sea or empty land to the east, and why the polar column is smaller.

## 5. Reusable launch vehicles

The Space Shuttle was the first partly reusable launcher (Part 3, pp. 32–34). Falcon 9 (p. 48) recovers its first stage by landing it on a pad or ship; by 11 September 2020 it had made 92 launches, 53 landings and 38 flights of previously flown rockets, and Falcon Heavy (p. 50) 3 launches, 7 landings and 4 reflights. The quoted capabilities (22,800 kg to LEO, 8,300 kg to GTO) are the manufacturer's figures for the expendable configuration; typical payloads in the Falcon 9 class are below 6,800 kg. Landing a stage needs propellant held back for the return burns and extra hardware (legs, grid fins), all of which is mass that could otherwise be payload: the rocket equation charges for reuse in payload, and the saving comes in cost per launch instead.

Second-generation reusable vehicles include the X-37 (p. 53), a small uncrewed winged orbiter, and the X-34 (p. 55), an air-launched reusable technology demonstrator.

## 6. Air launch

Pegasus (Part 3, p. 45) is carried to altitude under a TriStar and dropped before its first stage ignites. Starting high and moving has three advantages. The rocket begins above the densest air, so drag loss and aerodynamic loads are smaller; its first-stage nozzle can be designed for low ambient pressure, which raises the effective exhaust velocity; and the aircraft can fly to the best latitude and launch azimuth, so it is not tied to a fixed site. The aircraft's own speed, about 0.25 km/s, is a small part of the 8.75 km/s budget. The limit is the aircraft's carrying capacity, which keeps the payload small: 455 kg to LEO.

Two later air-launch systems (p. 51) are Virgin Orbit's LauncherOne, carried by a Boeing 747 (about 500 kg to sun-synchronous orbit; its maiden flight on 25 May 2020 failed), and Stratolaunch (6,000–8,000 kg to LEO), whose carrier aircraft is the largest by wingspan ever to fly (p. 52).

## 7. Single stage to orbit and air-breathing launchers

[[SESA1015 A04 - Rocket Equation and Launch Performance#9. Single stage to orbit|Single stage to orbit]] needs a very light structure and a high exhaust velocity. Statistics from the first stage of Ariane 1 (Part 3, p. 54) show where the propellant goes on a conventional launcher:

- the stage carries 120 t of propellant, 55 % of the rocket's initial mass, so the lift-off mass was about $120/0.55=218$ t;
- it accelerates the vehicle to 1.5 km/s, about 20 % of orbital velocity ($1.5/7.8=19$ %), at about 30 km altitude;
- two-thirds of that propellant by mass, 80 t, is oxidiser, all burnt inside the atmosphere, which already contains oxygen.

Carrying 80 t of oxygen through air suggests breathing the air instead. Reaction Engines' Skylon concept (p. 56, following the earlier HOTOL project) uses the SABRE engine, which combines rocket and gas-turbine technology. It runs in an air-breathing mode up to Mach 5.5 and then switches to rocket mode, using on-board oxygen, to reach orbital velocity. At about 26 km altitude, where the ISA temperature is about 223 K and the speed of sound $\sqrt{1.4\times287\times222.7}=299$ m/s, Mach 5.5 is about 1.65 km/s, roughly 21 % of orbital velocity, similar to the Ariane 1 first stage but without carrying that stage's oxidiser. The concept remains theoretical: the heat exchangers, structure and integration have not yet flown.

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]]
- Previous: [[SESA1015 A05 - Staging and Payload Fraction]] · Earlier: [[SESA1015 A04 - Rocket Equation and Launch Performance]] · Launch loads: [[SESA1015 A03 - Launch Environment]] · Mission context: [[SESA1015 A01 - Astronautics Foundations, Missions and Applications]]
- Concepts: [[Launch Vehicle Interfaces]] · [[Multistage Rocket Performance]] · [[Launch Environment Loads]] · [[Space Mission Architecture]]
- Later in the degree: [[SESA2024 01 - Systems Engineering and Spacecraft Design]] (interface control and budgets) · [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] and [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]] (transfer orbits after injection) · [[SESA2024 11 - Payload and Orbit Selection]] · [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]] (engine cycles of the vehicles here).

## Sources

- Astronautics Part 3, Launch Vehicles: p. 28 (typical launch system fairing), p. 29 (impacts of launcher selection), pp. 30–46 (Ariane 5, Space Shuttle, Delta II, Titan III, Atlas V, Proton, Energia, Soyuz, Pegasus and the characteristics table), pp. 47–50 (Falcon 9, Falcon Heavy), pp. 51–52 (future air-launch systems), pp. 53–56 (X-37, single stage to orbit with Ariane 1 statistics, X-34, Skylon), p. 57 (summary), p. 58 (reading: Fortescue, Stark and Swinerd, Chapter 7; *How Spacecraft Fly*, Chapter 5).
- Astronautics Part 1, Introduction: p. 10 (GEO radius 42,164 km). Astronautics Part 2, Environment: p. 39 (static accelerations).
- Background beyond the deck: the vehicle descriptions (propellants, strap-ons, recovery), the interface bending moment, the GTO and Earth-rotation calculations and the SABRE Mach-number estimate.
- Figures: `01 - Notes/Figures/generate_astro_a06_figures.py`.

## Self-study tasks

There are no exercises set in the Part 3 deck; the tasks below rework the slide material, plus three suggested problems.

### Core

- [ ] Sketch the typical launch system fairing and explain each labelled feature (Part 3, p. 28). → [[#2. The payload fairing and its interfaces]]
- [ ] List the impacts of launcher selection on the spacecraft and explain why each arises (Part 3, p. 29). → [[#3. Impacts of launcher selection on the spacecraft]]
- [ ] From the characteristics table, choose launchers for a 4 t GTO satellite and a 3 t polar Earth-observation satellite, and say what else must be checked (Part 3, p. 46). → [[#Launch vehicle characteristics table]]

### Further practice

- [ ] Suggested, not lecturer-set: find the interface bending moment for a 2000 kg spacecraft with its centre of mass 1.5 m above the separation plane under a 1.5 g lateral load. → [[#Centre of mass and interface bending moment]]
- [ ] Suggested, not lecturer-set: compute the extra $\Delta V$ from a 200 km LEO to GTO and the mass ratio it needs at $V_{ex}=4.4$ km/s. → [[#Why GTO and polar payloads are smaller]]
- [ ] Suggested, not lecturer-set: use the Ariane 1 statistics to find the lift-off mass and the oxidiser burnt in the atmosphere, and estimate the speed at SABRE's switch to rocket mode. → [[#7. Single stage to orbit and air-breathing launchers]]

## Transcript and slide slips

> [!warning] Slide slip (Part 3, pp. 48 and 50)
> Where: [[#Launch vehicle characteristics table]].
>
> The Falcon 9 fairing length is given as "~6.6 to ~11.4" m on p. 48 and "~6.7 to ~11" m on p. 50. The figures are approximate either way; the table above uses p. 48.
