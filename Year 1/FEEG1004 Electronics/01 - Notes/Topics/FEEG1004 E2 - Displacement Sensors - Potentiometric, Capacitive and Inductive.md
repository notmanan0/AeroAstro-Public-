---
title: "FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive"
module: "FEEG1004 Electronics"
type: topic
stream: "Part E: Transducers and Measurement"
order: 2
tags: [feeg1004, transducers, displacement, potentiometer, capacitive-sensor, lvdt, linearisation, loading, demodulation]
aliases: ["Transducers 02", "Displacement sensors", "Potentiometer sensor", "Capacitive sensor", "LVDT"]
date: 2026-09-27
status: lectured
coverage: "FEEG1004 Lecture 2 - Wk26 FEEG1004 L2(2) Sensors and Transducers (ll. 1–540)"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites:
  - "[[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]"
  - "[[FEEG1004 B4 - Operational Amplifiers]]"
  - "[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"
next_topics: ["[[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]"]
key_concepts:
  - "[[Potentiometric Displacement Sensor]]"
  - "[[Capacitive Displacement Sensor]]"
  - "[[Linear Variable Differential Transformer]]"
  - "[[Loading Effect and Buffering]]"
tutorial_sheets: []
sources:
  - "02 - Sources/S2 Transducers/S2-W26-31 Transducers 02 - Displacement Sensors - Lecture Slides.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2 - Wk26 FEEG1004 L2(2) Sensors and Transducers.txt"
---

# FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive

