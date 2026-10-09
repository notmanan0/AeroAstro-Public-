---
title: "FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions"
module: "FEEG1004 Electronics"
type: tutorial
stream: "Part D: AC Circuit Analysis"
tags: [feeg1004, tutorial-solutions, phasors, complex-numbers, impedance, current-divider]
sheet: "Tutorial sheet 7 - Problems on AC Circuits (1)"
theory_notes: ["[[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]", "[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"]
key_concepts: ["[[Phasor Representation]]", "[[Complex Impedance]]", "[[Current Divider]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance.pdf", "02 - Sources/Tutorial Sheets/Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance - Solutions.pdf"]
---

# FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions

> [!abstract] Sheet Info
> Complex arithmetic, time-domain → phasor conversion, a series RLC impedance, a series–parallel impedance, and a two-stage current divider.
> - An official solution sheet exists (its Q1/Q2 numbering is swapped relative to the question sheet). Every answer is reproduced ✔.
> - One printed value (Q1g) is a slip, noted below.

## Theory Links
- [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]] · [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]] · [[Complex Impedance]]

---

## Q1: Complex-number operations
| Part | Working | Result |
|---|---|---|
| (a) | $(6.21 + j3.24) + (4.13 - j9.47)$ | **10.34 − j6.23** ✔ |
| (b) | $(-24 + j12) - (35 - j16) - (17 - j24)$ | **−76 + j52** ✔ |
| (c) | $(4 + j2)(3 + j4) = 12 + j16 + j6 - 8$ | **4 + j22** ✔ |
| (d) | $\dfrac{1}{0.2 + j0.5} = \dfrac{0.2 - j0.5}{0.29}$ | **0.69 − j1.72** ✔ |
| (e) | $\dfrac{14 + j5}{4 - j} = \dfrac{(14 + j5)(4 + j)}{17} = \dfrac{51 + j34}{17}$ | **3 + j2** ✔ |
| (f) | $6 + j9$; $-21.4 + j33.3$ (**2nd quadrant**: $180° - 57.3°$) | **10.8∠56.3°**; **39.6∠122.7°** ✔ |
| (g) | $10\angle20° = 10\cos20° + j10\sin20°$; $142\angle-260.3°$ | **9.40 + j3.42**; **−23.9 + j140** |

For (g), the solution sheet prints 9.58 + j3.49 for the first value, which is inconsistent with $|z|$ = 10 (it would have magnitude 10.2). The correct value is 9.40 + j3.42.

## Q2: Time functions → phasors (rms, cosine reference)
- **(a)** $v = 50\sqrt2\cos(377t - 35°)$ gives **$\mathbf V$ = 50∠−35° V** ✔.
- **(b)** $v = 83.6\sin(400t - 15°) = 59.1\sqrt2\cos(400t - 105°)$ gives **59.1∠−105° V** ✔ (convert sine to cosine: −90°).
- **(c)** $i = 90.4\sqrt2\cos(754t - 48°)$ mA gives **90.4∠−48° mA** ✔.
- **(d)** $i = 3.46\sin(815t + 30°) = 2.45\sqrt2\cos(815t - 60°)$ gives **2.45∠−60° A** ✔.

## Q3: 200 Ω + 150 mH + 2 µF in series at 400 Hz
- $\omega = 2\pi(400)$ = 2513 rad/s.
- $X_L = \omega L$ = 377 Ω and $X_C = 1/\omega C$ = 199 Ω.

$$
Z = 200 + j377 - j199 = 200 + j178 = 268\angle41.7°\ \Omega\ ✔
$$

The net reactance is positive, so the circuit is **inductive** at 400 Hz; its resonance would be at 291 Hz. The phasor-domain circuit is the three impedances in series.

![[ee_t7_phasor_diagrams.png|900]]

## Q4: Impedance seen at A–B
The circuit is 1 Ω in series with the parallel pair $(0.2 - j1)\parallel(0.5 + j3)$:

$$
Z_{AB} = 1 + \frac{(0.2 - j1)(0.5 + j3)}{(0.2 - j1) + (0.5 + j3)} = 1 + \frac{3.1 + j0.1}{0.7 + j2} = 1.53 - j1.37\ \Omega = 2.05\angle-41.8°\ \Omega\ ✔
$$

The result is capacitive: the −j1 branch dominates the parallel pair.

## Q5: Currents $\mathbf I_1$ and $\mathbf I_2$ from a 20∠45° A source
**Topology**: the source feeds a 2 Ω shunt; in parallel with it is a j3 Ω series branch ($\mathbf I_1$) leading to 4 Ω ($\mathbf I_2$) in parallel with −j15 Ω.
- **Impedance to the right of the 2 Ω**:

$$Z_r = j3 + \frac{4(-j15)}{4 - j15} = 3.73 + j2.00 = 4.24\angle28.2°\ \Omega$$

- **First current divider** (2 Ω vs $Z_r$):

$$\mathbf I_1 = \frac{2}{2 + Z_r}\times20\angle45° = 5.93 + j2.86 = 6.59\angle25.7°\ \mathrm A\ ✔$$

- **Second current divider** (4 Ω vs −j15 Ω):

$$\mathbf I_2 = \frac{-j15}{4 - j15}\times\mathbf I_1 = 6.25 + j1.19 = 6.36\angle10.8°\ \mathrm A\ ✔$$

  The solution sheet rounds this to 6.4∠10.8°.
- **Check** by KCL: the 2 Ω branch carries $\mathbf I_s - \mathbf I_1$ = 13.9∠54.1° A, and the phasors close (right panel of the figure above).

## Sources
- FEEG1004 Tutorial sheet 7 and its solutions; all values re-computed.
