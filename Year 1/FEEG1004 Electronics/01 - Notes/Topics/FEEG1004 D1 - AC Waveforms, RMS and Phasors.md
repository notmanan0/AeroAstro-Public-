---
title: "FEEG1004 D1 - AC Waveforms, RMS and Phasors"
module: "FEEG1004 Electronics"
type: topic
stream: "Part D: AC Circuit Analysis"
order: 1
tags: [feeg1004, ac-circuits, waveform, rms, phasor, complex-numbers, euler]
aliases: ["AC Analysis 01", "Phasors", "RMS", "Complex phasor notation"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A5 - Inductors and Electrical Resonance]]", "[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"]
next_topics: ["[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"]
key_concepts: ["[[RMS Value]]", "[[Phasor Representation]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W22 AC Analysis 01 - Phasors and Complex Numbers - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf", "02 - Sources/S2 AC Analysis/S2 Complex Numbers for AC Analysis - Niu.pdf"]
---

# FEEG1004 D1 - AC Waveforms, RMS and Phasors

> [!abstract] Summary
> A steady AC quantity is written as a **cosine with an rms amplitude**: $v(t) = \sqrt2V\cos(\omega t + \theta)$.
> - **rms** is the DC value that heats a resistor equally: $V_{rms} = V_p/\sqrt2$.
> - Because every voltage and current in a linear circuit shares one $\omega$, only magnitude and phase matter. They are packed into a **complex phasor**, $\mathbf V = Ve^{j\theta} = V\angle\theta$.
> - Differential equations become algebra: this is **Euler's formula** at work.

## Key Concepts
- [[RMS Value]] · [[Phasor Representation]]

---

## 1. Describing a sinusoid (AC 01)
$$
v(t) = V_p\cos(\omega t + \theta) = \sqrt2\,V\cos(2\pi ft + \theta)
$$

| Parameter | Meaning |
|---|---|
| $V_p$ | peak; peak-to-peak $V_{pp} = 2V_p$ |
| $T = 1/f$ | period [s]; $f$ in Hz |
| $\omega = 2\pi f$ | angular frequency [rad/s] |
| $\theta$ | phase: the angle at $t = 0$ relative to a reference |
| $V = V_p/\sqrt2$ | rms value |

- **Convention**: this course always writes waveforms as **cosines**. Convert with $\sin x = \cos(x - 90°)$ and $-\sin x = \cos(x + 90°)$.

![[ee_d1_ac_waveform_rms.png|900]]

> [!example] Slides practice
> - **Practice 1**: $V_{pp}$ = 40 V and $T$ = 50 µs, so $f$ = 20 kHz and $\omega = 2\pi f$ = 1.257 × 10⁵ rad/s. The slide writes this as "40 000 rad/s", meaning $40\,000\pi$.
> - **Practice 2**: $v_1 = 40\sin\omega t = 40\cos(\omega t - 90°)$ and $v_2 = 30\sin(\omega t - 45°) = 30\cos(\omega t - 135°)$.
> - **Reading waveforms**:
>   - $230\sqrt2\cos(100\pi t + \pi/6)$: 230 V rms, 50 Hz, +30°;
>   - $141\cos(\omega t - \pi/3)$: 99.7 V rms, −60°;
>   - $100\sqrt2\sin(100\pi t)$: 100 A rms, phase −90° as a cosine.

## 2. Why rms
- For $v = V_p\cos\omega t$ across $R$: $p = v^2/R = \dfrac{V_p^2}{2R}(1 + \cos2\omega t)$. The power **pulses at 2ω** and averages to $V_p^2/2R$.
- The DC voltage giving the same heating satisfies $V_{dc}^2 = V_p^2/2$, so $V_{rms} = V_p/\sqrt2\approx0.707V_p$.
- **"230 V mains" is rms** (325 V peak). Meters read rms, and phasor magnitudes in this course are rms.

## 3. Phasors
- A phasor is a line whose **length** is the rms magnitude and whose **angle** is the phase. Imagine it rotating at ω; its projection on the real axis traces the waveform. Freeze it at $t = 0$.
- Phasors at the same frequency **add like vectors**. KCL and KVL hold for phasors.
- A positive angle difference means **leads**; negative means **lags**.

![[ee_d1_phasors.png|900]]

## 4. Complex phasor notation
Euler: $e^{j\theta} = \cos\theta + j\sin\theta$ ($j = \sqrt{-1}$; electrical engineers use $j$ because $i$ is current). So

$$
v(t) = \sqrt2V\cos(\omega t + \theta) = \Re\{\sqrt2\,\mathbf Ve^{j\omega t}\},\qquad \mathbf V = Ve^{j\theta} = V\angle\theta = V\cos\theta + jV\sin\theta
$$

> [!example] Two sources in series (AC 01 slides)
> - $v_1 = 60\sqrt2\cos\omega t$ and $v_2 = 40\sqrt2\cos(\omega t - \pi/3)$.
> - $\mathbf V_1 + \mathbf V_2 = 60 + (20 - j34.64) = 80 - j34.64$ = **87.2∠−23.4°** (−0.41 rad).
> - So $v_1 + v_2 = 87.2\sqrt2\cos(\omega t - 23.4°)$ V. The geometric construction gives the same result but becomes impractical for larger circuits.

## 5. Complex arithmetic toolkit
| Operation | Easiest form | Rule |
|---|---|---|
| add / subtract | Cartesian | add real and imaginary parts separately |
| multiply | polar | multiply magnitudes, **add** angles |
| divide | polar | divide magnitudes, **subtract** angles (Cartesian: multiply by the conjugate) |
| convert | | $r = \sqrt{x^2 + y^2}$, $\theta = \tan^{-1}(y/x)$ (**check the quadrant**); $x = r\cos\theta$, $y = r\sin\theta$ |

- Useful: $j = 1\angle90°$ and $1/j = -j = 1\angle-90°$.
- Python: `cmath.polar`, `cmath.rect`. MATLAB: `cart2pol`, `pol2cart`.
- The quadrant check matters: $-21.4 + j33.3$ lies in the **second** quadrant, at 122.7°, not −57.3° (Tutorial 7 Q1f).

## Year 2 bridge
- A phasor is the complex amplitude of $e^{j\omega t}$, the same object as the **frequency response** $G(j\omega)$ and the complex Fourier coefficient ([[Frequency Response Function]], [[Complex Fourier Series]], [[SESA2027 A5 - Frequency Response and Bode Plots]]).
- The steady-state part of the Laplace solution of a sinusoidally forced ODE is exactly the phasor solution ([[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]], [[Method of Undetermined Coefficients]]).
- Rotating vectors also appear in vibration analysis: FEEG1002's receptance used $X = \Re(Xe^{j\omega t})$ in exactly this way ([[FEEG1002 D6 - Single Degree of Freedom Vibration]]).

## Links
- Next: [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]
- Worked problems: [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions]] (Q1, Q2)

## Sources
- AC Analysis 01 slides and lecture notes (X. Niu); *Complex Numbers for AC Analysis*; Hughes Ch. 9, 13.
