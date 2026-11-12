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

Everything on one page, in the order of the topic notes. Each section links to the note that derives its results.

> [!warning] Conventions used in FEEG1004
> - Passive sign convention: current enters the terminal marked + for the component voltage, so $p = vi$ is power absorbed. The voltage arrow points to the + terminal.
> - KVL: crossing a component from − to + is a rise; a resistor crossed in its reference-current direction contributes $-IR$. A negative answer means the current flows the other way. Mesh currents are clockwise.
> - AC: waveforms are written as cosines and phasor magnitudes are rms, $v = \sqrt2\,V\cos(\omega t + \theta)\leftrightarrow\mathbf V = V\angle\theta$. The phase angle is $\phi = \theta_v - \theta_i$.
> - Complex power is $\mathbf S = \mathbf V\mathbf I^*$, so $Q > 0$ for an inductive (lagging) load and $Q < 0$ for a capacitive (leading) one.
> - Machines: $N_p$ is the total number of poles (not pole pairs), so $\text{rpm} = 120f/N_p$. $\omega$ is the mechanical speed in rad/s, $\omega = 2\pi\,\text{rpm}/60$, and $K_T = K_E$ in SI units (N m/A = V s/rad).
>
> Constants: $e = 1.602\times10^{-19}$ C, $\varepsilon_0 = 8.85\times10^{-12}$ F/m, $\mu_0 = 4\pi\times10^{-7}$ H/m.

## Part A: Fundamentals and DC circuits

### Electrostatics and current ([[FEEG1004 A1 - Electrostatics, Potential and Current]])

$$
Q = Ne,\qquad |F| = \frac{1}{4\pi\varepsilon_0}\frac{|q_1q_2|}{r^2}\ \ \text{(point charges in free space)},\qquad \mathbf E = \frac{\mathbf F}{q_t},\qquad |E| = \frac{1}{4\pi\varepsilon_0}\frac{|q|}{r^2},\qquad \mathbf E_{\text{total}} = \sum_k\mathbf E_k
$$

$$
\Delta U_e = q\,\Delta V,\qquad E_x = -\frac{dV}{dx},\qquad |\Delta V| = EL\ \ \text{(uniform field, plate gap } L),\qquad K_f - K_i = q(V_i - V_f)\ \ \text{(no losses)}
$$

$$
i = \frac{dQ}{dt},\qquad \Delta Q = I\,\Delta t\ \ \text{(steady current)},\qquad v_d = \frac{I}{e\rho_eA}\ \ (\rho_e = \text{free electrons per unit volume}),\qquad p = vi
$$

- Conventional current flows opposite to electron motion. Use the radius, not the diameter, in $A = \pi r^2$.

### Magnetism ([[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]])

$$
\Phi = \int_A\mathbf B\cdot d\mathbf A = BA\cos\theta\ \ (\text{uniform }B,\ \theta\text{ from the coil normal}),\qquad 1\ \text{Wb} = 1\ \text{T m}^2 = 1\ \text{V s}
$$

$$
\mathcal E = -\frac{d(N\Phi)}{dt} = -N\frac{d\Phi}{dt}\ \ \text{(same flux through every turn)},\qquad \mathcal E(t) = NBA\omega\sin\omega t\ \ \text{(coil rotating in uniform } B)
$$

$$
\mathbf F = q(\mathbf E + \mathbf v\times\mathbf B),\qquad |\mathbf F_B| = |q|vB\sin\alpha,\qquad P_B = \mathbf F_B\cdot\mathbf v = 0,\qquad F = BIL\ \ \text{(straight wire} \perp \text{uniform } B)
$$

- Lenz's law sets the sign: the induced current opposes the change of flux. Fleming's left-hand rule gives the force direction.

### Circuit laws ([[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]])

$$
V = IR,\qquad R = \frac{\rho L}{A},\qquad P = VI = I^2R = \frac{V^2}{R},\qquad \sum I_{\text{in}} = \sum I_{\text{out}},\qquad \sum_{\text{loop}} V = 0
$$

$$
R_s = R_1 + R_2 + \dots,\qquad \frac{1}{R_p} = \frac{1}{R_1} + \frac{1}{R_2} + \dots,\qquad R_1\parallel R_2 = \frac{R_1R_2}{R_1 + R_2}
$$

