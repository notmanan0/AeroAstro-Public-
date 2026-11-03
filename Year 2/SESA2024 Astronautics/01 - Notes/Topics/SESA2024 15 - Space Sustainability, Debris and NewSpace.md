---
title: "SESA2024 15 - Space Sustainability, Debris and NewSpace"
module: "SESA2024 Astronautics"
type: topic
stream: "Space Sustainability and Commercialisation"
order: 15
tags: [sesa2024, space-debris, sustainability, newspace, sbsp]
aliases: ["Space debris", "Space sustainability", "Industrialisation of space", "SBSP", "NewSpace"]
date: 2026-10-30
status: lectured
coverage: "Weeks 5–6 (Dr N. Vaidya). No recording of these lectures is in the vault, so this note is written from the two slide decks; the Planet Labs guest lecture she arranged is used in note 01."
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]", "[[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]"]
next_topics: []
key_concepts: ["[[Space Debris Mitigation]]", "[[Agile Aerospace]]", "[[Orbit Control Cycle]]"]
tutorial_sheets: []
sources: ["02 - Sources/Lectures/SESA2024_Space Sustainability_Debris_SBSP_2025_26.pdf", "02 - Sources/Lectures/SESA2024_Space_Industrialization_2025_26.pdf"]
---

# SESA2024 15 - Space Sustainability, Debris and NewSpace

> [!abstract] Summary
> Satellites help address global challenges, from disaster response to greenhouse-gas monitoring, but the debris they leave threatens the orbital environment that makes them possible. Mitigation follows the IADC and UN guidelines, above all post-mission disposal (25 years, now 5 years for FCC-licensed LEO satellites), usually by a retrograde burn that lowers the perigee so drag finishes the job; models show remediation by active debris removal is needed as well. The second lecture covers NewSpace: cheaper launch, mass-produced small satellites and constellations, and the trades between spatial, spectral and temporal resolution in Earth observation and between coverage, latency and bandwidth in communications.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks about debris sources, mitigation guidelines, disposal, how a fragment cloud evolves, space-based solar power or NewSpace trade-offs.
> - **Assumptions:** for the orbital-mechanics parts, impulsive burns and two-body motion, with drag only at the end.
> - **Method:** 1. Fragments: each gets a different ΔV at the same point, so a different $a$ and period; the cloud shears along the orbit. 2. Forward ΔV raises the far side and lengthens the period; backward lowers it and shortens the period. 3. Disposal: one retrograde burn at the current radius (which becomes apogee), $\Delta V=\sqrt{\mu/r_0}-\sqrt{\mu(2/r_0-2/(r_0+r_p))}$. 4. Cite the IADC four measures or UN seven guidelines. 5. For NewSpace, name the resolution or coverage trade.
> - **Common mistakes:** saying a fragment pushed forward moves ahead (it falls behind, having a longer period); quoting 25 years without the FCC 5-year rule.
> - **Practise:** [[#A disposal burn from 800 km]] · [[#Fragments from a 570 km break-up (2022/23 A6)]]

> [!note] Coverage
> Dr Vaidya's two lectures (in place of week 6 material; the 2025-10-30 lecture ends "next week you're going to talk about ... commercialisation") were not recorded in the vault. The content below follows her two slide decks, and the line references elsewhere in the module do not apply here.

Space is now essential infrastructure: navigation, communications, weather and Earth observation underpin a great deal of life on the ground, and the UK sector alone employs more than 52 000 people ([[SESA2024 01 - Systems Engineering and Spacecraft Design|module introduction]]). The orbits that host it are a shared and finite resource, and debris is the pollution that could close them. These two lectures set the technical material of the module in that context.

## 1. Space for global challenges

Satellites support the response to natural hazards (the slides show Hurricane Milton imaged from the ISS), the UN's work on interconnected disaster risks, and the 17 UN Sustainable Development Goals with their 169 targets. UNOOSA's Space4SDGs initiative maps Earth observation onto them: rapid-revisit imaging for disasters (Planet's constellation, [[SESA2024 01 - Systems Engineering and Spacecraft Design#8. A different route: agile aerospace (Planet)|note 01 §8]]), carbon and greenhouse-gas monitoring, agriculture and water. Past SESA2024 coursework concepts included wildfire, resource and storm-watch missions.

The Brundtland definition of sustainability (1987) is "meeting the needs of the present without compromising the ability of future generations to meet their own needs", with economic, environmental and social pillars. UN COPUOS applies it to space: the long-term sustainability of outer space activities means maintaining them indefinitely, with equitable access to their benefits for peaceful purposes, while preserving the space environment for future generations; that now has to include in-situ resource use and space mining. The Secure World Foundation's point, quoted on the slides, is that "risks to space sustainability are also business risks", and some have called for an 18th SDG covering space itself.

## 2. Space debris

The IADC defines space debris as "all human-made objects, including fragments and elements thereof, in Earth orbit or re-entering the atmosphere, that are non-functional." The sources are fragmentation (explosions of stages and batteries, collisions, anti-satellite tests), mission-related objects, dead satellites and rocket bodies, slag from solid motors, and paint flakes. NASA's break-up history shows that most catalogued fragments come from a few large events at 700–1000 km.

The ESA 2024 environment report puts the population at about 36 500 tracked objects, about a million larger than 1 cm, about 130 million larger than 1 mm, and some 12 400 t of material in orbit. The number of active satellites has risen steeply since 2019 with the Starlink and OneWeb constellations. At orbital speeds, even a centimetre-sized fragment can disable a spacecraft.

### How a fragment cloud spreads

When an object breaks up, every fragment starts from the same point but with a slightly different velocity (2021/22 A6, 5 marks). Each fragment's new orbit passes through the break-up point, as an impulsive change always does ([[SESA2024 05 - Orbital Transfers and the Hohmann Transfer|note 05]]), but has a different semi-major axis and so, by Kepler's third law, a different period. A fragment pushed forwards gains energy, its orbit grows, its period lengthens and it falls behind; one pushed backwards drops into a smaller, faster orbit and moves ahead, just like RemoveDebris leaving the ISS. Within a few orbits the cloud shears into a ring along the original orbit. Different along-track pushes also give different eccentricities, spreading the cloud in altitude, and over longer times differential nodal regression spreads the orbit planes.

A Gabbard diagram plots each fragment's apogee and perigee heights against its period, which makes this pattern easy to see (2022/23 A6).

## 3. Mitigation

The IADC guidelines (2007, updated 2021) rest on four measures: limit debris released in normal operations; minimise the potential for break-ups, by passivating spent stages and satellites (venting tanks, discharging batteries); dispose of spacecraft after the mission; and prevent collisions in orbit. The UN guidelines set out seven: limit debris released in normal operations; minimise break-ups during operations; limit the probability of accidental collision; avoid intentional destruction and other harmful activities; minimise post-mission break-ups from stored energy; limit long-term presence in LEO after the mission; and limit long-term interference with the GEO region, by moving GEO satellites into a graveyard orbit about 300 km above it.

The long-standing guideline was disposal within 25 years of the end of the mission. On 29 September 2022 the US Federal Communications Commission adopted a 5-year rule for the satellites it licenses in LEO.

### Implementing disposal

The usual method is to transfer to an orbit whose remaining natural lifetime is within the limit. The cheapest way is a single retrograde burn at the current altitude, which becomes the apogee of an ellipse with a lower perigee. Drag at the low perigee then shrinks $a$ and $e$ on every orbit until re-entry. For a circular orbit of radius $r_0$ and a target perigee radius $r_p$,

$$
\Delta V=V_0-V_a=\sqrt{\frac{\mu}{r_0}}-\sqrt{\mu\left(\frac{2}{r_0}-\frac{2}{r_0+r_p}\right)},
$$

the energy equation at apogee of the new ellipse with $a=(r_0+r_p)/2$. Chemical propulsion does it impulsively; electric propulsion spirals down and costs more ΔV; at low altitude a drag sail can replace propulsion ([[SESA2024 14 - Orbit Control, Drag and Payload Data Rate#1. Drag decay per orbit|note 14 §1]]). Apollo 9 lowered its perigee the same way before its de-orbit (2021/22 B1). For GEO the equivalent is a small Hohmann boost to the graveyard orbit.

## 4. Remediation

Even with good compliance, models of the LEO population show it continuing to grow through collisions between existing objects, the cascade known as the Kessler syndrome. Active debris removal is therefore needed as well as mitigation. Projects on the slides include the UK's COSMIC mission to remove dead UK satellites, Astroscale's ELSA-M multi-client end-of-life servicer, ClearSpace, and Surrey's RemoveDebris, which tested a net and a harpoon after its release from the ISS.

## 5. Space-based solar power

The Sun releases more energy every 1.5 microseconds than humanity uses in a year, and a collector in space receives more than ten times the energy of the same array on the ground, with no night and no weather. The idea goes back to Asimov's story *Reason* (1941) and Peter Glaser's concept (1968, patented 1974); current work includes ESA's SOLARIS study, Caltech's SSPP demonstrator and Aetherflux's LEO laser concept.

The slides describe a modular GEO architecture: 10 cm tiles of 1–2 W assembled into 2 by 60 m strips, then 60 by 60 m modules, then a system about 3 km square (about 10 km²) delivering 1–3 GW, with a peak power density at the ground receiver of about 1 kW/m². The photovoltaics have to reach more than 30 % efficiency and 2–10 kW/kg specific power, with ultralight panels that integrate the cells and the microwave transmitters.

## 6. NewSpace and the industrialisation of space

The second lecture traces the shift from government-led to commercial space. Reusable rockets have cut the launch cost per kilogram; mass-produced small satellites have cut the cost of the spacecraft (a CubeSat costs perhaps \$20 000–100 000 and a small satellite \$1–35 million, against \$250–400 million for a traditional one); and mega-constellations, in-orbit servicing (refuelling, repair and debris removal), manufacturing in microgravity (Space Forge), lunar and asteroid resources, AI-driven operations and space traffic management are all attracting investment, towards a projected trillion-dollar space economy. Planet's agile development ([[Agile Aerospace]]) is one model for how such companies work.

Earth-observation businesses trade three kinds of resolution: spatial (fine or coarse pixels), spectral (many or few bands) and temporal (how often a place is revisited). A single large satellite gives fine spatial and spectral resolution but slow revisit; constellations such as Satellogic's buy temporal resolution while keeping good spatial resolution. Communications businesses trade coverage, latency and bandwidth: a LEO constellation at about 600 km has a round-trip latency of 20–40 ms but small footprints, so it needs many satellites, while one GEO satellite covers about a third of the Earth with 450–750 ms of latency. The slides end with unusual concepts such as Reflect Orbital's "sunlight on demand" mirrors.

## Worked examples

### A disposal burn from 800 km

*(Suggested, not lecturer-set.)* A satellite in a circular orbit at 800 km lowers its perigee to 300 km so that drag will bring it down well within five years. With $r_0=7178$ km and $r_p=6678$ km,

$$
V_0=\sqrt{\frac{398\,600}{7178}}=7.452\ \mathrm{km/s},
\qquad
V_a=\sqrt{398\,600\left(\frac{2}{7178}-\frac{2}{13\,856}\right)}=7.316\ \mathrm{km/s},
$$

so $\Delta V=136$ m/s, a modest amount of propellant that has to be reserved from launch.

### Fragments from a 570 km break-up (2022/23 A6)

A satellite in a circular orbit at 570 km ($\tau=96.1$ min) breaks up. A fragment A thrown forwards at 10 m/s has its perigee at 570 km, an apogee of 607 km and a period of 96.4 min. A fragment B thrown backwards at 10 m/s has its apogee at 570 km, a perigee of 533 km and a period of 95.7 min. On a Gabbard diagram A plots up and to the right of the parent and B down and to the left, and after a few orbits B has moved ahead of the parent and A has fallen behind. Computed with the energy equation in Python.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]
- Concepts: [[Space Debris Mitigation]] · [[Agile Aerospace]] · [[Orbit Control Cycle]]
- Orbital mechanics used here: [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] · [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]
- Disposal as ECSS Phase F: [[SESA2024 01 - Systems Engineering and Spacecraft Design#5. Design phases (ECSS)|note 01 §5]]

## Sources

- "Space Sustainability, Space Debris and Space Based Solar Power" (`SESA2024_Space Sustainability_Debris_SBSP_2025_26.pdf`) and "The New Space Era and industrialisation of space" (`SESA2024_Space_Industrialization_2025_26.pdf`), Dr N. Vaidya, 2025-26, with material from Prof H. Lewis
- ESA Space Environment Report 2024 (population figures on the slides)
- No transcript; see the coverage note.

## Self-study tasks

No tasks were set that are recorded in the vault; these come from past papers.

### Core

- [ ] Explain how a fragment cloud spreads along the orbit (2021/22 A6, 5 marks). → [[#How a fragment cloud spreads]]
- [ ] Place fragments thrown forwards and backwards on a Gabbard diagram (2022/23 A6). → [[#Fragments from a 570 km break-up (2022/23 A6)]]
- [ ] List the IADC mitigation measures and explain how post-mission disposal is carried out in LEO and GEO. → [[#3. Mitigation]] · [[#Implementing disposal]]

### Further practice

- [ ] Compute the ΔV to lower the perigee from 800 km to 300 km. → [[#A disposal burn from 800 km]]
- [ ] Why is active debris removal needed even with full compliance? → [[#4. Remediation]]
- [ ] The resolution trades in Earth observation and the coverage–latency–bandwidth trade in communications. → [[#6. NewSpace and the industrialisation of space]]
