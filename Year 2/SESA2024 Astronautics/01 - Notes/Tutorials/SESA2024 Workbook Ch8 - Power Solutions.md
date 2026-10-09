---
title: "SESA2024 Workbook Ch8 - Power Solutions"
module: "SESA2024 Astronautics"
type: tutorial
stream: "Spacecraft Subsystems"
tags:
  - sesa2024
  - tutorial-solutions
  - power
sheet: "Problem Sheet Workbook 2025-26, Chapter 8 (pp. 97-106)"
theory_notes: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
key_concepts: ["[[Solar Cells and Arrays]]", "[[Battery Sizing]]", "[[Eclipse Duration]]", "[[Spacecraft Power Sources]]"]
status: complete
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# SESA2024 Workbook Ch8 - Power Solutions

> [!abstract] Sheet Info
> Ten questions. Q1–9 are descriptive. Q10 is the **GEO battery and array sizing** calculation, which is the template for every power question in the past papers: 2014/15 ISS, 2018/19 900 km, 2021/22 Meteosat, 2023/24 10 kW GEO and 2024/25 A5. All numbers were reproduced in Python ✔.

## Theory Links
- [[SESA2024 08 - Electrical Power Subsystem]]
- Concepts: [[Solar Cells and Arrays]] · [[Battery Sizing]] · [[Eclipse Duration]] · [[Spacecraft Power Sources]]

---

## Q1: Principles of operation
- **Solar cells**: large areas of semiconductor convert incident sunlight to electricity by the **photovoltaic effect**. They are the default choice for Earth orbiters, where sunlight is abundant.
- **Solar dynamic**: a concentrator (such as a parabolic mirror) heats a working fluid that drives a turbine and generator.
  - More efficient than PV, but heavy and needs mechanisms. Rarely used.
- **RTGs**: the heat from radioactive decay (Pu-238) is converted to electricity by the **Seebeck effect** (thermocouples). They are passive and suit missions far from the Sun.
  - Handling is difficult: heat and radiation affect the launch vehicle.
  - There are environmental ("Green lobby") concerns about a launch failure dispersing the material.

## Q2: Primary source by mission duration
- **A few hours**: batteries (primary cells). Examples: launch vehicles, probes.
- **Several years**: solar arrays near the Sun; RTGs if the spacecraft is far from the Sun; a nuclear reactor if the power demand is very high.
- Fuel cells suit crewed missions of days to weeks.

## Q3: Solar flux
- At 1 AU the flux is about **1.4 kW/m²** (the "solar constant"; the lecture uses 1350–1370 W/m²). It falls as $1/d^2$.
- At 5 AU it is $1400/5^2\approx55$ W/m², which gives only 5–6 W/m² of electrical power after array inefficiencies. That needs enormous arrays.
- **Beyond about 5 AU, RTGs are used.** (Juno at Jupiter is the famous solar exception.)

## Q4: Temperature effect and eclipse exit
- Efficiency falls as temperature rises. For silicon, about 0.4 %/°C: a 25 °C rise costs about 10 % of efficiency.
- In eclipse the array can cool to about −150 °C. On eclipse exit the cold array is very efficient, so there is a **power surge** until it warms to about 50 °C. The power regulator must handle it.

## Q5: Greatest long-term environmental effect
**High-energy particle radiation**: Van Allen belts, solar protons and cosmic rays.
- It damages the semiconductor lattice, which reduces $V_{oc}$, $I_{sc}$ and power.
- Mitigation: a cover glass; putting the n-type layer uppermost.
- This is the degradation factor $D_0$, from BOL to EOL.

## Q6: Raising voltage and current
- A typical Si cell gives $V_{oc}\approx0.5$ V and $I_{sc}\approx35$ mA/cm².
- Cells are wired in **series to add voltage** and in **parallel to add current**, forming *strings*.