$$
V_{out} = V_{in}\frac{R_1}{R_1 + R_2}\ \ (\text{unloaded, output across } R_1),\qquad V_{out} = V_{in}\frac{R_b}{R_2 + R_b},\ R_b = R_1\parallel R_L\ \ \text{(loaded)},\qquad I_1 = I\frac{R_2}{R_1 + R_2}
$$

- In the current divider the opposite branch's resistance goes on top.

### Capacitors ([[FEEG1004 A4 - Capacitors]])

$$
Q = CV_C,\qquad C = \frac{\varepsilon A}{d},\qquad i = C\frac{dv_C}{dt},\qquad v_C(t) = v_C(0) + \frac1C\int_0^t i\,dt',\qquad v_C(0^+) = v_C(0^-)\ \ \text{(finite current)}
$$

$$
E_C = \tfrac12CV_C^2 = \frac{Q^2}{2C},\qquad v_C(t) = V_s\left(1 - e^{-t/RC}\right),\quad i(t) = \frac{V_s}{R}e^{-t/RC}\ \ \text{(series RC from uncharged)}
$$

$$
v_C(t) = V_s + (V_0 - V_s)e^{-t/RC}\ \ (\text{initial } V_0),\qquad v_C(\tau) = 0.632V_s,\qquad v_C(t) = V_0 + \frac{I_0t}{C}\ \ \text{(constant current } I_0)
$$

### Inductors and resonance ([[FEEG1004 A5 - Inductors and Electrical Resonance]])

$$
N\Phi = Li,\qquad v_L = L\frac{di}{dt},\qquad i(t) = i(0) + \frac1L\int_0^t v_L\,dt',\qquad i(0^+) = i(0^-)\ \ \text{(finite voltage)},\qquad E_L = \tfrac12LI^2
$$

$$
i(t) = \frac{V_s}{R}\left(1 - e^{-Rt/L}\right),\quad v_L(t) = V_se^{-t/\tau},\quad \tau = \frac LR\ \ \text{(series RL switch-on from } i = 0)
$$

$$
\omega_0 = \frac{1}{\sqrt{LC}},\qquad f_0 = \frac{1}{2\pi\sqrt{LC}},\qquad \tfrac12CV_{pk}^2 = \tfrac12LI_{pk}^2\ \ \text{(lossless LC)}
$$

| | Capacitor | Inductor |
|---|---|---|
| V–I law | $i = C\,dv/dt$ | $v = L\,di/dt$ |
| energy | $\tfrac12CV^2$ | $\tfrac12LI^2$ |
| continuous quantity | voltage | current |
| DC steady state | open circuit | short circuit |
| time constant | $RC$ | $L/R$ |

General first-order switching response: $x(t) = x_\infty + (x_0 - x_\infty)e^{-t/\tau}$.

### Mesh analysis ([[FEEG1004 A6 - Mesh Analysis]])

$$
\mathbf R\mathbf I = \mathbf V,\qquad R_{kk} = \text{total resistance round mesh } k,\qquad R_{jk} = -(\text{resistance shared by meshes } j, k),\qquad V_k = \text{source rises round mesh } k
$$

- Planar circuit, resistors and independent voltage sources only. A shared resistor carries $I_j - I_k$; branch currents are sums and differences of mesh currents.

### Thévenin, superposition and relays ([[FEEG1004 A7 - Thevenin, Superposition and Relays]])

$$
V_{out} = V_{TH} - I_{out}R_{TH},\qquad I_L = \frac{V_{TH}}{R_{TH} + R_L},\qquad I_{short} = I_N = \frac{V_{TH}}{R_{TH}},\qquad R_{ESR} = \frac{V_b - V_{out}}{I_{out}}
$$

- $V_{TH}$ is the open-circuit voltage with all sources on. $R_{TH}$ is found with independent sources zeroed: voltage source → short, current source → open.
- Superposition (linear circuits, independent sources): add the signed voltages or currents from each source acting alone, never the powers.
- Relay flyback (coil $L$, $R$, diode drop $V_D$): $L\,di/dt = -Ri - V_D$, so $dE_L/dt = -Ri^2 - V_Di$ until the stored energy is gone.

