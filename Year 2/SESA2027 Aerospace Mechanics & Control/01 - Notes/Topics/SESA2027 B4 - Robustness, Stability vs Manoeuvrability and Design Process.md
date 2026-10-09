---
title: "SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part B: Control Systems"
order: 9
tags:
  - sesa2027
  - robustness
  - handling-qualities
  - control-design-process
aliases: ["Robust Control Design", "Stability vs Manoeuvrability"]
date: 2026-09-23
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]"]
next_topics: ["[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]"]
key_concepts: ["[[Gain and Phase Margins]]", "[[Stability vs Manoeuvrability]]", "[[Closed-Loop Transfer Function]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 2.07.pdf", "02 - Sources/Lectures/Lecture 2.08.pdf", "02 - Sources/Lectures/lecture_2.09.pdf"]
---

# SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process

> [!abstract] Summary
> A PID must always provide **negative feedback**: $T_D>0$, $T_I>0$, and the sign of $K_p$ matched to the plant. A **robust** controller stays stable and meets its specifications under **model uncertainty**, **disturbances** and **measurement noise**. The closed-loop output separates into three transfer functions, one each for reference, disturbance and noise. That separation shows the trade-offs: high loop gain rejects disturbances, but it also amplifies noise. In handling qualities, stability (high $\zeta$, low $\omega_n$) competes with manoeuvrability (high $\omega_n$ and bandwidth). The full design process runs from modelling to analysis, controller design, robustness checks, and interpretation of the results.

## Key Concepts
- [[Gain and Phase Margins]] · [[Stability vs Manoeuvrability]] · [[Closed-Loop Transfer Function]]

---

## 1. Allowable gain signs (L2.07)
With $C(s) = K_p\left(1+T_Ds+\dfrac{1}{T_Is}\right)$:
- **$T_D<0$**: turns damping into **anti-damping**. It injects energy at high frequency, amplifies noise, and can destabilise the loop.
- **$T_I<0$**: the integral action has the wrong sign, giving wind-up in the wrong direction and divergence. Never choose a negative $T_I$.
- **$K_p<0$**: flips the control action into positive feedback, which is usually unstable. **However**, if the plant gain is negative (e.g. elevator-up gives a nose-up moment, so $q/\eta<0$), a negative $K_p$ **restores** negative feedback. That is the case in the SPO examples.

> [!tip] Rule
> **Always choose $T_D>0$ and $T_I>0$.** If a design produces negative values, the controller structure is wrong.

## 2. Why robustness matters in aerospace
- Safety-critical systems.
- Regulations: CS/FAR-25 and MIL-F-8785C margin requirements.
- Passenger comfort.
- Operational variability (mass, CG, fuel, Mach, altitude).
- Environmental uncertainty (gusts, icing, sensor noise, actuator dynamics, flexibility).

**Real-world deviations**:
- **Model uncertainty**: derivatives vary with $h$, $M$ and $Re$; CG shifts; unmodelled sensor and actuator dynamics; flexible modes.
- **External disturbances**: turbulence (Dryden or von Kármán spectra), gust loads (CS 25.341), thrust variations, updrafts.
- **Measurement noise**: gyro drift, accelerometer bias, air-data noise, quantisation, surface-position feedback noise.

**Margins in regulations**:
- FAA/EASA do not specify numerical margins; see CS 25.672 (SAS), 25.173/175 (static longitudinal stability), 25.253 (high speed) and AC 25.629-1C (aeroelastic).
- **MIL-F-9490D**: GM ≥ 4.5 dB and PM ≥ 30° typical, up to GM 6 dB and PM 45° depending on mode frequency and airspeed.
- Used with MIL-STD-1797A (flying qualities).

## 3. The three closed-loop transfer functions
Using the general block diagram (controller $C$, plant $G$, sensor $H$, process noise $U_P$, measurement noise $X_N$):

$$
X(s) = \underbrace{\frac{GC}{1+GCH}}_{\text{reference}}R+\underbrace{\frac{G}{1+GCH}}_{\text{disturbance}}U_P-\underbrace{\frac{GCH}{1+GCH}}_{\text{noise}}X_N
$$

### (a) Sensitivity to model parameters
Take $U_P = X_N = 0$ and $H = 1$. For $G = \dfrac{K(s+z)}{s^2+2\zeta\omega_ns+\omega_n^2}$ with $C = K_p$:

$$
\frac{X}{R} = \frac{K(s+z)K_p}{s^2+(KK_p+2\zeta\omega_n)s+(\omega_n^2+KK_pz)}
$$

The closed-loop characteristic polynomial is a quadratic $as^2+bs+c$ with $a=1$, $b = KK_p+2\zeta\omega_n$ and $c = \omega_n^2+KK_pz$. A second-order polynomial is **stable iff $b>0$ and $c>0$**.
- Open loop stable means $\zeta>0$ and $\omega_n>0$.
- The sign of the zero $z$ may be positive or negative.
- $K$ and $K_p$ have opposite signs (see §1), so $KK_p<0$. Then $b>0$ requires $|KK_p|<2\zeta\omega_n$, and $c>0$ requires $\omega_n^2>|KK_pz|$ when $z>0$.

Errors in the estimated parameters move $b$ and $c$:
- errors in $z$ affect $c$;
- errors in $\omega_n$ affect $b$ and $c$;
- errors in $\zeta$ affect $b$.

A design with little margin can become unstable. Parabola picture: a negative $b$ shifts the parabola right, and a negative $c$ lowers it below the axis (L2.07 slide 16).

### (b) Disturbance rejection
With $R = X_N = 0$:

