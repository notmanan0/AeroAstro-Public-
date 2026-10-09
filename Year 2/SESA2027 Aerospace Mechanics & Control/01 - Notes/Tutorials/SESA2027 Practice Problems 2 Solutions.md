---
title: "SESA2027 Practice Problems 2 Solutions"
module: "SESA2027 Aerospace Mechanics & Control"
type: tutorial
stream: "Part B: Control Systems"
tags:
  - sesa2027
  - tutorial-solutions
  - bode-plot
  - pid
  - root-locus
  - ziegler-nichols
sheet: "Practice problems 2 (Feb 2026, Dr S. Araujo-Estrada)"
theory_notes: ["[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]", "[[SESA2027 A5 - Frequency Response and Bode Plots]]", "[[SESA2027 B1 - Control System Fundamentals and PID Control]]", "[[SESA2027 B2 - Root Locus Method]]", "[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]"]
key_concepts: ["[[Bode Plot]]", "[[Gain and Phase Margins]]", "[[Transfer Function]]", "[[PID Controller]]", "[[Root Locus]]", "[[Ziegler-Nichols Tuning]]"]
status: complete
sources: ["02 - Sources/Problem Sheets/SESA2027 practice problems 2.pdf"]
---

# SESA2027 Practice Problems 2 Solutions

> [!abstract] Sheet Info
> Eight questions spanning A2, A5 and B1–B3. There are no printed answers, so every number here was checked in Python (`numpy`/`sympy`).
>
> | Question | Headline answer |
> |---|---|
> | Q1 | $\zeta = 0.4$, $\omega_n = 5$, DC gain −13.98 dB; GM = PM = ∞ |
> | Q3 | $G = -4.888(s+0.1609)/(s^2+0.7446s+18.73)$ |
> | Q6 | Stable for all $K>0$ |
> | Q7 | $\phi = 30^\circ$, $T_D = 0.192$ s, $K_p = 3.46$ |
> | Q8 | PID $K_p = 1.44$, $T_I = 0.55$ s, $T_D = 0.1375$ s |

## Theory Links
- [[SESA2027 A5 - Frequency Response and Bode Plots]] · [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]] · [[SESA2027 B1 - Control System Fundamentals and PID Control]] · [[SESA2027 B2 - Root Locus Method]] · [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]

---

## Q1: Bode analysis of $G(s) = \dfrac{5}{s^2+4s+25}$

### (i) Magnitude and phase
Compare with $\dfrac{K\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}$:
- $\omega_n = 5$ rad/s;
- $\zeta = 4/(2\cdot5) = 0.4$;
- DC gain $K = 5/25 = 0.2$.

$$
G(j\omega) = \frac{5}{(25-\omega^2)+4j\omega},\qquad |G| = \frac{5}{\sqrt{(25-\omega^2)^2+16\omega^2}},\qquad \angle G = -\mathrm{atan2}(4\omega,\ 25-\omega^2)
$$

| $\omega$ (rad/s) | $\lvert G\rvert$ | dB | $\angle G$ |
|---|---|---|---|
| 0 | 0.2000 | −13.98 | 0° |
| 1 | 0.2055 | −13.74 | −9.46° |
| 5 | 0.2500 | −12.04 | −90.00° |
| 20 | 0.01304 | −37.69 | −167.96° |

At $\omega = 5$: $|G| = 5/(4\cdot5) = 0.25 = K/(2\zeta)$, exactly as expected at $\omega_n$.

### (ii) Sketch features
- **Low frequency**: flat at $20\log0.2 = -13.98$ dB, with phase near 0°.
- **Corner**: at $\omega_n = 5$ rad/s. A small resonant peak appears because $\zeta = 0.4<0.707$:
  - peak at $\omega_r = 5\sqrt{1-0.32} = 4.12$ rad/s;
  - $M_r = K/(2\zeta\sqrt{1-\zeta^2}) = 0.273$, i.e. −11.3 dB.
