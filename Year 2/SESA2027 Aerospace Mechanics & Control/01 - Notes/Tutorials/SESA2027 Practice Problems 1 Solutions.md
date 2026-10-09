---
title: "SESA2027 Practice Problems 1 Solutions"
module: "SESA2027 Aerospace Mechanics & Control"
type: tutorial
stream: "Part A: Dynamic Systems"
tags:
  - sesa2027
  - tutorial-solutions
  - dynamic-modes
  - step-response
  - frequency-response
sheet: "Practice problems 1 (Jan 2026, Dr S. Araujo-Estrada)"
theory_notes: ["[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]", "[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]", "[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
key_concepts: ["[[Short Period Oscillation]]", "[[Phugoid Mode]]", "[[Damping Ratio and Natural Frequency]]", "[[Step Response Specifications]]", "[[Frequency Response Function]]"]
status: complete
sources: ["02 - Sources/Problem Sheets/SESA2027 practice problems 1.pdf"]
---

# SESA2027 Practice Problems 1 Solutions

> [!abstract] Sheet Info
> Four questions on Part A: modes from the stability quartic, the SPO approximation, step-response specifications and frequency response. All given answers are reproduced ✔, with **one discrepancy**. In Q3 the sheet's $OS = 22.403\%$ comes from dropping a square root; the correct value is **25.38 %**.

## Theory Links
- [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]] · [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]] · [[SESA2027 A5 - Frequency Response and Bode Plots]]
- Concepts: [[Characteristic Equation and Eigenvalues]] · [[Damping Ratio and Natural Frequency]] · [[Short Period Oscillation]] · [[Phugoid Mode]] · [[Step Response Specifications]] · [[Frequency Response Function]]

**Toolkit**: for a mode $\lambda = \sigma\pm i\omega$,

$$
T = \frac{2\pi}{\omega},\qquad t_{1/2} = \frac{\ln2}{|\sigma|}\ (\sigma<0),\qquad t_2 = \frac{\ln2}{\sigma}\ (\sigma>0),\qquad \omega_n = \sqrt{\sigma^2+\omega^2},\quad \zeta = -\frac{\sigma}{\omega_n}
$$

---

## Q1: Stability quartic $(\lambda^2+1.40\lambda+9.49)(\lambda^2-0.0016\lambda+0.0016) = 0$

### (i) SPO
The SPO is the **fast** mode, so it is the quadratic with the larger $\omega_n$: $\lambda^2+1.40\lambda+9.49$, with $\omega_n = \sqrt{9.49} = 3.08$ rad/s against 0.04 rad/s for the other quadratic.

$$
\lambda = \frac{-1.40\pm\sqrt{1.96-37.96}}{2} = -0.7\pm3i
$$

- $\sigma = -0.7<0$, so the mode is **stable**. The damping ratio is $\zeta = 0.7/3.08 = 0.227$.
- $T = 2\pi/3 = \mathbf{2.09}$ **s**.
- $t_{1/2} = \ln2/0.7 = \mathbf{0.99}$ **s** ✔

### (ii) Phugoid
The phugoid is the slow quadratic, $\lambda^2-0.0016\lambda+0.0016$:

$$
\lambda = \frac{0.0016\pm\sqrt{0.0016^2-4(0.0016)}}{2} = 8.0\times10^{-4}\pm4.0\times10^{-2}i
$$

- $\sigma = +8\times10^{-4}>0$, so the mode is **unstable**. Equivalently, the negative coefficient of $\lambda$ means $\zeta = -0.02$.
- $T = 2\pi/0.039992 = \mathbf{157}$ **s**.
- Time to double: $t_2 = \ln2/0.0008 = \mathbf{866}$ **s** ✔

This is a slow divergence that a pilot corrects easily. It would still fail flying-qualities requirements for unattended flight.

### (iii) Main features

