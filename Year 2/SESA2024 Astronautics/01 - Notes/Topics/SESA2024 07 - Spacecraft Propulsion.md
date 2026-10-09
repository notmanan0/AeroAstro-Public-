---
title: "SESA2024 07 - Spacecraft Propulsion"
module: "SESA2024 Astronautics"
type: topic
stream: "Spacecraft Subsystems"
order: 7
tags:
  - sesa2024
  - propulsion
  - electric-propulsion
  - rocket-equation
aliases: ["Chapter 7", "Spacecraft propulsion"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]"]
next_topics: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
key_concepts: ["[[Tsiolkovsky Rocket Equation]]", "[[Rocket Performance Parameters]]", "[[Thrust Equation]]", "[[Chemical Propulsion Systems]]", "[[Electric Propulsion Sizing]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch7 - Propulsion Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 7/Chapter 7 - Propulsion - original slides(1)(1).pdf", "02 - Sources/Lectures/Chapter 7/2025 WEEK 3 Lecture 2 - Chapter 7 - Propulsion - complete.pdf"]
---

# SESA2024 07 - Spacecraft Propulsion

> [!abstract] Summary
> - Thrust $T = \sigma V_{ex}$ (momentum) $+ (P_e-P_a)A_e$ (pressure).
> - Specific impulse $I_{sp} = V_{ex}/g_0$ is the impulse per unit weight of propellant. The rocket equation makes ΔV proportional to $I_{sp}$.
> - **Chemical** systems are **energy-limited**: high thrust, $I_{sp}$ 50–450 s.
> - **Electric** systems are **power-limited**: tiny thrust, $I_{sp}$ 700–6000 s. Because the power plant mass grows with $V_{ex}^2$, EP has an **optimum** $V_{ex}\approx(0.5$–$0.85)V_c$, where $V_c = \sqrt{2\eta\beta t_b}$ is the characteristic velocity.

## Key Concepts
- [[Tsiolkovsky Rocket Equation]] · [[Rocket Performance Parameters]] · [[Thrust Equation]] · [[Chemical Propulsion Systems]] · [[Electric Propulsion Sizing]]

---

## 1. Types of propulsion
- **Primary**: launch vehicles and orbit transfer. Thrust 400–10⁶ N; burns of 100–500 s.
- **Secondary**: attitude and orbit control. Thrust 10⁻³–10 N; burns of 10⁻²–1 s, pulsed.

| Type | Thrust (N) | Burn time | P/S | Status |
|---|---|---|---|---|
| Chemical, liquid | up to 10⁷ | s–min | P and S | well developed |
| Chemical, solid | up to 10⁷ | s–min | P | well developed |
| Chemical, hybrid | up to 10⁵ | s–min | P | flown, experimental |
| Electric | 10⁻⁶–10² | up to years | P and S | flown; experimental in many applications |
| Nuclear thermal | up to 10⁵ | min–h | P | experimental (NERVA ended 1973) |
| Solar sail | ~10⁻⁶ N/m² | continuous | P and S | flown, experimental |

## 2. Fundamental performance parameters
**Momentum analysis** (Ch 3):

$$
M\frac{dV}{dt} = \sigma V_{ex}\ \Rightarrow\ T = \sigma V_{ex},\qquad \sigma = -\frac{dM}{dt}
$$

**Thrust equation** (7.1):

$$
T = \sigma V_e+(P_e-P_a)A_e
$$

- **Over-expanded** ($P_e<P_a$): the pressure thrust is negative. The Shuttle, with $P_e\approx0.08$ atm, lost about 20 % of its thrust at sea level.
- **Under-expanded** ($P_e>P_a$): the pressure thrust is positive, but the impulse thrust is reduced.
- The ideal $P_e = P_a$ is unachievable for launchers. Use the **effective exhaust velocity**, $T = \sigma V_{ex}$ (7.2).

See [[Thrust Equation]].

**Total impulse and specific impulse** (7.3, 7.4):