- **High frequency**: the slope is **−40 dB/decade** (two poles).
- **Asymptotes**: $|G|\to25\cdot0.2/\omega^2 = 5/\omega^2$ and $\angle G\to-180^\circ$. The phase passes −90° at $\omega_n$.

![[amc_ps2_q1_bode.png|620]]

### (iii) Crossovers and margins
- $|G|_{max} = 0.273<1$, so the magnitude **never reaches 0 dB** and **$\omega_{gc}$ does not exist**. The PM is therefore **∞**, or undefined.
- The phase only **tends to** −180° as $\omega\to\infty$, so **$\omega_{pc}$ does not exist** and **GM = ∞**.
- **Interpretation**:
  - GM is how much the loop gain could be multiplied before instability.
  - PM is how much extra phase lag (e.g. delay) could be tolerated.
  - Here, in unity feedback, the closed-loop characteristic polynomial $s^2+4s+(25+5k)$ is stable for every $k>0$. A second-order system with no delay can never be destabilised by gain. See [[Gain and Phase Margins]].

---

## Q2: Elevator derivatives

### (i) Show $Z_\eta = -\dfrac{S_T}{S}a_2$
The tail force acts along $-z$ (lift is upward), so $Z_T = -L_T = -\tfrac12\rho V_0^2S_TC_{L_T}$ with $C_{L_T} = a_0+a_1\alpha_T+a_2\eta$.

$$
\mathring Z_\eta = \frac{\partial Z_T}{\partial\eta} = -\tfrac12\rho V_0^2S_Ta_2
$$

Non-dimensionalise with $\tfrac12\rho V_0^2S$:

$$
Z_\eta = \frac{\mathring Z_\eta}{\tfrac12\rho V_0^2S} = -\frac{S_T}{S}a_2\qquad\blacksquare
$$

### (ii) Effect of a **negative** elevator deflection
A negative deflection means trailing edge up: $\Delta C_{L_T} = a_2\eta<0$, so the tail lift decreases (the tail is pushed down).
- **$X_\eta$**:
  - $X_\eta = -2\frac{S_T}{S}k_TC_{L_T}a_2$ is a second-order (induced-drag) effect and is **small**.
  - A negative $\eta$ changes $C_{L_T}$, so the tail's induced drag changes as $C_{L_T}^2$. Its axial effect is usually negligible.
- **$Z_\eta$**:
  - The derivative $Z_\eta = -\frac{S_T}{S}a_2<0$ itself does not depend on the sign of $\eta$.
  - The force $\Delta Z = \mathring Z_\eta\eta$ becomes **positive**, i.e. **downward**, on the tail. This is a small loss of total lift.
- **$M_\eta$**:
  - $M_\eta = -\bar V_Ta_2<0$ (a strong derivative, because of the long tail arm).
  - With $\eta<0$, $\Delta M = \mathring M_\eta\eta>0$: a **nose-up** pitching moment. This is how the pilot pulls up.
  - Note that the initial $\Delta Z$ briefly opposes the intended climb (non-minimum-phase behaviour in $h/\eta$).

### (iii) Why elevator derivatives sit in $\mathbf B$
- The elevator is an **external input** $u$, not a state.
- Its forces and moments $\Delta X_c = \mathring X_\eta\eta$, $\Delta Z_c = \mathring Z_\eta\eta$, $\Delta M_c = \mathring M_\eta\eta$ are linear in $\eta$. So they appear as the forcing term $\mathbf B'\mathbf u$ in $\mathbf M\dot{\mathbf x} = \mathbf A'\mathbf x+\mathbf B'\mathbf u$, giving $\mathbf B = \mathbf M^{-1}\mathbf B'$.
- $\mathbf A$ contains derivatives with respect to the **states** ($u, w, q, \theta$). $\mathbf B$ contains derivatives with respect to the **controls** (and gusts), and describes how inputs drive the dynamics. See [[State-Space Representation]].

