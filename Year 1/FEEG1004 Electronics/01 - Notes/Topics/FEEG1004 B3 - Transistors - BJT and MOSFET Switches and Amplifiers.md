---
title: "FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers"
module: "FEEG1004 Electronics"
type: topic
stream: "Part B: Electronics"
order: 3
tags: [feeg1004, electronics, transistor, bjt, mosfet, jfet, switch, amplifier, common-emitter]
aliases: ["EL2 transistors", "BJT", "MOSFET", "Transistor switch", "Common-emitter amplifier"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 B1 - Semiconductors and Diodes]]"]
next_topics: ["[[FEEG1004 B4 - Operational Amplifiers]]"]
key_concepts: ["[[Bipolar Junction Transistor]]", "[[MOSFET]]", "[[Transistor as a Switch]]", "[[Flyback Diode]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W08-EL2 Transistors - Recorded.pdf"]
---

# FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers

> [!abstract] Summary
> A transistor lets a **small control signal** govern a **large current**.
> - **BJT (npn)**: base current controls collector current. The base–emitter junction behaves like a 0.7 V diode.
>   - **Active mode**: $I_C = \beta I_B$ ($\beta\approx100$–200), used in amplifiers.
>   - **Saturation**: fully ON, $V_{CE}\approx0.2$ V, used as a switch.
>   - **Cut-off**: $I_B = 0$, OFF.
> - **MOSFET (n-channel enhancement)**: gate **voltage** above threshold opens a channel. The gate draws almost no current. When ON it behaves as a small resistance $R_{DS(on)}$.
>
> Exam emphasis: calculate the voltages and currents in transistor circuits. You will not be asked to explain the device physics.

## Key Concepts
- [[Bipolar Junction Transistor]] · [[MOSFET]] · [[Transistor as a Switch]] · [[Flyback Diode]]

---

## 1. Why transistors: the Arduino motor problem (W8)
- An Arduino digital pin can source only about **20 mA** continuously. A motor draws hundreds of mA, so driving it directly **destroys the pin**.
- Use the pin to switch a transistor, and the transistor to switch the motor from a separate supply.
- Of the options in the W8 question, only circuits C and E work.

| Pin | Current limit | Source |
|---|---|---|
| digital I/O | 20 mA | microcontroller chip |
| 5 V pin | ~500 mA | on-board regulator |
| 3.3 V pin | 50–100 mA | regulator |

## 2. The bipolar junction transistor (Mills §1.6.1)
- An npn transistor is a thin, lightly doped p **base** between an n **emitter** (heavily doped) and an n **collector**.
- With the base–emitter junction forward-biased and base–collector reverse-biased, about 99 % of the emitter electrons cross the narrow base into the collector. Hence $I_C\approx100I_B$.
- **Symbol**: the arrow on the emitter points in the direction of conventional current (out of the emitter for npn).

![[ee_b3_bjt_characteristics.png|820]]

| Mode | Condition | Model |
|---|---|---|
| **Cut-off** | $I_B = 0$ ($V_{BE} < 0.7$ V) | open switch, $I_C = 0$ |
| **Active (linear)** | the circuit can supply the demanded $I_C$ | $V_{BE} = 0.7$ V, $I_C = \beta I_B$ |
| **Saturation** | $\beta I_B$ exceeds what the load allows | closed switch, $V_{CE}\approx0.2$ V, $I_C < \beta I_B$ |

The **load line** (orange) of the collector circuit meets the curves at the operating point. A switch lives at its two ends.

## 3. Transistor switches (§1.6.7, W8)
![[ee_b3_transistor_switches.png|900]]

> [!example] BJT switching a 300 mA power LED from a 5 V signal (W8)
> - **Switch open**: no base current, so $I_C$ = **0**.
> - **Minimum base current** for 300 mA at $\beta = 100$: $I_B = 0.3/100$ = **3 mA**.
> - **$R_B$ for exactly that**: $R_B = (5 - 0.7)/0.003$ = **1.43 kΩ**.
>   - A **larger** $R_B$ gives too little base current, a dim LED and a hot transistor (active region, large $V_{CE}$).
>   - A **smaller** $R_B$ over-drives the base (fine for saturation, but it wastes current and risks the base junction).
>   - Designers deliberately choose $R_B$ smaller to guarantee saturation and let $R_L$ set the current.
> - **$R_L$** (saturated, $V_{CE}$ = 0.2 V, LED $V_F$ = 2.4 V): $R_L = (12 - 2.4 - 0.2)/0.3$ = **31.3 Ω**.