| | SPO | Phugoid |
|---|---|---|
| Speed | Fast (period of seconds) | Slow (period of minutes) |
| Damping | Heavy: tail $\Delta\alpha_T\approx ql/U$ gives large $\mathring M_q$ | Light: only the drag difference dissipates energy |
| States involved | $w$ ($\alpha$) and $q$, $\theta$; **speed nearly constant** | $u$, $\theta$, height; **$\alpha$ nearly constant** |
| Physics | Pitch stiffness ($M_w<0$) overshoots, damped by $M_q$ | Exchange of kinetic and potential energy, $mgh+\tfrac12mV^2\approx$ const |
| Pilot impact | Governs handling (response to stick) | Easily corrected; can even be slightly unstable |

### (iv) Sketch of the SPO pitch response
The sketch is a cosine with period 2.09 s inside an envelope $e^{-0.7t}$ that halves every 0.99 s. After about $3t_{1/2}\approx3$ s the amplitude is below 1/8 of the initial value.

![[amc_ps1_q1_spo_pitch.png|620]]

---

## Q2: SPO approximation for the given aircraft

**Data**: $m = 17642$ kg, $I_{yy} = 165669$ kg m², $U_\infty = 356$ m/s, $\mathring M_{\dot w} = -132.47$, $\mathring Z_w = -12809.54$, $\mathring M_w = -13465.56$, $\mathring M_q = -123272.02$.

The sheet prints $I_{yy}$ as "16,5669", a misplaced comma. The value is 165 669 kg m², the same as the F-4C in L1.06.

### (i) $\omega_n$ and $\zeta$
The SPO characteristic equation from [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]], divided by $mI_{yy}$, is

$$
\lambda^2-\left(\frac{\mathring Z_w}{m}+\frac{\mathring M_q}{I_{yy}}+\frac{U_\infty\mathring M_{\dot w}}{I_{yy}}\right)\lambda+\left(\frac{\mathring Z_w\mathring M_q}{mI_{yy}}-\frac{U_\infty\mathring M_w}{I_{yy}}\right) = 0
$$

Evaluate the three terms of the $\lambda$ coefficient:
- $\mathring Z_w/m = -0.72608$
- $\mathring M_q/I_{yy} = -0.74409$
- $U_\infty\mathring M_{\dot w}/I_{yy} = -0.28466$

Their sum is $-1.75483$, so the coefficient of $\lambda$ is $2\zeta\omega_n = 1.75483$.

For the constant term:
- $\mathring Z_w\mathring M_q/(mI_{yy}) = 0.54027$
- $-U_\infty\mathring M_w/I_{yy} = 28.93564$

So $\omega_n^2 = 29.47591$ and

$$
\boxed{\omega_n = 5.429\ \text{rad/s},\qquad \zeta = \frac{1.75483}{2(5.429)} = 0.162}\ ✔
$$

### (ii) Eigenvalues

$$
\lambda = -\zeta\omega_n\pm i\omega_n\sqrt{1-\zeta^2} = \boxed{-0.877\pm5.358i}\ ✔
$$

### (iii) Time characteristics

$$
T = \frac{2\pi}{5.358} = \mathbf{1.173}\ \text{s},\qquad t_{1/2} = \frac{\ln2}{0.877} = \mathbf{0.790}\ \text{s}\ ✔
$$

Compare with the F-4C at 178 m/s ($\omega_n = 1.41$, $\zeta = 0.26$). At double the speed:
- $\omega_n$ rises, mainly through $U_\infty\mathring M_w$;
- $\zeta$ falls to 0.16, below the Level 1 Category A minimum of 0.35.

That is a case for pitch-rate feedback, as discussed in [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]].

---

## Q3: Transfer function and step response

### (i) Roots of the denominator of $G(s)$
The roots of $A(s)$ are the **poles**. They are the roots of the characteristic equation, i.e. the **eigenvalues** of $\mathbf A$, and they define the system's natural modes: their decay rates ($\sigma$) and frequencies ($\omega$). They determine **stability**: every pole must satisfy $\mathrm{Re}<0$. The input only decides how strongly each mode is excited. See [[Poles and Zeros]].