## Part B: Electronics

### Semiconductors and diodes ([[FEEG1004 B1 - Semiconductors and Diodes]])

- Band gap: Si 1.1 eV. Group V donors make n-type, Group III acceptors make p-type. At equilibrium the diffusion and drift currents across the junction are equal.
- Diode models: ON is a source $V_{on}$ (0 V ideal, 0.7 V Si, 0.3 V Ge, 2.1 V for the indicator LED) with $I_D > 0$; OFF is an open circuit with $V_D < V_{on}$. Assume, solve, then check both conditions.

$$
I_D = \frac{V_S - V_{on}}{R}\ \ (V_S > V_{on}),\qquad \Delta\theta = 180^\circ - 2\arcsin\frac{V_{on}}{V_p}\ \ \text{(conduction angle, half-wave)}
$$

### Diode circuits ([[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]])

$$
V_{p,out} = V_{p,in} - 0.7\ \text{V (half-wave)},\qquad V_{p,out} = V_{p,in} - 1.4\ \text{V (four-diode bridge)}
$$

$$
\Delta V = \frac{i_{DC}}{fC}\ \text{(half-wave)},\qquad \Delta V = \frac{i_{DC}}{2fC}\ \text{(full-wave)},\qquad V_{average} = V_p - \frac{\Delta V}{2}\quad (\Delta V \ll V_p)
$$

$$
R_S = \frac{V_{in} - V_Z}{I_{load} + I_Z},\qquad I_Z = \frac{V_{in} - V_Z}{R_S} - I_{load},\qquad I_{load,max} = \frac{V_{in} - V_Z}{R_S} - I_{Z,min}\ \ \text{(Zener shunt regulator)}
$$

- Zener power is largest at zero load, $I_{Z,max} = (V_{in} - V_Z)/R_S$.
- Shunt limiter with two antiparallel Si diodes: $-0.7\ \text{V} \le v_{out} \le +0.7\ \text{V}$; with a bias source $V_x$ the clip level is $V_x + 0.7$ V.
- Clamp (series C, shunt Si diode, unloaded): $V_C = V_p - 0.7$ V, $v_{out}(t) = v_{in}(t) + (V_p - 0.7\ \text{V})$; the peak-to-peak swing is unchanged.
- Half-wave rectified sine: average $= I_p/\pi$ (or $V_p/\pi$) over a full cycle.

### Transistors ([[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]])

$$
I_E = I_B + I_C,\qquad I_C = \beta I_B\ \text{(active only)},\qquad V_{CE} = (V_{CC} - V_F) - I_CR_L,\qquad I_B = \frac{V_{in} - 0.7\ \text{V}}{R_B}
$$

$$
I_{C(sat)} = \frac{V_{CC} - V_F - V_{CE(sat)}}{R_L},\qquad R_{B,max} = \frac{\beta(V_{in} - 0.7\ \text{V})}{I_{C(sat)}}\ \ (\text{choose } R_B \text{ below this for overdrive})
$$

- npn BJT: $V_{BE} = 0.7$ V when conducting, $\beta \approx 100$–$200$, $V_{CE(sat)} \approx 0.2$ V. Saturated if $\beta I_B \ge I_{C(sat)}$, then $I_C = I_{C(sat)} < \beta I_B$. $V_F$ is any series load drop (LED).
- Common emitter: $V_{out} = V_{CC} - \beta R_CI_B$; bias for $I_CR_C \approx \tfrac12V_{CC}$; the AC output $v_c = -\beta R_Ci_b$ is inverted.
- Enhancement n-MOSFET: $I_G = 0$, so $V_{GS} = V_{supply}R_2/(R_1 + R_2)$ from an unloaded divider; OFF below $V_{GS(th)}$; ON as $R_{DS(on)}$.

$$
P_{MOSFET} = I_D^2R_{DS(on)},\qquad I_{D,max} = \sqrt{\frac{P_{max}}{R_{DS(on)}}}
$$

### Op-amps ([[FEEG1004 B4 - Operational Amplifiers]])