> [!example] MOSFET motor switch (W8)
> - An Arduino drives the gate directly; the gate draws almost no current. Add a **flyback diode** across the motor to protect the MOSFET at turn-off ([[Flyback Diode]]).
> - With $R_{DS(on)}$ = 0.04 Ω and a 100 W dissipation limit: $I = \sqrt{P/R} = \sqrt{100/0.04}$ = **50 A**.
> - The heat goes into a heatsink.
> - The datasheet's 200 W absolute maximum is not usable continuously because of limits on the chip conductors and the temperature.

**Mills circuit examples**:
- **Light-activated lamp**: a photodiode + 1.8 kΩ divider drives a MOSFET gate. In the dark the photocurrent falls, the gate voltage rises above threshold and the lamp turns ON. A MOSFET suits this because it needs no gate current.
- **Thermostat heater**: an NTC thermistor divider drives a BJT that energises a relay. As the room cools, $R_{NTC}$ rises, the base voltage rises and the relay closes. A **protective (flyback) diode** sits across the relay coil.

## 4. The common-emitter amplifier (§1.6.2)
- In active mode, $V_{out} = V_{CC} - I_CR_C = V_{CC} - \beta I_BR_C$. A small rise in $I_B$ gives a larger **fall** in $V_{out}$: the amplifier is **inverting** (180° phase shift).
- **Biasing**: $R_B$ from the supply sets a quiescent $I_B$ so that $V_C'\approx V_{CC}/2$. The AC signal can then swing both ways without cutting off or saturating.
- **Coupling capacitors** $C_1$ and $C_2$ pass the AC signal but **block DC**, so the bias is not disturbed by the source or load. They form high-pass filters with the circuit resistances.

![[ee_b3_common_emitter_waveforms.png|760]]

## 5. Field-effect transistors (§1.6.3–1.6.6)
| Device | Control | Notes |
|---|---|---|
| JFET (n-channel) | negative $V_{GS}$ widens the depletion regions and squeezes the channel | very high input resistance: microphone preamps, meter inputs |
| MOSFET, enhancement | positive $V_{GS}$ above threshold (~1–2 V) forms an inversion-layer channel | OFF at zero gate voltage; the standard switch; insulated gate means ~no gate current |
| MOSFET, depletion | channel exists at $V_{GS} = 0$; negative $V_{GS}$ depletes it, positive enhances it | versatile but less common |

- Terminals correspond to the BJT's: drain ↔ collector, gate ↔ base, source ↔ emitter.
- FETs are less temperature-sensitive and denser (large-scale ICs) but have lower gain than BJTs.
- The **common-source amplifier** (Mills Fig. 1.6.6) is the MOSFET analogue of the common emitter and is also inverting.
- A **Darlington pair** (two BJTs) has current gain $\beta_1\beta_2$.

## Year 2 bridge
- **Motor drives**: H-bridges and choppers are arrays of these switches ([[DC Motor Speed Control]], [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]). Reaction wheels and servo actuators use them ([[Reaction Wheels and Momentum Dumping]]).
- **Actuator interfacing** for control systems: a controller output (µC pin, DAC) must be power-amplified to drive the plant ([[SESA2027 B1 - Control System Fundamentals and PID Control]]).
- **Spacecraft**: MOSFETs switch power to payloads (latching current limiters), and radiation shifts their thresholds ([[SESA2024 08 - Electrical Power Subsystem]], [[Space Environment Hazards]]).

## Links
- Previous: [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]] · Next: [[FEEG1004 B4 - Operational Amplifiers]]
- Worked problems: [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]]

## Sources
- Mills notes §1.6; Week 8 recorded/interactive session (EL2).
