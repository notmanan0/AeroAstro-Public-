---
title: "FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions"
module: "FEEG1004 Electronics"
type: tutorial
stream: "Part D: AC Circuit Analysis"
tags: [feeg1004, tutorial-solutions, filters, transfer-function, frequency-response, power-factor, complex-power]
sheet: "Tutorial sheet 8 - Problems on AC Circuits (2)"
theory_notes: ["[[FEEG1004 D3 - AC Filters and Bode Plots]]", "[[FEEG1004 D4 - AC Power and Power Factor]]"]
key_concepts: ["[[RC Low-Pass and High-Pass Filters]]", "[[Thevenin and Norton Equivalent Circuits]]", "[[Active, Reactive and Apparent Power]]", "[[Power Factor Correction]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Tutorial Sheet 08 - AC Circuits 2 - Filters & Transfer Functions.pdf"]
---

# FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions

> [!abstract] Sheet Info
> A loaded RC low-pass (with the requested Python plot), two RL filters, and a furnace with cable impedance and a power-factor-correction capacitor.
> - No answers are printed. Everything was **solved with complex arithmetic in Python** and cross-checked by power conservation.

## Theory Links
- [[FEEG1004 D3 - AC Filters and Bode Plots]] · [[FEEG1004 D4 - AC Power and Power Factor]] · [[Thevenin and Norton Equivalent Circuits]]

---

## Q1: Loaded RC low-pass ($R_1$ = 1 kΩ, $C$ = 10 µF, $R_L$ = 10 kΩ)
**(a) Transfer function.**
- The output node X has $C\parallel R_L$ to ground.
- **Thévenin** at X (with C removed): $V_{TH} = KV_{in}$ where $K = R_L/(R_1 + R_L)$ = 0.909, and $R_{TH} = R_1\parallel R_L$ = 909 Ω.

$$
H(\omega) = \frac{V_{out}}{V_{in}} = \frac{K}{1 + j\omega R_{TH}C} = \frac{0.909}{1 + j\omega(9.09\times10^{-3})}
$$

- Equivalent direct form: $H = \dfrac{R_L}{R_1 + R_L + j\omega CR_1R_L}$.
- Frequency response: $|H| = 0.909/\sqrt{1 + (0.00909\,\omega)^2}$ and $\angle H = -\tan^{-1}(0.00909\,\omega)$.

**(b) Amplitude plot** over ω = 0.1–10⁶ rad/s (log x, linear y):

```python
import numpy as np, matplotlib.pyplot as plt
R1, C, RL = 1e3, 10e-6, 10e3
w = np.logspace(-1, 6, 800)
H = RL / (R1 + RL + 1j * w * C * R1 * RL)
fig, ax = plt.subplots()
ax.semilogx(w, np.abs(H)); ax.set_xlabel("omega (rad/s)"); ax.set_ylabel("|H|")
fig.savefig("q1.png"); plt.close(fig)
```

**(c) Cut-off**: $\omega_c = 1/(R_{TH}C)$ = **110 rad/s** ($f_c$ = 17.5 Hz). There $|H| = K/\sqrt2$ = 0.643, i.e. 3 dB below the pass-band gain.

![[ee_t8_q1_loaded_lowpass.png|900]]

## Q2: RL filters
- **(a) Series R, shunt L**:
  - $H = \dfrac{j\omega L}{R + j\omega L} = \dfrac{1}{1 + R/j\omega L}$, with $|H| = \dfrac{\omega L}{\sqrt{R^2 + \omega^2L^2}}$.
  - ω → 0: $H\to0$ (the inductor shorts the output). ω → ∞: $H\to1$. **High-pass**.
- **(b) Series L, shunt R**:
  - $H = \dfrac{R}{R + j\omega L}$, with $|H| = \dfrac{R}{\sqrt{R^2 + \omega^2L^2}}$.
  - ω → 0: $H\to1$. ω → ∞: $H\to0$ (the inductor blocks). **Low-pass**.
- Both have $\omega_c = R/L$.

![[ee_t8_q2_rl_filters.png|760]]

## Q3: Furnace ($R_1$ = 1 Ω, $L_1$ = 5 mH) fed through a cable (0.01 Ω, 50 µH), with 1 mF across the load, 400 V at 50 Hz
**Impedances** at ω = 314.16 rad/s:
- $Z_{cab} = 0.01 + j0.0157$ Ω;
- $Z_{load} = 1 + j1.571$ Ω;
- $Z_C = -j3.183$ Ω;
- $Z_p = Z_{load}\parallel Z_C = 2.815 + j1.355$ Ω.

**(c) Cable current** (taking $\mathbf V_s$ = 400∠0°):

$$\mathbf I_2 = \frac{400}{Z_{cab} + Z_p} = 127.4\angle-25.9°\ \mathrm A$$

**(a) Load voltage**:

$$\mathbf V = \mathbf I_2Z_p = 398.0\angle-0.18°\ \mathrm V$$

The cable drops only about 2 V.

**(b) Load power**: $\mathbf I_1 = \mathbf V/Z_{load}$ = 213.7∠−57.7° A, so

$$P_{load} = I_1^2R_1 = 45.7\ \mathrm{kW},\qquad Q_{load} = I_1^2X_{L1} = 71.8\ \mathrm{kVAR}\quad(\mathrm{pf}\ 0.54)$$

**(d) Supply**:

$$\mathbf S_s = \mathbf V_s\mathbf I_2^* = 45.8\ \mathrm{kW} + j22.2\ \mathrm{kVAR}\quad(\mathrm{pf}\ 0.90\ \text{lagging})$$

**Power bookkeeping** (conservation of P and Q separately):

| Element | P (kW) | Q (kVAR) |
|---|---|---|
| furnace | 45.68 | +71.75 |
| capacitor | 0 | −49.76 |
| cable | 0.16 | +0.25 |
| **supply** | **45.84** | **+22.25** ✔ |

- **Without the capacitor**, the cable would carry 212.7 A (pf 0.54).
- With it, the current falls to 127.4 A. Cable loss drops by $(213/127)^2\approx2.8\times$ for the same furnace power.

![[ee_t8_q3_power_factor.png|900]]

## Sources
- FEEG1004 Tutorial sheet 8; computed with Python complex arithmetic and checked by power balance.
