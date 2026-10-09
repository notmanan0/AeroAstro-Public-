---
title: "FEEG1004 D3 - AC Filters and Bode Plots"
module: "FEEG1004 Electronics"
type: topic
stream: "Part D: AC Circuit Analysis"
order: 3
tags: [feeg1004, ac-circuits, filters, low-pass, high-pass, transfer-function, bode, decibels, cut-off]
aliases: ["AC Analysis 03", "RC filters", "Low-pass filter", "High-pass filter", "Cut-off frequency"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"]
next_topics: ["[[FEEG1004 D4 - AC Power and Power Factor]]"]
key_concepts: ["[[RC Low-Pass and High-Pass Filters]]", "[[Decibels]]", "[[Bode Plot]]", "[[Transfer Function]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"]
---

# FEEG1004 D3 - AC Filters and Bode Plots

> [!abstract] Summary
> A filter is a **complex potential divider**. Its transfer function $H(\omega) = \mathbf V_{out}/\mathbf V_{in}$ has a gain $|H|$ and a phase $\angle H$ that both vary with frequency.
> - **RC low-pass**: $H = 1/(1 + j\omega RC)$. **RC high-pass**: $H = j\omega RC/(1 + j\omega RC)$.
> - Both have a **cut-off** $\omega_c = 1/RC$ where $|H| = 1/\sqrt2$: **−3 dB**, half power, ±45° phase.
> - On a **Bode plot** (dB against log frequency) first-order filters roll off at **20 dB/decade**.
> - Exam skills: derive $H$ and $\omega_c$ for **any** simple filter, recognise low- and high-pass forms, and choose components to meet a specification.

## Key Concepts
- [[RC Low-Pass and High-Pass Filters]] · [[Decibels]] · [[Bode Plot]] · [[Transfer Function]]

---

## 1. Why filters
- The tidal-turbine student project uses a DC generator whose output carries ripple. A **filter capacitor** removes it.
- A **low-pass** filter attenuates high frequencies (noise) and leaves low frequencies untouched. A **high-pass** does the reverse (blocking DC, as the coupling capacitors of an amplifier do).

## 2. RC low-pass
$$
H(\omega) = \frac{\mathbf V_{out}}{\mathbf V_{in}} = \frac{1/j\omega C}{R + 1/j\omega C} = \frac{1}{1 + j\omega RC},\qquad |H| = \frac{1}{\sqrt{1 + (\omega RC)^2}},\qquad \angle H = -\tan^{-1}(\omega RC)
$$

- ω → 0: $|H|\to1$ (the capacitor is open). ω → ∞: $|H|\to1/\omega RC\to0$ (the capacitor shorts the output).
- **Cut-off (corner, half-power, bandwidth)**: $\omega_c = 1/RC$, $f_c = 1/2\pi RC$. There $|H| = 1/\sqrt2$, the output power halves ($P\propto V^2$) and the phase is −45°.

## 3. RC high-pass
Swap R and C:

$$
H = \frac{R}{R + 1/j\omega C} = \frac{j\omega RC}{1 + j\omega RC},\qquad |H| = \frac{\omega RC}{\sqrt{1 + (\omega RC)^2}},\qquad \angle H = 90° - \tan^{-1}(\omega RC)
$$

It has the same $\omega_c$. The gain is ~$\omega RC$ (rising) at low frequency and →1 at high frequency.

## 4. Decibels and Bode plots
$$
G_{dB} = 10\log_{10}\frac{P_{out}}{P_{in}} = 20\log_{10}\frac{V_{out}}{V_{in}}
$$

| Voltage gain | dB |
|---|---|
| √2 ≈ 1.41 | +3 |
| 10 | +20 |
| 100 | +40 |
| 1/√2 ≈ 0.707 | −3 |
| 0.1 | −20 |
| 0.01 | −40 |

- A **Bode plot** shows dB against log frequency, plus phase against log frequency. It covers a wide frequency range, and the curves become **straight-line asymptotes**:
  - 0 dB below the corner;
  - **−20 dB/decade** above it (low-pass), or +20 dB/decade below it (high-pass).
- The worst error of the asymptote is 3 dB, at the corner.

![[ee_d3_bode_rc_filters.png|820]]

## 5. Designing and recognising filters
> [!example] Design for −20 dB at 50 Hz with $R$ = 1 kΩ (AC 03)
> - $|H| = 0.1$, so $1 + (\omega RC)^2 = 100$ and $\omega RC = \sqrt{99}$.
> - $C = \sqrt{99}/(2\pi\times50\times1000)$ = **31.7 µF**, and $f_c = 1/2\pi RC$ = **5.03 Hz**.
> - This is the **straight-line** result too: 20 dB down means one decade above the corner.
>
> ![[ee_d3_filter_design_50hz.png|760]]

> [!example] Identify the filter and size it: series R, shunt L (AC 03)
> - $H = j\omega L/(R + j\omega L) = 1/(1 + R/j\omega L)$.
> - ω → 0: the inductor shorts the output, so $H\to0$. ω → ∞: it is open, so $H\to1$. **High-pass**, with $\omega_c = R/L$.
> - For $f_c$ = 3 kHz with $L$ = 0.3 mH: $R = 2\pi f_cL$ = **5.65 Ω**.

> [!example] 10 V into an RC low-pass with 47 nF (AC 03 slides)
> - The slide heading says 47 kΩ, but the working uses **4.7 kΩ** (4700). With 4.7 kΩ:
>   - 100 Hz ($X_C$ = 33.9 kΩ): $V_{out}$ = 10 × 33.9/34.2 = **9.9 V**;
>   - 10 kHz ($X_C$ = 339 Ω): $V_{out}$ = 10 × 339/4712 = **0.72 V**.
> - With 47 kΩ the 100 Hz output would be 5.8 V; $f_c$ = 72 Hz with 47 kΩ versus 720 Hz with 4.7 kΩ.

**Loaded filters** (Tutorial 8 Q1):
- A load $R_L$ across the capacitor changes both the pass-band gain and the corner.
- Thévenin at the capacitor node gives $K = R_L/(R_1 + R_L)$ and $R_p = R_1\parallel R_L$, so $H = K/(1 + j\omega R_pC)$ with $\omega_c = 1/R_pC$.

![[ee_t8_q1_loaded_lowpass.png|900]]

**Beyond first order**:
- a **band-pass** filter combines high- and low-pass stages;
- an **active** filter adds an op-amp for gain and buffering, so the load no longer shifts the corner ([[FEEG1004 B4 - Operational Amplifiers]]).

## Year 2 bridge
- This is **SESA2027's Bode plot**: a first-order lag $1/(1 + s\tau)$ with $s = j\omega$, corner at $1/\tau$, −20 dB/dec and −90° ultimately ([[Bode Plot]], [[Transfer Function]], [[SESA2027 A5 - Frequency Response and Bode Plots]]).
- **Anti-aliasing**: an analogue RC low-pass before the ADC must remove content above the Nyquist frequency ([[Nyquist Sampling and Aliasing]], [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]). Its digital cousin is the recursive IIR low-pass ([[Digital Filtering]]).
- **Sensor dynamics**: a first-order sensor *is* an RC low-pass; the RC-filter Bode view appears in [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]] and [[Sensor Dynamic Models]].
- **Complementary filters** blend a low-passed and a high-passed sensor, whose $H_{LP} + H_{HP} = 1$, exactly the two filters here ([[Complementary Filter]]).
- **Decibels** are shared with link budgets ([[Decibels]], [[Link Budget Equation]]).

## Links
- Previous: [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]] · Next: [[FEEG1004 D4 - AC Power and Power Factor]]
- Worked problems: [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions]] (Q1, Q2)

## Sources
- AC Analysis 03 slides; Niu AC notes (RC filters, decibels); Hughes Ch. 17.
