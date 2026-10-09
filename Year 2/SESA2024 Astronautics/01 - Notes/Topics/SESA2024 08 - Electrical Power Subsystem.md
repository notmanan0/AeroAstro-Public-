---
title: "SESA2024 08 - Electrical Power Subsystem"
module: "SESA2024 Astronautics"
type: topic
stream: "Spacecraft Subsystems"
order: 8
tags:
  - sesa2024
  - power
  - solar-arrays
  - batteries
aliases: ["EPS", "Chapter 8", "Power subsystem"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 03 - Orbital Elements and Conic Sections]]"]
next_topics: ["[[SESA2024 09 - Communications]]"]
key_concepts: ["[[Spacecraft Power Sources]]", "[[Solar Cells and Arrays]]", "[[Battery Sizing]]", "[[Eclipse Duration]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch8 - Power Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 8/2025 WEEK 7 - Chapter 8 - Power - complete.pdf", "02 - Sources/Lectures/Chapter 8/2025 Chapter 8 - Power - prerecord slides.pdf"]
---

# SESA2024 08 - Electrical Power Subsystem

> [!abstract] Summary
> The power subsystem must deliver **reliable, continuous** power. An interruption can be catastrophic for the payload, the ACS and thermal control.
>
> The standard architecture is a **solar array** (primary) plus a **battery** (secondary) on a regulated bus. Sizing is a fixed recipe:
> 1. worst-case eclipse $t_e$ → number of cycles → DoD;
> 2. battery capacity $C = Pt_e/(\text{DoD}\,V_B)$ and mass $= CV_B/\bar\varepsilon$;
> 3. charge current $R = \text{DoD}\,C/t_s$;
> 4. array power $P+RV_A$;
> 5. array area $A = P/[S\cos\theta\,\eta\,\eta_p(1-D_0)]$.

## Key Concepts
- [[Spacecraft Power Sources]] · [[Solar Cells and Arrays]] · [[Battery Sizing]] · [[Eclipse Duration]]

---

## 1. Power sources
See [[Spacecraft Power Sources]].
- **Primary system**: the main source of electrical energy. For Earth orbiters, this is usually solar arrays.
- **Secondary system**: storage. Almost always rechargeable batteries.

| Source | Principle | Typical use |
|---|---|---|
| **Solar arrays** | photovoltaic conversion of about 1370 W/m² at 1 AU; only about 100 W/m² useful | Earth orbit and inner planets (to about 5 AU) |
| Primary batteries | non-rechargeable | short missions (minutes to hours), launch vehicles |
| **Fuel cells** | H₂ + O₂ → power + **water** | crewed missions; duration limited by reactant supply |
| Solar dynamic | concentrator → working fluid → turbine | more efficient than PV but heavy; rarely used |
| **RTGs** | Pu-238 decay heat → thermocouples (Seebeck effect); about 40 kg for 200 W, 1 m × 0.3 m | deep space: Ulysses, Voyager, Galileo, Cassini |
| Nuclear reactor | fission | very high power |

"Mission usage" chart: batteries for hours, fuel cells for days to weeks, solar for months to years at 1–100 kW, RTGs for years at low power, reactors at high power.

## 2. Power system overview (fully regulated bus)
Solar array → **solar array regulator** (shunt) → **bus** → payload and subsystem loads. Batteries sit on the bus through a **battery charge controller** and a **battery discharge controller**.

## 3. Solar cells
See [[Solar Cells and Arrays]].
- **Band gap**:
  - conductors have a partially filled conduction band;
  - insulators have a large gap;
  - **semiconductors** have a gap of about 1–2 eV. Silicon's is 1.1 eV, so $\lambda_{max}\approx1.1$ µm.
- A p–n junction: n-type is Si doped with P (5 valence electrons); p-type is Si doped with B (3).
- Efficiency: $\eta = P_{out}/P_{in}$, typically 0.10–0.30.
- Typical Si cell at 30 °C and about 1400 W/m²:
  - $V_{oc}\approx0.55$ V;
  - $I_{sc}\approx35$ mA/cm²;
  - $P_{max}\approx14$ mW/cm² (about 10 %).

**What degrades output** (asked in 2014/15, 2016/17 and 2019/20):
- **Temperature**: hot means less power, about −0.4 %/°C for Si. Cold means more power, so **eclipse exit gives a power surge**.
- **Sun angle**: power is roughly proportional to $\cos\theta$ off-normal.
- **Radiation**: reduces $P$, $V_{oc}$ and $I_{sc}$. It depends on cell and cover-glass thickness; an n-type top layer is more resistant. EOL power is predicted from the radiation environment. The degradation factor $D_0$ runs from BOL to EOL.
- **Arrays**: cells in **series** for voltage and **parallel** for current. Body-mounted panels (spinners) or deployed, Sun-tracking panels.
- The **maximum power point** is where $VI$ is largest on the $I$–$V$ curve. MPP tracking adjusts the load to stay there.

