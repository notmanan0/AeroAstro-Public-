---
title: "FEEG1004 D4 - AC Power and Power Factor"
module: "FEEG1004 Electronics"
type: topic
stream: "Part D: AC Circuit Analysis"
order: 4
tags: [feeg1004, ac-circuits, power, active-power, reactive-power, complex-power, power-factor, pfc]
aliases: ["AC Analysis 04", "AC power", "Power factor", "Complex power", "Power triangle", "Power factor correction"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"]
next_topics: ["[[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]"]
key_concepts: ["[[Active, Reactive and Apparent Power]]", "[[Power Factor Correction]]", "[[RMS Value]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W25 AC Analysis 04 - AC Power - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"]
---

# FEEG1004 D4 - AC Power and Power Factor

> [!abstract] Summary
> Instantaneous AC power pulses at 2ω, so we describe it by three averages:
> - **Active** $P = VI\cos\phi$ [W]: real energy (heat, work). Only resistance absorbs it.
> - **Reactive** $Q = VI\sin\phi$ [VAR]: energy sloshing in and out of L and C. Inductors **absorb** it ($Q > 0$); capacitors **generate** it ($Q < 0$).
> - **Complex** $\mathbf S = \mathbf V\mathbf I^* = P + jQ$, with **apparent** power $|\mathbf S| = VI$ [VA].
>
> **Power factor** $\cos\phi = P/|S|$. A low power factor means more current for the same useful power, so bigger losses and voltage sag. Mostly-inductive loads are corrected with **parallel capacitors**.

## Key Concepts
- [[Active, Reactive and Apparent Power]] · [[Power Factor Correction]] · [[RMS Value]]

---

## 1. Power in R, L and C
With $v = \sqrt2V\cos\omega t$:

| Element | $p(t)$ | Average $P$ | Reactive $Q$ |
|---|---|---|---|
| R | $VI(1 + \cos2\omega t)$, never negative | $VI = I^2R = V^2/R$ | 0 |
| L | $VI\sin2\omega t$ | 0 | $+VI = I^2X_L = V^2/X_L$ (absorbs) |
| C | $-VI\sin2\omega t$ | 0 | $-VI = -I^2X_C$ (generates) |

- An inductor stores magnetising energy for a quarter cycle and returns it for the next: on average nothing is consumed. But the current still flows, causes line losses and drops voltage. That is why $Q$ matters.
- The **peak** of the instantaneous power in a pure reactance equals $|Q|$.

![[ee_d4_instantaneous_power.png|1000]]

> [!example] Recap practice (AC 04): 10 A rms through each element
> - 4 Ω resistor: $P = I^2R$ = **400 W**, $Q$ = 0.
> - 5 Ω inductive reactance: $P$ = 0, $Q = I^2X_L$ = **+500 VAR** (absorbed).
> - 3 Ω capacitive reactance: $P$ = 0, $Q = -I^2X_C$ = **−300 VAR** (generated).
> - Energy conservation holds for **P and Q separately**: the supply's P and Q are the sums over all elements.

## 2. Mixed loads and the power triangle
For $\mathbf V = V\angle\theta_v$ and $\mathbf I = I\angle\theta_i$, with $\phi = \theta_v - \theta_i$ (positive for an inductive load):

$$
P = VI\cos\phi,\qquad Q = VI\sin\phi,\qquad \mathbf S = \mathbf V\mathbf I^* = P + jQ,\qquad |\mathbf S| = VI = \sqrt{P^2 + Q^2}
$$

- $\mathbf I^*$ is the **complex conjugate**. Using $\mathbf I$ instead would give the wrong sign of $Q$.

> [!example] AC 04 Example 1: 50∠0° V into 6 + j11.31 Ω
> - $|Z|$ = 12.8 Ω at 62.05°, so $\mathbf I$ = **3.905∠−62.05° A**.
> - $P = I^2R$ = **91.5 W**, $Q = I^2X$ = **172.5 VAR**.
> - Check: $\mathbf S = \mathbf V\mathbf I^* = 50\times3.905\angle62.05°$ = 195.3∠62.05° = 91.5 + j172.5 ✔. Apparent power **195.3 VA**, pf = 0.47 lagging.

## 3. Why power factor matters
- Utilities charge for **kWh** (fuel ∝ P). A **poor pf** (below about 0.85) means extra current, so more transmission loss and bigger generators and cables. Customers pay a penalty or correct it.
- **Niu notes experiment**: a 50 W load at 10 V fed through a 0.2 + j1 Ω line, with the power factor varied:

![[ee_d4_pf_effects.png|900]]

- Loss $= I^2(0.2)$ with $I = 50/(10\cos\phi)$: 5 W at pf 1 but 13.9 W at pf 0.6.
- **Lagging** loads need a much higher source voltage (large regulation); **leading** loads push the load voltage *above* the source (the Ferranti-type rise). Neither extreme is desirable.
- Regulation is defined as $(|V_S| - |V_L|)/|V_S|$.

## 4. Power-factor correction
- Most loads (motors, transformers) are **inductive**. Supply their reactive power **locally** with a capacitor bank across the load, whose $Q_C = -V^2\omega C$.
- **P is unchanged**; Q, |S| and the line current fall.

> [!example] Niu notes: 80 kVA, pf 0.5 lagging, 400 V, 50 Hz; add 1 mF
> - $P = 80\times0.5$ = **40 kW** and $Q = 80\sin60°$ = **69.3 kVAR**.
> - $Q_C = -400^2(2\pi50)(10^{-3})$ = **−50.3 kVAR**.
> - The new $Q$ = 19.0 kVAR, $|S|$ = 44.3 kVA, so **pf = 0.90 lagging**. The notes round $Q_C$ to 50 and quote 44 kVA and 0.9.
>
> ![[ee_d4_power_triangle_pfc.png|640]]

**Tutorial 8 Q3** adds the cable impedance, so the load voltage and the capacitor's Q come from a full phasor solution. See [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions]].

## Year 2 bridge
- **Aircraft AC buses** (115 V, 400 Hz) run many inductive loads (motors, transformer-rectifier units). Generators are rated in kVA, not kW, because the current (and hence heating) depends on |S| ([[FEEG1004 C3 - Transformers and AC Power Transmission]]).
- **Spacecraft power budgets** are DC (P only), but the same book-keeping of sources, losses and loads drives array and battery sizing ([[SESA2024 08 - Electrical Power Subsystem]], [[Battery Sizing]]).
- Three-phase balanced power is constant; single-phase pulses at 2ω, which shows up as torque ripple in single-phase motors ([[Three-Phase Star and Delta Connections]]).

## Links
- Previous: [[FEEG1004 D3 - AC Filters and Bode Plots]] · Next: [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]
- Worked problems: [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions]] (Q3)

## Sources
- AC Analysis 04 slides; Niu AC notes (power, power factor, correction example, Figs 27–40); Hughes Ch. 12–13.