- Open loop: $V_{out} = A_{OL}(V_+ - V_-)$, $A_{OL} \approx 2\times10^5$ (741), saturating at $\pm V_{max} \approx \pm(V_{CC} - 1\ \text{V})$. Comparator (no negative feedback): $+V_{max}$ if $V_+ > V_-$, $-V_{max}$ if $V_+ < V_-$.
- Golden rules, valid only with negative feedback to $V_-$ and an unsaturated output: $V_+ = V_-$ and $I_+ = I_- = 0$.

| Circuit | $V_{out}$ |
|---|---|
| inverting ($R_1$ in, $R_F$ feedback) | $-(R_F/R_1)V_{in}$ |
| non-inverting ($R_1$ feedback, $R_2$ to ground) | $(1 + R_1/R_2)V_{in}$ |
| follower | $V_{in}$ |
| summing | $-(R_F/R_1\,V_1 + R_F/R_2\,V_2 + R_F/R_3\,V_3)$ |
| differential ($V_1$ to the inverting side) | $(R_2/R_1)(V_2 - V_1)$ |
| T-network feedback | $-\dfrac{R_2}{R_1}\left(1 + \dfrac{R_4}{R_2} + \dfrac{R_4}{R_3}\right)V_{in}$ |
| integrator | $-\dfrac{1}{RC}\displaystyle\int V_{in}\,dt$ |
| differentiator | $-RC\,dV_{in}/dt$ |
| general AC inverting | $-(Z_f/Z_{in})V_{in}$ |

- Binary-weighted summing amplifier as a 4-bit DAC: $R_F/R_i$ in the ratio 8 : 4 : 2 : 1.
- Practical limits: $\text{SR} = |dV_{out}/dt|_{max}$, so a step $\Delta V$ needs $\Delta t \ge \Delta V/\text{SR}$; $\text{GBP} = |A_{CL}|f_{max} = f_{unity}$ (741: 1 MHz).

### Combinational logic ([[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]])

$$
\overline{A + B} = \overline A\cdot\overline B,\qquad \overline{A\cdot B} = \overline A + \overline B,\qquad A\oplus B = A\overline B + \overline AB
$$

| Law | OR form | AND form |
|---|---|---|
| dominance | $A + 1 = 1$ | $A\cdot0 = 0$ |
| identity | $A + 0 = A$ | $A\cdot1 = A$ |
| idempotence | $A + A = A$ | $A\cdot A = A$ |
| complement | $A + \overline A = 1$ | $A\cdot\overline A = 0$ |
| distributivity | $A + BC = (A + B)(A + C)$ | $A(B + C) = AB + AC$ |
| absorption | $A + AB = A$ | $A(A + B) = A$ |

- A truth table has $2^n$ rows. SOP: OR together one minterm per row with $F = 1$ (variable plain if 1, barred if 0).
- K-map: Gray-coded axes 00, 01, 11, 10; rectangular groups of $2^k$ cells, as large and as few as possible; edges wrap; no diagonals.
- NAND-only: double-invert the SOP and apply De Morgan; a NAND with tied inputs is an inverter. 5 V TTL: logic 1 > 2.0 V, logic 0 < 0.8 V.

### Sequential logic ([[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]])

$$
Q^{(k+1)} = D^{(k)}\ \ \text{(D flip-flop, on the active edge)},\qquad f_Q = \frac{f_{clock}}{2}\ \ (\overline Q \to D),\qquad f_m = \frac{f_{clock}}{2^m},\qquad N \text{ stages} \to 2^N \text{ states}
$$

- Synchronous stages all use their pre-edge inputs. A ripple counter reads as $DCBA_2$ with the slowest stage as the most significant bit. An $N$-bit shift register loads in $N$ clock periods.

## Part C: Electric machines

### Magnetic circuits and EMF ([[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]])

$$
\mathcal F = Ni = \oint H\,dl = \sum_k H_kl_k = \Phi\mathcal R,\qquad B = \frac{\Phi}{A} = \mu_0\mu_rH,\qquad \mathcal R = \frac{l}{\mu_0\mu_rA}\ \ \text{(linear iron, no fringing)}
$$

