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
status: lectured
coverage: "L1.08 (poles and zeros, sinusoidal response), L1.09 (Bode plots)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]"]
next_topics: ["[[SESA2027 B1 - Control System Fundamentals and PID Control]]"]
key_concepts: ["[[Frequency Response Function]]", "[[Bode Plot]]", "[[Poles and Zeros]]", "[[Gain and Phase Margins]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 1 Solutions]]", "[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 1.08.pdf", "02 - Sources/Lectures/Lecture 1.09.pdf", "02 - Sources/Lectures/Lecture 1.08 recording.txt", "02 - Sources/Lectures/Lecture 1.09 recording.txt"]
---

# SESA2027 A5 - Frequency Response and Bode Plots

> [!abstract] Summary
> A stable LTI system driven by $u = A\sin\omega t$ settles to $x_{ss} = A|G(i\omega)|\sin(\omega t+\angle G(i\omega))$: the same frequency, scaled by $|G(i\omega)|$ and shifted by $\angle G(i\omega)$. The Bode plot shows that magnitude in dB and the phase in degrees against log-frequency. Because $20\log$ turns products into sums, it is built by adding simple factors: gains, poles and zeros at the origin, real poles and zeros (±20 dB/dec) and second-order pairs (±40 dB/dec).

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives $G(s)$ and asks for $\lvert G(i\omega)\rvert$ and $\angle G(i\omega)$ at stated frequencies, a Bode sketch with asymptotes, the bandwidth or the frequency for a given attenuation, or whether a pole–zero map is stable and physical.
> - **Assumptions:** linear, time-invariant and stable (otherwise there is no steady state); sinusoidal input; phase from `atan2` so it can pass −90°; dB formulas are given on the question sheet (L1.09, l. 123).
> - **Method:** 1. Substitute $s=i\omega$. 2. $\lvert G\rvert=\lvert\text{num}\rvert/\lvert\text{den}\rvert$, $\angle G=\angle\text{num}-\angle\text{den}$. 3. Convert: $\lvert G\rvert_{dB}=20\log_{10}\lvert G\rvert$. 4. Sketch factor by factor: flat at the DC gain, then $-20$ dB/dec per pole and $+20$ per zero after each corner. 5. Read $\omega_{gc}$ (0 dB), $\omega_{pc}$ (−180°), −3 dB bandwidth, any peak.
> - **Common mistakes:** quoting $-10$ or $-20$ dB/decade for first and second order (the L1.09 slip; it is $-20$ and $-40$); taking $\arctan$ without the quadrant, which stops the phase at $-90°$.
> - **Practise:** [[#Five-step recipe (SPO example)]] · [[SESA2027 Mock Questions#Q5. Bode magnitude and phase|Mock Q5]] · [[SESA2027 Practice Problems 2 Solutions]]

Instead of a step, waggle the elevator back and forth sinusoidally and wait for the transients to die. The aircraft ends up oscillating at exactly the waggling frequency, with no new frequencies created, because it is linear. Only two things change: the size of the response and how far it lags behind the input. Waggle slowly and the aircraft follows faithfully. Waggle near its natural frequency and it over-responds, a quarter-cycle late. Waggle fast and its inertia wins: the response is tiny and almost in anti-phase.

Those two numbers, gain and lag, at every frequency, are the frequency response $G(i\omega)$. The Bode plot draws them on log axes, where the multiplying factors of $G(s)$ become added straight lines. That makes Bode plots quick to sketch by hand and, in Part B, the natural tool for designing controllers with safety margins.

---

## 1. Poles, zeros and the complex plane (L1.08)

$$
G(s) = \frac{X(s)}{U(s)} = \frac{(s-z_1)(s-z_2)\cdots(s-z_{n-1})}{(s-p_1)(s-p_2)\cdots(s-p_n)}
$$

- An $n$th-order system has $n$ poles. For a physical (causal) system the numerator order cannot exceed the denominator order, so there are at most $n$ zeros. The lecture assumes $n-1$ zeros (strictly proper), the usual case for the aircraft transfer functions here (L1.08, ll. 43–67).
- On the complex plane, poles are plotted as × and zeros as ○.

A pole–zero map is read like this (L1.08, ll. 84–181). The system is stable if every pole is in the left half-plane, and it is physical only if complex poles and zeros come in conjugate pairs, mirror images about the real axis. The real part sets decay (negative) or growth (positive), the imaginary part sets the oscillation frequency, and real roots give no oscillation. A pure sinusoid has its poles on the imaginary axis, which is why the frequency response is described as "motion along the imaginary axis", $s = i\omega$.

> [!info] Stated exam/quiz question (L1.08, ll. 107–112)
> "Determine whether this system is stable or not, just by looking at the representation of the poles and zeros in the complex plane." For a map with right-half-plane poles that are not conjugate pairs: "this system is not stable, but then, that is not physical. And if you put those two, you get full marks."

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

This is the frequency response function.

**Combining the two steady-state terms, line by line.** Write $\alpha = r_{n+1}$, $\beta = r_{n+2}$, and define $B_0 = \sqrt{\alpha^2+\beta^2}$ and $\phi$ by $\cos\phi = \beta/B_0$, $\sin\phi = \alpha/B_0$:

$$
\alpha\cos\omega t+\beta\sin\omega t = B_0\left(\frac{\alpha}{B_0}\cos\omega t+\frac{\beta}{B_0}\sin\omega t\right)
$$

$$
= B_0(\sin\phi\cos\omega t+\cos\phi\sin\omega t)
$$

$$
= B_0\sin(\omega t+\phi)
$$

So the steady state is a single sinusoid at the input frequency, scaled and shifted (L1.08, ll. 848–936).

Why the scale is $\lvert G(i\omega)\rvert$ and the shift is $\angle G(i\omega)$ (the step the slides state without proof; not examined, L1.08, ll. 316–321). Factor the input term as $s^2+\omega^2=(s-i\omega)(s+i\omega)$ and use complex partial fractions for the two steady-state poles:

$$
X(s)=G(s)\frac{A\omega}{(s-i\omega)(s+i\omega)}=\ldots+\frac{c}{s-i\omega}+\frac{\bar c}{s+i\omega}
$$

The cover-up rule gives $c$ by multiplying by $(s-i\omega)$ and setting $s=i\omega$:

$$
c=G(i\omega)\frac{A\omega}{2i\omega}=\frac{A\,G(i\omega)}{2i}
$$

Write $G(i\omega)=\lvert G\rvert e^{i\phi}$ with $\phi=\angle G(i\omega)$. The two terms invert to $ce^{i\omega t}+\bar ce^{-i\omega t}=2\,\mathrm{Re}\left(ce^{i\omega t}\right)$:

$$
x_{ss}(t)=2\,\mathrm{Re}\left(\frac{A\lvert G\rvert e^{i(\omega t+\phi)}}{2i}\right)=A\lvert G\rvert\,\mathrm{Re}\left(-i\,e^{i(\omega t+\phi)}\right)
$$

$$
x_{ss}(t)=A\lvert G(i\omega)\rvert\sin\left(\omega t+\angle G(i\omega)\right)
$$

since $\mathrm{Re}(-ie^{i\psi})=\sin\psi$. The system poles only add the transient terms, which decay if the system is stable.

![[amc_sine_in_out_three_freqs.png|820]]

> [!info] Lecturer intuition on the steady state (L1.08)
> - The transfer function belongs to the system, not the input. In L1.07 the $1/s$ was the step input, not part of $G(s)$; to get $G(s)$ from a forced ODE, "you would need to remove the input first" (ll. 245–300).
> - The transient stops mattering after about the settling time, $4.6/(\zeta\omega_n)$, after which the total response is the steady-state sinusoid (ll. 660–705).
> - Causal systems lag. A phase lead in the steady state would mean "predicting time", so physical systems show a phase lag (ll. 1199–1215; L1.09, ll. 29–32).
> - Only the step is used for transient analysis in this module (ll. 36–38).

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

The input amplitude $A = mI_{yy}\omega_n^2$ is chosen only to make the numerator equal to $\omega_n^2$, so $|G(0)| = 1$ (0 dB). The lecturer calls this "cheating" to make the analysis easier (L1.08, ll. 1340–1390; L1.09, ll. 285–292). Without it the whole magnitude curve shifts down by a constant number of dB.

> [!warning] When is there a peak at $\omega_n$?
> The lecture says the magnitude at $\omega_n$ exceeds 1 "for a system with a damping ratio less than one" (L1.08, ll. 2202–2213). That is too loose. At $\omega = \omega_n$, $|G| = 1/(2\zeta)$, which exceeds 1 only if $\zeta<0.5$. A resonant peak above the low-frequency gain exists only if $\zeta<1/\sqrt2\approx0.707$, and it sits at $\omega_r = \omega_n\sqrt{1-2\zeta^2}$, slightly below $\omega_n$ (as L1.09, ll. 228–232 says). Here $\zeta = 0.264$, so $|G(i\omega_n)| = 1.90$ and the peak is at $\omega_r = 1.31$ rad/s.

Deriving the resonant peak (assumptions: $G=\omega_n^2/(s^2+2\zeta\omega_ns+\omega_n^2)$, unit DC gain). The magnitude is

$$
\lvert G(i\omega)\rvert=\frac{\omega_n^2}{\sqrt{D(\omega)}},\qquad D(\omega)=(\omega_n^2-\omega^2)^2+(2\zeta\omega_n\omega)^2
$$

so the peak in $\lvert G\rvert$ is the minimum of $D$. Differentiate with respect to $\omega^2$ (call it $v$):

$$
\frac{dD}{dv}=-2(\omega_n^2-v)+4\zeta^2\omega_n^2=0
$$

$$
v=\omega_n^2(1-2\zeta^2)\quad\Rightarrow\quad\omega_r=\omega_n\sqrt{1-2\zeta^2}
$$

which is real only if $1-2\zeta^2>0$, i.e. $\zeta<1/\sqrt2$. Substitute back: $\omega_n^2-\omega_r^2=2\zeta^2\omega_n^2$, so

$$
D(\omega_r)=4\zeta^4\omega_n^4+4\zeta^2\omega_n^4(1-2\zeta^2)=4\zeta^2\omega_n^4(1-\zeta^2)
$$

$$
\lvert G\rvert_{\max}=\frac{1}{2\zeta\sqrt{1-\zeta^2}}
$$

> [!check] SPO numbers
> $\zeta=0.2638$: $\omega_r=1.4115\sqrt{1-0.1392}=1.310$ rad/s and $\lvert G\rvert_{\max}=1/(2\times0.2638\times0.9646)=1.965=5.87$ dB, matching the computed column in the table below.

## 3. Bode plot (L1.09)
- Magnitude (top) and phase (bottom) plotted against $\log\omega$.
- In dB: $|G|_{dB} = 20\log_{10}|G|$ and $|G| = 10^{|G|_{dB}/20}$.
- 0 dB means gain 1, negative dB means $<1$, positive dB means $>1$.

![[amc_bode_second_order_family.png|600]]

**Frequency-domain specifications**:

| Spec | Definition |
|---|---|
| Cut-off (corner) frequency | Output drops to −3 dB below its low-frequency value (half power, ×0.707) |
| Bandwidth | Frequency range over which the gain stays within −3 dB of the low-frequency value |
| Peaking | Any increase in gain above the low-frequency gain |
| Resonant frequency | Frequency of maximum magnitude, $\omega_r = \omega_n\sqrt{1-2\zeta^2}$ (peak only exists if $\zeta<0.707$) |
| Gain crossover $\omega_{gc}$ | Magnitude crosses 0 dB |
| Phase crossover $\omega_{pc}$ | Phase reaches −180° |
| Gain slope | Rate of change of magnitude (dB/decade) |

The lecturers read a Bode plot in three ways. A second-order system is a low-pass filter with its cut-off near $\omega_n$, so as a ballpark anything above the natural frequency is already being attenuated, and quickly (L1.09, ll. 59–65). Overshoot in time means peaking in frequency: "when you see an overshoot on the time response, you are going to see peaking on the frequency response" (L2.09, ll. 69–70), and both come from a small $\zeta$. And a change of slope reveals a hidden pole, since each pole adds another −20 dB/decade to the high-frequency roll-off; if the plot falls 40 dB over one decade and 60 dB over the next, another pole sits near the decade boundary (L2.05, ll. 133–149).

> [!example] Reading the SPO Bode plot (L1.09, ll. 160–249; values computed)
> For $G(s) = 1.992/(s^2+0.744s+1.992)$:
>
> | Quantity | Lecture estimate | Computed |
> |---|---|---|
> | Bandwidth (−3 dB) | "0 to 2 rad/s" | 0 to 2.08 rad/s (phase −147°) |
> | Peaking | "between 5 and 10" dB | 5.87 dB at $\omega_r = 1.31$ rad/s |
> | Gain crossover | magnitude rises above 0 dB, then crosses back | $\omega_{gc} = 1.85$ rad/s |
> | Phase crossover | at infinity | phase only tends to −180° |
> | −20 dB (×0.1) | 4.65 rad/s, about −170° | 4.65 rad/s, −170.0° |
> | −40 dB (×0.01) | "about 14 rad/s" | 14.17 rad/s, −177.0° |
> | −60 dB (×0.001) | 44.65 rad/s | 44.65 rad/s, −179.0° |
> | High-frequency slope | — | −40 dB/decade (second order) |
>
> Exam/quiz form: "tell me what is the value of frequency where the system attenuates the signal at a thousandth of its value". Read it off the plot; a range is acceptable (ll. 175–177).

**Why −3 dB, and the bandwidth formula.** Power goes as amplitude squared, so half power is amplitude $1/\sqrt2$: $20\log_{10}(1/\sqrt2)=-10\log_{10}2=-3.01$ dB. For the unit-DC-gain second-order system set $\lvert G\rvert^2=1/2$, i.e. $D(\omega_b)=2\omega_n^4$. With $v=\omega_b^2/\omega_n^2$:

$$
(1-v)^2+4\zeta^2v=2
$$

$$
v^2-2(1-2\zeta^2)v-1=0
$$

Take the positive root:

$$
\omega_b=\omega_n\sqrt{1-2\zeta^2+\sqrt{4\zeta^4-4\zeta^2+2}}
$$

For the SPO, $\zeta=0.2638$: $1-2\zeta^2=0.8608$, $\sqrt{4\zeta^4-4\zeta^2+2}=1.3195$, so $\omega_b=1.4115\sqrt{2.180}=2.084$ rad/s, the 2.08 in the table.

> [!warning] Gain-slope slip in L1.09
> The lecture said "for a first-order system, it will be 10 dBs per decade. For a second-order system, it will be 20 dBs per decade" (L1.09, ll. 245–249). The correct high-frequency slopes are −20 dB/decade per pole: −20 for first order, −40 for second order, −60 for third. The same lecture's own example drops "almost minus 40 dBs" in one decade (ll. 107–108), and L2.05 states the correct values (ll. 133–137).

> [!info] dB conversions in the exam (L1.09, ll. 116–124)
> "I'm going to give you the equations in the question sheet if a question regarding this comes in the exam." Remember the pattern: every −20 dB divides the amplitude by 10, so −20, −40, −60 dB are 0.1, 0.01, 0.001 (ll. 145–147). A negative dB value is attenuation, not a negative magnitude.

The Bode plot matters in practice because it shows where the input still has authority (L1.09, ll. 74–100). If you must deflect the elevator ever more to move the aircraft a fraction of a degree, "that's not a good operating point", and above the bandwidth the system barely responds.

## 4. Building a Bode plot from factors
Write $G(s)$ in ZPK form, $G(s) = \dfrac{k(s-z_1)(s-z_2)}{\prod(s-p_i)}$. Since $\log(xy) = \log x+\log y$, magnitudes in dB add and phases add.

| Factor | $\vert G(i\omega)\vert$ | Magnitude slope | Phase |
|---|---|---|---|
| Gain $k$ | $k$ | flat at $20\log k$ | 0 (or −180° if $k<0$) |
| Zero at origin $s$ | $\omega$ | +20 dB/dec | +90° |
| Pole at origin $1/s$ | $1/\omega$ | −20 dB/dec | −90° |
| Real zero $s-z$ | $\sqrt{z^2+\omega^2}$ | 0, then +20 dB/dec for $\omega>\vert z\vert$ | 0 → +90° (about +45°/dec from $0.1\vert z\vert$ to $10\vert z\vert$) |
| Real pole $1/(s-p)$ | $1/\sqrt{p^2+\omega^2}$ | 0, then −20 dB/dec | 0 → −90° |
| 2nd-order zeros $s^2+2\zeta\omega_ns+\omega_n^2$ | $\omega_n^2$ → $2\zeta\omega_n^2$ at $\omega_n$ → $\omega^2$ | +40 dB/dec | 0 → +90° at $\omega_n$ → +180° |
| 2nd-order poles | $1/\omega_n^2$ → $1/(2\zeta\omega_n^2)$ → $1/\omega^2$ | −40 dB/dec | 0 → −90° at $\omega_n$ → −180°; a sharper transition at low $\zeta$ |

**Where the real-pole asymptotes come from.** Write the pole in time-constant form, $G=1/(1+i\omega/a)$:

$$
\lvert G\rvert_{dB}=-20\log_{10}\sqrt{1+(\omega/a)^2}=-10\log_{10}\left(1+\frac{\omega^2}{a^2}\right)
$$

- For $\omega\ll a$: $\lvert G\rvert_{dB}\approx0$, the flat asymptote.
- For $\omega\gg a$: $\lvert G\rvert_{dB}\approx-20\log_{10}(\omega/a)$, which falls 20 dB for each factor of 10 in $\omega$.
- At $\omega=a$: $-10\log_{10}2=-3.01$ dB, the largest error of the straight lines.
- Phase: $\angle G=-\arctan(\omega/a)$, which is $-45°$ at the corner, $-5.7°$ at $0.1a$ and $-84.3°$ at $10a$. Hence the straight-line rule "0 to −90° over two decades".

![[amc_first_order_asymptotes.png|700]]

A second-order pair behaves the same way with twice the slope ($\pm40$ dB/dec), plus a correction near $\omega_n$ that depends on $\zeta$ (the resonant peak above).

**Example**: the elevator-to-pitch-angle TF (Blakelock),

$$
\frac{\theta(s)}{\delta_e(s)} = \frac{-1.31(s+0.016)(s+0.3)}{(s^2+0.00466s+0.0053)(s^2+0.806s+1.311)}
$$

- The phugoid pair at $\omega_n = 0.073$ rad/s gives a sharp resonant peak.
- The SPO pair at $1.14$ rad/s gives a smaller peak.
- The negative gain shifts the phase by −180°.

**Application**: the Bell XV-15 tiltrotor. Frequency sweeps in flight identified the SPO ($\approx0.467$ Hz) and phugoid ($\approx0.029$ Hz) modes, as well as aeroelastic wing modes (NASA TP-3330 / TM-2013-217976).

The XV-15's antisymmetric wing beam mode peaks at about 5–6 Hz, roughly ten times the SPO frequency. Keeping structural modes well above the rigid-body modes matters, in the lecturer's words, because "otherwise the interaction between the structural modes and the longitudinal modes could be very dangerous" (L1.09, ll. 364–372).

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

## Lecturer emphasis and exam hints (transcripts)

> [!info] Exam and quiz signals
> - Pole–zero map → stable/unstable and physical/non-physical (L1.08, ll. 107–112).
> - The full partial-fraction derivation for a sinusoidal input is not expected: "I'm not going to expect you to do all of the derivation" (L1.08, ll. 316–321).
> - "The output amplitude is scaled and phase shifted. Please bear this in mind when you're answering your quiz" (L1.08, ll. 2245–2254).
> - Read frequencies for a given attenuation off a Bode plot (L1.09, ll. 175–177). dB formulas will be on the question sheet (l. 123).
> - In the labs Python produces the Bode plot in dB (L1.09, l. 124).

## Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> | Where | Transcript says | Correct |
> |---|---|---|
> | L1.08, l. 1 | "LAT-plus transform", "La Trasse transform" (l. 206) | Laplace transform |
> | L1.08, l. 32 | "the polynomial l" | the polynomial $A(s)$ |
> | L1.08, l. 67 | "for the system to be causal, at least the order of the numerator and the denominator has to be the same" | the numerator order must be at most the denominator order |
> | L1.08, l. 84 | "a knot, or a zero" | a nought (○) |
> | L1.08, l. 95 | conjugates are "a mirror image on the imaginary axis" | mirror images about the real axis |
> | L1.08, ll. 115–117 | (answering a student) instability "can happen as well if the zeros are on the positive side of the complex plane" | open-loop stability depends only on the poles. Right-half-plane zeros matter once the loop is closed: the closed-loop poles are the roots of $A(s)+KB(s)$, so the zeros in $B(s)$ move them and can push them into the right half-plane at high gain (L2.03, ll. 268–272; [[SESA2027 B2 - Root Locus Method\|B2]]) |
> | L1.08, ll. 396–398 | "the geolentical multiply by the geolentical" | $G(s)$ multiplied by $U(s)$ |
> | L1.08, l. 755 | roots "halal of negative part" | have a negative real part |
> | L1.08, ll. 829–835 | "the denominator order is greater, or at least equal to the denominator" | at least equal to the numerator order |
> | L1.08, ll. 855–860 | "cosine and psi functions", "psi function" | cosine and sine; a single sine |
> | L1.08, ll. 1281–1286 | "real part A and the imaginary part B, that should be B" | real part $a$, imaginary part $b$ |
> | L1.08, ll. 2121–2134 | at "a thousand … 0.002 … minus one hundred and seventy nine point fifty" | at $\omega = 100$: $1.99\times10^{-4}$, −179.6°; at 1000: $1.99\times10^{-6}$, −179.96° |
> | L1.08, ll. 2202–2213 | peak above 1 "for a system with a damping ratio less than one" | $\vert G(i\omega_n)\vert>1$ needs $\zeta<0.5$; a peak exists for $\zeta<0.707$ |
> | L1.09, ll. 8, 69 | "body plots" | Bode plots (throughout Parts A and B) |
> | L1.09, l. 23 | "the friction response function" | frequency response function |
> | L1.09, l. 61 | "the cutter frequency" | the cut-off frequency |
> | L1.09, l. 146 | "minus 40 is 1 times to the minus 3, sorry, minus 2" | −40 dB is $10^{-2}$ (self-corrected) |
> | L1.09, ll. 154, 263 | "logarithmic loss" | laws of logarithms |
> | L1.09, l. 174 | "minus, sorry, 44.65" | 44.65 rad/s |
> | L1.09, ll. 245–249 | "first-order … 10 dBs per decade, second-order … 20 dBs per decade" | −20 and −40 dB/decade |
> | L1.09, l. 266 | "the buy and conquer" | divide and conquer |
> | L1.09, l. 314 | "about 20 degrees per decade" | +20 dB per decade for $G = s$ |
> | L1.09, ll. 318–319 | "for every pole every zero that you add" | each zero at the origin adds +90°; each pole −90° |
> | L1.09, l. 354 | "40 45 degrees per decade" | about 45° per decade |
> | L1.09, l. 360 | "set set line" | the $\zeta$ term |
> | L1.09, l. 364 | "the xb15" | the XV-15 |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| frequency response function (FRF) $G(i\omega)$ | frequency response, sinusoidal transfer function, $G(j\omega)$ | L1.08, L1.09 | the course writes $i$ |
| magnitude / gain $\lvert G(i\omega)\rvert$ | amplitude ratio, $B/A$ | L1.08 | |
| phase $\angle G(i\omega)$ | phase shift, phase lag (when negative) | L1.08 | |
| Bode plot | Bode diagram (magnitude and phase plots) | L1.09 | "body plots" in the transcripts |
| cut-off (corner) frequency | break frequency, −3 dB point, half-power point | L1.09 slide 6 | for a real pole the corner and the −3 dB point coincide |
| bandwidth | −3 dB bandwidth, $\omega_b$ | L1.09 | |
| peaking | resonant peak $M_r$ | L1.09 | |
| gain slope (dB/decade) | roll-off; also quoted as dB/octave (−6 dB/oct = −20 dB/dec) | L1.09 | |
| ZPK form | zero-pole-gain form, factored form | L1.09 slide 9 | |
| transient / steady-state response | natural / forced response | L1.08 | |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]] · Next: [[SESA2027 B1 - Control System Fundamentals and PID Control]]
- Concepts: [[Frequency Response Function]] · [[Bode Plot]] · [[Poles and Zeros]] · [[Gain and Phase Margins]]
- Used for: [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]] and sensor/filter design in [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]