## 4. Batteries
See [[Battery Sizing]]. Terms:

| Term | Meaning | Units |
|---|---|---|
| Capacity $C$ | current × time at 100 % discharge (40 A for 1 h = 40 A·h) | A·h |
| Cycles | number of charge/discharge cycles over the life | – |
| **DoD** | fraction of capacity used per discharge. **Controls cycle life**: deeper discharge means fewer cycles | % |
| Stored energy $\mathcal E = CV_B$ | | W·h |
| Energy density $\bar\varepsilon$ | stored energy per kg | W·h/kg |
| Charge rate $R$ | current the battery accepts | A |
| $V_B$ | cells in series × cell discharge voltage | V |

| | NiCd | NiH₂ | Li-ion |
|---|---|---|---|
| Energy density (W·h/kg) | 25–30 | 50–80 | **120–150** |
| Operating temperature (°C) | −10 to +40 | −10 to +40 | 0 to +45 |
| Cell voltage (V) | 1.25 | 1.30 | **4.1** |
| Status | obsolete | being phased out; volumetrically inefficient pressure vessels; deeper DoD than NiCd for the same life | today's choice (first commercial use: Eutelsat W3A, 2004) |

The key parameter for cycle lifetime is the **depth of discharge** (2015/16 Q1(iv), 1 mark).

## 5. Power budgets
Example: SOHO. List each subsystem's power per mode (launch, cruise, operations, safe), add a margin, and use the results to size the arrays and batteries.

## 6. Preliminary sizing: worked example (lecture)
**LEO, 800 km circular, 1 kW average, 2 years.**

**Eclipse** (worst case: Sun vector in the orbit plane). See [[Eclipse Duration]].

$$
t_e = \frac{180^\circ-2\cos^{-1}[R_E/(R_E+h)]}{360^\circ}\tau
$$

- $\tau$ = 1.68 h, **$t_e$ = 0.59 h**, $t_s$ = 1.09 h;
- cycles = 2 yr / $\tau$ = **10 420**;
- NiCd at this cycle count, so DoD = **30 %** (with margin).

**Battery** (NiCd, $V_{BUS}$ = 28 V, 30 W·h/kg, $V_c$ = 1.25 V):
- $N_c = 28/1.25 = 22.4$, so choose **22 cells**, giving $V_B$ = 27.5 V;
- $C = \dfrac{(1000)(0.6)}{(0.3)(27.5)} = \mathbf{72.7\ A\cdot h}$;
- $\mathcal E = 72.7\times27.5 = 2000$ W·h;
- $M_{batt} = 2000/30 = \mathbf{67\ kg}$.

**Array** (BOL $\eta$ = 11.5 %, $D_0$ = 0.1, $\theta$ = 3°, $S$ = 1350 W/m², $\eta_p$ = 0.9, $V_A = 1.2V_B$ = 33 V):
- $R = \text{DoD}\cdot C/t_s = 0.3(72.7)/1.09 = 20$ A;
- $P_A = 1000+RV_A = 1000+20(33) = \mathbf{1660\ W}$;
- $A_{SA} = \dfrac{1660}{1350\cos3^\circ(0.115)(0.9)(1-0.1)} = \mathbf{13.2\ m^2}$.

![[ast_eclipse_vs_altitude.png|650]]

> [!warning] Recurring exam traps
> - Use the **worst-case** eclipse (Sun in the orbit plane) unless told otherwise. For a Sun-synchronous dawn–dusk orbit there may be none.
> - DoD in the capacity formula is a fraction.
> - The array also supplies $RV_A$ for charging, not just the load.
> - $(1-D_0)$, not $D_0$.

## 7. Impacts on the spacecraft
- Power interfaces with every electrical subsystem and the payload.
- The mission determines the primary source (distance from the Sun, duration, power level).
- **Power-raising pointing** (Sun-tracking arrays) affects the configuration and the ACS.
- The eclipse fraction, set by the orbit and the LST of the node, drives battery mass, array size and thermal design (heaters).

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 07 - Spacecraft Propulsion]] · Next: [[SESA2024 09 - Communications]]
- Solutions: [[SESA2024 Workbook Ch8 - Power Solutions]]
- LST and eclipse: [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]

## Sources
- Chapter 8 lecture and pre-recorded slides (H. Sykulska-Lawrence), equations 8.1–8.11; Fortescue, Stark & Swinerd, Ch. 10
