---
title: "FEEG1004 D2 - Impedance and Phasor Circuit Analysis"
module: "FEEG1004 Electronics"
type: topic
stream: "Part D: AC Circuit Analysis"
order: 2
tags: [feeg1004, ac-circuits, impedance, reactance, phasor-analysis, civil, inductive-load, capacitive-load]
aliases: ["AC Analysis 02", "Impedance", "Generalised Ohm's law", "Phasor circuit analysis", "CIVIL"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]", "[[FEEG1004 A6 - Mesh Analysis]]"]
next_topics: ["[[FEEG1004 D3 - AC Filters and Bode Plots]]"]
key_concepts: ["[[Complex Impedance]]", "[[Phasor Representation]]", "[[Current Divider]]", "[[Potential Divider]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W22-23 AC Analysis 02 - Impedance and Phasor Analysis - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"]
---

# FEEG1004 D2 - Impedance and Phasor Circuit Analysis

> [!abstract] Summary
> In phasor form, every element obeys a **generalised Ohm's law** $\mathbf V = Z\mathbf I$:
> $$Z_R = R,\qquad Z_L = j\omega L = jX_L,\qquad Z_C = \frac{1}{j\omega C} = -jX_C$$
> The whole DC toolkit (series/parallel, dividers, KCL/KVL, mesh, Thévenin, superposition) then works unchanged with complex numbers.
> - **CIVIL**: in a **C**apacitor **I** leads **V**; in an inductor (**L**) **V** leads **I**.
> - A load with $\Im(Z) > 0$ is **inductive** (current lags); with $\Im(Z) < 0$ it is **capacitive** (current leads).

## Key Concepts
- [[Complex Impedance]] · [[Phasor Representation]] · [[Current Divider]] · [[Potential Divider]]

---

## 1. Why phasors: the RL example (Niu notes)
- In the time domain, $L\,di/dt + Ri = \sqrt2V\cos\omega t$ needs a trial solution $i = \sqrt2I\cos(\omega t + \phi)$ and messy trigonometry.
- Replace the waveforms by complex exponentials and the derivative becomes multiplication by $j\omega$:

$$
(R + j\omega L)\mathbf I = \mathbf V\ \Rightarrow\ \mathbf I = \frac{V\angle0}{\sqrt{R^2 + \omega^2L^2}\ \angle\tan^{-1}(\omega L/R)}
$$

- **Procedure**:
  1. Draw the **phasor-domain circuit**: sources become phasors, elements become impedances.
  2. Solve it like a DC circuit with complex numbers.
  3. Convert back: $\mathbf I = I\angle\phi\ \to\ i(t) = \sqrt2I\cos(\omega t + \phi)$.

## 2. Impedance of R, L and C
| Element | Resistance $R$ | Reactance $X$ | Impedance $Z$ | Phase |
|---|---|---|---|---|
| resistor | $R$ | 0 | $R$ | V, I in phase |
| inductor | 0 | $X_L = \omega L$ | $j\omega L = \omega L\angle90°$ | I **lags** V by 90° |
| capacitor | 0 | $X_C = 1/\omega C$ | $-j/\omega C = X_C\angle-90°$ | I **leads** V by 90° |

- **Inductor**: $v = L\,di/dt$ turns $\sqrt2I\cos(\omega t + \theta)$ into $\sqrt2\omega LI\cos(\omega t + \theta + 90°)$, i.e. multiplication by $j\omega L$.
- **Frequency limits**:
  - an inductor is a **short at DC** and **open at high frequency**;
  - a capacitor is **open at DC** and a **short at high frequency**.
  - These limits are how filters are recognised ([[FEEG1004 D3 - AC Filters and Bode Plots]]).

![[ee_d2_rlc_phase.png|1000]]

![[ee_d2_reactance_frequency.png|760]]

> [!example] Single-element checks (AC 02)
> - **Resistive heater** 60 Ω on 240 V: $\mathbf I = 240\angle0/60$ = **4∠0° A**, in phase; $P = I^2R$ = **960 W**.
> - **Capacitor** on $v = 325\cos(314t - 20°)$, i.e. 229.8∠−20° V rms, with 200 µF:
>   - $X_C = 1/(314\times200\times10^{-6})$ = 15.9 Ω, so $\mathbf I$ = **14.4∠70° A**, leading by 90°.
>   - The slide rounds 325/√2 to 240 V and quotes 15∠70° A.