### (ii) Specifications for $\omega_n = 3.65$ rad/s, $\zeta = 0.40$

$$
t_r\approx\frac{1.8}{\omega_n} = \mathbf{0.493}\ \text{s}\ ✔,\qquad t_s\approx\frac{4.6}{\zeta\omega_n} = \frac{4.6}{1.46} = \mathbf{3.151}\ \text{s}\ ✔
$$

$$
OS = e^{-\zeta\pi/\sqrt{1-\zeta^2}}\times100\% = e^{-0.4\pi/0.9165} = e^{-1.3711} = \mathbf{25.38\%}
$$

> [!warning] Sheet answer 22.403 % is inconsistent with the formula
> $e^{-0.4\pi/0.84} = e^{-1.4960} = 22.40\%$. The sheet divided by $1-\zeta^2 = 0.84$ instead of $\sqrt{1-\zeta^2} = 0.9165$. The lecture formula (L1.07 slide 21) and a direct simulation both give **25.4 %**. The peak occurs at $t_p = \pi/\omega_d = 0.939$ s.
>
> Also, the exact 10–90 % rise time for $\zeta = 0.4$ is about $1.46/\omega_n = 0.40$ s. The $1.8/\omega_n$ rule is only approximate.

### (iii) Sketch
The input $u(s) = \omega_n^2mI_{yy}/s$ cancels the $1/(mI_{yy})$ factor in $G$, so the response settles at **1**. Annotate:
- $t_r$, between the 10 % and 90 % crossings;
- the first peak at $t_p\approx0.94$ s, at height $1.254$;
- $t_s$, where the response enters the ±1 % band.

![[amc_ps1_q3_step_annotated.png|620]]

---

## Q4: Frequency response

### (i) Transient vs steady-state
- **Transient response**: the part generated by the **system's poles**, $\sum r_ie^{p_it}$. It is the natural response set by the initial conditions and the start of the input. For a stable system it decays to zero.
- **Steady-state response**: the part generated by the **input's poles** (here $\pm i\omega$). It is the forced response, which persists as long as the input does. For a sinusoid it is a sinusoid at the same frequency, scaled by $|G(i\omega)|$ and shifted by $\angle G(i\omega)$.

### (ii) $|G|$ and $\angle G$ for $\omega_n = 1.9$, $\zeta = 0.35$, $\omega = 1.7$
With $A = mI_{yy}\omega_n^2$, the normalised response is

$$
\frac{G(i\omega)}{\text{(per unit }A)} = \frac{\omega_n^2}{(\omega_n^2-\omega^2)+i\,2\zeta\omega_n\omega} = \frac{3.61}{(3.61-2.89)+i(2)(0.35)(1.9)(1.7)} = \frac{3.61}{0.72+2.261i}
$$

$$
|G| = \frac{3.61}{\sqrt{0.72^2+2.261^2}} = \frac{3.61}{2.373} = \boxed{1.521}\ ✔,\qquad \angle G = -\tan^{-1}\frac{2.261}{0.72} = \boxed{-72.34^\circ}\ ✔
$$

### (iii) Interpretation
$|G| = 1.52>1$: the output amplitude is **52 % larger** than the static response. The forcing frequency, 1.7 rad/s, is close to the resonant frequency $\omega_r = \omega_n\sqrt{1-2\zeta^2} = 1.65$ rad/s. The system is lightly damped ($\zeta = 0.35<0.707$), so near resonance it **amplifies** the input.

The output also lags the input by 72°, just short of the 90° lag reached at $\omega = \omega_n$. Physically, pitch inputs (or gusts) near the SPO frequency produce disproportionately large pitch oscillations. That is one reason the SPO needs heavy damping.

## Related
- [[SESA2027 Practice Problems 2 Solutions]] · [[SESA2027 Aerospace Mechanics & Control Hub]] · [[SESA2027 Formula Sheet]]
