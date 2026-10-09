---
title: "SESA2024 15 - Space Sustainability, Debris and NewSpace"
module: "SESA2024 Astronautics"
type: topic
stream: "Space Sustainability and Commercialisation"
order: 15
tags:
  - sesa2024
  - space-debris
  - sustainability
  - newspace
  - sbsp
aliases: ["Space debris", "Space sustainability", "Industrialisation of space", "SBSP"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]", "[[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]"]
next_topics: []
key_concepts: ["[[Space Debris Mitigation]]", "[[Orbit Control Cycle]]"]
tutorial_sheets: []
sources: ["02 - Sources/Lectures/SESA2024_Space Sustainability_Debris_SBSP_2025_26.pdf", "02 - Sources/Lectures/SESA2024_Space_Industrialization_2025_26.pdf"]
---

# SESA2024 15 - Space Sustainability, Debris and NewSpace

> [!abstract] Summary
> Two guest lectures (N. Vaidya):
> 1. **Sustainability and debris.** Satellites help with global challenges (UN SDGs, disaster response), but the growing debris population threatens the orbital environment. Mitigation follows the IADC and UN guidelines, including post-mission disposal (25 years, now **5 years** under the FCC). Disposal lowers the perigee, and drag does the rest. Remediation (active debris removal) is also needed. Space-based solar power is a sustainability opportunity.
> 2. **NewSpace.** Launch costs fell, small satellites spread, and investment grew. EO trades **spatial, spectral and temporal** resolution; comms trades **coverage, latency and bandwidth**.
>
> Examined qualitatively, and through the orbital mechanics of fragments and disposal burns (2021/22 A6, 2022/23 A6).

## Key Concepts
- [[Space Debris Mitigation]] · [[Orbit Control Cycle]] (drag)

---

## 1. Space for global challenges
- Satellites support: natural hazards and disasters (Hurricane Milton imaged from the ISS); UN global issues and **interconnected disaster risks** (2023 report); the **17 UN Sustainable Development Goals** with 169 targets (the 2030 Agenda).
- **Space4SDGs** (UNOOSA): EO for disaster response (rapid revisit, e.g. Planet), carbon and GHG monitoring (thermally leaky buildings), agriculture, water.
- Previous SESA2024 coursework concepts included multispectral, wildfire (Blaze), resource and storm-watch missions.
- *"Risks to space sustainability are also business risks"* (Secure World Foundation). There have been calls for an **18th SDG** covering space itself.

**Sustainability** (Brundtland, 1987): *meeting the needs of the present without compromising the ability of future generations to meet their own needs.* It has three pillars: economy, environment, society.

**Long-term sustainability of outer space activities** (UN COPUOS): maintaining space activities indefinitely, with equitable access to the benefits for peaceful purposes, while preserving the space environment for future generations. This includes in-situ resource utilisation (ISRU) and space mining.

## 2. Space debris
**IADC definition**: *all human-made objects, including fragments and elements thereof, in Earth orbit or re-entering the atmosphere, that are non-functional.*

**Sources**:
- fragmentation (explosions of stages and batteries, collisions, ASAT tests);
- mission-related objects;
- dead satellites and rocket bodies;
- solid-motor slag;
- paint flakes.

The breakup-event history (NASA ODQN) shows most catalogued fragments come from a few large events at 700–1000 km.

**Population (ESA, 2024)**:

| Size | Number |
|---|---|
| Tracked / catalogued | ~36 500 |
| > 1 cm | ~1 000 000 |
| > 1 mm | ~130 000 000 |
| Total mass in orbit | ~12 400 t |

The number of active satellites has grown steeply since 2019, driven by the Starlink and OneWeb mega-constellations.

### Why a fragment cloud spreads along the orbit (2021/22 A6, 5 marks)
- Each fragment receives a different ΔV at the same point. Its new orbit passes through the explosion point but has a **different $a$, and therefore a different period** (Kepler 3).
- Fragments pushed forward have longer periods and fall behind. Those pushed back have shorter periods and move ahead.
- The differential period makes the cloud **shear along-track**. Within a few orbits it becomes a ring around the original orbit.
- Different along-track ΔVs give different $e$, which spreads the altitudes. (Differential nodal precession later spreads the planes too.)

> [!example] Gabbard-diagram reasoning (2022/23 A6)
> Parent S: 570 km circular, $\tau$ = 96 min.
> - **A** (ΔV forward): perigee stays at 570 km; apogee rises; **$\tau$ > 96 min**. Plot it up and to the right.
> - **B** (ΔV backward): apogee stays at 570 km; perigee drops; **$\tau$ < 96 min**. Plot it at the same apogee (570 km), to the left.

## 3. Mitigation guidelines
**IADC (2007, updated 2021): four fundamental measures**
1. Limit debris released during normal operations.
2. Minimise the potential for on-orbit break-ups (passivation: vent tanks, discharge batteries).
3. **Post-mission disposal.**
4. Prevent on-orbit collisions.

**UN guidelines (seven)**:
1. limit debris released during normal operations;
2. minimise break-ups during operations;
3. limit the probability of accidental collision;
4. avoid intentional destruction and other harmful activities;
5. minimise post-mission break-ups from stored energy;
6. limit long-term presence in **LEO** after end of mission;
7. limit long-term interference with the **GEO** region after end of mission (re-orbit to a graveyard orbit about 300 km above GEO).

**FCC "5-year rule"**: proposed on 8 September and adopted on 29 September 2022. It shortens the 25-year post-mission deorbit guideline to **5 years** for FCC-licensed LEO satellites.

### Implementing disposal
- Transfer to an orbit whose **residual natural lifetime is less than 25 (or 5) years**.
- The **lowest-ΔV** way is a single retrograde burn at the current altitude (which becomes apogee) that **lowers the perigee**. The apogee stays at the original altitude, and drag at the low perigee shrinks $a$ and $e$ each orbit until re-entry.

$$
\Delta V = V_0-V_a = \sqrt{\frac{\mu}{r_0}}-\sqrt{\mu\Big(\frac{2}{r_0}-\frac{2}{r_0+r_p}\Big)}
$$

- Chemical propulsion does this impulsively. Electric propulsion spirals down and costs more ΔV. A **drag sail** can replace propulsion at low altitude (2019/20 B3).
- Apollo 9 did the same thing: lowering its perigee prepared for the de-orbit (2021/22 B1).

## 4. Remediation
Even with good compliance, models show the LEO population **keeps growing** from collisions (the Kessler syndrome), so **active debris removal (ADR)** is needed:
- UK COSMIC (ADR of dead satellites);
- **Astroscale ELSA-M** (end-of-life servicing, multi-client);
- **ClearSpace**;
- **RemoveDebris** (Surrey): net and harpoon demonstration, deployed from the ISS. See the quiz in [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]].