$$
I = \int_0^tT\,dt = V_{ex}M_e,\qquad I_{sp} = \frac{I}{M_eg_0} = \frac{V_{ex}}{g_0}\ \text{(s)},\qquad T = \sigma g_0I_{sp}
$$

- On a graph of $T$ against $t$, $I$ is the **area** under the curve (2018/19 Q1(iv)).
- $I_{sp}\propto\sqrt{T_c/\mathcal M}$: a high chamber temperature and a **low molecular weight** exhaust give a high $I_{sp}$.

**Rocket equation** (7.5, 7.6):

$$
\Delta V = V_{ex}\ln\frac{M_0}{M_b} = g_0I_{sp}\ln\frac{M_0}{M_b},\qquad \boxed{M_e = M_0\left(1-e^{-\Delta V/V_{ex}}\right)}
$$

![[ast_rocket_equation.png|520]]

For launch vehicles, add **gravity and drag losses**: $\Delta V = \Delta V_{ideal}-\Delta V_g-\Delta V_D$. The trade-off: climb steeply to leave the dense air (less drag), but that increases gravity loss. See [[Rocket Staging]] and the SESA2023 notes. (2016/17 and 2014/15 Q2: Ariane 5 staging.)

## 3. Chemical systems
See [[Chemical Propulsion Systems]].

| System | How | $T$ | $I_{sp}$ |
|---|---|---|---|
| **Monoprop (hydrazine)** | N₂H₄ over a Pt/Ir catalyst on Al₂O₃ → hot N₂, NH₃, H₂ | 1–10 N | 230–240 s (290 s power-augmented) |
| **Biprop** MMH/N₂O₄ (hypergolic) | fuel + oxidiser; unified system | 1–400 N | ~310 s |
| Biprop LOX/LH₂ | cryogenic | high | ~450 s |
| Fluorine-based | very hot, corrosive, cryogenic | – | ~410 s |
| **Solid** | fuel and oxidiser cast as a grain; grain shape sets $T(t)$ | up to 10⁷ N | ~260 s |
| **Hybrid** | one solid, one liquid; throttleable and restartable | up to 10⁵ N | – |
| **Cold gas** | N₂ or Ar at high pressure through a regulator | ~20 mN | ~50 s |

- **Hypergolic**: ignites on contact, so no igniter is needed. N₂O₄ boils at 294 K, which makes it storable.
- **Mono/solid trade-offs**: ✔ simpler, more reliable, easy storage, better dry/wet mass ratio. ✘ lower $I_{sp}$, not throttleable, no restart (solid), hazardous handling (hydrazine).
- **Biprop trade-offs**: ✔ higher $I_{sp}$, throttleable, restartable. ✘ complex (less reliable), worse dry/wet ratio, hazardous.
- Solids are "one-shot", used for launchers and GEO apogee motors. They are not used for attitude control, except gimballed launcher nozzles.

## 4. Electric propulsion
EP uses electrical power to accelerate the propellant. It gives very high $V_{ex}$ but a tiny mass flow, so **thrust is small but $I_{sp}$ is very high**. It is **power-limited**, because it needs a separate power plant.

### Simple sizing model
See [[Electric Propulsion Sizing]].
- Masses: $M_0 = M_p+M_W+M_e$ (payload, power plant, propellant). (7.10)
- Jet power: $W_{jet} = \tfrac12\sigma V_{ex}^2 = \eta W$. (7.7)
- Specific power: $\beta = W/M_W$ (W/kg). (7.8)
- Constant flow: $\sigma = M_e/t_b$. (7.9)

$$
M_W = \frac{M_eV_{ex}^2}{2\eta\beta t_b}
$$

$$
\boxed{M_e = \frac{M_0-M_p}{1+V_{ex}^2/V_c^2},\qquad M_W = \frac{M_0-M_p}{1+V_c^2/V_{ex}^2},\qquad V_c = \sqrt{2\eta\beta t_b}}
$$

Substituting into the rocket equation (7.15):

$$
\frac{\Delta V}{V_c} = \frac{V_{ex}}{V_c}\ln\left[\frac{1+(V_{ex}/V_c)^2}{M_p/M_0+(V_{ex}/V_c)^2}\right]
$$