$$
\mathcal R_{tot} = \mathcal R_c + \mathcal R_g,\quad \mathcal R_g = \frac{l_g}{\mu_0A},\quad \frac{\mathcal R_g}{\mathcal R_c} = \mu_r\frac{l_g}{l_c},\qquad L = \frac{N\Phi}{i} = \frac{N^2}{\mathcal R} = \frac{\mu_0\mu_rN^2A}{l}
$$

$$
E = NBLu\ \ (B, L, u \text{ mutually} \perp;\ \times\sin\theta \text{ otherwise}),\qquad F = BiL\ (NBiL \text{ for } N \text{ conductors}),\qquad Ei = Fu
$$

- $L$ is the active length inside the field only. Right-hand rule for the generator EMF, left-hand rule for the motor force.

### Synchronous generators and three-phase ([[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]])

$$
f = \frac{N_p\,\text{rpm}}{120},\qquad \omega_e = \frac{N_p}{2}\,\omega,\qquad e = E_m\sin\omega_et,\ E_m = N\omega_e\Phi_m\ \ \text{(single coil, } \omega_e = 2\pi f)
$$

$$
u = \frac{\omega D}{2},\qquad E_{peak} = NB_{peak}(2L_{rotor})u = NB_{peak}L_{rotor}\omega D,\qquad E_{rms} = \frac{E_{peak}}{\sqrt2}\ \ \text{(fully pitched coils, sinusoidal flux)}
$$

$$
e_A + e_B + e_C = 0,\qquad \text{star: } V_L = \sqrt3\,V_{ph},\ I_L = I_{ph},\qquad \text{delta: } V_L = V_{ph},\ I_L = \sqrt3\,I_{ph}
$$

$$
P = 3V_{ph}I_{ph}\cos\phi = \sqrt3\,V_LI_L\cos\phi,\qquad i_N = 0 \text{ and } p(t) = \text{constant (balanced load)}
$$

### Transformers ([[FEEG1004 C3 - Transformers and AC Power Transmission]])

$$
\frac{V_2}{V_1} = \frac{N_2}{N_1} = \frac{I_1}{I_2},\qquad Z_L' = \left(\frac{N_1}{N_2}\right)^2Z_L,\qquad \eta = \frac{P_2}{P_1}\ \ \text{(ideal: lossless, no leakage, rms values)}
$$

$$
E_{rms} = \frac{2\pi}{\sqrt2}fN\Phi_m = 4.44fN\Phi_m,\qquad B_m = \frac{V_1}{4.44fN_1A} \lesssim 1.5\ \text{T}\ \ (A \text{ in m}^2)
$$

$$
P_{loss} = I^2R_{line} = \frac{P^2R_{line}}{V^2}\ \ \text{(unity power factor)}
$$

### DC generators ([[FEEG1004 C4 - DC Generators and the Commutator]])

$$
E = K_E\omega,\qquad K_E = \frac{Z}{a}BL\frac D2 = \frac{ZN_p\Phi}{2\pi a}\ \ \text{[V s/rad]},\qquad \Phi = \frac{\pi BLD}{N_p}\ \ \text{(flux per pole)},\qquad K_E = \frac{V_{oc}}{\omega}
$$

$$
V = E - iR_a - L_a\frac{di}{dt}\ \to\ V = K_E\omega - iR_a\ \ \text{(steady state)},\qquad T_{em} = K_Ti\ \text{(counter-torque)}
$$

- $Z$ conductors in $a$ parallel paths. A single coil gives $|E_m\sin\omega t|$; with $n$ coils the ripple is $1 - \cos(\pi/2n)$.

### DC motors ([[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]])

$$
i_c = \frac ia,\qquad T = K_Ti,\qquad E' = K_E\omega,\qquad K_T = K_E = \frac{Z}{a}BL\frac D2 = \frac{ZN_p\Phi}{2\pi a}
$$

$$
V = E' + iR_a\ \ \text{(steady state)},\qquad P_{in} = Vi,\quad P_{cu} = i^2R_a,\quad P_{em} = E'i = T_{em}\omega,\quad P_{out} = P_{em} - P_{rot},\quad \eta = \frac{P_{out}}{P_{in}}
$$

