---
title: "FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers"
module: "FEEG1004 Electronics"
type: topic
stream: "Part A: Electrical Fundamentals and DC Circuits"
order: 3
tags: [feeg1004, fundamentals, dc-circuits, ohms-law, kirchhoff, potential-divider, resistors]
aliases: ["Lecture 3a-3b", "Circuit laws", "KCL and KVL", "Potential divider"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A1 - Electrostatics, Potential and Current]]"]
next_topics: ["[[FEEG1004 A4 - Capacitors]]"]
key_concepts: ["[[Ohm's Law and Resistivity]]", "[[Kirchhoff's Current and Voltage Laws]]", "[[Series and Parallel Resistors]]", "[[Potential Divider]]", "[[Current Divider]]", "[[Hydraulic Analogy for Circuits]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf", "02 - Sources/S1 Fundamentals/S1-W04 Circuits and Capacitors - Interactive.pdf"]
---

# FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers

> [!abstract] Summary
> Five rules solve **every** circuit in this module. Each component then adds its own V–I law.
> 1. **KCL**: currents into a node sum to zero (charge conservation).
> 2. **KVL**: voltages around any loop sum to zero (energy conservation / single-valued potential).
> 3. **Ohm**: $V = IR$ for a resistor.
> 4. **Power**: $P = VI$ into any two-terminal element.
> 5. **Sources**: an ideal voltage source fixes $V$; an ideal current source fixes $I$; a wire fixes $V = 0$.
>
> Shortcuts built from them are series/parallel combination and the potential and current dividers.

## Key Concepts
- [[Ohm's Law and Resistivity]] · [[Kirchhoff's Current and Voltage Laws]] · [[Series and Parallel Resistors]] · [[Potential Divider]] · [[Current Divider]] · [[Hydraulic Analogy for Circuits]]

---

## 1. The hydraulic analogy (L3a)
| Hydraulic | Electrical |
|---|---|
| pressure [Pa] | voltage [V] |
| volume flow rate [m³/s] | current [A] |
| pipe resistance [Pa s/m³] | resistance [Ω = V/A] |
| power = pressure × flow | $P = VI$ |
| conservation of water | KCL |
| pressure difference independent of route | KVL |
| elastic membrane | capacitor ([[FEEG1004 A4 - Capacitors]]) |
| heavy water-wheel (inertia) | inductor ([[FEEG1004 A5 - Inductors and Electrical Resonance]]) |

- The analogy works because the governing equations have the **same form** (for laminar flow).
- The benefit runs both ways: circuit tools solve fluidic networks (microfluidics, pipe networks).

## 2. Ohm's law and resistance
$$
V = IR,\qquad R = \frac{\rho L}{A}
$$

- A current through a resistor creates a voltage drop **in the direction of the current**. The + end is where the current enters.
- Resistance rises with temperature (copper: about **+0.4 %/K**). A lamp filament's resistance is far higher hot than cold, so a bulb draws a surge at switch-on.
- **Meters**: a voltmeter connects **in parallel** (across nodes) and should have infinite resistance. An ammeter connects **in series** and should have zero resistance.

## 3. KCL and KVL
- **KCL**: $\sum I_{in} = 0$ at a node. What goes in must come out.
- **KVL**: $\sum V = 0$ around any closed loop, like the height changes on a walk that returns to its start.
- **Sign discipline**:
  - Pick a current direction. If the answer is negative, the current flows the other way.
  - Walk around the loop adding **rises** (− to + through a source) and subtracting **drops** (across each resistor in the current direction).
  - Use one convention consistently.

**Nodes**: a node is a point with one voltage (measured relative to **ground**, ⏚). Wires may be stretched or components dragged: if the topology is unchanged, the circuit is unchanged. Counting unique nodes correctly is the first step of every analysis.

## 4. Series and parallel
- **Series** (each shared node has *nothing else attached*, so the same current flows): $R_s = R_1 + R_2 + \dots$
- **Parallel** (all start and end on the *same pair of nodes*, so the same voltage appears): $\dfrac{1}{R_p} = \dfrac{1}{R_1} + \dfrac{1}{R_2} + \dots$. For two resistors, "product over sum": $R_p = \dfrac{R_1R_2}{R_1+R_2}$.
  - The parallel result is always **smaller** than the smallest branch. For example 2 Ω ∥ 4 Ω = 4/3 Ω.
  - A **short circuit** (0 Ω) in parallel makes the combination 0 Ω. That is why a shorted bulb goes out.
- Both derivations use exactly Ohm + KCL + KVL (Tutorial 1 Q4).

## 5. Potential and current dividers (L3b)
![[ee_a3_divider_circuits.png|920]]

**Potential divider**:
- KVL with a common current $i = V_{in}/(R_1 + R_2)$ gives

$$
V_{out} = V_{in}\frac{R_1}{R_1 + R_2}
$$

- It is valid **only if negligible current is drawn from the output node**. Otherwise the load appears in parallel with $R_1$.
- Real use: a sensor $R_s$ in a divider converts resistance to voltage, $V_{out} = V_{in}R_s/(R_s + R_f)$. This is **not linear** in $R_s$.
- An op-amp buffer draws no current, so the output stays predictable ([[Loading Effect and Buffering]]).

**Current divider**:

$$
I_1 = I\frac{R_2}{R_1 + R_2}
$$

The *other* resistor goes on top, the mirror image of the potential divider.

> [!example] LED current limiting (L3b)
> - Required: 20 mA at 2 V from 12 V.
> - KVL: $12 - V_R - 2 = 0$, so $V_R = 10$ V. KCL means the resistor carries the LED current, so $R = 10/0.02$ = **500 Ω**.
> - Power: LED 40 mW, resistor **200 mW**, so the circuit is only 17 % efficient.
> - It is still useful: the LED's exponential V–I curve makes it hard to drive from a voltage source directly. The resistor makes the current insensitive to supply variation.
> - A standard axial resistor is rated 0.25 W, so check that the resistor can dissipate its share.

> [!example] Interactive W4 checks
> - 8 V across two 50 Ω in series: $I = 8/100$ = **0.08 A** in each (KCL). $P_{R_2} = I^2R$ = **320 mW**.
> - Power in $R_2$ when it sits **directly across** the source is $V_s^2/R_2$, **independent of $R_1$**.
> - Two identical batteries in parallel give the **same voltage** as one; each supplies half the current. In series they add, and the bulb is brighter.

## Year 2 bridge
- The divider with a buffer is the first block of every sensor signal chain ([[Measurement Chain]], [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]).
- Loading error $Z_{out}/(Z_{out} + Z_{in})$ is the divider formula applied to meter and sensor impedances ([[Loading Effect and Buffering]]).
- KCL/KVL become the **nodal and mesh matrix methods** of circuit simulators. Stiffness-matrix assembly in FE is the same bookkeeping ([[Global Stiffness Matrix Assembly]], [[FEEG1004 A6 - Mesh Analysis]]).
- **Spacecraft power buses**: harness mass and $I^2R$ loss set bus voltage choices (28 V vs 100 V buses) ([[SESA2024 08 - Electrical Power Subsystem]]).

## Links
- Previous: [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]] · Next: [[FEEG1004 A4 - Capacitors]]
- Worked problems: [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]] (Q2–Q4)

## Sources
- Recorded lecture 3a (KCL, resistors) and 3b (KVL, dividers), P. Glynne-Jones; Week 4 interactive session.