---

## Q3: State space to transfer function

$$
\mathbf A = \begin{bmatrix}-0.2956&178\\-0.1045&-0.4490\end{bmatrix},\quad\mathbf B = \begin{bmatrix}-6.300\\-4.888\end{bmatrix},\quad\mathbf C = [0\ \ 1]
$$

### (i) $G(s) = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B$

$$
s\mathbf I-\mathbf A = \begin{bmatrix}s+0.2956&-178\\0.1045&s+0.4490\end{bmatrix},\qquad \det = (s+0.2956)(s+0.4490)+178(0.1045) = s^2+0.7446s+18.7337
$$

$$
\mathrm{adj}(s\mathbf I-\mathbf A) = \begin{bmatrix}s+0.4490&178\\-0.1045&s+0.2956\end{bmatrix}
$$

$\mathbf C$ picks the second row, so

$$
\mathbf C\,\mathrm{adj}\,\mathbf B = -0.1045(-6.300)+(s+0.2956)(-4.888) = -4.888s-0.7865
$$

$$
\boxed{G(s) = \frac{q(s)}{\eta(s)} = \frac{-4.888s-0.7865}{s^2+0.7446s+18.7337}}
$$

### (ii) Standard form

$$
G(s) = \frac{K(s+z)}{s^2+2\zeta\omega_ns+\omega_n^2}:\qquad K = -4.888,\quad z = 0.1609,\quad \omega_n = \sqrt{18.734} = 4.328\ \text{rad/s},\quad \zeta = \frac{0.7446}{2(4.328)} = 0.0860
$$

### (iii) Poles and behaviour
Poles: $s = -0.3723\pm4.312i$. The zero is at $s = -0.161$.
- **Stable**: both poles have $\mathrm{Re}<0$.
- **Oscillatory** and **very lightly damped** ($\zeta = 0.086$):
  - $\omega_d = 4.31$ rad/s, so $T = 1.46$ s;
  - $t_{1/2} = \ln2/0.3723 = 1.86$ s;
  - the pole-based $OS\approx e^{-\zeta\pi/\sqrt{1-\zeta^2}} = 76\%$;
  - $t_s(1\%)\approx4.6/0.3723 = 12.4$ s.
- **Negative gain** ($K<0$): a positive elevator input gives a negative pitch rate, i.e. trailing edge down gives nose down. The DC gain is $Kz/\omega_n^2 = -0.042$.
- The slow zero near the origin gives a small, slow tail in the response.

The poorly damped short period makes this a clear candidate for pitch-rate feedback (a SAS).

---

## Q4: Control objectives and P control

### (i) Definitions
- **Regulation**: hold the output at a constant set point despite disturbances (e.g. altitude hold).
- **Tracking**: make the output follow a time-varying reference (e.g. a commanded pitch-rate profile).
- **Disturbance rejection**: minimise the effect of external inputs such as gusts and thrust changes on the output.
- **Performance management**: meet the transient specifications (rise time, overshoot, settling time) and steady-state accuracy, within actuator and control-effort limits.

### (ii) Effect of increasing $|K_p|$ for the Q3 plant
The closed loop is

$$
\frac{X}{R} = \frac{K_pK(s+z)}{s^2+(2\zeta\omega_n+K_pK)s+(\omega_n^2+K_pKz)}
$$

Since $K<0$, negative feedback needs **$K_p<0$** (see [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]). Then $K_pK>0$.

| $K_p$ | $\omega_n$ | $\zeta$ | OS (pole estimate) | DC gain $X/R$ | $e_{ss}$ |
|---|---|---|---|---|---|
| −0.1 | 4.34 | 0.14 | 64 % | 0.004 | 99.6 % |
| −0.5 | 4.37 | 0.37 | 29 % | 0.021 | 97.9 % |
| −1 | 4.42 | 0.64 | 7 % | 0.040 | 96.0 % |
| −2 | 4.51 | 1.17 | 0 | 0.078 | 92.3 % |
| −10 | 5.16 | 4.81 | 0 | 0.296 | 70.4 % |