$$
A = \frac{Zi_c}{\pi D},\qquad V_R = \frac{\pi D^2L}{4},\qquad T = 2BAV_R,\qquad V_R = \frac{P}{2BA\omega} \propto \frac{P}{\omega}
$$

- Shaft torque $T_{shaft} = P_{out}/\omega$, less than $T_{em}$ by the rotational losses (friction, windage, core).

### DC motor characteristics and speed control ([[FEEG1004 C6 - DC Motor Characteristics and Speed Control]])

$$
\omega = \frac VK - \frac{R_a}{K^2}T,\qquad \omega_0 = \frac VK,\qquad T_{stall} = \frac{KV}{R_a},\qquad \omega = \frac{V - i(R_a + R)}{K(\Phi)}\ \ \text{(series } R,\ \text{field weakening)}
$$

$$
\text{series motor: } K = k_si,\quad T = k_si^2,\quad \omega = \frac{V}{\sqrt{k_sT}} - \frac{R_a + R_f}{k_s}\ \ \text{(runaway at no load)}
$$

$$
\omega_m = G\omega_L,\quad T_m = \frac{T_L}{G},\quad V_R = \frac{T_L}{2GBA}\ \ \text{(ideal gearbox)},\qquad T_L = T_0\ \text{(constant)},\quad T_L = k\omega^2,\ P_L = k\omega^3\ \text{(fan)}
$$

$$
\delta = \frac{t_{on}}{T_{sw}},\qquad V_{avg} = \delta V_S\ \text{(ideal switch)},\qquad V_{avg} = \delta(V_S - V_{sw})\ \text{(switch drop)},\qquad V_{avg} = \delta(V_S - V_{sw}) - (1 - \delta)V_D\ \text{(and diode drop)}
$$

- Fan on a chopper: $(R_ak/K)\omega^2 + K\omega - V_{avg} = 0$; take the positive root. Direction is reversed with an H-bridge.

## Part D: AC circuits

### Phasors and RMS ([[FEEG1004 D1 - AC Waveforms, RMS and Phasors]])

$$
v(t) = V_p\cos(\omega t + \theta) = \sqrt2\,V\cos(\omega t + \theta),\qquad V = \frac{V_p}{\sqrt2}\ \ \text{(sinusoid only)},\qquad \omega = 2\pi f = \frac{2\pi}{T}
$$

$$
\sin(\omega t + \phi) = \cos(\omega t + \phi - 90^\circ),\qquad -\cos(\omega t + \phi) = \cos(\omega t + \phi \pm 180^\circ),\qquad \cos^2\theta = \frac{1 + \cos2\theta}{2}
$$

$$
e^{j\theta} = \cos\theta + j\sin\theta,\qquad \mathbf V = Ve^{j\theta} = V\angle\theta,\qquad v(t) = \Re\{\sqrt2\,\mathbf Ve^{j\omega t}\}
$$

$$
r = \sqrt{x^2 + y^2},\quad \theta = \arctan\frac yx\ (\pm180^\circ \text{ if } x < 0),\qquad z_1z_2 = r_1r_2\angle(\theta_1 + \theta_2),\quad \frac{z_1}{z_2} = \frac{r_1}{r_2}\angle(\theta_1 - \theta_2),\quad zz^* = |z|^2
$$

- Add and subtract in Cartesian form; multiply and divide in polar form.

### Impedance ([[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]])

$$
\mathbf V = Z\mathbf I,\qquad Z_R = R,\qquad Z_L = j\omega L = jX_L,\ X_L = \omega L,\qquad Z_C = \frac{1}{j\omega C} = -jX_C,\ X_C = \frac{1}{\omega C}
$$

$$
Z = R + j\left(\omega L - \frac{1}{\omega C}\right)\ \text{(series RLC)},\qquad |Z| = \sqrt{R^2 + X^2},\quad \theta_Z = \arctan\frac XR,\qquad \omega_0 = \frac{1}{\sqrt{LC}}
$$

$$
Z_1\parallel Z_2 = \frac{Z_1Z_2}{Z_1 + Z_2},\qquad \mathbf V_2 = \frac{Z_2}{Z_1 + Z_2}\mathbf V_{in},\qquad \mathbf I_1 = \frac{Z_2}{Z_1 + Z_2}\mathbf I_{in}
$$

