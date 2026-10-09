---
title: "FEEG1004 Formula Sheet"
module: "FEEG1004 Electronics"
type: formula
aliases: ["FEEG1004 formulae", "Electrical and Electronic Systems formula sheet", "Electronics formula sheet"]
tags: [feeg1004, formula, exam-prep]
status: complete
sources: ["01 - Notes/Topics", "02 - Sources/S1 Fundamentals/S1 Equations Sheet.pdf"]
---

# FEEG1004 Formula Sheet

Everything on one page, organised by part. Each section links to its topic note.

> [!warning] Conventions used in FEEG1004
> - **Voltage arrows** point to the more positive end. Current enters a resistor at its + end.
> - **KVL**: add rises and subtract $IR$ drops going round in the current direction. A negative answer means the current flows the other way.
> - **AC**: waveforms are written as **cosines**; phasor magnitudes are **rms**: $v = \sqrt2V\cos(\omega t + \theta)\leftrightarrow\mathbf V = V\angle\theta$.
> - **Machines**: $K_T = K_E$ in SI units (N m/A = V s/rad). ω is in rad/s; convert rpm × 2π/60.

## Part A: Fundamentals and DC circuits

### Electrostatics and current ([[FEEG1004 A1 - Electrostatics, Potential and Current]])
$$
F = \frac{1}{4\pi\varepsilon_0}\frac{q_1q_2}{r^2},\quad \mathbf E = \frac{\mathbf F}{q},\quad V = \frac{W}{q},\quad E_x = -\frac{dV}{dx}\ (V = EL\ \text{uniform}),\quad I = \frac{dQ}{dt} = neAv_d,\quad P = VI
$$
$\varepsilon_0 = 8.85\times10^{-12}$ F/m, $e = 1.602\times10^{-19}$ C.

### Magnetism ([[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]])
$$
\Phi = \int\mathbf B\cdot d\mathbf A = BA\cos\theta,\qquad \mathcal E = -N\frac{d\Phi}{dt},\qquad \mathbf F = q(\mathbf E + \mathbf v\times\mathbf B),\qquad F = BIL
$$

### Circuit laws ([[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]])
$$
V = IR,\quad R = \frac{\rho L}{A},\quad P = I^2R = \frac{V^2}{R},\quad \sum I_{node} = 0,\quad \sum V_{loop} = 0
$$
$$
R_s = \sum R_k,\quad \frac{1}{R_p} = \sum\frac{1}{R_k},\quad V_{out} = V_{in}\frac{R_1}{R_1 + R_2}\ (\text{unloaded}),\quad I_1 = I\frac{R_2}{R_1 + R_2}
$$

### Capacitors, inductors, transients ([[FEEG1004 A4 - Capacitors]], [[FEEG1004 A5 - Inductors and Electrical Resonance]])
| | Capacitor | Inductor |
|---|---|---|
| definition | $Q = CV$, $C = \varepsilon A/d$ | $N\Phi = LI$, $L = N^2/\mathcal R$ |
| V–I law | $i = C\,dv/dt$ | $v = L\,di/dt$ |
| energy | $\tfrac{1}{2}CV^2$ | $\tfrac{1}{2}LI^2$ |
| continuous quantity | voltage | current |
| DC steady state | open circuit | short circuit |
| time constant | $RC$ | $L/R$ |

$$
x(t) = x_\infty + (x_0 - x_\infty)e^{-t/\tau},\qquad \omega_0 = \frac{1}{\sqrt{LC}}
$$

### Network theorems ([[FEEG1004 A6 - Mesh Analysis]], [[FEEG1004 A7 - Thevenin, Superposition and Relays]])
- **Mesh**: $\mathbf{RI} = \mathbf V$, with $R_{kk}$ = the resistance around mesh $k$ and $R_{jk}$ = −(shared resistance). Branch currents are differences of loop currents.
- **Thévenin**: $V_{TH}$ = open-circuit voltage; $R_{TH}$ = resistance with sources zeroed (V source → short, I source → open). **Norton**: $I_N = V_{TH}/R_{TH}$.
- **Superposition** (linear circuits only): sum the one-source-at-a-time responses.
- **Maximum power**: $R_L = R_{TH}$, $P_{max} = V_{TH}^2/4R_{TH}$.