- **Rise time**:
  - A larger $|K_p|$ adds damping ($b = 0.7446+4.888|K_p|$) faster than it raises $\omega_n$.
  - The oscillatory rise first becomes faster and cleaner.
  - At high gain the system becomes overdamped, and the response is set by the slow closed-loop pole approaching the zero.
  - In the classic P-control picture, a higher gain gives a faster rise.
- **Overshoot**: here it falls with $|K_p|$, because P feedback of $q$ acts like **pitch damping**. In the generic case of a plant without this structure, a higher P gain increases overshoot.
- **Steady-state error**: it falls as $|K_p|$ rises, but **never reaches zero** without integral action. For this plant it stays large, because the plant's DC gain is tiny. That motivates the I term.
- **Robustness**:
  - This loop stays stable for all $K_p<0$ (it is second order: $b,c>0$).
  - Real loops add actuator lag, sensor lag and delay, so a high gain erodes GM and PM, amplifies measurement noise and can saturate the elevator.

---

## Q5: PID actions

### (i) Advantages and drawbacks

| Action | Advantage | Drawback |
|---|---|---|
| **P** | Immediate response proportional to the error; simple; speeds up the response | Leaves a steady-state error; a high gain gives oscillation and noise sensitivity |
| **I** | **Eliminates steady-state error** (a pole at the origin) | Adds −90° of phase lag, which slows the response and adds overshoot; **integrator wind-up** under saturation |
| **D** | Anticipates the error trend, **adds damping**, reduces overshoot | **Amplifies high-frequency noise**; derivative kick on reference steps |

### (ii) Noise sensitivity of D
- $C_D(j\omega) = K_Dj\omega$ has a gain that **grows linearly with frequency** (+20 dB/dec).
- Measurement noise is broadband and small, but fast. Differentiating it multiplies each component by $\omega$.
- In discrete form, $(n[k]-n[k-1])/T_s$ gets divided by a small $T_s$. See [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]].

**Mitigations**:
- A **filtered derivative**, $K_D\dfrac{s}{1+s/N}$ (a first-order low-pass on the D term).
- Differentiating the **measurement rather than the error** avoids derivative kick.
- Using a **rate gyro** measures $q$ directly instead of differentiating $\theta$.
- Limiting the bandwidth and adding anti-alias filtering.

---

## Q6: Root locus of $G = \dfrac{K}{s(s+4)}$

### (i) Sketch
- **Poles** at $0$ and $-4$; **no zeros**, so $n-m = 2$ branches go to infinity.
- **Real-axis segment**: $[-4,0]$, because a point there has one pole to its right (an odd count).
- **Asymptotes**:
  - angles $\theta = (2k+1)180^\circ/2 = \pm90^\circ$;
  - centroid $\sigma_a = (0-4)/2 = -2$.
- **Breakaway**: $K = -s(s+4)$, and $dK/ds = -(2s+4) = 0$ gives $s = -2$, at $K = 4$.
- The branches leave $0$ and $-4$, meet at $-2$, then split vertically along $\mathrm{Re}(s) = -2$.

![[amc_ps2_q6_root_locus.png|700]]

### (ii) Range of $K$ for stability
The characteristic equation is $s^2+4s+K = 0$. A quadratic is stable iff all coefficients are positive, so the condition is **$K>0$**, i.e. stable for every positive gain.

- $\mathrm{Re}(s) = -2$ for all $K>4$.
- $\zeta = 2/\sqrt K$ falls as $K$ grows. The system is more oscillatory, but never unstable.

### (iii) Adding a PD zero at $s = -1$
The open loop becomes $G = K(s+1)/[s(s+4)]$, and the characteristic equation is $s^2+(4+K)s+K = 0$.

