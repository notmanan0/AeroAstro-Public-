---
title: "SESA2024 08 - Electrical Power Subsystem"
module: "SESA2024 Astronautics"
type: topic
stream: "Spacecraft Subsystems"
order: 8
tags: [sesa2024, power, solar-arrays, batteries, eclipse]
aliases: ["EPS", "Power subsystem", "Chapter 8"]
date: 2026-10-30
status: lectured
coverage: "Week 7 (2025-11-11; 2025-11-13 had no audio) plus the pre-recorded Chapter 8 lecture"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]", "[[SESA2024 07 - Spacecraft Propulsion]]"]
next_topics: ["[[SESA2024 09 - Communications]]"]
key_concepts: ["[[Spacecraft Power Sources]]", "[[Solar Cells and Arrays]]", "[[Battery Sizing]]", "[[Eclipse Duration]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch8 - Power Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 8/2025 WEEK 7 - Chapter 8 - Power - complete.pdf", "02 - Sources/Lectures/Chapter 8/2025 Chapter 8 - Power - prerecord slides.pdf", "02 - Sources/Lectures/SESA2024 Lecture Chapter 8 - Power - prerecorded material.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-11 - 1200.txt"]
---

# SESA2024 08 - Electrical Power Subsystem

> [!abstract] Summary
> The power subsystem must give every other subsystem reliable, continuous power for the whole mission. Earth-orbiting spacecraft use solar arrays as the primary source and rechargeable batteries as the secondary source through eclipse; deep-space missions far from the Sun use RTGs. Sizing runs backwards from the orbit: the worst-case eclipse and the number of cycles set the depth of discharge and the battery capacity, and the array must then supply the load plus the battery recharge at end of life, after temperature, pointing, packing and radiation losses.