## Part B: Electronics

### Diodes ([[FEEG1004 B1 - Semiconductors and Diodes]], [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]])
- Si forward drop ≈ 0.7 V (Ge 0.3 V). A bridge loses 2 × 0.7 V.
$$
\Delta V_{ripple} = \frac{I}{2fC}\ \text{(full-wave)},\quad \frac{I}{fC}\ \text{(half-wave)},\qquad V_{avg} = V_p - \frac{\Delta V}{2},\qquad R_S = \frac{V_{in} - V_Z}{I_L + I_Z}
$$
- Half-wave average over a full cycle: $V_p/\pi$. Conduction angle for a 0.7 V diode: $180° - 2\arcsin(0.7/V_p)$.

### Transistors ([[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]])
$$
\text{BJT: } V_{BE} = 0.7\ \mathrm V,\ I_C = \beta I_B\ \text{(active)},\ V_{CE(sat)}\approx0.2\ \mathrm V;\qquad R_B = \frac{V_{drive} - 0.7}{I_C/\beta},\qquad \text{MOSFET: } P = I^2R_{DS(on)}
$$

### Op-amps ([[FEEG1004 B4 - Operational Amplifiers]])
- **Open loop**: $V_{out} = A_{OL}(V_+ - V_-)$, saturating at ≈ $V_{CC} - 1$ V. **Golden rules** (negative feedback only): $V_+ = V_-$ and no input current.

| Circuit | $V_{out}$ |
|---|---|
| follower | $V_{in}$ |
| inverting | $-(R_F/R_1)V_{in}$ |
| non-inverting | $(1 + R_1/R_2)V_{in}$ |
| summing | $-R_F\sum V_k/R_k$ |
| differential | $(R_2/R_1)(V_2 - V_1)$ |
| integrator | $-\frac{1}{RC}\int V_{in}\,dt$ |
| differentiator | $-RC\,dV_{in}/dt$ |
| general AC | $-(Z_f/Z_{in})V_{in}$ |

- T-network: $-\dfrac{R_2}{R_1}\left(1 + \dfrac{R_4}{R_2} + \dfrac{R_4}{R_3}\right)$. Gain × bandwidth ≈ constant (741: 1 MHz).

### Digital logic ([[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]], [[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]])
$$
\overline{A + B} = \overline A\,\overline B,\quad \overline{AB} = \overline A + \overline B,\quad A + BC = (A + B)(A + C),\quad A + AB = A,\quad A\oplus B = A\overline B + \overline AB
$$
- K-map axes 00, 01, 11, 10; groups of $2^n$; edges wrap.
- D flip-flop: $Q\leftarrow D$ on the clock edge. Toggle ($\overline Q\to D$) divides the frequency by 2.

## Part C: Electric machines

### Magnetic circuits and EMF ([[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]], [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]])
$$
\mathcal F = Ni = \sum H_kl_k = \mathcal R\Phi,\qquad \mathcal E = NBLu,\qquad F = BiL,\qquad \mathrm{rpm} = \frac{120f}{N_p},\qquad E_{peak} = NB(2L_{rotor})\frac{\omega D}{2}
$$
- Balanced three-phase: $i_N = 0$ and $p = 3V_{ph}I_{ph}\cos\phi$ = constant.

### Transformers ([[FEEG1004 C3 - Transformers and AC Power Transmission]])
$$
\frac{V_1}{V_2} = \frac{N_1}{N_2} = \frac{I_2}{I_1},\qquad E_{rms} = 4.44fN\Phi_m,\qquad B_m = \Phi_m/A\ (\lesssim1.5\ \mathrm T),\qquad \eta = P_2/P_1
$$

