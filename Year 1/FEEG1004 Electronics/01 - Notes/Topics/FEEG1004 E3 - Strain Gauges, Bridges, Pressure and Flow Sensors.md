---
title: "FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors"
module: "FEEG1004 Electronics"
type: topic
stream: "Part E: Transducers and Measurement"
order: 3
tags: [feeg1004, transducers, strain-gauge, gauge-factor, wheatstone-bridge, load-cell, pressure-sensor, venturi, pitot]
aliases: ["Transducers 03", "Strain gauges", "Wheatstone bridge", "Pressure sensors", "Flow measurement"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]", "[[FEEG1004 B4 - Operational Amplifiers]]"]
next_topics: []
key_concepts: ["[[Gauge Factor]]", "[[Strain Gauge Bridge Configurations]]", "[[Wheatstone Bridge and Strain Gauges]]", "[[Stagnation Pressure and Pitot Tube]]"]
tutorial_sheets: []
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 03 - Complete Systems - Lecture Slides.pdf"]
---

# FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors

> [!abstract] Summary
> - A **strain gauge** is a resistor whose resistance changes with strain: $\Delta R/R = G\varepsilon$. The gauge factor is $G\approx2$ for metal foil (geometric) and 100–120 for semiconductor (piezoresistive).
> - Tiny $\Delta R$ is read with a **Wheatstone bridge**:
>
> $$V = \frac{N\,E\,G\,\varepsilon}{4}\qquad(N = \text{number of active gauges})$$
>
> - Placing gauges in adjacent or opposite arms lets the bridge **add** the wanted strain and **cancel** unwanted strain and temperature.
> - Gauges on a **diaphragm** make pressure sensors. Differential pressure across a **Venturi** or **pitot-static** probe gives flow and airspeed through Bernoulli.

## Key Concepts
- [[Gauge Factor]] · [[Strain Gauge Bridge Configurations]] · [[Wheatstone Bridge and Strain Gauges]] · [[Stagnation Pressure and Pitot Tube]]

---