> [!abstract] Summary
> Resistance, capacitance and inductance each contain a length or an area in their constitutive laws, $R=\rho L/A$, $C=\varepsilon_0\varepsilon_r A/d$ and $L=N^2/\mathcal R=\mu_0\mu_r N^2A/\ell$, so a mechanical displacement can be turned into an impedance change. An unloaded potentiometer gives $V_{\text{out}}/V_{\text{in}}=x/x_{\text{max}}$, independent of the track resistance, but a finite load makes it non-linear, and an op-amp voltage follower removes that loading. A variable-gap capacitor has $C\propto 1/x$, which an AC-driven inverting op-amp with the sensor in its feedback path turns into $|\mathbf V_{\text{out}}|\propto x$. An LVDT's series-opposed secondaries give an output amplitude proportional to core displacement, with a $180^\circ$ phase reversal across the null that encodes direction.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the output of a potentiometer, capacitive or LVDT displacement sensor, how a loading error or a non-linear gap law is corrected with an op-amp, or a comparison between the sensor types.
> - **Assumptions:** a uniform potentiometer track; an ideal op-amp (infinite input impedance, zero output impedance, no voltage between its inputs); a parallel-plate capacitor without fringing; an LVDT core within its linear stroke.
> - **Method:** 1. Identify which geometric quantity the displacement changes ($L$, $A$, $d$, $\varepsilon_r$ or the magnetic path). 2. Write $R(x)$, $C(x)$ or the secondary voltages in terms of $x$. 3. Add the circuit: the load in parallel with the lower track, or $Z_f$ and $Z_{\text{in}}$ of the inverting amplifier. 4. Simplify to $V_{\text{out}}(x)$ and test linearity at the endpoints or by doubling $x$. 5. State the excitation and demodulation (DC, AC carrier with envelope detection, or phase-sensitive).
> - **Common mistakes:** putting the gap capacitor at the input instead of in the feedback path, which gives $|\mathbf V_{\text{out}}|\propto 1/x$; putting the load resistance in parallel with the whole track instead of only the lower section $\tilde x R_p$.
> - **Practise:** [[#Worked examples]] · [[#Core|Self-study core tasks]] (no tutorial sheet covers transducers)

Flight-control computers need the deflection of aileron and elevator hydraulic actuators, industrial robots and machine tools track carriage position to micrometre or nanometre accuracy, and fuel management systems monitor liquid levels across complex wing tanks. Each of these is a measurement of linear or angular displacement.

Optical interferometers and encoders exist, but most industrial and aerospace displacement transducers are **passive sensors** built from resistors, capacitors and inductors. Moving the target changes the geometry of the element, and an excitation voltage turns the resulting impedance change into a signal.

The raw response is not always linear. A potentiometer becomes non-linear when the readout circuit loads it, and a gap capacitor follows $C\propto 1/x$. In both cases a suitably chosen op-amp stage ([[FEEG1004 B4 - Operational Amplifiers]]) restores a linear relation between output voltage and displacement.

## 1. Potentiometer displacement sensors

### Unloaded output and track resistance

The resistance of a uniform conductor of resistivity $\rho$, length $L$ and cross-sectional area $A$ is

$$
R = \frac{\rho L}{A} \quad [\Omega].
$$

A **displacement potentiometer** (resistive position transducer) uses $R\propto L$. It is a three-terminal resistive element of total length $x_{\text{max}}$ (or total angle $\theta_{\text{max}}$ in a rotary pot) and end-to-end resistance $R_p$, along which a movable contact, the **wiper**, slides with the object whose position $x \in [0,\ x_{\text{max}}]$ is being measured. Depending on cost, resolution and environment, the track is resistance wire wound tightly round an insulating mandrel (wire-wound), printed carbon film, thick-film cermet paste, or a smooth conducting polymer for long-life servo applications.

With a DC excitation $V_{\text{in}}$ across the fixed ends of the track ($x=0$ at ground and $x=x_{\text{max}}$ at $V_{\text{in}}$), the dimensionless fractional wiper position is

$$
\tilde{x} = \frac{x}{x_{\text{max}}} \in [0,\ 1].
$$

With uniform $A$ and $\rho$ along the track, the resistance $R_{\text{bot}}$ between ground and the wiper and the resistance $R_{\text{top}}$ between the wiper and the top terminal are proportional to their lengths:

$$
R_{\text{bot}} = \frac{x}{x_{\text{max}}}\,R_p = \tilde{x}R_p, \qquad R_{\text{top}} = \left(1 - \frac{x}{x_{\text{max}}}\right)R_p = (1 - \tilde{x})R_p.
$$

With the wiper **unloaded**, connected to an ideal voltmeter of infinite input resistance so that no current leaves through it, the same current $I = V_{\text{in}} / R_p$ flows through the whole track. Ohm's law, or the potential-divider rule from [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]], gives the unloaded output

$$
\begin{aligned}
V_{\text{out}} &= I\,R_{\text{bot}} \\
&= \left(\frac{V_{\text{in}}}{R_p}\right)\left(\frac{x}{x_{\text{max}}}\,R_p\right) \\
&= V_{\text{in}}\,\frac{x}{x_{\text{max}}} = \tilde{x}\,V_{\text{in}}.
\end{aligned}
$$

This result has two useful properties. First, the output is linear in $x$, with constant sensitivity $S = \mathrm{d}V_{\text{out}}/\mathrm{d}x = V_{\text{in}}/x_{\text{max}}\ [\text{V m}^{-1}]$. Second, $R_p$ cancels between numerator and denominator, so the output does not depend on the track resistance. If the ambient temperature swings from $-50\,^\circ\text{C}$ to $+60\,^\circ\text{C}$ and changes the resistivity $\rho(T)$ uniformly along the track, $R_{\text{bot}}$ and $R_p$ scale by the same factor and $V_{\text{out}}$ has no thermal cross-sensitivity. For the same reason, a manufacturing tolerance of, say, $\pm 10\%$ in $R_p$ between potentiometers needs no recalibration of the position scale factor.

### Loading and the op-amp buffer

In practice the wiper drives a readout circuit, meter or ADC input with a finite input resistance $R_L$, the **load resistance**, connected between the wiper and ground. Once $R_L < \infty$, current leaves through the wiper and the track is no longer a single series path. The lower section $R_{\text{bot}} = \tilde{x}R_p$ is now in parallel with $R_L$, while the upper section $R_{\text{top}} = (1 - \tilde{x})R_p$ sits in series between $V_{\text{in}}$ and the wiper node.

The parallel combination of the lower track and the load is

$$
R_p' = (\tilde{x}R_p) \parallel R_L = \frac{\tilde{x}R_p R_L}{\tilde{x}R_p + R_L}.
$$

The potential-divider rule applied to $R_{\text{top}}$ and $R_p'$ gives

$$
\begin{aligned}
\frac{V_{\text{out}}}{V_{\text{in}}} &= \frac{R_p'}{R_{\text{top}} + R_p'} \\
&= \frac{\dfrac{\tilde{x}R_p R_L}{\tilde{x}R_p + R_L}}{(1 - \tilde{x})R_p + \dfrac{\tilde{x}R_p R_L}{\tilde{x}R_p + R_L}}.
\end{aligned}
$$

Multiplying numerator and denominator by $(\tilde{x}R_p + R_L)$ clears the inner fractions:

$$
\frac{V_{\text{out}}}{V_{\text{in}}} = \frac{\tilde{x}R_p R_L}{(1 - \tilde{x})R_p(\tilde{x}R_p + R_L) + \tilde{x}R_p R_L}.
$$

Dividing numerator and denominator by $R_p R_L$,

$$
\frac{V_{\text{out}}}{V_{\text{in}}} = \frac{\tilde{x}}{(1 - \tilde{x})\left(\tilde{x}\dfrac{R_p}{R_L} + 1\right) + \tilde{x}}.
$$

Expanding the bracket and grouping the terms without $R_p/R_L$,

$$
\frac{V_{\text{out}}}{V_{\text{in}}} = \frac{\tilde{x}}{(1 - \tilde{x} + \tilde{x}) + \dfrac{R_p}{R_L}\,\tilde{x}(1 - \tilde{x})}.
$$

Since $1-\tilde x+\tilde x=1$, the loaded potentiometer equation is

$$
\frac{V_{\text{out}}}{V_{\text{in}}} = \frac{\tilde{x}}{1 + \dfrac{R_p}{R_L}\,\tilde{x}(1 - \tilde{x})}.
$$

Dividing top and bottom by $\tilde{x} = x/x_{\text{max}}$ gives the equivalent reciprocal form

$$
\frac{V_{\text{out}}}{V_{\text{in}}} = \frac{1}{\dfrac{x_{\text{max}}}{x} + \dfrac{R_p}{R_L}\left(1 - \dfrac{x}{x_{\text{max}}}\right)}.
$$

This is the **loading effect**. At the endpoints $\tilde{x} = 0$ and $\tilde{x} = 1$ the term $\tilde{x}(1 - \tilde{x})$ vanishes, so $V_{\text{out}}/V_{\text{in}}$ is $0$ at $x = 0$ and $1$ at $x = x_{\text{max}}$ whatever the value of $R_L$. Between the endpoints ($0 < \tilde{x} < 1$) the denominator exceeds 1, which pulls $V_{\text{out}}/V_{\text{in}}$ below the ideal straight line $\tilde{x}$, makes the sensor non-linear and brings back a dependence on $R_p$. The sag grows with $R_p/R_L$, that is, as $R_L$ becomes smaller relative to $R_p$. Only when $R_L \gg R_p$, so that $R_p/R_L \to 0$, does the output return to $V_{\text{out}}/V_{\text{in}} \to x/x_{\text{max}}$.

Rather than redesigning the downstream circuit to have a very large $R_L$, a unity-gain **voltage follower** (buffer, [[FEEG1004 B4 - Operational Amplifiers]]) is inserted between the wiper and the load. The wiper connects to the op-amp's non-inverting input ($+$), whose input impedance is effectively infinite ($R_{\text{in}} \to \infty$). No current is drawn from the wiper, so the potentiometer sees $R_p/R_{\text{in}} = 0$ and produces the linear voltage $V_+ = V_{\text{in}}(x/x_{\text{max}})$. Negative feedback, with the output wired directly back to the inverting input ($-$), forces $V_o = V_- = V_+ = V_{\text{in}}(x/x_{\text{max}})$, and the op-amp's near-zero output impedance ($R_{\text{out}} \to 0$) supplies whatever current $R_L$ demands without a voltage drop.

![[ee_e2_pot_loading.png|900]]

| Advantages of displacement potentiometers | Disadvantages of displacement potentiometers |
| :--- | :--- |
| • Very low cost and simple excitation and readout circuitry<br>• Lightweight and compact<br>• Operates over a wide temperature range (with the op-amp electronics located remotely if needed)<br>• High-grade conductive-polymer versions available for servo feedback | • The sliding mechanical contact creates friction and wear over repeated cycles<br>• Prone to contact noise, debris contamination and in-service failure, so unsuitable for flight-critical or high-reliability applications<br>• Rotary potentiometers always have a mechanical dead zone at the end contacts, so they cannot turn continuously through $360^\circ$ |

## 2. Capacitive displacement sensors

### Variable area, gap and dielectric

**Capacitive displacement sensors** avoid the friction, wear and limited life of a sliding wiper by measuring position without contact, through the electric field between conducting plates. They resolve displacements down to nanometres and are used in semiconductor lithography stages, MEMS accelerometers, proximity detectors, touch screens and aircraft fuel-level probes.

For a parallel-plate capacitor with overlap area $A$, plate separation (gap) $x$ (or $d$), permittivity of free space $\varepsilon_0 = 8.854 \times 10^{-12}\ \text{F m}^{-1}$ and relative permittivity $\varepsilon_r$ ([[FEEG1004 A4 - Capacitors]]),

$$
C = \frac{\varepsilon_0\varepsilon_r A}{x} \quad [\text{F}].
$$

A displacement transducer varies one of the three quantities on the right while holding the other two fixed.

Varying the overlap area gives a linear sensor. If one plate slides parallel to the other along $x$, with constant width $b$ and fixed gap $d$ so that $A = bx$, then

$$
C(x) = \frac{\varepsilon_0\varepsilon_r b}{d}\,x \propto x.
$$

Interleaved semicircular rotor and stator plates turning through an angle $\theta$, or an inner cylindrical rod sliding coaxially inside an outer tube, behave the same way. Because $x$ is in the numerator, variable-area sensors are inherently linear.

Varying the gap gives a non-linear sensor. If the target moves perpendicular to a fixed plate of area $A$, changing the air gap $x$, the capacitance is inversely proportional to $x$:

$$
C_u(x) = \frac{\varepsilon_0\varepsilon_r A}{x} \propto \frac{1}{x}.
$$

The sensitivity $\mathrm{d}C_u/\mathrm{d}x = -\varepsilon_0\varepsilon_r A / x^2$ then changes strongly with gap, so the raw transducer needs hardware or software linearisation.

Varying the dielectric is the basis of liquid-level gauging. With the plate area $A = wh$ and the separation $d$ fixed, a fluid of relative permittivity $\varepsilon_r > 1$ fills the space between the plates to a height $x \in [0,\ h]$, with air ($\varepsilon_{\text{air}} \approx 1$) in the remaining height $h - x$. The wetted lower section and the dry upper section are two capacitors in parallel, so their capacitances add; substituting each, collecting the terms in $x$ and factoring out the dry value gives

$$
\begin{aligned}
C(x) &= C_{\text{fuel}}(x) + C_{\text{air}}(h - x) \\
&= \frac{\varepsilon_0\varepsilon_r (w x)}{d} + \frac{\varepsilon_0 (1)\big(w(h - x)\big)}{d} \\
&= \frac{\varepsilon_0 w h}{d} + \frac{\varepsilon_0(\varepsilon_r - 1)w}{d}\,x \\
&= C_{\text{dry}}\left[1 + (\varepsilon_r - 1)\frac{x}{h}\right],
\end{aligned}
$$

where $C_{\text{dry}} = \varepsilon_0 w h / d$ is the empty-tank capacitance at $x = 0$. The capacitance is linear in fluid height, provided the fluid's relative permittivity is constant and accurately known.

That proviso decides how fuel level is measured in cars and in aircraft. A car's fuel tank is cost-driven and not safety-critical, since running low means pulling onto the hard shoulder, so cars use a low-cost float arm driving a rotary wiper potentiometer inside the tank. Roadside petrol and diesel also vary widely in additives and permittivity, which would cause large calibration errors in a capacitive probe. A commercial aircraft's fuel tanks are safety-critical (there is no hard shoulder at $35\,000\ \text{ft}$), span complex wing geometries that need several probes, and must work reliably with no moving parts or sparking contacts. Aircraft therefore use coaxial cylindrical capacitive probes immersed in Jet A-1 kerosene, whose specification and relative permittivity ($\varepsilon_r \approx 2.1$) are tightly controlled worldwide. Blending Sustainable Aviation Fuels (SAF), up to $20\%+$ synthetic bio-derived hydrocarbons, into Jet A-1 is a research problem: variations in SAF aromatic content shift $\varepsilon_r$, so compensating reference capacitances at the bottom of the tank are needed to prevent fuel-mass miscalculation ([[#Aircraft fuel-level gauge with an SAF blend]]).

### Inverting op-amp lineariser and carrier demodulation

To turn $C_u(x) = \varepsilon_0\varepsilon_r A / x$ into an output proportional to $x$, the sensor capacitor goes in the negative-feedback path of an **inverting AC amplifier** ([[FEEG1004 B4 - Operational Amplifiers]], [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]). A fixed, known reference capacitor $C_s$ sits at the input, driven by a constant-amplitude sinusoidal oscillator $\mathbf{V}_{\text{in}}$ at angular frequency $\omega = 2\pi f$. The input impedance is

$$
Z_{\text{in}} = \frac{1}{j\omega C_s} = -jX_s, \qquad X_s = \frac{1}{\omega C_s},
$$

and the feedback impedance is

$$
Z_f = \frac{1}{j\omega C_u(x)} = -jX_u, \qquad X_u = \frac{1}{\omega C_u(x)}.
$$

The inverting closed-loop gain is $-Z_f/Z_{\text{in}}$. Substituting the impedances, then the reactances, then $C_u(x)$:

$$
\begin{aligned}
\frac{\mathbf{V}_{\text{out}}}{\mathbf{V}_{\text{in}}} &= -\frac{Z_f}{Z_{\text{in}}} \\
&= -\frac{-jX_u}{-jX_s} \\
&= -\frac{X_u}{X_s} \\
&= -\frac{\dfrac{1}{\omega C_u(x)}}{\dfrac{1}{\omega C_s}} \\
&= -\frac{C_s}{C_u(x)} \\
&= -\frac{C_s}{\dfrac{\varepsilon_0\varepsilon_r A}{x}} \\
&= -\left(\frac{C_s}{\varepsilon_0\varepsilon_r A}\right)x.
\end{aligned}
$$

Multiplying by $\mathbf{V}_{\text{in}}$ shows that the output amplitude is proportional to the plate separation:

$$
\mathbf{V}_{\text{out}} = -\mathbf{V}_{\text{in}}\left(\frac{C_s}{\varepsilon_0\varepsilon_r A}\right)x \implies |\mathbf{V}_{\text{out}}| = |\mathbf{V}_{\text{in}}|\left(\frac{C_s}{\varepsilon_0\varepsilon_r A}\right)x \propto x.
$$

The linearisation works because two reciprocals cancel. The feedback impedance $Z_f = 1/(j\omega C_u)$ is inversely proportional to $C_u$, and $C_u = \varepsilon_0\varepsilon_r A / x$ is inversely proportional to $x$, so $1/(1/x) = x$.

> [!warning] Sensor in the feedback path, not at the input
> With $C_u$ at the input and $C_s$ in the feedback path, the gain becomes $|\mathbf{V}_{\text{out}}| \propto C_u / C_s \propto 1/x$, and the non-linearity of the gap sensor is kept.

![[ee_e2_capacitive_sensor.png|900]]

Two practical requirements follow. The first is a high carrier frequency, $f > 50\text{--}100\ \text{kHz}$. Practical air-gap sensor capacitances are small, typically $1\ \text{pF}$ to $500\ \text{pF}$. At the $50\ \text{Hz}$ mains frequency a $1\ \text{pF}$ capacitor has reactance

$$
X_C = \frac{1}{2\pi(50)(10^{-12})} = 3.18\ \text{G}\Omega,
$$

which stray board leakage and op-amp bias currents would swamp. Exciting the circuit with an oscillator above $100\ \text{kHz}$ brings $X_C$ down into a manageable $\text{k}\Omega\text{--}\text{M}\Omega$ range, and $C_s$ is chosen larger than $C_u$ to give high voltage gain ($C_s / C_u \gg 1$).

The second is demodulation. When the gap $x(t)$ varies with time, for example on a structure vibrating at $1\ \text{Hz}$ to $10\ \text{kHz}$, the op-amp output

$$
v_{\text{out}}(t) = -\left(\frac{C_s V_{\text{in},p}}{\varepsilon_0\varepsilon_r A}\right)x(t)\cos(\omega_{\text{carrier}} t)
$$

is an **amplitude-modulated (AM)** carrier above $100\ \text{kHz}$ whose envelope traces $x(t)$. A rectifier or envelope detector followed by a low-pass filter ([[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]], [[FEEG1004 D3 - AC Filters and Bode Plots]]) strips away the carrier, which is **demodulation**, and recovers the displacement waveform $x(t)$.

## 3. Inductive sensors and the LVDT

### Self-inductance and reluctance sensing

From [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]], the self-inductance of an $N$-turn coil on a magnetic circuit of reluctance $\mathcal{R}$ (also written $S$) is

$$
L = \frac{N^2}{S}\ [\text{H}], \qquad \text{where } S = \frac{\ell}{\mu_0\mu_r A}\ [\text{A Wb}^{-1} \text{ or } \text{H}^{-1}],
$$

with $\mu_0 = 4\pi \times 10^{-7}\ \text{H m}^{-1}$. Substituting $S$ gives $L = \mu_0\mu_r N^2 A/\ell$. A passive inductive displacement transducer changes $L$ in one of three ways: a ferromagnetic plunger moves into or out of a solenoid, changing the effective relative permeability $\mu_r$ and the reluctance $S(x)$; the length $\ell(x)$ of an air gap in a ferromagnetic core varies, so that $S \propto x$; or a contact slides along the turns to vary $N$.

### LVDT construction and phase-sensitive demodulation

The most widely used inductive position transducer in aerospace and mechanical engineering is the **linear variable differential transformer (LVDT)**. Its cylindrical housing contains four elements:

1. a single primary winding along the length of the cylinder, excited by a constant-amplitude AC carrier at several kilohertz ($1\text{--}10\ \text{kHz}$);
2. two identical secondary windings, $a$ and $b$, wound symmetrically on either side of the centre line;
3. a movable high-permeability nickel-iron ($\text{NiFe}$) core, slotted lengthwise to suppress eddy-current losses, attached to the target by a non-ferromagnetic push-rod (so that the rod does not distort the magnetic field) and sliding freely without touching the bore;
4. the connection of secondaries $a$ and $b$ in **series opposition** (anti-phase), so that the output phasor is the difference of the two induced voltages,

$$
\mathbf{V}_{\text{out}} = \mathbf{V}_a - \mathbf{V}_b.
$$

The differential connection encodes both the size and the sign of the core displacement $x$ from the central null ($x = 0$). At the null the core spans the two secondaries equally, the same alternating flux links each, and $\mathbf{V}_a = \mathbf{V}_b$. The series-opposed coils cancel:

$$
\mathbf{V}_{\text{out}}(0) = \mathbf{V}_a - \mathbf{V}_b = 0\ \text{V}.
$$

When the core moves towards coil $a$ ($x > 0$), more flux links $a$ than $b$, so $V_a > V_b$. The difference $\mathbf{V}_{\text{out}} = (V_a - V_b)\angle 0^\circ$ is in phase with $\mathbf{V}_a$, and over the central stroke its amplitude grows linearly with displacement, $|\mathbf{V}_{\text{out}}| = K_{\text{LVDT}}|x|$. When the core moves towards coil $b$ ($x < 0$), more flux links $b$, so $V_b > V_a$ and $V_a - V_b < 0$. Multiplying a phasor by $-1 = e^{j\pi}$ shifts its phase by $180^\circ$ ($\pi\ \text{rad}$), so $\mathbf{V}_{\text{out}} = (V_b - V_a)\angle 180^\circ$.

A standard diode rectifier would give $|V_a - V_b| \propto |x|$ and lose the sign of $x$. LVDT electronics instead use **phase-sensitive demodulation**: the output $v_{\text{out}}(t) = K_{\text{LVDT}}\,x\cos(\omega t)$ is multiplied by the primary reference carrier $\cos(\omega t)$,

$$
v_{\text{out}}(t)\cos(\omega t) = K_{\text{LVDT}}\,x\cos^2(\omega t) = \tfrac{1}{2}K_{\text{LVDT}}\,x(1 + \cos 2\omega t),
$$

and low-pass filtering the product leaves a signal that carries both the magnitude $|x|$ and the sign of $x$ from the $0^\circ/180^\circ$ phase flip. Because the core floats without touching the coil bore, the LVDT has no friction or contact wear, high linearity and sensitivity, survives harsh vibration and temperature environments, and has effectively infinite mechanical resolution, limited only by the noise floor of the readout electronics.

![[ee_e2_lvdt.png|900]]

## Worked examples

### Potentiometer loading error and buffering

A linear displacement potentiometer has a stroke $x_{\text{max}} = 100\ \text{mm}$, a track resistance $R_p = 10.0\ \text{k}\Omega$ and a stable DC supply $V_{\text{in}} = 10.0\ \text{V}$. Find (a) the unloaded sensitivity $S$ in $\text{V mm}^{-1}$ and the unloaded output at $x = 50.0\ \text{mm}$ and $x = 70.0\ \text{mm}$; (b) the loaded output, the error $V_{\text{out}} - V_{\text{ideal}}$ and the percentage full-scale error at both positions when the wiper drives a data-acquisition input with $R_L = 10.0\ \text{k}\Omega$; (c) the same for $R_L = 2.0\ \text{k}\Omega$, and the output when an ideal op-amp voltage follower is inserted between the wiper and the $2.0\ \text{k}\Omega$ load.

(a) Unloaded ($R_L \to \infty$), $V_{\text{ideal}}(x) = V_{\text{in}}\,x/x_{\text{max}}$, so the sensitivity is

$$
S = \frac{V_{\text{in}}}{x_{\text{max}}} = \frac{10.0\ \text{V}}{100\ \text{mm}} = 0.100\ \text{V mm}^{-1}.
$$

At $x = 50.0\ \text{mm}$ ($\tilde{x} = 0.50$), $V_{\text{ideal}} = 0.50 \times 10.0\ \text{V} = 5.000\ \text{V}$. At $x = 70.0\ \text{mm}$ ($\tilde{x} = 0.70$), $V_{\text{ideal}} = 0.70 \times 10.0\ \text{V} = 7.000\ \text{V}$.

(b) With $R_L = 10.0\ \text{k}\Omega$, $R_p / R_L = 10.0\ \text{k}\Omega / 10.0\ \text{k}\Omega = 1.00$. Substituting into the loaded equation from [[#Loading and the op-amp buffer]] at $\tilde{x} = 0.50$:

$$
\begin{aligned}
V_{\text{out}} &= V_{\text{in}}\,\frac{\tilde{x}}{1 + \dfrac{R_p}{R_L}\,\tilde{x}(1 - \tilde{x})} \\
&= 10.0\ \text{V} \times \frac{0.50}{1 + 1.00 \times 0.50 \times (1 - 0.50)} \\
&= 10.0\ \text{V} \times \frac{0.50}{1.25} = 4.000\ \text{V}.
\end{aligned}
$$

The loading error is $4.000\ \text{V} - 5.000\ \text{V} = -1.000\ \text{V}$, which is $10.0\%$ of the $10.0\ \text{V}$ full scale and corresponds to a $-10.0\ \text{mm}$ position error. At $\tilde{x} = 0.70$,

$$
V_{\text{out}} = 10.0\ \text{V} \times \frac{0.70}{1 + 1.00 \times 0.70 \times 0.30} = \frac{7.00\ \text{V}}{1.21} = 5.785\ \text{V}.
$$

The loading error is $5.785\ \text{V} - 7.000\ \text{V} = -1.215\ \text{V}$, or $12.15\%$ of full scale ($-12.15\ \text{mm}$).

(c) With $R_L = 2.0\ \text{k}\Omega$, $R_p / R_L = 5.00$. At $\tilde{x} = 0.50$,

$$
V_{\text{out}} = \frac{5.00\ \text{V}}{1 + 5.00(0.25)} = \frac{5.00\ \text{V}}{2.25} = 2.222\ \text{V},
$$

an error of $-2.778\ \text{V}$, or $27.8\%$ of full scale. At $\tilde{x} = 0.70$,

$$
V_{\text{out}} = \frac{7.00\ \text{V}}{1 + 5.00(0.21)} = \frac{7.00\ \text{V}}{2.05} = 3.415\ \text{V},
$$

an error of $-3.585\ \text{V}$, or $35.9\%$ of full scale.

With an ideal voltage follower between the wiper and the $2.0\ \text{k}\Omega$ load, the wiper sees $R_{\text{in}} = \infty$ ($R_p / R_{\text{in}} = 0$), and the op-amp output supplies the load current $I_L = V_{\text{out}} / (2.0\ \text{k}\Omega)$ from its power rails. The outputs return to $V_{\text{out}}(50\ \text{mm}) = 5.000\ \text{V}$ and $V_{\text{out}}(70\ \text{mm}) = 7.000\ \text{V}$, with no loading error.

> [!check] Direct parallel-resistance check at mid-stroke
> With $R_L = 10.0\ \text{k}\Omega$ and $\tilde{x} = 0.50$, the upper track is $R_{\text{top}} = 5.0\ \text{k}\Omega$ and the lower track $R_{\text{bot}} = 5.0\ \text{k}\Omega$ is in parallel with $R_L$:
> $$R_p' = 5.0\ \text{k}\Omega \parallel 10.0\ \text{k}\Omega = \frac{5.0 \times 10.0}{5.0 + 10.0} = 3.333\ \text{k}\Omega$$
> The divider rule then gives $V_{\text{out}} = 10.0\ \text{V} \times \dfrac{3.333\ \text{k}\Omega}{5.0\ \text{k}\Omega + 3.333\ \text{k}\Omega} = 10.0 \times \dfrac{1/3}{5/6} = 4.000\ \text{V}$, the same as the loaded formula.

### Capacitive gap sensor with an op-amp lineariser

An air-gap ($\varepsilon_r = 1.00$) capacitive proximity transducer has circular plates of overlap area $A = 1.00\ \text{cm}^2 = 1.00 \times 10^{-4}\ \text{m}^2$ and works over a gap from $x_{\min} = 0.10\ \text{mm}$ to $x_{\max} = 2.00\ \text{mm}$, with $\varepsilon_0 = 8.854 \times 10^{-12}\ \text{F m}^{-1}$. Find (a) the sensor capacitance $C_u(x)$ at $x = 0.10$, $0.50$, $1.00$ and $2.00\ \text{mm}$, and the reactance $X_u$ at $1.00\ \text{mm}$ for excitation at $f = 50\ \text{Hz}$ and at $f = 100\ \text{kHz}$; (b) the RMS output $|V_{\text{out}}|$ at each gap and the linearised sensitivity $S = \mathrm{d}|V_{\text{out}}|/\mathrm{d}x$ in $\text{V mm}^{-1}$, when the sensor is in the feedback loop of an inverting op-amp with a reference capacitor $C_s = 10.0\ \text{pF}$ at the input, driven by a $100\ \text{kHz}$ oscillator of RMS voltage $V_{\text{in}} = 1.00\ \text{V}$.

(a) The constant in $C_u(x) = \varepsilon_0 A / x$ is

$$
\varepsilon_0 A = (8.8542 \times 10^{-12}\ \text{F m}^{-1})(1.00 \times 10^{-4}\ \text{m}^2) = 8.8542 \times 10^{-16}\ \text{F m} = 0.8854\ \text{pF}\cdot\text{mm},
$$

so

$$
\begin{aligned}
x &= 0.10\ \text{mm}:\quad C_u = \frac{0.8854\ \text{pF}\cdot\text{mm}}{0.10\ \text{mm}} = 8.854\ \text{pF} \\
x &= 0.50\ \text{mm}:\quad C_u = \frac{0.8854\ \text{pF}\cdot\text{mm}}{0.50\ \text{mm}} = 1.771\ \text{pF} \\
x &= 1.00\ \text{mm}:\quad C_u = \frac{0.8854\ \text{pF}\cdot\text{mm}}{1.00\ \text{mm}} = 0.8854\ \text{pF} \\
x &= 2.00\ \text{mm}:\quad C_u = \frac{0.8854\ \text{pF}\cdot\text{mm}}{2.00\ \text{mm}} = 0.4427\ \text{pF}
\end{aligned}
$$

At $x = 1.00\ \text{mm}$ ($C_u = 0.8854 \times 10^{-12}\ \text{F}$), the reactance $X_u = 1/(2\pi f C_u)$ at the two frequencies is

$$
\begin{aligned}
X_u(50\ \text{Hz}) &= \frac{1}{2\pi(50\ \text{Hz})(0.8854 \times 10^{-12}\ \text{F})} = 3.595 \times 10^9\ \Omega = 3.60\ \text{G}\Omega \\
X_u(100\ \text{kHz}) &= \frac{1}{2\pi(100 \times 10^3\ \text{Hz})(0.8854 \times 10^{-12}\ \text{F})} = 1.798 \times 10^6\ \Omega = 1.80\ \text{M}\Omega
\end{aligned}
$$

The $100\ \text{kHz}$ carrier reduces the impedance by a factor of $2000$, from an unmeasurable $3.60\ \text{G}\Omega$ to $1.80\ \text{M}\Omega$.

(b) The lineariser gives $|V_{\text{out}}| = V_{\text{in}}\,C_s/C_u(x) = V_{\text{in}}(C_s/\varepsilon_0 A)\,x$. With $V_{\text{in}} = 1.00\ \text{V}$ and $C_s = 10.0\ \text{pF}$:

$$
\begin{aligned}
x &= 0.10\ \text{mm}:\quad |V_{\text{out}}| = 1.00\ \text{V} \times \frac{10.0\ \text{pF}}{8.854\ \text{pF}} = 1.129\ \text{V} \\
x &= 0.50\ \text{mm}:\quad |V_{\text{out}}| = 1.00\ \text{V} \times \frac{10.0\ \text{pF}}{1.771\ \text{pF}} = 5.647\ \text{V} \\
x &= 1.00\ \text{mm}:\quad |V_{\text{out}}| = 1.00\ \text{V} \times \frac{10.0\ \text{pF}}{0.8854\ \text{pF}} = 11.29\ \text{V} \\
x &= 2.00\ \text{mm}:\quad |V_{\text{out}}| = 1.00\ \text{V} \times \frac{10.0\ \text{pF}}{0.4427\ \text{pF}} = 22.59\ \text{V}
\end{aligned}
$$

The linearised sensitivity is constant over the whole stroke:

$$
S = \frac{\mathrm{d}|V_{\text{out}}|}{\mathrm{d}x} = \frac{V_{\text{in}} C_s}{\varepsilon_0 A} = \frac{(1.00\ \text{V})(10.0\ \text{pF})}{0.8854\ \text{pF}\cdot\text{mm}} = 11.29\ \text{V mm}^{-1}.
$$

> [!check] Ratio linearity check
> Doubling the gap from $0.50\ \text{mm}$ to $1.00\ \text{mm}$ halves $C_u$ (from $1.771\ \text{pF}$ to $0.8854\ \text{pF}$) and doubles $|V_{\text{out}}|$ (from $5.647\ \text{V}$ to $11.294\ \text{V}$); doubling again to $2.00\ \text{mm}$ doubles $|V_{\text{out}}|$ again to $22.588\ \text{V}$. At $100\ \text{kHz}$ the input capacitor $C_s = 10.0\ \text{pF}$ has reactance $X_s = 159.15\ \text{k}\Omega$, and the ratio $X_u(1\ \text{mm}) / X_s = 1797.5\ \text{k}\Omega / 159.15\ \text{k}\Omega = 11.294 = C_s / C_u$.

### Aircraft fuel-level gauge with an SAF blend

A vertical coaxial capacitive fuel-level probe of height $h = 1.00\ \text{m}$ in an airliner wing tank has a dry (air, $\varepsilon_{\text{air}} = 1.00$) capacitance $C_{\text{dry}} = 50.0\ \text{pF}$ and is calibrated for Jet A-1 kerosene with $\varepsilon_r = 2.10$. Find (a) the probe capacitance half full ($x = 0.50\ \text{m}$) and full ($x = 1.00\ \text{m}$) of Jet A-1, and the capacitance sensitivity in $\text{pF m}^{-1}$; (b) the capacitance and the apparent level $x_{\text{apparent}}$ reported by the uncompensated Jet A-1 calibration when the tank is refuelled to $100\%$ ($x_{\text{true}} = 1.00\ \text{m}$) with an SAF blend of $\varepsilon_{r,\text{SAF}} = 2.04$.

(a) The dielectric-level formula from [[#Variable area, gap and dielectric]] with Jet A-1 gives

$$
C(x) = C_{\text{dry}}\left[1 + (\varepsilon_r - 1)\frac{x}{h}\right] = 50.0\ \text{pF}\left[1 + (2.10 - 1.00)\frac{x}{1.00\ \text{m}}\right] = 50.0\ \text{pF} + \left(55.0\ \text{pF m}^{-1}\right)x.
$$

Half full, $C(0.50\ \text{m}) = 50.0 + 55.0(0.50) = 77.5\ \text{pF}$. Full, $C(1.00\ \text{m}) = 50.0 \times 2.10 = 105.0\ \text{pF}$. The sensitivity is $S_C = \mathrm{d}C/\mathrm{d}x = C_{\text{dry}}(\varepsilon_r - 1)/h = 55.0\ \text{pF m}^{-1}$.

(b) With the probe fully immersed ($x_{\text{true}} = 1.00\ \text{m}$) in the SAF blend, the capacitance is

$$
C_{\text{meas}} = \varepsilon_{r,\text{SAF}}\,C_{\text{dry}} = 2.04 \times 50.0\ \text{pF} = 102.0\ \text{pF}.
$$

The avionics computer, calibrated for Jet A-1, inverts $C_{\text{meas}} = 50.0 + 55.0\,x_{\text{apparent}}$ to infer the fuel height:

$$
\begin{aligned}
x_{\text{apparent}} &= \frac{C_{\text{meas}} - C_{\text{dry}}}{55.0\ \text{pF m}^{-1}} \\
&= \frac{102.0\ \text{pF} - 50.0\ \text{pF}}{55.0\ \text{pF m}^{-1}} = \frac{52.0}{55.0}\ \text{m} = 0.9455\ \text{m} \quad (94.5\%\text{ full})
\end{aligned}
$$

A $-2.86\%$ shift in relative permittivity ($2.10 \to 2.04$) therefore causes a $-5.45\%$ error in the indicated fuel volume.

> [!check] Compensator reference cell check
> Since $x_{\text{apparent}}/h = \dfrac{\varepsilon_{r,\text{SAF}} - 1}{\varepsilon_{r,\text{JetA1}} - 1} = \dfrac{1.04}{1.10} = 0.9455$, the fractional level error is the permittivity error amplified by $\varepsilon_r / (\varepsilon_r - 1) \approx 2$. Modern fuel-quantity indicating systems (FQIS) remove this SAF error with a small, permanently submerged reference capacitor $C_{\text{ref}} = \varepsilon_{r,\text{actual}}C_{\text{ref,dry}}$ at the bottom of the tank, which measures $\varepsilon_{r,\text{actual}} - 1$ continuously in flight:
> $$\frac{x}{h} = \frac{(C_{\text{meas}} / C_{\text{dry}}) - 1}{(C_{\text{ref}} / C_{\text{ref,dry}}) - 1} = \frac{2.04 - 1}{2.04 - 1} = 1.000$$

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]
- Next: [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]
- Concepts: [[Potentiometric Displacement Sensor]] · [[Capacitive Displacement Sensor]] · [[Linear Variable Differential Transformer]] · [[Loading Effect and Buffering]]
- LVDTs, and rotary RVDTs, are the standard position-feedback sensors on primary hydraulic and electro-hydrostatic flight-control actuators and on jet-engine fuel-metering valves, because they run without friction and are unaffected by hydraulic-fluid contamination.
- Micromachined accelerometers and gyroscopes in aircraft and smartphone inertial measurement units (IMUs) measure proof-mass deflection with differential variable-gap and interdigitated comb-drive capacitors; see [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]].
- The potentiometer loading derivation and the voltage-follower fix underpin the Year 2 input and output impedance-matching analysis in [[Loading Effect and Buffering]] and [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]].

## Sources

- `02 - Sources/S2 Transducers/S2-W26-31 Transducers 02 - Displacement Sensors - Lecture Slides.pdf`: $R$, $C$, $L$ constitutive equations, unloaded and loaded displacement potentiometer derivations, op-amp voltage-follower buffer, potentiometer advantages and disadvantages, capacitive displacement sensors (area, gap, Jet A-1 dielectric), inverting op-amp lineariser and AM demodulation, inductive reluctance sensors and LVDT construction and waveforms.
- `02 - Sources/Lectures/FEEG1004 Lecture 2 - Wk26 FEEG1004 L2(2) Sensors and Transducers.txt` (ll. 1–540): temperature independence of unloaded potentiometers, loading non-linearity derivation and buffer fix, variable-area, gap and dielectric capacitors, aircraft Jet A-1 capacitive fuel probe against automotive float potentiometer, SAF permittivity challenge, inverting op-amp linearisation at $>50\text{--}100\ \text{kHz}$ and demodulation, LVDT series-opposition secondaries and $180^\circ$ phase direction encoding.

## Self-study tasks

### Core

- [ ] Explain why the unloaded output $V_{\text{out}} = V_{\text{in}}(x/x_{\text{max}})$ is independent of track resistance and temperature, and derive the loaded equation $V_{\text{out}}/V_{\text{in}} = \tilde{x}/[1 + (R_p/R_L)\tilde{x}(1-\tilde{x})]$ (Transducers 02 slides 6–8; L2(2) transcript ll. 110–168). → [[#Unloaded output and track resistance]]; [[#Loading and the op-amp buffer]]; [[#Potentiometer loading error and buffering]]
- [ ] Explain how a unity-gain voltage follower removes the loading non-linearity of a displacement potentiometer (Transducers 02 slide 9; L2(2) transcript ll. 169–197). → [[#Loading and the op-amp buffer]]
- [ ] Compare aircraft capacitive and automotive float-potentiometer fuel-level sensors for principle, reliability, accuracy and sensitivity to fuel permittivity (Transducers 02 slide 15; L2(2) transcript ll. 284–359). → [[#Variable area, gap and dielectric]]; [[#Aircraft fuel-level gauge with an SAF blend]]
- [ ] Show that $C_u(x) = \varepsilon_0\varepsilon_r A/x$ in the feedback path of an AC-driven inverting op-amp gives $|V_{\text{out}}| \propto x$, and explain why a carrier above $50\text{--}100\ \text{kHz}$ and demodulation are needed (Transducers 02 slides 17–21; L2(2) transcript ll. 360–446). → [[#Inverting op-amp lineariser and carrier demodulation]]; [[#Capacitive gap sensor with an op-amp lineariser]]
- [ ] Describe the primary, series-opposed secondaries and $\text{NiFe}$ core of an LVDT, and explain how magnitude and direction are both recovered from $V_{\text{out}} = V_a - V_b$ (Transducers 02 slides 24–27; L2(2) transcript ll. 456–523). → [[#LVDT construction and phase-sensitive demodulation]]

### Further practice

- [ ] In the weak-loading regime ($k = R_p/R_L \ll 1$, where the loading error $\Delta(\tilde{x}) = \tilde{x} - \tilde{x}/[1 + k\tilde{x}(1-\tilde{x})] \approx k\tilde{x}^2(1-\tilde{x})$), differentiate with respect to $\tilde{x}$ to show that the largest non-linearity error occurs at $\tilde{x} = 2/3$ ($x = 0.667\,x_{\text{max}}$) with magnitude $\Delta_{\max} \approx \tfrac{4}{27}(R_p/R_L)\,V_{\text{in}}$ (suggested, not lecturer-set). → [[#Loading and the op-amp buffer]]

## Transcript and slide slips

> [!warning] Capacitance axis labelled in pC instead of pF (Transducers 02, slide 16)
> Where: [[#Variable area, gap and dielectric]]
> The slide 16 graph of the inverse relation $C \propto 1/x$ between capacitance and air gap $x\ (\text{mm})$ labels its vertical axis `C (pC)`. The picocoulomb is a unit of charge $Q$; capacitance is in picofarads ($\text{pF}$), as slide 20 states correctly ("Sensor capacitances usually lie between $1\ \text{pF}$ and $500\ \text{pF}$").

> [!warning] Relative permittivity transcribed as "ETA R" (L2(2) transcript, l. 233)
> Where: [[#Variable area, gap and dielectric]]
> At l. 233 the automated transcript records the relative permittivity in $C = \varepsilon_0\varepsilon_r A / x$ as "this relative permittivity, ETA R". The symbol on slide 13 is the Greek epsilon ($\varepsilon_r$), not eta ($\eta$).
