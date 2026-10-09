---
title: "SESA2027 A5 - Frequency Response and Bode Plots"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part A: Dynamic Systems"
order: 5
tags:
  - sesa2027
  - frequency-response
  - bode-plot
aliases: ["Frequency Response", "Bode Plots"]
date: 2026-09-23
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]"]
next_topics: ["[[SESA2027 B1 - Control System Fundamentals and PID Control]]"]
key_concepts: ["[[Frequency Response Function]]", "[[Bode Plot]]", "[[Poles and Zeros]]", "[[Gain and Phase Margins]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 1 Solutions]]", "[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 1.08.pdf", "02 - Sources/Lectures/Lecture 1.09.pdf"]
---

# SESA2027 A5 - Frequency Response and Bode Plots

> [!abstract] Summary
> A stable LTI system driven by $u = A\sin\omega t$ settles to $x_{ss} = A|G(i\omega)|\sin(\omega t+\angle G(i\omega))$. The output has the same frequency, but it is **scaled** by the magnitude $|G(i\omega)|$ and **shifted** by the phase $\angle G(i\omega)$. The **Bode plot** shows magnitude in dB and phase in degrees against log-frequency. Because $20\log$ turns products into sums, a Bode plot is built by adding simple factors: gain, poles and zeros at the origin, real poles and zeros ($\pm20$ dB/dec), and second-order pairs ($\pm40$ dB/dec).

## Key Concepts
- [[Frequency Response Function]] · [[Bode Plot]] · [[Poles and Zeros]] · [[Gain and Phase Margins]]

---

## 1. Poles, zeros and the complex plane (L1.08)

$$
G(s) = \frac{X(s)}{U(s)} = \frac{(s-z_1)(s-z_2)\cdots(s-z_{n-1})}{(s-p_1)(s-p_2)\cdots(s-p_n)}
$$

- An $n$th-order system has $n$ poles and at most $n-1$ zeros (causality).
- On the complex plane, poles are plotted as **×** and zeros as **○**.

## 2. Response to a sinusoidal input
Neglect $B(s)$ for simplicity, and apply $u(t) = A\sin\omega t$, so $U(s) = A\omega/(s^2+\omega^2)$. Partial fractions give

$$
X(s) = \underbrace{\frac{r_1}{s-p_1}+\cdots+\frac{r_n}{s-p_n}}_{\text{system poles}\to\text{transient}}+\underbrace{\frac{r_{n+1}s}{s^2+\omega^2}+\frac{r_{n+2}\omega}{s^2+\omega^2}}_{\text{input}\to\text{steady state}}
$$

$$
x(t) = \underbrace{r_1e^{p_1t}+\dots+r_ne^{p_nt}}_{\text{transient}}+\underbrace{r_{n+1}\cos\omega t+r_{n+2}\sin\omega t}_{\text{steady state}}
$$

- **Transient response**: the system's natural response to initial conditions. If the system is stable (all $\mathrm{Re}(p_i)<0$), it decays to zero.
- **Steady-state response**: the forced response to the periodic input.

Using $\alpha\cos\omega t+\beta\sin\omega t = \sqrt{\alpha^2+\beta^2}\sin(\omega t+\phi)$:

$$
x_{ss}(t) = B(\omega)\sin[\omega t+\phi(\omega)] = A|G(i\omega)|\sin[\omega t+\angle G(i\omega)]
$$

$$
\boxed{|G(i\omega)| = \frac{B}{A}\ (\text{gain}),\qquad \angle G(i\omega) = \phi\ (\text{phase})}
$$

This is the **frequency response function**.

### Five-step recipe (SPO example)
For $G(s) = \dfrac{1.992}{s^2+0.744s+1.992}$, where the input amplitude $A = mI_{yy}\omega_n^2$ normalises the numerator:
1. Substitute $s = i\omega$: $G(i\omega) = \dfrac{1.992}{(1.992-\omega^2)+0.744\omega i}$.
2. Separate real and imaginary parts.
3. Magnitude: $|G| = \dfrac{1.992}{\sqrt{(1.992-\omega^2)^2+(0.744\omega)^2}}$.
4. Phase: numerator phase minus denominator phase, $\angle G = 0-\arctan\dfrac{0.744\omega}{1.992-\omega^2}$. Use `atan2` so the angle continues past $-90^\circ$.
5. Evaluate:

| $\omega$ (rad/s) | 0 | 0.1 | $\omega_n=1.41$ | 10 | 100 | $\infty$ |
|---|---|---|---|---|---|---|
| $\vert G\vert$ | 1.0 | 1.004 | 1.896 | $2.03\times10^{-2}$ | $1.99\times10^{-4}$ | 0 |
| $\angle G$ (deg) | 0 | −2.15 | −90 | −175.7 | −179.6 | −180 |

- At low frequency the output follows the input.
- Near $\omega_n$ the output is amplified (resonance) and lags by 90°.
- At high frequency the output is strongly attenuated and in anti-phase.