- CIVIL: in a capacitor I leads V; in an inductor V leads I. $X > 0$ is inductive (current lags), $X < 0$ capacitive (current leads). Add phasors, not rms magnitudes.

### Filters ([[FEEG1004 D3 - AC Filters and Bode Plots]])

$$
H_{LP} = \frac{1}{1 + j\omega RC},\quad |H| = \frac{1}{\sqrt{1 + (\omega RC)^2}},\quad \phi = -\arctan\omega RC;\qquad H_{HP} = \frac{j\omega RC}{1 + j\omega RC},\quad \phi = 90^\circ - \arctan\omega RC
$$

$$
\omega_c = \frac{1}{RC}\ \ \left(\frac RL \text{ for RL}\right),\qquad f_c = \frac{\omega_c}{2\pi},\qquad |H(\omega_c)| = \frac{H_{max}}{\sqrt2}\ (-3.01\ \text{dB}),\quad \phi(\omega_c) = \mp45^\circ
$$

$$
G_{dB} = 20\log_{10}\frac{V_{out}}{V_{in}} = 10\log_{10}\frac{P_{out}}{P_{in}},\qquad |H| = 10^{G_{dB}/20},\qquad G_{dB,total} = G_{dB,1} + G_{dB,2}\ \ \text{(cascade)}
$$

$$
\text{loaded RC low-pass: } H = \frac{K}{1 + j\omega R_{TH}C},\quad K = \frac{R_L}{R_1 + R_L},\quad R_{TH} = R_1\parallel R_L;\qquad \text{active: } H = -\frac{R_2/R_1}{1 + j\omega R_2C}
$$

- RL: series L, shunt R is low-pass; series R, shunt L is high-pass. First-order Bode asymptotes have slopes 0 and ±20 dB/decade, meeting at $\omega_c$.

### Power ([[FEEG1004 D4 - AC Power and Power Factor]])

$$
P = VI\cos\phi = I^2R,\qquad Q = VI\sin\phi = I^2X,\qquad \mathbf S = \mathbf V\mathbf I^* = I^2Z = P + jQ,\qquad S = VI = \sqrt{P^2 + Q^2}
$$

$$
Q_L = +I^2X_L = +\frac{V^2}{\omega L},\qquad Q_C = -I^2X_C = -\omega CV^2,\qquad \text{PF} = \cos\phi = \frac PS = \frac{R}{|Z|},\qquad \mathbf S_{supply} = \sum_k\mathbf S_k
$$

$$
I = \frac{P}{V_L\,\text{PF}},\qquad P_{loss} = \frac{P^2R_{line}}{V_L^2\,\text{PF}^2},\qquad \text{regulation} = \frac{|\mathbf V_s| - |\mathbf V_L|}{|\mathbf V_s|},\quad \mathbf V_s = \mathbf V_L + \mathbf IZ_{line}
$$

$$
C = \frac{P(\tan\phi_1 - \tan\phi_2)}{2\pi fV^2}\ \ \text{(shunt correction, } P \text{ unchanged)},\qquad C_{unity} = \frac{P\tan\phi_1}{2\pi fV^2}
$$

- PF is lagging when $Q > 0$, leading when $Q < 0$. Use $P = V^2/R$ only with the voltage across $R$ itself.

## Part E: Transducers

### Measurement and temperature ([[FEEG1004 E1 - Measurement Systems and Temperature Sensors]])

$$
S = \frac{dA_{out}}{dA_{in}},\qquad \Delta V_{res} = \frac{V_{FS}}{2^n},\qquad f_s > 2f_{max},\qquad f_{alias} = |f_{sig} - kf_s| \le \frac{f_s}{2}
$$

$$
\text{RTD: } R = R_0(1 + \alpha_1T + \alpha_2T^2 + \dots)\ (T \text{ in }^\circ\text{C}),\qquad \text{NTC: } R = R_0\exp\left[B\left(\frac1T - \frac{1}{T_0}\right)\right],\ \alpha = -\frac{B}{T^2}\ (T \text{ in K})
$$