![[ast_ep_optimisation.png|640]]

- **Why a maximum**: raising $V_{ex}$ saves propellant, but $W\propto V_{ex}^2$ makes the power plant heavy. Beyond the optimum, the extra $M_W$ outweighs the saving.
- For maximum payload, $V_{ex}/V_c\approx1$, so $V_{ex}\approx\sqrt{2\eta\beta t_b}$. That needs **long burn times** and **high specific power**.

> [!example] Pluto orbiter (workbook Q12)
> ΔV = 17 km/s, $M_p/M_0$ = 0.1, $t_b$ = 2 yr, $M_0$ = 3000 kg, $\eta$ = 1.
> - Optimum $V_{ex}/V_c\approx0.65$ gives $V_c$ = 26.2 km/s and $V_{ex}$ = 17 km/s ($I_{sp}$ = 1733 s → **ion**).
> - $\beta$ = 5.4 W/kg → **RTG**.
> - $M_e\approx1900$ kg, $M_W\approx800$ kg, $W\approx4.3$ kW, $T\approx0.5$ N.

> [!example] Reading $\Delta V$ off the curve (2024/25 A2)
> $M_p/M_0$ = 0.1 and $I_{sp}$ = 1200 s give $V_{ex}$ = 11 772 m/s.
> - "Optimised" means operating at the peak: $V_{ex}/V_c\approx0.65$ and $\Delta V/V_c\approx0.65$.
> - So $V_c$ = 18.1 km/s and **ΔV ≈ 11.8 km/s**.

### EP devices (examples at $T$ = 50 mN)
| Type | Mechanism | $T$ range | $I_{sp}$ | $\eta$ | Power at 50 mN |
|---|---|---|---|---|---|
| **Resistojet** (electrothermal) | resistive heating to 1600–2500 °C, then a nozzle. Cheap. Xe, water, butane | 5 mN–0.5 N | ≤ 700 s | 0.9 | ~200 W |
| **Arcjet** (electrothermal) | an arc through the gas; hundreds of amps; limited burn hours | 0.05–5 N | 450–1500 s | 0.3 | ~1.2 kW |
| **Electromagnetic** (MPD, Hall) | Lorentz force on a plasma, $\mathbf j\times\mathbf B$; kiloamps; Xe | – | – | – | – |
| **Ion** (electrostatic) | ionise, then accelerate through a potential difference. GEO station-keeping, deep space (Deep Space 1, 1998) | 10⁻⁶–0.5 N | 2000–6000 s | 0.75 | ~1.6 kW |

The **three categories** (2019/20 A1(v)) are **electrothermal, electromagnetic and electrostatic**.

**Chemical vs electric for a lunar mission** (2022/23 A1, 4 marks):
- Chemical: high thrust means short transfers (about 3 days) and impulsive burns for capture and landing, but low $I_{sp}$ means a heavy propellant load.
- EP: very high $I_{sp}$ means much less propellant, but tiny thrust means months-long spiral transfers, a large power demand (big arrays), and no landing capability.
- Landing needs chemical propulsion. For cargo, EP saves mass.

## 5. Impacts on the spacecraft system
- Propulsion dominates the **mass budget**: propellant and tanks.
- **Burn stabilisation** for primary propulsion affects the ACS and the mass distribution (spin-up for solid motors).
- **Thermal**: heaters for tanks, valves and lines (hydrazine freezes at 2 °C); heat soak after engine burns.
- **EP**: power (big arrays or an RTG), thermal dissipation of $(1-\eta)W$, plume contamination of optics and arrays.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 06 - Attitude Control]] · Next: [[SESA2024 08 - Electrical Power Subsystem]]
- Deeper treatment: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]] (SESA2023)

## Year 1 foundation
- Impulse–momentum and recoil (the boy throwing bricks is a discrete rocket): [[FEEG1002 D4 - Linear Impulse and Momentum]].

## Sources
- Chapter 7 lecture (H. Sykulska-Lawrence), equations 7.1–7.16; Fortescue, Stark & Swinerd, Ch. 6