## 3. Bode plot (L1.09)
- Magnitude (top) and phase (bottom) plotted against $\log\omega$.
- In dB: $|G|_{dB} = 20\log_{10}|G|$ and $|G| = 10^{|G|_{dB}/20}$.
- 0 dB means gain 1, negative dB means $<1$, positive dB means $>1$.

![[amc_bode_second_order_family.png|600]]

**Frequency-domain specifications**:

| Spec | Definition |
|---|---|
| Cut-off (corner) frequency | Output drops to **−3 dB** below its low-frequency value (half power, ×0.707) |
| Bandwidth | Frequency range over which the gain stays within −3 dB of the low-frequency value |
| Peaking | Any increase in gain above the low-frequency gain |
| Resonant frequency | Frequency of maximum magnitude, $\omega_r = \omega_n\sqrt{1-2\zeta^2}$ (peak only exists if $\zeta<0.707$) |
| Gain crossover $\omega_{gc}$ | Magnitude crosses 0 dB |
| Phase crossover $\omega_{pc}$ | Phase reaches −180° |
| Gain slope | Rate of change of magnitude (dB/decade) |

## 4. Building a Bode plot from factors
Write $G(s)$ in ZPK form, $G(s) = \dfrac{k(s-z_1)(s-z_2)}{\prod(s-p_i)}$. Since $\log(xy) = \log x+\log y$, **magnitudes in dB add and phases add**.

| Factor | $\vert G(i\omega)\vert$ | Magnitude slope | Phase |
|---|---|---|---|
| Gain $k$ | $k$ | flat at $20\log k$ | 0 (or −180° if $k<0$) |
| Zero at origin $s$ | $\omega$ | +20 dB/dec | +90° |
| Pole at origin $1/s$ | $1/\omega$ | −20 dB/dec | −90° |
| Real zero $s-z$ | $\sqrt{z^2+\omega^2}$ | 0, then +20 dB/dec for $\omega>\vert z\vert$ | 0 → +90° (about +45°/dec from $0.1\vert z\vert$ to $10\vert z\vert$) |
| Real pole $1/(s-p)$ | $1/\sqrt{p^2+\omega^2}$ | 0, then −20 dB/dec | 0 → −90° |
| 2nd-order zeros $s^2+2\zeta\omega_ns+\omega_n^2$ | $\omega_n^2$ → $2\zeta\omega_n^2$ at $\omega_n$ → $\omega^2$ | +40 dB/dec | 0 → +90° at $\omega_n$ → +180° |
| 2nd-order poles | $1/\omega_n^2$ → $1/(2\zeta\omega_n^2)$ → $1/\omega^2$ | −40 dB/dec | 0 → −90° at $\omega_n$ → −180°; a sharper transition at low $\zeta$ |

**Example**: the elevator-to-pitch-angle TF (Blakelock),

$$
\frac{\theta(s)}{\delta_e(s)} = \frac{-1.31(s+0.016)(s+0.3)}{(s^2+0.00466s+0.0053)(s^2+0.806s+1.311)}
$$

- The phugoid pair at $\omega_n = 0.073$ rad/s gives a sharp resonant peak.
- The SPO pair at $1.14$ rad/s gives a smaller peak.
- The negative gain shifts the phase by −180°.

**Application**: the Bell XV-15 tiltrotor. Frequency sweeps in flight identified the SPO ($\approx0.467$ Hz) and phugoid ($\approx0.029$ Hz) modes, as well as aeroelastic wing modes (NASA TP-3330 / TM-2013-217976).

> [!example] PS2 Q1: $G(s) = 5/(s^2+4s+25)$, so $\omega_n=5$, $\zeta = 0.4$, DC gain $0.2$ (−13.98 dB)
>
> | $\omega$ | 0 | 1 | 5 | 20 |
> |---|---|---|---|---|
> | $\vert G\vert$ | 0.200 | 0.2055 | 0.250 | 0.01304 |
> | dB | −13.98 | −13.74 | −12.04 | −37.69 |
> | Phase | 0° | −9.46° | −90° | −167.96° |
>
> The magnitude never reaches 0 dB and the phase only tends to −180°, so $\omega_{gc}$ and $\omega_{pc}$ do not exist and GM = PM = ∞. See [[SESA2027 Practice Problems 2 Solutions]].

![[amc_ps2_q1_bode.png|600]]

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]] · Next: [[SESA2027 B1 - Control System Fundamentals and PID Control]]
- Used for: [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]] and sensor/filter design in [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]

## Year 1 foundation
- The receptance FRF $X/F = 1/(k - \omega^2m + j\omega c)$ and its stiffness-, damping- and mass-controlled regions: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources
- Lectures 1.08–1.09; Blakelock (1991) *Automatic Control of Aircraft and Missiles*; Acree & Tischler (1993) NASA TP-3330