## Q7: Maximum power point
- The MPP is the point on the $I$–$V$ curve where the rectangle $P = VI$ has maximum area.
- **MPP tracking**: adjust the electrical load seen by the array (through the shunt regulator or power conditioning) so that the cells operate at the MPP as temperature, illumination and ageing change.

## Q8: Battery terms
- **Total capacity $C$** (A·h): the current available over time at 100 % discharge. 50 A·h gives 50 A for 1 h, or 1 A for 50 h.
- **Energy density** (W·h/kg): stored energy per kg of battery.
- **Depth of discharge (DoD)**: the fraction of capacity used per discharge. DoD = 40 % leaves 60 %. DoD sets the **cycle life**: deeper discharge means fewer cycles.

## Q9: NiCd vs NiH₂ packaging
- **NiCd**: rectangular cells, so packs are volumetrically efficient.
- **NiH₂**: cylindrical pressure vessels with hemispherical end caps, so packs are volumetrically inefficient. Their higher energy density and deeper DoD make them lighter, though.
- (Li-ion is today's choice: 120–150 W·h/kg at 4.1 V per cell.)

---

## Q10: GEO communications spacecraft, 8000 W continuous, 10-year life

**Data**:
- $R_{GEO} = 6.611R_E$;
- NiCd: DoD 40 %, energy density 30 W·h/kg, $V_B = 27.5$ V;
- array: $V_A = 33$ V, $S = 1350$ W/m², $\delta\theta = 7^\circ$, $\eta = 0.105$, $\eta_p = 0.9$, $D_0 = 0.2$.

### Step 1: worst-case eclipse
The worst case has the Earth–Sun vector in the orbit plane (at the equinoxes for GEO).

$$
\cos\alpha = \frac{R_E}{R_{GEO}} = \frac{1}{6.611}\Rightarrow\alpha = 81.3^\circ,\qquad \theta = 180^\circ-2\alpha
$$

$$
t_{ecl} = \frac{180^\circ-2\alpha}{360^\circ}\tau = \mathbf{1.157\ h},\qquad t_{sun} = 23.935-1.157 = \mathbf{22.778\ h}
$$

![[ast_eclipse_vs_altitude.png|650]]

### Step 2: cycles
$$n = \frac{10\ \text{yr}}{\tau}\approx\mathbf{3660}$$

In practice GEO has only about 90 eclipses a year, in two equinox seasons, but the sheet takes the worst case on every orbit.

### Step 3: battery (NiCd)

$$
C = \frac{P_{EOL}t_{ecl}}{\text{DoD}\cdot V_B} = \frac{(8000)(1.157)}{0.4(27.5)} = \mathbf{841.4\ A\cdot h}
$$

$$
\mathcal E = CV_B = 841.4\times27.5 = 23\,140\ \text{W·h},\qquad M_{batt} = \frac{23\,140}{30} = \mathbf{771\ kg}
$$

### Step 4: charge power and array area

$$
R = \frac{\text{DoD}\cdot C}{t_{sun}} = \frac{0.4(841.4)}{22.778} = 14.78\ \text{A}
$$

$$
P_{EOL} = 8000+RV_A = 8000+14.78(33) = \mathbf{8488\ W}
$$

$$
A = \frac{P_{EOL}}{S\cos\delta\theta\,\eta\,\eta_p(1-D_0)} = \frac{8488}{1350\cos7^\circ(0.105)(0.9)(0.8)}\approx\mathbf{84\ m^2}
$$

> [!warning] Common slips
> - $D_0$ enters as $(1-D_0)$, not $D_0$.
> - The **array** voltage (33 V) multiplies the charge current; the **battery** voltage (27.5 V) goes in the capacity.
> - Use hours consistently: $C$ is in A·h.

## Sources
- Workbook 2025-26 Chapter 8 questions (p. 97–98) and solutions (p. 103–106)
- Chapter 8 lecture: the 800 km, 1 kW, 2-year worked example (slides 30–38)