## 3. Series and parallel combinations
> [!example] Series RC (AC 02): 10 Ω + 100 µF on $100\sqrt2\cos314t$
> - $X_C = 1/(314\times10^{-4})$ = 31.85 Ω, so $Z = 10 - j31.85$ = 33.4∠−72.6° Ω.
> - $\mathbf I = 100\angle0/Z$ = **3.0∠72.6° A** (leads: capacitive).
> - $\mathbf V_R$ = 30∠72.6° V and $\mathbf V_C$ = 95.5∠−17.4° V.
> - The **voltage triangle**: $\sqrt{30^2 + 95.5^2}$ = 100 V. The magnitudes do not add ($30 + 95.5\neq100$); the phasors do.
> - The potential divider gives $\mathbf V_C$ directly: $\mathbf V_C = \mathbf VZ_C/(Z_R + Z_C)$.

> [!example] Series RLC (Niu Example 1; AC 02 slides): 3.6 Ω, 1.2 mH, 0.04 mF at ω = 4000 rad/s, 140∠−10° V
> - $Z = 3.6 + j4.8 - j6.25$ = 3.88∠−21.9° Ω, so $\mathbf I$ = **36.1∠11.9° A**.
> - $\mathbf V_R$ = 130∠11.9°, $\mathbf V_L$ = 173∠102° and $\mathbf V_C$ = 225∠−78.1° V. The individual element voltages exceed the supply, which is normal near resonance.
> - Back in time: $i = 36.1\sqrt2\cos(4000t + 11.9°)$ A.
>
> ![[ee_d2_rlc_example.png|900]]

> [!example] Series–parallel (Niu notes, Fig. 24): 10 Ω + [j20 ∥ (15 − j30)], 100∠20° V
> - $Z_p = \dfrac{j20(15 - j30)}{15 - j10}$ = 37.2∠60.3° = 18.5 + j32.3 Ω. Use polar to multiply and divide, Cartesian to add.
> - $Z = 28.5 + j32.3$ = 43.1∠48.6° Ω, so $\mathbf I$ = **2.32∠−28.6° A** (inductive: lags).
> - Divider twice: $\mathbf V_1$ = 86.4∠31.6° V, then $\mathbf V_C = \mathbf V_1(-j30)/(15 - j30)$ = **77.3∠5.1° V**.

## 4. Inductive and capacitive loads (AC 03)
![[ee_d2_impedance_triangles.png|880]]

- The **impedance triangle** has sides $R$, $X$ and $|Z|$. It is the voltage triangle divided by $I$.
- Whether a load is inductive or capacitive depends on the **net** reactance, not on which components are present. A load with an inductor can still be capacitive.
- Examples:
  - $1 + j5 - j2 = 1 + j3$ Ω: inductive, $\mathbf I = 10/(1 + j3)$ = 3.16∠−71.6° A;
  - $2 + j1 - j6 = 2 - j5$ Ω: capacitive, 1.86∠+68.2° A.

> [!example] Reactance and impedance vs frequency (AC 03): 2.2 kΩ + 47 nF
> - 100 Hz: $X_C$ = 33.9 kΩ, $|Z|$ = 33.9 kΩ (the capacitor dominates).
> - 10 kHz: $X_C$ = 339 Ω, $|Z|$ = 2.23 kΩ (the resistor dominates).

## 5. Phasor diagrams (Niu notes, Fig. 22–23)
- **Graphical KVL**: draw $\mathbf V_R$ parallel to $\mathbf I$, then $\mathbf V_L$ at +90° to $\mathbf I$, tip-to-tail. The closing side is the source.
- Example: a source feeds a load through a 2 Ω + j5 Ω cable carrying $\mathbf I$ = 2∠−30° A. Then $\mathbf V_R$ = 4∠−30° V and $\mathbf V_L$ = 10∠60° V, and the source phasor is $\mathbf V_R + \mathbf V_L + \mathbf V_{load}$.

## Year 2 bridge
- $Z(j\omega)$ is a **transfer function** evaluated on the imaginary axis. $1/Z$ for a series RLC is the admittance with a resonant peak, the electrical twin of the receptance FRF ([[Transfer Function]], [[Frequency Response Function]], [[FEEG1002 D6 - Single Degree of Freedom Vibration]]).
- **Capacitive and inductive sensors** are read through their reactance at high frequency (>100 kHz for pF sensors) ([[Capacitive Displacement Sensor]]).
- **Antenna and RF matching** in communications uses complex impedances ([[SESA2024 09 - Communications]]).

## Links
- Previous: [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]] · Next: [[FEEG1004 D3 - AC Filters and Bode Plots]]
- Worked problems: [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions]] (Q3–Q5)

## Sources
- AC Analysis 02–03 slides; Niu AC lecture notes (Examples, Figs 6–24); Hughes Ch. 10, 13, 15.