### DC machines ([[FEEG1004 C4 - DC Generators and the Commutator]], [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]], [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]])
$$
E = K_E\omega,\quad T = K_Ti,\quad K_E = K_T = \frac{ZN_p\Phi}{2\pi a},\quad \text{motor } V = E + iR_a,\quad \text{generator } V = E - iR_a
$$
$$
\omega = \frac{V}{K} - \frac{R_a}{K^2}T,\qquad P_{in} = Vi,\ P_{em} = Ei = T\omega,\ P_{out} = P_{em} - P_{rot},\qquad T = 2BAV_R,\ A = \frac{Zi_c}{\pi D}
$$
- Chopper: $V_{avg} = \delta V_S$. A series motor has $T\propto i^2$. Fan loads: $T\propto\omega^2$, $P\propto\omega^3$.

## Part D: AC circuits

### Phasors and impedance ([[FEEG1004 D1 - AC Waveforms, RMS and Phasors]], [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]])
$$
V_{rms} = \frac{V_p}{\sqrt2},\quad \omega = 2\pi f,\quad \mathbf V = V\angle\theta = Ve^{j\theta},\quad Z_R = R,\ Z_L = j\omega L,\ Z_C = \frac{1}{j\omega C} = -\frac{j}{\omega C},\quad \mathbf V = Z\mathbf I
$$
- **CIVIL**: capacitor I leads V; inductor V leads I. $\Im Z > 0$ is inductive (lagging).
- Add and subtract in Cartesian form; multiply and divide in polar form (add or subtract angles). Check the quadrant of $\tan^{-1}$.

### Filters ([[FEEG1004 D3 - AC Filters and Bode Plots]])
$$
H_{LP} = \frac{1}{1 + j\omega RC},\quad H_{HP} = \frac{j\omega RC}{1 + j\omega RC},\quad \omega_c = \frac{1}{RC}\ \left(\frac{R}{L}\ \text{for RL}\right),\quad |H(\omega_c)| = \frac{1}{\sqrt2}\ (-3\ \mathrm{dB})
$$
$$
G_{dB} = 20\log_{10}\frac{V_{out}}{V_{in}} = 10\log_{10}\frac{P_{out}}{P_{in}},\qquad \text{first-order roll-off } \pm20\ \mathrm{dB/decade}
$$

### Power ([[FEEG1004 D4 - AC Power and Power Factor]])
$$
\mathbf S = \mathbf V\mathbf I^* = P + jQ,\quad P = VI\cos\phi = I^2R,\quad Q = VI\sin\phi = I^2X,\quad |\mathbf S| = VI,\quad \mathrm{pf} = \cos\phi = P/|S|
$$
- $Q_L > 0$ (absorbs) and $Q_C = -V^2\omega C < 0$ (generates). Power-factor correction adds parallel C; P is unchanged.

## Part E: Transducers

### Measurement and temperature ([[FEEG1004 E1 - Measurement Systems and Temperature Sensors]])
- Sensitivity $= \Delta A_{out}/\Delta A_{in}$. $n$-bit ADC resolution $= V_{FS}/2^n$.
- RTD: $R = R_0(1 + \alpha_1T + \alpha_2T^2)$. Thermocouple: $V\approx S(T_{hot} - T_{ref})$.

### Displacement ([[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]])
$$
R = \frac{\rho L}{A},\quad C = \frac{\varepsilon_0\varepsilon_rA}{d},\quad L = \frac{N^2}{S},\ S = \frac{l}{\mu_0\mu_rA},\quad \frac{V_{out}}{V_{in}} = \frac{x}{1 + (R_p/R_L)x(1 - x)},\quad V_{out} = -\frac{C_s}{C_u}V_{in}\propto d
$$
- LVDT: $V_{out} = V_a - V_b\propto$ displacement; the phase flips through the null.

### Strain, pressure, flow ([[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]])
$$
G = \frac{\Delta R/R}{\varepsilon} = \frac{\Delta\rho/\rho}{\varepsilon} + 1 + 2\nu,\qquad V_{bridge} = \frac{NEG\varepsilon}{4},\qquad p_0 - p = \tfrac{1}{2}\rho U^2,\qquad p_a - p_b = \tfrac{1}{2}\rho(v_b^2 - v_a^2)
$$
- $G$ ≈ 2 for foil and 100–120 for semiconductor gauges.