## 5. Space-based solar power (SBSP)
- The largest renewable source: the Sun releases more energy every 1.5 µs than humanity uses in a year. Space gets **more than 10× the energy** of a ground array, with no night or weather.
- History: Asimov's *Reason* (1941), Glaser's concept (1968, patented 1974), then many feasibility studies. Today: **ESA SOLARIS**, Caltech SSPP, Aetherflux (LEO, lasers).
- **Modular GEO architecture**: tile (10 × 10 cm, 1–2 W) → strip (2 × 60 m) → module (60 × 60 m) → system (about 3 × 3 km, about 10 km²) giving **1–3 GW**, with about 1 kW/m² peak ground power density.
- Photovoltaic targets: **efficiency > 30 %**, **specific power 2–10 kW/kg** (ultralight, integrated PV plus microwave transmission).

## 6. NewSpace and the industrialisation of space
**Drivers**:
- the shift from government to private industry;
- **reusable rockets and falling launch cost per kg**;
- miniaturised, mass-produced **small satellites** (CubeSats cost about $20k–100k; smallsats $1–35M; a traditional satellite $250–400M);
- mega-constellations;
- in-orbit servicing (refuelling, repair, debris removal);
- space manufacturing (**Space Forge**: microgravity as a service);
- lunar and asteroid mining;
- AI and data-driven operations;
- regulation and space traffic management;
- growing investment (Seraphim; about $1 trillion space economy projected).

**EO mission drivers**: the classic trade between **spatial** (fine or coarse), **spectral** (many or few bands) and **temporal** (rapid or slow revisit) resolution.
- Satellogic, for example, uses constellations to buy temporal resolution while keeping good spatial resolution.
- Business opportunities map onto resolution against revisit time.

**Comms mission drivers**: **coverage** against **latency** against **bandwidth**.
- LEO (about 600 km): about 20–40 ms latency, small footprint, needs a constellation.
- GEO (36 000 km): 450–750 ms latency, one satellite covers about a third of the Earth.

Unusual concepts: Reflect Orbital ("sunlight on demand" via orbital mirrors), Aetherflux.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]
- Orbital mechanics used here: [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]], [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]

## Sources
- "Space Sustainability, Space Debris and Space Based Solar Power" and "The New Space Era and industrialisation of space" (N. Vaidya, 2025-26), with material from H. Lewis; ESA Space Environment Report 2024