$$
X = \frac{G}{1+GC}U_P
$$

Gusts enter through $\mathbf B'$ via $u_g$ and $w_g$. A typical model is the 1-cosine gust, $\alpha_g(t) = \frac{A_g}{2}[1-\cos(2\pi t/T_g)]$.
- The controller appears only in the denominator. It cannot shape the disturbance directly and can only react through feedback.
- **Higher low-frequency loop gain and bandwidth give better rejection.**

### (c) Measurement noise
With $R = U_P = 0$:

$$
X = -\frac{GCH}{1+GCH}X_N
$$

- Noise enters through the feedback path and is subtracted at the summing junction.
- High controller gain at high frequency amplifies noise, so the bandwidth must be chosen carefully.
- **Sampling**: Nyquist–Shannon requires $f_s>2f_{max}$; in practice use about $10f_{max}$. Noise above Nyquist **aliases** into the loop, so use anti-alias filters before the ADC. See [[Nyquist Sampling and Aliasing]].

### Controller adjustments for robustness

| Problem | Solution |
|---|---|
| Poor stability margin due to uncertainty | Add lead or damping, reduce gain |
| Poor gust rejection | Increase low-frequency gain |
| Noise amplification | Reduce bandwidth, add low-pass filtering |
| Sensitivity to $C_{m_\alpha}$ | Add pitch-rate feedback |

Other strategies:
- Reduce the crossover frequency to improve noise tolerance.
- Use washout filters.
- Limit actuator bandwidth so structural modes are not excited.

**Beyond SISO**:
- Lead-lag compensators.
- Nested (cascaded) loops, e.g. ArduCopter and Crazyflie: position → velocity → attitude → rate PID loops.
- Gain scheduling across the flight envelope.

## 4. Stability vs manoeuvrability (L2.08)
- **Static stability**: $C_{m_\alpha}<0$ for pitch stability.
- **Dynamic stability**: the oscillations decay (SPO and phugoid).
- **Manoeuvrability**: the ability to change the flight path quickly on command, measured by $\left|\dfrac{\partial q}{\partial\eta}\right|_{max}$. High manoeuvrability means a large DC gain, high bandwidth and lower (but still stable) damping.

| Highly stable aircraft | Highly manoeuvrable aircraft |
|---|---|
| Large negative $C_{m_\alpha}$ | Small or positive $C_{m_\alpha}$ (relaxed stability) |
| High damping $\zeta$ | Lower damping, faster response |
| Sluggish, smooth response | Quick, agile response |
| Low control effort | High control power required |
| Transport aircraft (B777, A350), gliders | Fighters (F-16, Typhoon: unstable, fly-by-wire) |

**On the SPO**:
- More stability means $\zeta$ up and/or $\omega_n$ down: the poles move left, response is slower but better damped.
- More manoeuvrability means $\omega_n$ up and $\zeta$ down: the poles move right, response is faster but less damped.
- The trade-off is visible directly: bandwidth $\propto\omega_n$ and overshoot $\propto e^{-\zeta\pi/\sqrt{1-\zeta^2}}$.

**Handling qualities**:
- **Cooper–Harper scale** (1–10), and Levels 1–3 of flying qualities.
- Short-period damping limits (Cook Table 10.4). For Level 1:

| Category | $\zeta_{min}$ | $\zeta_{max}$ |
|---|---|---|
| A | 0.35 | 1.30 |
| B | 0.30 | 2.00 |
| C | 0.50 | 1.30 |

- The **thumbprint** plot of $\omega_n$ against $\zeta$ (Etkin) shows the "satisfactory" region.

**Controller design to balance them**:
- For passenger aircraft (more stable): pitch-rate feedback (damping), low-pass filters, lead–lag for margins.
- For fighters (more manoeuvrable): reduced static margin, high-bandwidth fly-by-wire, state feedback (LQR), command shaping.

Modern aircraft do not rely only on natural stability; the control system provides synthetic stability. See [[Stability vs Manoeuvrability]].

## 5. The control system design process (L2.09)
1. **Model the aircraft dynamics**: EOM, then linearise about trim, then state space, then extract the mode (SPO), then a second-order model $G = \dfrac{K(s+z)}{s^2+2\zeta\omega_ns+\omega_n^2}$. The model hierarchy runs PDEs → nonlinear ODEs → linear ODEs → LTV → **LTI**.
2. **Analyse the dynamics**: time response ($\omega_n$, $\zeta$, $t_r$, $t_s$, OS) and frequency response (Bode, crossovers, bandwidth, margins).
3. **Select and design a controller**: root locus (pole placement), frequency response (margin shaping), or ZN (crude on its own). Example specifications: stable, $t_r<1.0$ s, $t_s(5\%)<6.0$ s, $OS<20\%$.
4. **Evaluate robustness**: vary the model, e.g. $\Delta\omega_n = 0.8$, $1.0$, $1.2$.
   - With $K_p = -1.75$, $T_D = 5\times10^{-2}$, $T_I = 2.5\times10^{-1}$, the OS specification is violated under uncertainty.
   - Retuning to $T_D = 1.5\times10^{-1}$ meets all specifications.
5. **Interpret the results**: adequate margins? handling-qualities goals met? sensitivity? consistent across the envelope? bandwidth neither too high (noise) nor too low (sluggish)? Always keep in mind safety, regulations, handling qualities and comfort.

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]] · Next: [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]
- Static margin link: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Year 3: [[SESA3047 Advanced Aerospace Mechanics & Control]]

## Sources
- Lectures 2.07–2.09; Cook (2007) Ch. 10; Etkin (2000); MIL-F-9490D, MIL-STD-1797A
