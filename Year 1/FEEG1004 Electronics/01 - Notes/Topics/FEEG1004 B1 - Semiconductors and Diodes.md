---
title: "FEEG1004 B1 - Semiconductors and Diodes"
module: "FEEG1004 Electronics"
type: topic
stream: "Part B: Electronics"
order: 1
tags: [feeg1004, electronics, semiconductors, band-theory, doping, pn-junction, diode, zener]
aliases: ["EL1 semiconductors", "Band theory", "P-N junction", "Diode characteristic"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"]
next_topics: ["[[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]"]
key_concepts: ["[[Band Theory and Semiconductor Doping]]", "[[P-N Junction Diode]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W07-EL1 Semiconductors Diodes and Limiters - Interactive.pdf"]
---

# FEEG1004 B1 - Semiconductors and Diodes

> [!abstract] Summary
> Semiconductors sit between conductors and insulators.
> - Their narrow **band gap** (1.1 eV in Si) lets heat promote a few electrons, leaving mobile **holes**. **Doping** multiplies the carriers: group V donors make **n-type**, group III acceptors make **p-type**.
> - Joining p and n forms a **depletion region** with a built-in field. The junction conducts one way only:
>   - **forward bias** (anode +) conducts once about 0.7 V (Si) is overcome;
>   - **reverse bias** passes only µA leakage until **breakdown**, which Zener diodes exploit.
> - For circuit analysis a diode is a switch that is closed (with 0.7 V drop) or open.

## Key Concepts
- [[Band Theory and Semiconductor Doping]] · [[P-N Junction Diode]]

---

## 1. Band theory (Mills §1.2)
- Electrons in an isolated atom occupy discrete levels. Pack many atoms into a solid and each level **splits into a band**, with forbidden gaps between bands.
- Only the top two bands matter: the **valence band** (bonding electrons) and the **conduction band** (mobile electrons).

![[ee_b1_energy_bands.png|880]]

| Material | Band structure | Conduction |
|---|---|---|
| Conductor | conduction band part-filled or overlapping | vacant states everywhere: conducts |
| Insulator | full valence band, **wide** gap | no vacant reachable states |
| Semiconductor | full valence band, **narrow** gap (1.1 eV) | occasional thermal promotion: conducts slightly, and **more when hot** |

- The last row is why semiconductor electronics are **temperature-sensitive**, and why NTC thermistors work ([[RTDs and Thermistors]]).

## 2. Holes and doping (§1.3)
- A promoted electron leaves a **hole** in the valence band. Neighbouring electrons hop into it, so the hole drifts towards the negative terminal like a **positive carrier**.
- **Intrinsic** (pure) silicon conducts very little. **Extrinsic** (doped) silicon has controlled carriers:

| Dopant | Group | Effect | Type | Majority carrier |
|---|---|---|---|---|
| phosphorus | V (5 valence e⁻) | one loosely bound electron just below the conduction band ("donor") | **n-type** | electrons |
| boron | III (3 valence e⁻) | a hole just above the valence band ("acceptor") | **p-type** | holes |

- Thermally generated carriers of the other sign are **minority carriers**.

## 3. The p-n junction (§1.4)
- **Bring p and n together**:
  - electrons diffuse n → p and holes diffuse p → n, recombining near the boundary;
  - fixed ions remain: + on the n side, − on the p side, forming the **depletion region**;
  - the resulting field (pointing n → p) grows until drift balances diffusion.
- **Reverse bias** (+ to n): the carriers are pulled away and the depletion region **widens**. Only a tiny thermal **leakage** current flows.
- **Forward bias** (+ to p): the depletion region **narrows**. Once the built-in step (≈0.7 V Si, ≈0.3 V Ge) is overcome, current flows freely.
- **Symbol**: the arrow points **p → n**, anode → cathode, the direction of forward conventional current. The bar marks the cathode.
- **LEDs**: recombination releases energy as light in direct-band-gap materials. **Photodiodes** run the process backwards ([[Transistor as a Switch]] light-sensor example).

## 4. The diode V–I characteristic (§1.5.1)
![[ee_b1_diode_vi.png|900]]

| Region | Behaviour | Model used in this course |
|---|---|---|
| forward, $V_D\gtrsim0.7$ V | current rises steeply (exponentially); $V_D$ barely changes | **0.7 V constant drop** (or ideal 0 V) |
| reverse, $0 > V_D > -V_{BD}$ | µA leakage, rising with temperature | **open circuit** |
| breakdown $V_D\approx-V_Z$ | voltage fixed, current free | **Zener regulator** |

- **"Very ideal" diode** (0 V drop): used for quick analysis (Tutorial 3 Q1–Q3).
- **Realistic ideal diode** (0.7 V drop): used when the drop matters (Tutorial 3 Q5, Q6).

**Analysis recipe**:
1. Assume each diode is ON or OFF.
2. Replace ON with a 0.7 V source (or a short) and OFF with an open circuit.
3. Solve and **check consistency**: an ON diode must carry forward current; an OFF diode must see less than 0.7 V forward.
4. If a check fails, flip the assumption.

> [!example] LED current limiting (W7)
> - An LED needs 2.1 V at 60 mA from 5 V: $R = (5 - 2.1)/0.06$ = **48 Ω**.
> - The same logic as the lecture 3b LED circuit ([[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]). Each LED colour has its own forward voltage.

## Year 2 bridge
- **Solar cells** are large-area p-n junctions under illumination. The photocurrent flows in the reverse direction, and the I–V curve is a shifted diode curve ([[Solar Cells and Arrays]], [[SESA2024 08 - Electrical Power Subsystem]]).
- **Radiation** in orbit creates defects in the silicon lattice, degrading solar-cell efficiency and shifting transistor thresholds ([[Space Environment Hazards]]).
- **Temperature dependence** of carrier numbers makes semiconductor sensors possible (thermistors, IC temperature sensors for cold-junction compensation) and forces thermal control of avionics ([[Thermocouples and Cold-Junction Compensation]], [[SESA2024 10 - Thermal Control]]).

## Links
- Next: [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- Worked problems: [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]] (Q1)

## Sources
- J. Mills, *Diodes, Transistors, Op-amps and Digital Electronics* (2015), §1.1–1.5.1; Week 7 interactive session (X. Niu).