> [!summary]- Exam use: quick path
> - **Use it when:** you must choose a power source, find an eclipse time, size a battery, or size a solar array.
> - **Assumptions:** circular orbit with the Sun in the orbit plane (worst-case eclipse); cylindrical Earth shadow; the load is constant through sunlight and eclipse; the array is sized for end of life.
> - **Method:** 1. $\cos\alpha=R_E/(R_E+h)$, $t_e=\tau(180^\circ-2\alpha)/360^\circ$, $t_s=\tau-t_e$. 2. Cycles $=$ lifetime$/\tau$, then DoD from the battery type's cycle-life curve. 3. Cells in series $N_c=V_{bus}/V_c$, $V_B=N_cV_c$, capacity $C=P_{EOL}t_e/(\mathrm{DoD}\,V_B)$, mass $=CV_B/\varepsilon$. 4. Charge rate $R=\mathrm{DoD}\cdot C/t_s$, array voltage $V_A\approx1.2V_B$, array power $P=P_{load}+RV_A$. 5. Area $A=P/[S\cos\theta\,\eta\,\eta_p(1-D)]$.
> - **Common mistakes:** sizing the array for the load alone and forgetting the battery recharge; using the beginning-of-life efficiency without the radiation degradation factor.
> - **Practise:** [[#800 km LEO spacecraft, 1 kW for two years]] · [[SESA2024 Workbook Ch8 - Power Solutions#Q10. GEO communications spacecraft, 8000 W continuous, 10-year life|Workbook Q10]]

Every electrical component on the spacecraft draws on this subsystem, and losing it, even briefly, can end the mission: "if you lose thermal control, even if it's just for a matter of minutes", a component may go outside its temperature limits and fail (2025-11-11, ll. 26–60). The job is therefore not only to generate enough energy on average, but to supply it continuously, including through every eclipse, and still to manage it at the end of the mission when the arrays and batteries have degraded.

For most of an orbit sunlight falls on the arrays and powers the spacecraft; for part of it the Earth blocks the Sun and the batteries take over, and they then have to be recharged in the next sunlit period. The arrays therefore have to be bigger than the load alone requires, and the batteries bigger than a single eclipse requires, because using only a small fraction of a battery's charge each cycle is what lets it survive tens of thousands of cycles.

## 1. Power sources

The class named solar arrays, batteries, RTGs and fuel cells; the slides add solar dynamic systems and nuclear reactors (2025-11-11, ll. 51–100). The primary power system is the main source over the mission, usually solar arrays for Earth orbit. Because the arrays are sometimes in shadow or pointed away from the Sun, a secondary system stores energy: almost always a rechargeable battery, though flywheels, compressed gas, superconducting magnets or double-layer capacitors are possible (ll. 101–150).

### Solar arrays

Arrays convert the solar flux of about 1370 W/m² near the Earth with efficiencies of roughly 10–20 %, so a square metre facing the Sun gives of the order of 100 W (ll. 151–175). The ISS carries about 2500 m² of array. Because sunlight falls off with the square of the distance from the Sun, arrays become impractical in the outer Solar System (ll. 176–230):

$$
S(d)=\frac{1370}{d^2}\ \mathrm{W/m^2},\quad d\text{ in AU}.
$$

With 10 % efficiency, Jupiter at about 5 AU gives $1370/25\times0.1\approx5.5\ \mathrm{W/m^2}$ and Saturn at about 10 AU only $1.4\ \mathrm{W/m^2}$. Rosetta, at about 5.25 AU from the Sun, used solar arrays, and Juno does at Jupiter; beyond that other sources are needed.

### Primary batteries and fuel cells

Primary (non-rechargeable) batteries suit short missions and launch vehicles (ll. 230–250). Fuel cells combine hydrogen and oxygen to give power and water, which makes them useful on crewed missions, and reach kilowatts for short durations.

### Solar dynamic systems

A concentrator heats a working fluid that drives a turbine (ll. 251–275). It converts sunlight more efficiently than cells, but it is heavier and mechanically complex, so it is rarely used.

### Radioisotope thermoelectric generators

An RTG generates electricity by the Seebeck effect: thermocouples between a hot source, the heat of decaying plutonium-238, and a cold sink, which in space is easy to find (ll. 276–350). A typical unit is about 1 m long, 30 cm in diameter, weighs about 40 kg and gives about 200 W. Its output lasts for decades, which is why Voyager 1 and 2 still operate nearly fifty years after launch, but it pumps out heat at every stage from the integration hall to orbit, and its radioactive source is tightly regulated: launching one from Europe is very difficult, and in the USA it needs presidential approval.

### Choosing a source

The slides plot power level against mission duration (ll. 351–390). Primary batteries cover short, low-power missions; fuel cells short missions at kilowatts; solar arrays and RTGs long missions (the choice between them set by the distance from the Sun); solar dynamic systems long missions at high power; and only nuclear reactors give very high power for very long durations, which regulation currently rules out.

## 2. Solar cells

The pre-recorded lecture covers the physics (ll. 1–125). A semiconductor has a band gap of 1–2 eV between its valence and conduction bands. A solar cell joins an n-type layer (excess electrons) to a p-type layer (deficit of electrons); a photon with more energy than the band gap frees an electron, and the junction drives a current.

Each cell is tuned to one band gap, which limits its efficiency. A photon below the gap does nothing; a photon above it frees an electron but its excess energy becomes heat. Set the gap high and few photons qualify; set it low and most of the energy is wasted as heat.

> [!warning] Transcript slip (pre-recorded lecture, ll. 26–30)
> The example says a 1.7 eV photon falling on a 1.1 eV cell loses "1.6 electron volts" as heat. The excess is $1.7-1.1=0.6$ eV.

The cell efficiency is the electrical output over the solar input,

$$
\eta=\frac{P_{out}}{P_{in}}=\frac{P_{out}}{1370\ \mathrm{W/m^2}\times A},
$$

a little over 10 % for production silicon cells, about 20 % for gallium arsenide, and higher for dual- and triple-junction cells, which stack junctions tuned to different parts of the spectrum (ll. 126–150).

### The I-V curve and the maximum power point

A cell's current and voltage depend on the load across it (ll. 51–80). At one extreme is the short-circuit current $I_{sc}$ (no voltage), at the other the open-circuit voltage $V_{oc}$ (no current). Power is $IV$, which peaks near the knee of the curve: the maximum power point, about 14 mW/cm² for a silicon cell. Maximum power point tracking adjusts the load so the array works there. The same mechanism disposes of surplus power: operating off the peak deliberately wastes it.

![[ast_solar_cell_iv.png|900]]

### Temperature, pointing and radiation

A hot cell gives slightly more current but much less voltage, so its power falls; a cold cell gives more power (ll. 80–100). Silicon loses about 0.44 % of its power per °C, gallium arsenide 0.16 % and indium phosphide 0.21 %. Since the cells sit in sunlight, the back of a deployed array is made a good radiator to keep them cool, which a body-mounted array cannot do as well. Coming out of eclipse, the cold cells briefly produce a power surge that the regulator must handle.

Power falls roughly as the cosine of the angle between the array normal and the Sun (ll. 101–110):

$$
P(\theta)\approx P(0)\cos\theta.
$$

Radiation damage reduces both $I_{sc}$ and $V_{oc}$ over the mission (ll. 110–150). The array is therefore sized for end of life (EOL), which means it produces too much power at beginning of life (BOL); the surplus is shed by switching off sections, operating off the maximum power point, or dumping it in a shunt or heater. Cover glass thickness and putting the n-type layer on top improve radiation resistance. The slide table:

| Cell | Production efficiency | Power loss per °C | Efficiency left after the reference radiation dose | Relative density and cost |
|---|---|---|---|---|
| Silicon | just over 10 % | 0.44 % | 67 % | 1 (reference) |
| Gallium arsenide | about 20 % | 0.16 % | 78 % | higher |
| Indium phosphide | just over 10 % | 0.21 % | 94 % | higher |

### From cells to arrays

Cells are wired in series to reach the bus voltage and in parallel to reach the current (ll. 176–200). They are mounted, with cover glass and an insulating layer, on honeycomb panels with CFRP or aluminium face sheets, or on tensioned flexible blankets. The wiring gaps mean not all the area generates power, which introduces a packing efficiency $\eta_p$. Two-winged arrays rotating about one axis (Olympus) give symmetric drag and one degree of freedom for Sun tracking; boom-mounted arrays (ERS) give two; spinners such as Meteosat and Intelsat 6 have body-mounted cells, as Chapter 6 explained (ll. 151–200).

## 3. Batteries

The pre-recorded lecture's terminology (ll. 201–300): a primary battery is not rechargeable; a secondary battery is, and that is the near-universal choice for spacecraft secondary power. The chemistries in use have moved from nickel–cadmium (compact cells, now obsolete) through nickel–hydrogen (individual pressure vessels, better energy storage but bulky, still on some communications satellites and the ISS) to lithium-ion (first on a commercial platform in 2004, now standard), with lithium polymer under qualification.

| Parameter | Symbol, units | Meaning |
|---|---|---|
| Capacity | $C$, A h | 40 A h is 40 A for 1 h or 4 A for 10 h |
| Depth of discharge | DoD, % | fraction of capacity used per cycle; 30 % DoD leaves 70 % |
| Stored energy | $E=CV_B$, W h | capacity times discharge voltage |
| Energy density | $\varepsilon$, W h/kg | stored energy per unit mass |
| Charge rate | $R$, A | rate at which charge is put back |
| Battery voltage | $V_B=N_cV_c$ | cells in series times cell voltage |

| | NiCd | NiH₂ | Li-ion |
|---|---|---|---|
| Cell voltage | 1.25 V | 1.3 V | 4.1 V |
| Operating temperature | −10 to +40 °C | −10 to +40 °C | 0 to +44 °C |
| Energy density | lowest | middle | highest |

Temperature matters because a battery taken outside its range can be killed quickly. Cycle life depends above all on the depth of discharge (ll. 301–350): on the NiCd curve, 20 % DoD gives some 20 000–30 000 cycles but 60 % only about 1000. So a long-lived battery is mostly charge that is never used, as with a phone you drain to zero every day. Nickel–hydrogen tolerates a deeper discharge for the same number of cycles. A car's lead–acid battery would last only a few hundred cycles at modest depth.

## 4. The power bus and power budgets

Connecting the array straight to the loads would not work: its output varies with eclipse, temperature and pointing. A regulator on the primary bus gives a steady supply, and a charge/discharge controller protects the battery (2025-11-11, ll. 390–430).

Each mission phase has its own power requirement (ll. 431–500). The SOHO budget on the slides lists the service module and payload demands for pre-launch, ascent, parking orbit, transfer orbit, cruise and on-station, each with a 15 % margin (87.5 W becomes 101 W); the payload draws nothing until cruise. The power subsystem must meet every phase.

## 5. Sizing a battery and an array

The order matters (ll. 501–550). The array must power the spacecraft in sunlight and also recharge the battery, so it cannot be sized until the battery is known; the battery cannot be sized until the eclipse and the number of cycles are known; and those come from the orbit. So: orbit, then battery, then array, all at end of life.

### Worst-case eclipse

For a circular orbit of altitude $h$, the worst case is the Sun in the orbit plane. Treat the Earth's shadow as a cylinder of radius $R_E$ (ll. 601–725). The spacecraft enters and leaves the shadow where its radius vector makes an angle $\alpha$ with the Earth–Sun line, with

$$
\cos\alpha=\frac{R_E}{R_E+h}.
$$

The orbit arc inside the shadow subtends $180^\circ-2\alpha$ at the Earth's centre, so with the orbital period $\tau$

$$
t_e=\tau\,\frac{180^\circ-2\alpha}{360^\circ},
\qquad
t_s=\tau-t_e.
$$

It applies to circular orbits only.

> [!warning] Transcript slip (2025-11-11, ll. 701–705)
> The fraction is read out as "180 degrees minus alpha as a proportion of that 60 degrees". The slide's equation (8.2) is right: $(180^\circ-2\alpha)/360^\circ$.

### Battery

The bus voltage sets the cells in series, $N_c=V_{bus}/V_c$, rounded to a whole number, giving $V_B=N_cV_c$. The battery must deliver the end-of-life load $P_{EOL}$ for the eclipse time while using only the allowed depth of discharge:

$$
C=\frac{P_{EOL}\,t_e}{\mathrm{DoD}\cdot V_B},
\qquad
E=CV_B,
\qquad
M_{battery}=\frac{E}{\varepsilon}.
$$

### Array

The array must charge the battery at the rate $R$ that puts back the discharged capacity in one sunlit period, at an array voltage $V_A$ above the battery voltage (about 1.2 $V_B$):

$$
R=\frac{\mathrm{DoD}\cdot C}{t_s},
\qquad
P_{array}=P_{load}+RV_A.
$$

The area follows from the flux $S$, the worst off-Sun angle $\theta$, the cell efficiency $\eta$, the packing efficiency $\eta_p$ and the radiation degradation $D$ over the mission:

$$
A_{SA}=\frac{P_{array}}{S\cos\theta\;\eta\;\eta_p\,(1-D)}.
$$

## 6. Impact on the spacecraft

The power subsystem interfaces with every electrical subsystem and the payload (slide 39). The mission fixes the primary source (Sun distance, duration, power level). Pointing the arrays at the Sun shapes the configuration and the ACS: wings and drives on a three-axis spacecraft, body-mounted cells on a spinner. And mass: in the example below the battery alone is 67 kg for a 1 kW spacecraft.

## Worked examples

### 800 km LEO spacecraft, 1 kW for two years

The lecture example (slides 30–38; set up live on 2025-11-11, ll. 551–725, then continued on 2025-11-13, whose recording has no audio). Estimate the battery and array for a spacecraft in an 800 km circular orbit needing 1 kW for payload and subsystems at the end of a two-year life. Constants: $R_E=6378$ km, $\mu=398\,600\ \mathrm{km^3/s^2}$. Recomputed in Python.

Orbit. $r=7178$ km, so

$$
\tau=2\pi\sqrt{\frac{7178^3}{398\,600}}=6052\ \mathrm s=1.68\ \mathrm h,
\qquad
\alpha=\cos^{-1}\frac{6378}{7178}=27.3^\circ,
$$

$$
t_e=1.68\times\frac{180-54.6}{360}=0.59\ \mathrm h,
\qquad
t_s=1.68-0.59=1.09\ \mathrm h.
$$

This is the homework the lecture ended on (l. 726). Two years is $2\times365.25\times24/1.68\approx10\,430$ cycles (the slide says 10 420). From the NiCd cycle-life curve, take DoD = 30 % with margin.

Battery: bus 28 V, NiCd cells of 1.25 V, energy density 30 W h/kg at 100 % discharge. $N_c=28/1.25=22.4$, so choose 22 cells and $V_B=22\times1.25=27.5$ V. With the eclipse rounded to 0.6 h,

$$
C=\frac{1000\times0.6}{0.3\times27.5}=72.7\ \mathrm{A\,h},
\qquad
E=72.7\times27.5=2000\ \mathrm{W\,h},
\qquad
M=\frac{2000}{30}=67\ \mathrm{kg}.
$$

Array: BOL cell efficiency 11.5 %, radiation degradation $D=0.1$ over two years, worst off-normal Sun angle $3^\circ$, $S=1350\ \mathrm{W/m^2}$, packing efficiency 90 %, $V_A=1.2V_B=33$ V.

$$
R=\frac{0.3\times72.7}{1.09}=20.0\ \mathrm A,
\qquad
P_{array}=1000+20.0\times33=1660\ \mathrm W,
$$

$$
A_{SA}=\frac{1660}{1350\cos3^\circ\times0.115\times0.9\times0.9}=13.2\ \mathrm{m^2}.
$$

> [!check] Sense of scale
> The recharge adds two-thirds to the array power (660 W on top of 1000 W). With the exact eclipse of 0.586 h the capacity would be 71.0 A h, so the slide's rounding to 0.6 h is a small extra margin.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 07 - Spacecraft Propulsion]]
- Next: [[SESA2024 09 - Communications]]
- Concepts: [[Spacecraft Power Sources]] · [[Solar Cells and Arrays]] · [[Battery Sizing]] · [[Eclipse Duration]]
- Workbook: [[SESA2024 Workbook Ch8 - Power Solutions]]
- Eclipse in the case study: [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]
- Year 1: p–n junctions, [[FEEG1004 B1 - Semiconductors and Diodes]]; regulators, [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]

## Sources

- `2025 Chapter 8 - Power - prerecord slides.pdf` with transcript `SESA2024 Lecture Chapter 8 - Power - prerecorded material.txt` (solar cells, arrays, batteries)
- `2025 WEEK 7 - Chapter 8 - Power - complete.pdf` with transcript `SESA2024 Lecture 2025-11-11 - 1200.txt` (Dr H. Sykulska-Lawrence: sources, power bus, budgets, eclipse). The 2025-11-13 lecture, which finished the sizing example, has a silent audio track, so slides 33–39 are the only source for the battery and array sizing.
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 10

## Self-study tasks

### Core

- [ ] Work out the eclipse and sunlit times for the 800 km example ("I'm going to leave this as a little bit of homework", 2025-11-11, ll. 725–730). Targets 0.59 h and 1.09 h. → [[#Worst-case eclipse]] · [[#800 km LEO spacecraft, 1 kW for two years]]
- [ ] Finish the example: battery capacity, mass, charge rate and array area (slides 33–38). Targets 72.7 A h, 67 kg, 20 A, 13.2 m². → [[#800 km LEO spacecraft, 1 kW for two years]]
- [ ] GEO communications spacecraft, 8 kW continuous for 10 years (Workbook Ch8 Q10). → [[SESA2024 Workbook Ch8 - Power Solutions#Q10. GEO communications spacecraft, 8000 W continuous, 10-year life|Workbook solution]]
- [ ] Primary source by mission duration and power (Workbook Ch8 Q2). → [[#Choosing a source]] · [[SESA2024 Workbook Ch8 - Power Solutions#Q2. Primary source by mission duration|Workbook Q2]]

### Further practice

- [ ] Principles of operation of solar cells, RTGs and fuel cells (Workbook Ch8 Q1). → [[#1. Power sources]] · [[#2. Solar cells]]
- [ ] Temperature effect on cells and the surge at eclipse exit; the maximum power point (Workbook Ch8 Q4, Q7). → [[#Temperature, pointing and radiation]] · [[#The I-V curve and the maximum power point]]
- [ ] Battery terms, and NiCd versus NiH₂ packaging (Workbook Ch8 Q8, Q9). → [[#3. Batteries]]
- [ ] Power at Jupiter and Saturn per square metre of array (done on the board, 2025-11-11, ll. 201–225). → [[#Solar arrays]]
- [ ] Maximum Sun angle for a small array to give 4 W at end of life (2024/25 A5). → [[SESA2024 2024-25 Exam Solutions#Section A|2024/25 A5]]