## 1. Why measure strain
- Static and dynamic strain tell you the load-bearing capability and the **fatigue** life of a structure.
- Gauges are also the sensing element inside **load cells, force transducers, accelerometers and pressure sensors**.
- Mechanics refresher: $\varepsilon = \Delta L/L$, $\sigma = F/A$, $E = \sigma/\varepsilon$ ([[Stress, Strain and Young's Modulus]]).

## 2. How a strain gauge works
For a wire, $R = \rho L/A$ with $A = \pi d^2/4$. Stretching raises $L$, and Poisson contraction ($\nu = -\dfrac{\Delta d/d}{\Delta L/L}$) shrinks $d$:

$$
\frac{\Delta R}{R} = \underbrace{\frac{\Delta\rho}{\rho}}_{\text{piezoresistive}} + \underbrace{(1 + 2\nu)\,\varepsilon}_{\text{geometric}},\qquad G = \frac{\Delta R/R}{\Delta L/L} = \frac{\Delta R/R}{\varepsilon}
$$

| Gauge | G | Notes |
|---|---|---|
| metal foil or wire (Cu-Ni, Ni-Cr) | ≈ 2 | geometric-dominated; 120 or 350 Ω ± 0.2 %; sold in matched sets |
| semiconductor (doped Si or Ge) | 100–120 | piezoresistive-dominated; very sensitive but temperature-sensitive, non-linear, about 10× the cost |

**Practical challenges**:
- the temperature coefficient of resistance, and differential thermal expansion between gauge and structure (gauges are **matched** to steel or aluminium);
- temperature limits of −200 to +800 °C, including the adhesive;
- bonding quality (strain transfer);
- a current limit of about 10 mA, which caps the excitation;
- a finite fatigue life of the gauge itself.

## 3. The Wheatstone bridge
- Two dividers in parallel, "bridged" by a voltmeter. When **balanced** the voltmeter reads 0, so it detects tiny ΔR very sensitively.
- **Trimming**: gauge tolerances unbalance the bridge. A potentiometer $R_p$ with an **isolation resistor** $R_i$ sets the initial zero.
- Sensitivity is greatest when all four arms are equal. For small strain:

$$
V = \frac{NEG\varepsilon}{4}\qquad(\text{quarter } N = 1,\ \text{half } N = 2,\ \text{full } N = 4)
$$

![[ee_e3_strain_bridge.png|920]]

- **Temperature compensation**: gauges in **adjacent** arms subtract, so a common temperature change cancels. **Dummy gauges** see temperature but not stress.

## 4. Bridge configurations
![[ee_e3_gauge_configurations.png|880]]

| Measurand | Layout | Output | Temp. comp. | Rejects |
|---|---|---|---|---|
| bending | top +ε, bottom −ε in adjacent arms (half) | $EG\varepsilon/2$ (×2) | yes | axial |
| bending | 4 gauges (full) | $EG\varepsilon$ (×4) | yes | axial |
| axial | 2 active in opposite arms | $EG\varepsilon/2$ (×2) | **no** | bending |
| axial | 2 active + 2 dummy | ×2 | yes | bending |
| torsion | 4 gauges at ±45° | ×4 | yes | bending and axial |

- For a cantilever, place gauges close to the fixture (root), where the bending strain is largest.
- **Load cells**: gauges bonded to a structure that deforms predictably under force. The bridge output ∝ force.
- **Signal chain**: excitation $E$ → bridge (with a set-zero trim) → **differential amplifier** $V_{out} = (R_f/R_{in})(V_2 - V_1)$ ([[Standard Op-Amp Configurations]]).

## 5. Pressure sensors
- Pressure is measured via a **force collector** (diaphragm, piston or bellows). Its deflection is read by strain gauges, capacitance, inductance (LVDT, eddy current, Hall effect), piezoelectric, optical-fibre or **MEMS** elements.
- **Diaphragm with four gauges**: pressure stretches some regions and compresses others. Wiring the stretched and compressed gauges into a full bridge gives about 4× the signal and temperature compensation.
- **References**:
  - **absolute** (sealed vacuum behind the diaphragm);
  - **gauge** (vented to atmosphere);
  - **differential** (two ports).

## 6. Flow and airspeed from differential pressure
- **Venturi meter**: a constriction speeds the flow. Bernoulli gives $p_a - p_b = \tfrac{1}{2}\rho(v_b^2 - v_a^2)$; with continuity $A_av_a = A_bv_b$ this yields the flow rate.
- **Pitot-static tube**: static + dynamic = total pressure. A **differential** sensor between the total and static ports reads $\tfrac{1}{2}\rho U^2$, so $U = \sqrt{2\Delta p/\rho}$.

![[ee_e3_pitot_venturi.png|900]]

Because $\Delta p\propto U^2$, the sensitivity $d(\Delta p)/dU = \rho U$ **vanishes at low speed**: pitot airspeed is poor near zero.

## Year 2 bridge
- **Airspeed measurement** and the pitot tube are covered in [[Stagnation Pressure and Pitot Tube]], [[Airspeed Measures]] and [[Bernoulli Equation]] ([[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]], [[SESA1016 T10 - Euler and Bernoulli Equations]]). Compressible and supersonic pitot corrections are in [[Compressible Pitot Probe]] and [[Rayleigh Pitot Formula]].
- **Strain gauges and rosettes** return in structures: [[Strain Gauge Rosettes]] ([[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]). SESA2027 derives the quarter-bridge equation: [[Wheatstone Bridge and Strain Gauges]].
- **Wind-tunnel balances** are strain-gauge load cells ([[SESA2022 Wind Tunnel Lab Summary]]). Fatigue monitoring feeds lifing ([[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]).
- **Pressure transducers** on combustion chambers and intakes appear in propulsion testing ([[Intake Pressure Recovery]]).

## Links
- Previous: [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- Module hub: [[FEEG1004 Electronics Hub]]

## Sources
- Transducers and Measurement Systems lecture 3 of 3 (C. Holmes, 2024).