## Year 1 foundation
- The receptance FRF $X/F = 1/(k - \omega^2m + j\omega c)$ and its stiffness-, damping- and mass-controlled regions: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources
- Lectures 1.08–1.09 (Dr S. Araujo-Estrada): slides `Lecture 1.08.pdf`, `Lecture 1.09.pdf`
- Transcripts (speech-to-text): `Lecture 1.08 recording.txt`, `Lecture 1.09 recording.txt`
- Blakelock (1991) *Automatic Control of Aircraft and Missiles*; Acree & Tischler (1993) NASA TP-3330
- Figures: `01 - Notes/Figures/generate_amc_a5_figures.py`

## Self-study tasks

One exercise was set in L1.08 (marked lecturer-set). The pole–zero stability/physicality question and reading an attenuation frequency off a Bode plot were named as exam or quiz questions (L1.08, ll. 107–112; L1.09, ll. 175–177).

### Core

- [ ] Lecturer-set (L1.08, ll. 1910–2088, an in-class exercise; for ω = 100, "I will let you do that on your own time", l. 2088): evaluate $\vert G(i\omega)\vert$ and $\angle G(i\omega)$ for the SPO TF at $\omega = 0, 0.1, 10, 100, \infty$, then guess and check the value at $\omega_n$ (ll. 2170–2182). → [[#Five-step recipe (SPO example)]]
- [ ] Decide whether a given pole–zero map is stable and physical (stated exam question). → [[#1. Poles, zeros and the complex plane (L1.08)]]
- [ ] Find the bandwidth, peaking and the −60 dB frequency of the SPO TF from its Bode plot. → [[#3. Bode plot (L1.09)]]
- [ ] PS2 Q1. → [[SESA2027 Practice Problems 2 Solutions]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q5. Bode magnitude and phase|Mock Q5]]

### Further practice

- [ ] Sketch the asymptotic Bode plot of the Blakelock $\theta/\delta_e$ TF factor by factor (suggested). → [[#4. Building a Bode plot from factors]]
- [ ] Derive $\omega_r=\omega_n\sqrt{1-2\zeta^2}$ and $\lvert G\rvert_{\max}=1/(2\zeta\sqrt{1-\zeta^2})$ (suggested). → [[#2. Response to a sinusoidal input]]
- [ ] Show that the steady-state output is $A\lvert G(i\omega)\rvert\sin(\omega t+\angle G)$ by complex partial fractions (suggested). → [[#2. Response to a sinusoidal input]]