$$
V_{meas} = S_{AB}(T_{hot} - T_{ref}),\qquad V_{CJC} = S_{AB}(T_{ref} - 0\,^\circ\text{C}),\qquad V_{out} = G(V_{meas} + V_{CJC}) = GS_{AB}T_{hot}
$$

- Pt100: about +0.39 %/°C. NTC thermistor: about −4 %/°C. Thermocouples give tens of µV/°C. Passive transducers need excitation; active ones generate their own signal. Resolution is not precision when the noise floor exceeds one LSB.

### Displacement ([[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]])

$$
\frac{V_{out}}{V_{in}} = \tilde x = \frac{x}{x_{max}}\ \text{(unloaded)},\qquad \frac{V_{out}}{V_{in}} = \frac{\tilde x}{1 + (R_p/R_L)\,\tilde x(1 - \tilde x)}\ \ (R_L \text{ across the lower } \tilde xR_p)
$$

$$
C = \frac{\varepsilon_0\varepsilon_rA}{x}\ \text{(gap)},\qquad C \propto x\ \text{(overlap)},\qquad C = C_{dry}\left[1 + (\varepsilon_r - 1)\frac xh\right]\ \text{(liquid level)}
$$

$$
\mathbf V_{out} = -\frac{Z_f}{Z_{in}}\mathbf V_{in} = -\frac{C_s}{C_u}\mathbf V_{in} = -\left(\frac{C_s}{\varepsilon_0\varepsilon_rA}\right)x\,\mathbf V_{in}\ \ (\text{gap sensor } C_u \text{ in the feedback path})
$$

$$
L = \frac{N^2}{S},\quad S = \frac{\ell}{\mu_0\mu_rA},\qquad \text{LVDT: } \mathbf V_{out} = \mathbf V_a - \mathbf V_b \propto x
$$

- An op-amp follower removes potentiometer loading. The LVDT phase reverses by 180° through the null, so phase-sensitive demodulation gives the direction.

### Strain, pressure, flow ([[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]])

$$
\varepsilon = \frac{\Delta\ell}{\ell},\qquad \frac{\Delta d}{d} = -\nu\varepsilon,\qquad \frac{\Delta R}{R} = \frac{\Delta\rho}{\rho} + (1 + 2\nu)\varepsilon = G\varepsilon,\qquad G = 1 + 2\nu + \frac{\Delta\rho/\rho}{\varepsilon}
$$

$$
V_{out} = E\left(\frac{R_4}{R_3 + R_4} - \frac{R_2}{R_1 + R_2}\right),\qquad \text{balance: } R_1R_4 = R_2R_3
$$

$$
V_{out} \approx \frac E4(\delta_1 - \delta_2 - \delta_3 + \delta_4),\quad \delta_k = \frac{\Delta R_k}{R}\ \ (G\varepsilon \ll 1),\qquad V_{out} = \frac{NEG\varepsilon}{4}\ \ (N \text{ active gauges})
$$

$$
V_{amp} = \frac{R_f}{R_{in}}(V_2 - V_1),\qquad \Delta p = \tfrac12\rho v_b^2\left[1 - \left(\frac{A_b}{A_a}\right)^2\right]\ \text{(Venturi)},\qquad U = \sqrt{\frac{2(p_{total} - p_{static})}{\rho}}\ \text{(Pitot-static)}
$$

- $G \approx 2$ for metal foil, 100–120 for semiconductor gauges. Adjacent arms subtract and opposite arms add, so a temperature change common to adjacent arms cancels.

| Layout | $N$ | $V_{out}$ | Temperature compensated |
|---|---|---|---|
| bending, half bridge (adjacent arms) | 2 | $EG\varepsilon_b/2$ | yes |
| bending, full bridge | 4 | $EG\varepsilon_b$ | yes |
| axial, two active gauges in opposite arms | 2 | $EG\varepsilon_a/2 + E\delta_T/2$ | no |
| axial, two active plus two dummy gauges | 2 | $EG\varepsilon_a/2$ | yes |
| shaft torque, four gauges at ±45° | 4 | $EG\varepsilon_t$ | yes |
- Bernoulli conditions: steady, incompressible, inviscid flow along a horizontal streamline.