- Real-axis segments are now $[-1,0]$ and $(-\infty,-4]$. Now $n-m = 1$, so there is a single asymptote along 180°.
- The discriminant is $(4+K)^2-4K = K^2+4K+16>0$ for all $K$. So the **locus never leaves the real axis**: one branch runs $0\to-1$ (to the zero), and the other runs $-4\to-\infty$.
- **Behaviour**:
  - no oscillation (the closed-loop poles are real), always stable;
  - the zero pulls the locus left, which is the phase lead from D;
  - the dominant pole approaches $-1$ from the right, so the speed is limited by the zero location;
  - the zero itself adds a little overshoot in the step response.

---

## Q7: Frequency-response PD design
Given $|G(3i)| = 0.25$ and $\angle G(3i) = -155^\circ$, with target PM $= 55^\circ$ at $\omega_{gc} = 3$ rad/s.

### (i) Required phase lead

$$
PM = 180^\circ+\angle C+\angle G\;\Rightarrow\;\phi_{PD} = 55^\circ-(180^\circ-155^\circ) = \boxed{30^\circ}
$$

The plant alone would have a PM of 25°.

### (ii) Derivative time

$$
\tan^{-1}(\omega_{gc}T_D) = 30^\circ\;\Rightarrow\;T_D = \frac{\tan30^\circ}{3} = \boxed{0.1925\ \text{s}}
$$

### (iii) Proportional gain

$$
|1+j\omega_{gc}T_D| = \sqrt{1+\tan^230^\circ} = \sec30^\circ = 1.1547,\qquad K_p = \frac{1}{0.25\times1.1547} = \boxed{3.464}
$$

**Check**: $|K_p(1+3T_Dj)G| = 3.464\times1.1547\times0.25 = 1.000$ ✔, and the phase is $30^\circ-155^\circ = -125^\circ$, so PM $= 55^\circ$ ✔.

The PD form is $C(s) = 3.464(1+0.1925s)$, i.e. $K_d = K_pT_D = 0.667$.

---

## Q8: Ziegler–Nichols ultimate-sensitivity tuning
Given $K_u = 2.4$ and $T_u = 1.1$ s.

### (i) Gains

| Controller | $K_p$ | $T_I$ | $T_D$ | $K_i = K_p/T_I$ | $K_d = K_pT_D$ |
|---|---|---|---|---|---|
| **P** | $0.5K_u = 1.20$ | – | – | – | – |
| **PI** | $0.45K_u = 1.08$ | $T_u/1.2 = 0.917$ s | – | 1.178 | – |
| **PID** | $0.6K_u = 1.44$ | $0.5T_u = 0.55$ s | $0.125T_u = 0.1375$ s | 2.618 | 0.198 |

### (ii) Why ZN is aggressive and needs refinement
- ZN targets **quarter-amplitude decay**. Each oscillation peak is a quarter of the previous one, which corresponds to $\zeta\approx0.2$ and roughly 25–50 % overshoot.
- The rules are **empirical**: they are derived from process-control plants, and they assume the plant can be driven to sustained oscillation. That is dangerous to try on an aircraft.
- They ignore actuator limits, noise, delays and structural modes, and give no guaranteed margins.
- **Aerospace refinement** is needed for:
  - handling-qualities limits, e.g. SPO damping of at least 0.35 for Level 1;
  - passenger comfort and structural loads;
  - robustness across the flight envelope (MIL-F-9490D requires GM ≥ 4.5–6 dB and PM ≥ 30–45°);
  - certification.
- So ZN serves as a **starting point**. It is followed by frequency-response or root-locus retuning and robustness checks. See [[Ziegler-Nichols Tuning]].

## Related
- [[SESA2027 Practice Problems 1 Solutions]] · [[SESA2027 Part C Problem Sheet Solutions]] · [[SESA2027 Aerospace Mechanics & Control Hub]] · [[SESA2027 Formula Sheet]]
