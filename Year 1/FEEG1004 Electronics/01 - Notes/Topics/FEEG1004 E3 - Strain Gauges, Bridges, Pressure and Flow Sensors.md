---
title: "FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors"
module: "FEEG1004 Electronics"
type: topic
stream: "Part E: Transducers and Measurement"
order: 3
tags: [feeg1004, transducers, strain-gauge, gauge-factor, wheatstone-bridge, load-cell, pressure-sensor, venturi, pitot]
aliases: ["Transducers 03", "Strain gauges", "Wheatstone bridge", "Pressure sensors", "Flow measurement"]
date: 2026-09-27
status: lectured
coverage: "FEEG1004 Lecture 3 (ll. 1–564)"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites:
  - "[[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]"
  - "[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"
  - "[[FEEG1004 B4 - Operational Amplifiers]]"
next_topics: []
key_concepts:
  - "[[Gauge Factor]]"
  - "[[Strain Gauge Bridge Configurations]]"
  - "[[Wheatstone Bridge and Strain Gauges]]"
  - "[[Stagnation Pressure and Pitot Tube]]"
tutorial_sheets: []
sources:
  - "02 - Sources/S2 Transducers/S2-W26-31 Transducers 03 - Complete Systems - Lecture Slides.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 3.txt"
---

# FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors

> [!abstract] Summary
> Mechanical strain $\varepsilon = \Delta\ell/\ell$ is the measurand behind structural stress and fatigue monitoring, load cells, diaphragm pressure transducers and differential-pressure flow and airspeed sensors. A resistive strain gauge changes resistance through its length, its Poisson contraction and its resistivity, $\Delta R/R = \Delta\rho/\rho + (1+2\nu)\varepsilon = G\varepsilon$, with $G \approx 2$ for metallic foil and $G \approx 100\text{--}120$ for doped semiconductor gauges. Because $\Delta R$ is a fraction of an ohm on a $120\ \Omega$ or $350\ \Omega$ baseline, gauges are wired into a Wheatstone bridge whose linearised output is $V_{\text{out}} = NEG\varepsilon/4$ for $N$ active gauges; adjacent arms subtract and opposite arms add, which cancels temperature drift and unwanted strain components before a differential amplifier scales the signal. Four gauges on a diaphragm measure absolute, gauge or differential pressure, and a differential pressure across a Venturi or a Pitot-static probe gives flow speed through Bernoulli's equation, $U = \sqrt{2\Delta p/\rho}$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for a strain-gauge resistance change or gauge factor, a Wheatstone bridge output or balance condition, the bridge layout for bending, axial load, torsion or a pressure diaphragm, or a flow speed or airspeed from a differential pressure.
> - **Assumptions:** small strain ($G\varepsilon \ll 1$), so the bridge equation can be linearised; equal unstrained arms $R$; a high-impedance detector drawing no current from the bridge midpoints; steady, incompressible, inviscid flow along a horizontal streamline for Bernoulli.
> - **Method:** 1. Find the strain, e.g. $\varepsilon = \sigma/E_{\text{Young}}$. 2. Convert each gauge's strain, including thermal and parasitic parts, to $\delta = \Delta R/R = G\varepsilon$. 3. Place the gauges in arms and apply $V_{\text{out}} \approx \frac{E}{4}(\delta_1 - \delta_2 - \delta_3 + \delta_4)$. 4. Scale with $V_{\text{amp}} = (R_f/R_{\text{in}})(V_2 - V_1)$. 5. For flow, convert $\Delta p$ with $\Delta p = \frac{1}{2}\rho U^2$ or the Venturi relation.
> - **Common mistakes:** placing two axial gauges in adjacent arms, where their signals cancel; assuming two active axial gauges in opposite arms are temperature compensated without dummy gauges.
> - **Practise:** [[#Worked examples]] · [[#Core|Self-study core tasks]] (no tutorial sheet covers transducers)

Forces, moments, pressures and fluid velocities in real structures, from composite UAV wings and wind-tunnel balances to jet-engine bearings and hydraulic actuators, cannot be wired directly into an amplifier. A mechanical element such as a cantilever beam, a load-cell billet or a thin diaphragm acts as the **primary sensing element**, converting force or pressure into surface **strain** $\varepsilon$, and a bonded strain gauge converts that strain into a resistance change.

Typical engineering strains are tiny. Under a heavy working stress of $100\ \text{MPa}$, an aluminium wing spar ($E_{\text{Young}} = 70\ \text{GPa}$) stretches by only $\varepsilon = 0.00143$ ($1430\ \mu\varepsilon$, or $0.14\%$). A metallic foil gauge bonded to that spar changes its $120\ \Omega$ resistance by less than $0.35\ \Omega$, a shift that a few degrees of ambient temperature change can swamp unless the gauge sits in a balanced Wheatstone bridge followed by a differential op-amp.

## 1. Strain and the resistive strain gauge

### Stress, strain and Poisson's ratio

An axial tensile force $F\ [\text{N}]$ on a member of original length $\ell\ [\text{m}]$ and cross-sectional area $A\ [\text{m}^2]$ stretches it by $\Delta\ell$. Three quantities describe its elastic deformation ([[Stress, Strain and Young's Modulus]]). The **axial strain** is dimensionless and is often quoted in **microstrain**, $1\ \mu\varepsilon = 10^{-6}\ \text{m m}^{-1}$:

$$
\varepsilon = \frac{\text{change in length}}{\text{original length}} = \frac{\Delta\ell}{\ell}.
$$

The **normal stress** $\sigma\ [\text{Pa} = \text{N m}^{-2}]$ and **Young's modulus** $E_{\text{Young}}\ [\text{GPa} = 10^9\ \text{N m}^{-2}]$ are

$$
\sigma = \frac{F}{A}, \qquad E_{\text{Young}} = \frac{\text{stress}}{\text{strain}} = \frac{\sigma}{\varepsilon}.
$$

A wire or bar of diameter $d$ stretched axially ($\Delta\ell/\ell > 0$) contracts laterally ($\Delta d/d < 0$). **Poisson's ratio** $\nu$, dimensionless and typically $0 \le \nu \le 0.5$ with $\nu \approx 0.30$ for structural metals, sets the size of that contraction:

$$
\nu = -\frac{\Delta d / d}{\Delta\ell / \ell} = -\frac{\Delta d / d}{\varepsilon},
$$

so the transverse strain is

$$
\frac{\Delta d}{d} = -\nu\varepsilon.
$$

### Strain-gauge equation and gauge factor

A resistive **strain gauge** is a long, thin conductive filament laid in a back-and-forth grid on a thin insulating backing film, so that many parallel grid lines add up the active length along the strain axis, and bonded firmly to the surface of the test structure. Consider a cylindrical wire segment of length $\ell$, diameter $d$, cross-sectional area $A = \pi d^2/4$ and resistivity $\rho\ [\Omega\text{ m}]$. Its unstrained resistance is

$$
R = \frac{\rho\ell}{A}.
$$

Under axial strain $\varepsilon = \Delta\ell/\ell$, the length $\ell$, the area $A$ and the resistivity $\rho$ can all change. Differentiating $R(\varepsilon) = \rho(\varepsilon)\,\ell(\varepsilon)/A(\varepsilon)$ with respect to $\varepsilon$ by the product rule separates two physical effects:

$$
\frac{\mathrm{d}R}{\mathrm{d}\varepsilon} = \underbrace{\frac{\ell}{A}\frac{\mathrm{d}\rho}{\mathrm{d}\varepsilon}}_{\text{piezoresistive}} + \underbrace{\rho\frac{\mathrm{d}}{\mathrm{d}\varepsilon}\!\left(\frac{\ell}{A}\right)}_{\text{geometric}}.
$$

The geometric derivative follows from the quotient rule:

$$
\frac{\mathrm{d}}{\mathrm{d}\varepsilon}\!\left(\frac{\ell}{A}\right) = \frac{1}{A}\frac{\mathrm{d}\ell}{\mathrm{d}\varepsilon} - \frac{\ell}{A^2}\frac{\mathrm{d}A}{\mathrm{d}\varepsilon}.
$$

Since $\Delta\ell = \ell\,\varepsilon$, a small strain increment $\mathrm{d}\varepsilon = \mathrm{d}\ell/\ell$ gives $\mathrm{d}\ell/\mathrm{d}\varepsilon = \ell$. For the circular section $A = \pi d^2/4$, the chain rule through $d$ gives

$$
\begin{aligned}
\frac{\mathrm{d}A}{\mathrm{d}\varepsilon} &= \frac{\mathrm{d}}{\mathrm{d}d}\!\left(\frac{\pi d^2}{4}\right)\frac{\mathrm{d}d}{\mathrm{d}\varepsilon} \\
&= \left(\frac{2\pi d}{4}\right)\frac{\mathrm{d}d}{\mathrm{d}\varepsilon} \\
&= 2\left(\frac{\pi d^2}{4}\right)\left(\frac{1}{d}\frac{\mathrm{d}d}{\mathrm{d}\varepsilon}\right) \\
&= 2A\left(\frac{1}{d}\frac{\mathrm{d}d}{\mathrm{d}\varepsilon}\right).
\end{aligned}
$$

Poisson's ratio gives $\mathrm{d}d/d = -\nu\,\mathrm{d}\varepsilon$, so $(1/d)(\mathrm{d}d/\mathrm{d}\varepsilon) = -\nu$ and

$$
\frac{\mathrm{d}A}{\mathrm{d}\varepsilon} = -2\nu A.
$$

Substituting $\mathrm{d}\ell/\mathrm{d}\varepsilon = \ell$ and $\mathrm{d}A/\mathrm{d}\varepsilon = -2\nu A$ into the geometric derivative,

$$
\begin{aligned}
\frac{\mathrm{d}}{\mathrm{d}\varepsilon}\!\left(\frac{\ell}{A}\right) &= \frac{\ell}{A} - \frac{\ell}{A^2}(-2\nu A) \\
&= \frac{\ell}{A}(1 + 2\nu).
\end{aligned}
$$

Putting this into $\mathrm{d}R/\mathrm{d}\varepsilon$ gives

$$
\frac{\mathrm{d}R}{\mathrm{d}\varepsilon} = \frac{\ell}{A}\frac{\mathrm{d}\rho}{\mathrm{d}\varepsilon} + \frac{\rho\ell}{A}(1 + 2\nu).
$$

Dividing every term by $R = \rho\ell/A$,

$$
\frac{1}{R}\frac{\mathrm{d}R}{\mathrm{d}\varepsilon} = \frac{1}{\rho}\frac{\mathrm{d}\rho}{\mathrm{d}\varepsilon} + (1 + 2\nu).
$$

For small strains the derivatives become finite changes, which gives the **strain-gauge resistance equation**:

$$
\frac{\Delta R}{R} = \underbrace{\frac{\Delta\rho}{\rho}}_{\text{piezoresistive effect}} + \underbrace{(1 + 2\nu)\varepsilon}_{\text{geometric effect}}.
$$

Both effects are summarised in one calibrated number, the dimensionless **gauge factor** $G$:

$$
G = \frac{\Delta R / R}{\Delta\ell / \ell} = \frac{\Delta R / R}{\varepsilon} = 1 + 2\nu + \frac{\Delta\rho / \rho}{\varepsilon} \quad \Longleftrightarrow \quad \frac{\Delta R}{R} = G\varepsilon.
$$

### Gauge families and practical limits

| Strain gauge family | Typical materials | Gauge factor $G$ | Dominant mechanism | Characteristics and trade-offs |
| :--- | :--- | :--- | :--- | :--- |
| Metallic foil or wire gauges | Annealed copper, constantan ($\text{Cu-Ni}$), nichrome ($\text{Ni-Cr}$) | $G \approx 2.0$ | Geometric ($\nu \approx 0.3 \implies 1 + 2\nu = 1.6$; small $\Delta\rho/\rho \approx 0.4\varepsilon$) | Standard resistances $120\ \Omega$ or $350\ \Omega \pm 0.2\%$; linear, low cost, sold in matched sets; limited stress and fatigue life |
| Semiconductor gauges | Doped single-crystal silicon ($\text{Si}$) or germanium ($\text{Ge}$) | $G \approx 100\text{--}120$ | Piezoresistive (strain deforms the crystal band gap and changes carrier mobility) | $50\times$ the sensitivity of foil gauges; much more sensitive to temperature, non-linear, fragile, and $\approx 10\times$ the cost of foil gauges |

Temperature affects a bonded gauge twice: it changes the gauge resistivity through its temperature coefficient of resistance, and it changes the dimensions of the host structure through differential thermal expansion. Foil gauges are therefore made "self-temperature-compensated", with alloys matched to the thermal expansion coefficient of a specific host such as mild steel ($\approx 11\ \text{ppm }^\circ\text{C}^{-1}$) or aluminium ($\approx 23\ \text{ppm }^\circ\text{C}^{-1}$).

The cyanoacrylate or epoxy adhesive layer must transmit surface strain from the structure into the foil without creeping or delaminating. Refractory gauges can operate from $-200\,^\circ\text{C}$ to $+800\,^\circ\text{C}$, but the adhesive often sets a much lower service ceiling.

The thin grid is bonded over a small area, so $I^2R$ Joule heating warms the gauge and causes thermal drift. The maximum gauge current is typically $I_{g,\max} \approx 10\ \text{mA}$, which limits the excitation of a $120\ \Omega$ bridge to $E \approx 2\ \text{V}$ ([[#Excitation limit, bridge outputs and amplifier gain]]).

## 2. Wheatstone bridge and conditioning chain

### Balance, trimming and the quarter bridge

Even at a large strain of $\varepsilon = 1000\ \mu\varepsilon = 10^{-3}$, a $120\ \Omega$ foil gauge with $G = 2.0$ changes its resistance by only $\Delta R = RG\varepsilon = 120 \times 2.0 \times 10^{-3} = 0.24\ \Omega$, a $0.2\%$ change on a $120\ \Omega$ baseline. Measuring $120.24\ \Omega$ directly with an ohmmeter spends almost the whole dynamic range of the ADC on the static $120\ \Omega$ offset.

The **Wheatstone bridge** (invented by Samuel Hunter Christie and popularised by Charles Wheatstone) removes the baseline by connecting two potential dividers in parallel across a DC excitation $E$ and measuring the difference between their midpoint voltages. The left divider is $R_1$ (upper) in series with $R_2$ (lower), and the right divider is $R_3$ (upper) in series with $R_4$ (lower). If a high-impedance voltmeter or differential amplifier draws negligible current from the midpoints, the node voltages $V_1$ (between $R_1$ and $R_2$) and $V_2$ (between $R_3$ and $R_4$), measured from the $0\ \text{V}$ rail, are

$$
V_1 = E\,\frac{R_2}{R_1 + R_2}, \qquad V_2 = E\,\frac{R_4}{R_3 + R_4}.
$$

The bridge output is their difference:

$$
V_{\text{out}} = V_2 - V_1 = E\left(\frac{R_4}{R_3 + R_4} - \frac{R_2}{R_1 + R_2}\right).
$$

The bridge is **balanced** ($V_{\text{out}} = 0\ \text{V}$) when the two dividers have equal voltage ratios:

$$
\begin{aligned}
\frac{R_4}{R_3 + R_4} &= \frac{R_2}{R_1 + R_2} \\
R_4(R_1 + R_2) &= R_2(R_3 + R_4) \\
R_1 R_4 + R_2 R_4 &= R_2 R_3 + R_2 R_4 \\
R_1 R_4 &= R_2 R_3 \quad \Longleftrightarrow \quad \frac{R_1}{R_2} = \frac{R_3}{R_4}.
\end{aligned}
$$

Commercial gauges have a resistance tolerance of $\pm 0.2\%$, which is $\pm 0.24\ \Omega$ on $120\ \Omega$ and as large as a $1000\ \mu\varepsilon$ strain signal, so an unstrained bridge rarely reads $0\ \text{V}$ when first assembled. Initial balancing ("trimming") uses a **trimming potentiometer** $R_p$ wired across the excitation $E$, with its wiper connected to one output node through a high-value **isolation resistor** $R_i$ (typically $R_i \gg R_b$, where $R_b$ is the bridge-arm resistance). Adjusting it nulls the unstrained output to $0.000\ \text{V}$ before the structure is loaded.

Bridge sensitivity $\Delta V_{\text{out}}/\Delta\varepsilon$ is greatest when all four unstrained arms are equal, $R_1 = R_2 = R_3 = R_4 = R$. In a **quarter bridge** one arm, $R_4 = R + \Delta R$, is an active gauge and the other three are fixed resistors of value $R$. Substituting into $V_{\text{out}}$:

$$
\begin{aligned}
V_{\text{out}} &= E\left(\frac{R + \Delta R}{R + (R + \Delta R)} - \frac{R}{R + R}\right) \\
&= E\left(\frac{R + \Delta R}{2R + \Delta R} - \frac{1}{2}\right) \\
&= E\,\frac{2(R + \Delta R) - (2R + \Delta R)}{2(2R + \Delta R)} \\
&= E\,\frac{\Delta R}{4R + 2\Delta R} \\
&= \frac{E}{4}\,\frac{\Delta R / R}{1 + \dfrac{\Delta R}{2R}}.
\end{aligned}
$$

For metallic foil gauges $|\Delta R / R| = G|\varepsilon| \ll 1$ (typically below $0.01$), so $\Delta R/(2R)$ is negligible next to 1 in the denominator. This leaves the linearised quarter-bridge equation

$$
V_{\text{out}} \approx \frac{E}{4}\,\frac{\Delta R}{R} = \frac{E G \varepsilon}{4} \quad (\text{quarter bridge, } N = 1).
$$

![[ee_e3_strain_bridge.png|900]]

### Four-arm bridge equation and temperature compensation

Suppose all four arms of an initially equal-arm bridge ($R_{k,0} = R$) are strain gauges with small fractional changes $\delta_k = \Delta R_k / R$ ($|\delta_k| \ll 1$), so that $R_k = R(1 + \delta_k)$ for $k \in \{1, 2, 3, 4\}$. Each divider ratio then has the form $(1+\delta_a)/(2+\delta_a+\delta_b)$, which to first order is

$$
\begin{aligned}
\frac{1 + \delta_a}{2 + \delta_a + \delta_b} &= \frac{1}{2}\,\frac{1 + \delta_a}{1 + \frac{1}{2}(\delta_a + \delta_b)} \\
&\approx \frac{1}{2}\left(1 + \delta_a - \frac{1}{2}\delta_a - \frac{1}{2}\delta_b\right) \\
&= \frac{1}{2} + \frac{\delta_a - \delta_b}{4}.
\end{aligned}
$$

Applying this to the left divider ($a = 2$, $b = 1$) and the right divider ($a = 4$, $b = 3$) gives the midpoint voltages

$$
V_1 \approx E\left(\frac{1}{2} + \frac{\delta_2 - \delta_1}{4}\right), \qquad V_2 \approx E\left(\frac{1}{2} + \frac{\delta_4 - \delta_3}{4}\right).
$$

Their difference $V_{\text{out}} = V_2 - V_1$ is the four-arm Wheatstone bridge equation:

$$
V_{\text{out}} \approx \frac{E}{4}\big(\delta_4 - \delta_3 - \delta_2 + \delta_1\big) = \frac{E}{4}\left(\frac{\Delta R_1}{R} - \frac{\Delta R_2}{R} - \frac{\Delta R_3}{R} + \frac{\Delta R_4}{R}\right).
$$

The signs of arms $(1,\ 2,\ 3,\ 4)$ are $(+,\ -,\ -,\ +)$. Adjacent arms have opposite signs, so their changes subtract: arm 1 is adjacent to arm 2 on the left leg and to arm 3 across the top, and arm 4 is adjacent to arm 3 on the right leg and to arm 2 across the bottom. Diagonally opposite arms have the same sign, so their changes add: arms 1 and 4 are both positive, and arms 2 and 3 are both negative.

This sign pattern does three jobs at once. The first is signal multiplication. With $N \in \{1, 2, 4\}$ active gauges placed so that tensile gauges ($+\varepsilon$) occupy the positive arms $R_1, R_4$ and compressive gauges ($-\varepsilon$) occupy the negative arms $R_2, R_3$, every contribution adds with the same sign:

$$
V_{\text{out}} = \frac{N E G \varepsilon}{4},
$$

where $N$ is the number of **active** gauges ($N = 1$ quarter bridge, $N = 2$ half bridge, $N = 4$ full bridge).

The second is temperature compensation. Two identical gauges on the same structure in adjacent arms ($R_1$ and $R_2$, or $R_3$ and $R_4$) see the same fractional thermal change $\delta_T$ for a uniform ambient temperature change $\Delta T$. Adjacent arms subtract, $\delta_T - \delta_T = 0$, so the drift cancels.

The third is cross-axis rejection. Unwanted strain components, such as axial tension when bending is wanted, or bending when axial tension or shaft torque is wanted, can be arranged to give equal-sign changes in adjacent arms, where they cancel.

### Bending, axial and torsion layouts

![[ee_e3_gauge_configurations.png|900]]

Five standard structural layouts follow from the four-arm equation.

For cantilever bending with a half bridge ($N = 2$), a cantilever clamped at its root and loaded downwards at its free tip carries tensile strain $+\varepsilon_b$ on its top surface and an equal compressive strain $-\varepsilon_b$ on its bottom surface, with zero strain on the neutral axis and the largest strain near the root. The top gauge ($R_G + \Delta R_b$) and bottom gauge ($R_G - \Delta R_b$) go in adjacent arms of one leg, $R_3 = R_G - \Delta R_b$ and $R_4 = R_G + \Delta R_b$, with fixed resistors $R_1 = R_2 = R_G$:

$$
V_{\text{out}} = \frac{E}{4}\big[(+\delta_b + \delta_T) - (-\delta_b + \delta_T)\big] = \frac{2 E G \varepsilon_b}{4} = \frac{E G \varepsilon_b}{2}.
$$

The thermal terms cancel ($\delta_T - \delta_T = 0$). A pure axial force stretches both surfaces by $+\varepsilon_a$, which also cancels in adjacent arms ($+\delta_a - \delta_a = 0$).

For cantilever bending with a full bridge ($N = 4$), two gauges on the top surface ($+\varepsilon_b$) go in the opposite arms $R_1, R_4$ and two on the bottom surface ($-\varepsilon_b$) in the other opposite pair $R_2, R_3$:

$$
V_{\text{out}} = \frac{E}{4}\big[(+\delta_b) - (-\delta_b) - (-\delta_b) + (+\delta_b)\big] = \frac{4 E G \varepsilon_b}{4} = E G \varepsilon_b.
$$

All four arms share $\delta_T$ and any axial $+\delta_a$, so both cancel.

For axial strain with two active gauges ($N = 2$), an axial tensile force $F$ puts the top and bottom surfaces under the same strain $+\varepsilon_a$. In adjacent arms these signals would cancel, so the two active gauges go in diagonally opposite arms, $R_1 = R_4 = R_G + \Delta R_a$, with fixed resistors $R_2 = R_3 = R_G$:

$$
V_{\text{out}} = \frac{E}{4}\big[(+\delta_a + \delta_T) - 0 - 0 + (+\delta_a + \delta_T)\big] = \frac{2 E G \varepsilon_a}{4} + \frac{E}{2}\delta_T = \frac{E G \varepsilon_a}{2} + \frac{E}{2}\delta_T.
$$

Parasitic bending stretches the top by $+\varepsilon_b$ and compresses the bottom by $-\varepsilon_b$, and in opposite arms these sum to $+\delta_b + (-\delta_b) = 0$.

> [!warning] Opposite-arm axial gauges are not temperature compensated
> With fixed resistors in $R_2$ and $R_3$, away from the structure, the thermal shifts $+\delta_T$ of the two active gauges add instead of cancelling, which leaves the $\tfrac{E}{2}\delta_T$ term in the output above.

For temperature-compensated axial strain with two active and two dummy gauges ($N = 2$), the fixed resistors $R_2, R_3$ are replaced by two **dummy gauges** on an unstressed block of the same host metal (or a transverse or unloaded region), in thermal contact with the beam so that they see the same $\delta_T$ but no mechanical strain ($\varepsilon_{\text{dummy}} = 0$):

$$
V_{\text{out}} = \frac{E}{4}\big[(+\delta_a + \delta_T) - (\delta_T) - (\delta_T) + (+\delta_a + \delta_T)\big] = \frac{2 E G \varepsilon_a}{4} = \frac{E G \varepsilon_a}{2}.
$$

The dummy gauges add nothing to $N$, and bending still cancels.

For shaft torque with a full bridge ($N = 4$), pure torque $T$ on a cylindrical shaft produces principal tensile and compressive strains $+\varepsilon_t$ and $-\varepsilon_t$ along $+45^\circ$ and $-45^\circ$ helices to the shaft axis. Four active gauges are bonded at $\pm 45^\circ$, with the two $+45^\circ$ tensile gauges in opposite arms $R_1, R_4$ and the two $-45^\circ$ compressive gauges in $R_2, R_3$. This gives $N = 4$, full temperature compensation, and cancellation of both bending and axial strain.

| Layout | Active gauges $N$ | Signal | Temperature compensated | Rejects |
| :--- | :---: | :--- | :---: | :--- |
| Cantilever bending, half bridge | 2 | $\times 2$ | Yes | Axial strain |
| Cantilever bending, full bridge | 4 | $\times 4$ | Yes | Axial strain |
| Axial, two active gauges in opposite arms | 2 | $\times 2$ | No | Bending strain |
| Axial, two active plus two dummy gauges | 2 | $\times 2$ | Yes | Bending strain |
| Shaft torque, full bridge at $\pm 45^\circ$ | 4 | $\times 4$ | Yes | Bending and axial strain |

### Load cells and the differential amplifier

A **load cell** is a precision-machined metal block, often with binocular cut-outs that concentrate bending strain at four thin webs where four foil gauges are bonded as a full bridge, calibrated so that the bridge output is proportional to the applied force $F$. Even a full-bridge output $V_{\text{out}} = V_2 - V_1 = EG\varepsilon$ is only a few millivolts, so the midpoints $V_1$ and $V_2$ (with the zero-trim network $R_b, R_i$) feed an op-amp **differential amplifier** ([[FEEG1004 B4 - Operational Amplifiers]]) with matched input resistors $R_{\text{in}}$ and feedback resistors $R_f$:

$$
V_{\text{amp}} = \frac{R_f}{R_{\text{in}}}(V_2 - V_1) = \frac{R_f}{R_{\text{in}}}\left(\frac{N E G \varepsilon}{4}\right).
$$

## 3. Pressure, flow and airspeed sensors

### Diaphragm pressure transducers

Fluid pressure $p = F/A\ [\text{Pa}]$ is measured by letting the fluid deflect a mechanical **force collector**, most often a clamped circular elastic **diaphragm** (or a bellows or piston), and sensing the resulting strain or displacement. The deflection can be sensed by capacitance, inductance (LVDT, Hall effect, eddy currents), piezoelectric crystals or optical fibres, but the usual industrial and aerospace pressure sensor bonds four resistive strain gauges onto the diaphragm, or diffuses four piezoresistive silicon gauges into a **MEMS** chip, and wires them as a full Wheatstone bridge.

When positive pressure acts on the left face, the centre of the diaphragm bulges outwards in tension, stretching gauges $R_1$ and $R_4$ near the centre so that they increase by $+\Delta R$. The region near the clamped rim bends in radial compression, so gauges $R_2$ and $R_3$ near the rim decrease by $-\Delta R$. With the central gauges in one pair of opposite arms and the rim gauges in the other, the diaphragm forms an $N = 4$ full bridge with $\times 4$ sensitivity and temperature compensation. If the pressure difference reverses, the centre goes into compression and the rim into tension, and $V_{\text{out}}$ changes sign.

The reference pressure on the back face of the diaphragm sets what the sensor reads:

| Mode | Back face of the diaphragm | Reading | Typical use |
| :--- | :--- | :--- | :--- |
| Absolute | Hermetically sealed cavity under high vacuum, $p_{\text{ref}} = 0\ \text{Pa}$ | Pressure relative to vacuum | Barometric altimeters, manifold absolute pressure |
| Gauge | Vented to ambient atmosphere, $p_{\text{ref}} = p_{\text{atm}}$ | $p_{\text{gauge}} = p - p_{\text{atm}}$ | Tyre or hydraulic-line pressure |
| Differential | Second fluid port, pressures $p_1$ and $p_2$ on the two faces | $\Delta p = p_1 - p_2$ | Venturi and Pitot-static sensors (next section) |

### Venturi meter and Pitot-static probe

A differential pressure transducer combined with Bernoulli's equation for steady, incompressible, inviscid flow along a horizontal streamline,

$$
p + \tfrac{1}{2}\rho v^2 = \text{constant},
$$

where $\rho$ is the fluid density in $\text{kg m}^{-3}$ and $v$ the flow speed in $\text{m s}^{-1}$, becomes a velocity or volumetric flow meter.

A **Venturi meter** is a pipe of upstream cross-sectional area $A_a$ that narrows smoothly to a throat of smaller area $A_b < A_a$. For an incompressible fluid, continuity makes the volumetric flow rate $Q\ [\text{m}^3\text{ s}^{-1}]$ the same at both stations, $Q = A_a v_a = A_b v_b$, so the fluid speeds up in the throat, $v_b = (A_a/A_b)v_a > v_a$. Bernoulli between the upstream tapping $a$ and the throat tapping $b$ gives

$$
p_a + \frac{1}{2}\rho v_a^2 = p_b + \frac{1}{2}\rho v_b^2,
$$

so the pressure drop is

$$
\Delta p = p_a - p_b = \frac{1}{2}\rho\big(v_b^2 - v_a^2\big).
$$

Written as $p_b - p_a$, the right-hand side is $\frac{1}{2}\rho(v_a^2 - v_b^2) < 0$. Substituting $v_a = (A_b/A_a)v_b$,

$$
\Delta p = \frac{1}{2}\rho v_b^2\left[1 - \left(\frac{A_b}{A_a}\right)^2\right].
$$

Solving for the throat speed, and multiplying by $A_b$ for the volumetric flow rate $Q = A_b v_b$,

$$
v_b = \sqrt{\frac{2\,\Delta p}{\rho\left[1 - (A_b / A_a)^2\right]}}, \qquad Q = A_b\sqrt{\frac{2\,\Delta p}{\rho\left[1 - (A_b / A_a)^2\right]}}.
$$

A **Pitot-static probe**, the standard aircraft airspeed sensor, pairs a forward-facing **Pitot tube** with flush side-wall **static ports**. The side port measures the undisturbed freestream **static pressure** $p_{\text{static}}$. The open forward tip brings the oncoming air of speed $U$ to rest (stagnation, $v = 0$) and measures the **total (stagnation) pressure** $p_{\text{total}}$:

$$
\underbrace{p_{\text{static}}}_{\text{static pressure}} + \underbrace{\frac{1}{2}\rho U^2}_{\text{dynamic pressure}} = \underbrace{p_{\text{total}}}_{\text{total pressure}}.
$$

Connecting the total and static ports to the two sides of a differential strain-gauge diaphragm measures the **dynamic pressure** $\Delta p = p_{\text{total}} - p_{\text{static}} = \frac{1}{2}\rho U^2$ directly. Inverting this gives the airspeed:

$$
U = \sqrt{\frac{2\,\Delta p}{\rho}} = \sqrt{\frac{2(p_{\text{total}} - p_{\text{static}})}{\rho}}.
$$

> [!warning] Low-speed sensitivity of Pitot-static and Venturi sensors
> Dynamic pressure scales with the square of velocity, $\Delta p = \frac{1}{2}\rho U^2$, so its derivative with respect to $U$ shows that the transducer sensitivity vanishes at low airspeed:
> $$\frac{\mathrm{d}(\Delta p)}{\mathrm{d}U} = \rho U \to 0 \quad \text{as } U \to 0$$
> At very low speeds (a hovering helicopter or a slow taxi, for example) $\Delta p$ is only a few pascals, and a small transducer offset causes a large error in the inferred airspeed $U = \sqrt{2\Delta p/\rho}$.

![[ee_e3_pitot_venturi.png|900]]

## Worked examples

### Excitation limit, bridge outputs and amplifier gain

Four matched metallic foil gauges with $R_G = 120.0\ \Omega$ and $G = 2.00$ are bonded to an aluminium cantilever ($E_{\text{Young}} = 70.0\ \text{GPa}$). Each gauge may carry at most $I_{g,\max} = 10.0\ \text{mA}$ to avoid thermal drift. Find (a) the largest DC bridge excitation $E_{\max}$; (b) the surface strain in $\mu\varepsilon$ and the gauge resistance change $\Delta R$ when, at a conservative $E = 2.00\ \text{V}$, the root bending stress reaches $\sigma = 105\ \text{MPa}$; (c) the bridge output for a quarter bridge ($N = 1$, both exact and linearised), a half bridge ($N = 2$) and a full bridge ($N = 4$); (d) the feedback resistance $R_f$ that gives $V_{\text{amp}} = 3.00\ \text{V}$ at $\sigma = 105\ \text{MPa}$ when the full bridge feeds a differential amplifier with $R_{\text{in}} = 1.00\ \text{k}\Omega$.

(a) In an equal-arm bridge ($R_1 = R_2 = R_3 = R_4 = R_G = 120.0\ \Omega$), each vertical leg is two gauges in series ($2R_G = 240.0\ \Omega$) across $E$. Limiting the branch current $I_g = E/(2R_G)$ to $I_{g,\max} = 10.0\ \text{mA} = 0.0100\ \text{A}$ gives

$$
E_{\max} = 2 R_G I_{g,\max} = 2 \times 120.0\ \Omega \times 0.0100\ \text{A} = 2.40\ \text{V}.
$$

This is why a $10\ \text{mA}$ current rating limits bridge excitation to about $2\ \text{V}$.

(b) By Hooke's law, the surface strain at $\sigma = 105\ \text{MPa} = 105 \times 10^6\ \text{Pa}$ on aluminium ($E_{\text{Young}} = 70.0 \times 10^9\ \text{Pa}$) is

$$
\varepsilon = \frac{\sigma}{E_{\text{Young}}} = \frac{105 \times 10^6\ \text{Pa}}{70.0 \times 10^9\ \text{Pa}} = 1.500 \times 10^{-3} = 1500\ \mu\varepsilon.
$$

From $\Delta R/R_G = G\varepsilon$, the resistance change of an active gauge is

$$
\Delta R = R_G G \varepsilon = (120.0\ \Omega)(2.00)(1.500 \times 10^{-3}) = 0.3600\ \Omega.
$$

(c) With $E G \varepsilon = (2.00\ \text{V})(2.00)(1.500 \times 10^{-3}) = 6.000\ \text{mV}$ in the linearised equation $V_{\text{out}} = NEG\varepsilon/4$, the quarter bridge gives, linearised and exact,

$$
\begin{aligned}
V_{\text{out,lin}}(N=1) &= \frac{1 \times 6.000\ \text{mV}}{4} = 1.500\ \text{mV} \\
V_{\text{out,exact}}(N=1) &= E\left(\frac{R_G + \Delta R}{2R_G + \Delta R} - \frac{1}{2}\right) = 2.00\left(\frac{120.36}{240.36} - 0.5\right) = 1.4978\ \text{mV}
\end{aligned}
$$

The linearised value differs from the exact potential-divider result by only $0.15\%$. The half bridge gives $V_{\text{out}}(N=2) = 2 \times 6.000\ \text{mV}/4 = 3.000\ \text{mV}$, and the full bridge $V_{\text{out}}(N=4) = 4 \times 6.000\ \text{mV}/4 = 6.000\ \text{mV}$.

(d) From $V_{\text{amp}} = (R_f/R_{\text{in}})(V_2 - V_1)$ with $V_2 - V_1 = 6.000\ \text{mV}$, $V_{\text{amp}} = 3.00\ \text{V}$ and $R_{\text{in}} = 1.00\ \text{k}\Omega$:

$$
\begin{aligned}
\frac{R_f}{R_{\text{in}}} &= \frac{V_{\text{amp}}}{V_2 - V_1} = \frac{3.00\ \text{V}}{6.000 \times 10^{-3}\ \text{V}} = 500 \\
R_f &= 500\,R_{\text{in}} = 500 \times 1.00\ \text{k}\Omega = 500\ \text{k}\Omega
\end{aligned}
$$

> [!check] Exact full-bridge potential-divider check
> In the bending full bridge ($R_1 = R_4 = R_G + \Delta R = 120.36\ \Omega$ and $R_2 = R_3 = R_G - \Delta R = 119.64\ \Omega$), each vertical leg totals $R_1 + R_2 = R_3 + R_4 = (R_G + \Delta R) + (R_G - \Delta R) = 2R_G = 240.00\ \Omega$. The denominator does not depend on $\Delta R$, so a symmetric full bridge has no bridge non-linearity:
> $$V_2 - V_1 = 2.00\left(\frac{120.36}{240.00} - \frac{119.64}{240.00}\right) = 2.00\,\frac{0.720}{240.00} = 6.0000\ \text{mV}$$
> The exact and linearised results are identical.

### Bridge balance and dummy-gauge compensation

(a) Three candidate bridges have arm resistances $(R_1, R_2)$ on the left divider and $(R_3, R_4)$ on the right divider:

| Bridge | $R_1$ | $R_2$ | $R_3$ | $R_4$ |
| :---: | :---: | :---: | :---: | :---: |
| A | $100\ \Omega$ | $300\ \Omega$ | $120\ \Omega$ | $360\ \Omega$ |
| B | $100\ \Omega$ | $300\ \Omega$ | $360\ \Omega$ | $120\ \Omega$ |
| C | $120\ \Omega$ | $120\ \Omega$ | $120\ \Omega$ | $360\ \Omega$ |

Find which is balanced and the output $V_{\text{out}} = V_2 - V_1$ of each with $E = 4.00\ \text{V}$. (b) A tie-rod carries a pure axial strain $\varepsilon_a = 800\ \mu\varepsilon$, a parasitic bending strain $\pm\varepsilon_b = \pm 300\ \mu\varepsilon$ (top and bottom) and a temperature rise $\Delta T = +20\,^\circ\text{C}$ that gives an apparent thermal strain $\varepsilon_T = +150\ \mu\varepsilon$ in every gauge on the steel. With $E = 4.00\ \text{V}$ and $G = 2.00$, compare the bridge output when the two active axial gauges ($R_1$ on top, $R_4$ on the bottom) are paired with two fixed, temperature-invariant reference resistors $R_2, R_3$ in the instrument box, and with two unstressed dummy gauges $R_2, R_3$ on the same steel at the same temperature.

(a) Bridge A has $R_1/R_2 = 100/300 = 1/3$ and $R_3/R_4 = 120/360 = 1/3$ (each lower resistor is $3\times$ its upper resistor), so it is balanced:

$$
V_1 = 4.00\,\frac{300}{100 + 300} = 3.00\ \text{V}, \qquad V_2 = 4.00\,\frac{360}{120 + 360} = 3.00\ \text{V} \implies V_{\text{out,A}} = 0.00\ \text{V}.
$$

Bridge B has $V_1 = 3.00\ \text{V}$ and $V_2 = 4.00 \times 120/(360 + 120) = 1.00\ \text{V}$, so $V_{\text{out,B}} = 1.00 - 3.00 = -2.00\ \text{V}$ (unbalanced). Bridge C has $V_1 = 4.00 \times 120/240 = 2.00\ \text{V}$ and $V_2 = 4.00 \times 360/480 = 3.00\ \text{V}$, so $V_{\text{out,C}} = 3.00 - 2.00 = +1.00\ \text{V}$ (unbalanced).

(b) In the top gauge $R_1$ the total effective strain is $\varepsilon_1 = +\varepsilon_a + \varepsilon_b + \varepsilon_T = 800 + 300 + 150 = +1250\ \mu\varepsilon$. In the bottom gauge $R_4$ the axial and thermal strains keep their positive sign while the bending strain is compressive: $\varepsilon_4 = +\varepsilon_a - \varepsilon_b + \varepsilon_T = 800 - 300 + 150 = +650\ \mu\varepsilon$.

With fixed resistors in $R_2, R_3$ ($\varepsilon_2 = \varepsilon_3 = 0$),

$$
\begin{aligned}
V_{\text{out}} &= \frac{E G}{4}\big(\varepsilon_1 - \varepsilon_2 - \varepsilon_3 + \varepsilon_4\big) \\
&= \frac{(4.00\ \text{V})(2.00)}{4}\big(1250 - 0 - 0 + 650\big)\times 10^{-6} \\
&= (2.00\ \text{V})(1900 \times 10^{-6}) = 3.800\ \text{mV}.
\end{aligned}
$$

The $\pm 300\ \mu\varepsilon$ bending strain cancels ($+300 - 300 = 0$), but the two $+150\ \mu\varepsilon$ thermal drifts add ($+150 + 150 = +300\ \mu\varepsilon$), inflating the true $1600\ \mu\varepsilon$ axial sum to $1900\ \mu\varepsilon$, an $18.75\%$ thermal error.

With unstressed dummy gauges in $R_2, R_3$ ($\varepsilon_2 = \varepsilon_3 = \varepsilon_T = +150\ \mu\varepsilon$),

$$
\begin{aligned}
V_{\text{out}} &= \frac{(4.00\ \text{V})(2.00)}{4}\big(1250 - 150 - 150 + 650\big)\times 10^{-6} \\
&= (2.00\ \text{V})(1600 \times 10^{-6}) = 3.200\ \text{mV} = \frac{2 E G \varepsilon_a}{4}.
\end{aligned}
$$

Both the $\pm 300\ \mu\varepsilon$ bending strain and the $+150\ \mu\varepsilon$ thermal drift cancel, leaving the $\times 2$ axial signal of $3.200\ \text{mV}$.

> [!check] Component-by-component superposition check
> Splitting $\varepsilon_1 - \varepsilon_2 - \varepsilon_3 + \varepsilon_4$ by physical effect for the dummy-gauge bridge, the axial part gives $\times 2$ enhancement and the other two cancel:
> $$\begin{aligned}\text{axial:}&\quad (+800) - (0) - (0) + (+800) = +1600\ \mu\varepsilon \\ \text{bending:}&\quad (+300) - (0) - (0) + (-300) = 0\ \mu\varepsilon \\ \text{thermal:}&\quad (+150) - (+150) - (+150) + (+150) = 0\ \mu\varepsilon\end{aligned}$$

### Pitot-static sensitivity and Venturi flow rate

(a) An aircraft Pitot-static tube connected to a differential diaphragm pressure sensor flies at sea level ($\rho_{\text{air}} = 1.225\ \text{kg m}^{-3}$). Find the dynamic pressure $\Delta p = p_{\text{total}} - p_{\text{static}}$ and the local sensitivity $\mathrm{d}(\Delta p)/\mathrm{d}U$ at a low taxi or approach speed $U_1 = 10.0\ \text{m s}^{-1}$ and at a cruise speed $U_2 = 80.0\ \text{m s}^{-1}$, and the airspeed error a $+15.0\ \text{Pa}$ transducer zero drift causes at each speed. (b) A horizontal Venturi tube carrying water ($\rho_w = 1000\ \text{kg m}^{-3}$) tapers from an upstream diameter $D_a = 100\ \text{mm}$ to a throat diameter $D_b = 50.0\ \text{mm}$. A differential pressure sensor between $a$ and $b$ reads $\Delta p = p_a - p_b = 15.0\ \text{kPa}$. Find the throat velocity $v_b$, the upstream velocity $v_a$ and the volumetric flow rate $Q$ in $\text{L s}^{-1}$.

(a) Using $\Delta p = \frac{1}{2}\rho_{\text{air}} U^2$ and $\mathrm{d}(\Delta p)/\mathrm{d}U = \rho_{\text{air}} U$ at $U_1 = 10.0\ \text{m s}^{-1}$,

$$
\Delta p_1 = \frac{1}{2}(1.225\ \text{kg m}^{-3})(10.0\ \text{m s}^{-1})^2 = 61.25\ \text{Pa}, \qquad \left.\frac{\mathrm{d}(\Delta p)}{\mathrm{d}U}\right|_{10} = 12.25\ \text{Pa (m s}^{-1})^{-1}.
$$

With the $+15.0\ \text{Pa}$ bias the sensor reads $\Delta p_{\text{meas}} = 61.25 + 15.0 = 76.25\ \text{Pa}$, and the indicated airspeed is

$$
U_{\text{ind},1} = \sqrt{\frac{2(76.25\ \text{Pa})}{1.225\ \text{kg m}^{-3}}} = 11.16\ \text{m s}^{-1} \quad (\text{error } +1.16\ \text{m s}^{-1},\text{ or } +11.6\%).
$$

At $U_2 = 80.0\ \text{m s}^{-1}$,

$$
\Delta p_2 = \frac{1}{2}(1.225\ \text{kg m}^{-3})(80.0\ \text{m s}^{-1})^2 = 3920\ \text{Pa}, \qquad \left.\frac{\mathrm{d}(\Delta p)}{\mathrm{d}U}\right|_{80} = 98.00\ \text{Pa (m s}^{-1})^{-1}.
$$

With the same bias, $\Delta p_{\text{meas}} = 3935\ \text{Pa}$, and the indicated airspeed is

$$
U_{\text{ind},2} = \sqrt{\frac{2(3935\ \text{Pa})}{1.225\ \text{kg m}^{-3}}} = 80.15\ \text{m s}^{-1} \quad (\text{error } +0.15\ \text{m s}^{-1},\text{ or } +0.19\%).
$$

(b) The upstream and throat areas are

$$
\begin{aligned}
A_a &= \frac{\pi D_a^2}{4} = \frac{\pi(0.100\ \text{m})^2}{4} = 7.8540 \times 10^{-3}\ \text{m}^2 \\
A_b &= \frac{\pi D_b^2}{4} = \frac{\pi(0.050\ \text{m})^2}{4} = 1.9635 \times 10^{-3}\ \text{m}^2
\end{aligned}
$$

The area ratio is $A_b/A_a = (D_b/D_a)^2 = (0.050/0.100)^2 = 0.2500$, so $1 - (A_b/A_a)^2 = 1 - 0.0625 = 0.9375 = 15/16$. Substituting $\Delta p = 15\,000\ \text{Pa}$ and $\rho_w = 1000\ \text{kg m}^{-3}$ into the throat-velocity equation,

$$
\begin{aligned}
v_b &= \sqrt{\frac{2\,\Delta p}{\rho_w\big[1 - (A_b / A_a)^2\big]}} \\
&= \sqrt{\frac{2(15\,000\ \text{Pa})}{(1000\ \text{kg m}^{-3})(0.9375)}} = \sqrt{32.00}\ \text{m s}^{-1} = 5.657\ \text{m s}^{-1}.
\end{aligned}
$$

By continuity the upstream speed is $v_a = (A_b/A_a)v_b = 0.2500 \times 5.6569 = 1.414\ \text{m s}^{-1}$, and the volumetric flow rate is

$$
Q = A_b v_b = (1.9635 \times 10^{-3}\ \text{m}^2)(5.6569\ \text{m s}^{-1}) = 1.111 \times 10^{-2}\ \text{m}^3\text{ s}^{-1} = 11.11\ \text{L s}^{-1}.
$$

> [!check] Bernoulli pressure-drop check
> Putting $v_a = \sqrt{2}\ \text{m s}^{-1} = 1.4142\ \text{m s}^{-1}$ and $v_b = 4\sqrt{2}\ \text{m s}^{-1} = 5.6569\ \text{m s}^{-1}$ back into Bernoulli's equation recovers the measured drop:
> $$p_a - p_b = \frac{1}{2}\rho_w\big(v_b^2 - v_a^2\big) = \frac{1}{2}(1000)\big(32.00 - 2.00\big) = 500 \times 30.00 = 15\,000\ \text{Pa} = 15.0\ \text{kPa}$$

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- Concepts: [[Gauge Factor]] · [[Strain Gauge Bridge Configurations]] · [[Wheatstone Bridge and Strain Gauges]] · [[Stagnation Pressure and Pitot Tube]]
- The incompressible Pitot relation $U = \sqrt{2\Delta p/\rho}$ is extended to calibrated, equivalent and true airspeed (CAS, EAS, TAS) and to subsonic and supersonic Mach number measurement in [[Stagnation Pressure and Pitot Tube]], [[Airspeed Measures]], [[Bernoulli Equation]], [[Compressible Pitot Probe]], [[Rayleigh Pitot Formula]], [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]] and [[SESA1016 T10 - Euler and Bernoulli Equations]].
- Multiaxial plane strain is resolved with three-gauge strain rosettes in [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]] and [[Strain Gauge Rosettes]], and measured strain histories feed the fatigue damage models in [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]].
- Six-component wind-tunnel sting balances use full-bridge strain-gauge load cells to separate lift, drag, side force and moments ([[SESA2022 Wind Tunnel Lab Summary]]); instrumentation-amplifier bridge conditioning is analysed in [[Wheatstone Bridge and Strain Gauges]] and [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]].

## Sources

- `02 - Sources/S2 Transducers/S2-W26-31 Transducers 03 - Complete Systems - Lecture Slides.pdf`: stress, strain and Poisson definitions, calculus derivation of $\mathrm{d}R/\mathrm{d}\varepsilon$ (geometric and piezoresistive), gauge factor $G$ for metallic foil and semiconductor gauges, strain-gauge challenges (slide 12: a $10\ \text{mA}$ current rating limits bridge energisation to about $2\ \text{V}$), Wheatstone bridge balance and trimming ($R_p$, $R_i$), $V_{\text{out}} = NEG\varepsilon/4$, temperature compensation and bending, axial and torsional bridge configurations (slides 20–26), differential op-amp conditioning, diaphragm pressure sensors with absolute, gauge and differential references (slide 32), Venturi flow meters and Pitot-static airspeed sensors.
- `02 - Sources/Lectures/FEEG1004 Lecture 3.txt` (ll. 1–564): static and dynamic strain monitoring, composite UAV wing and DIC calibration context, derivation of geometric and piezoresistive strain effects, Vevox Wheatstone bridge balance poll, trimming, cantilever bending (half and full bridges), axial bridges with dummy-gauge temperature compensation, load cells, torque shafts, differential amplifier, diaphragm pressure transducers, Venturi meters and Pitot-static probes.

## Self-study tasks

### Core

- [ ] Starting from $R = \rho\ell/A$ and $A = \pi d^2/4$, differentiate with respect to $\varepsilon$ to separate the piezoresistive and geometric terms, and contrast metallic foil ($G \approx 2$) with semiconductor ($G \approx 100\text{--}120$) gauges (Transducers 03 slides 5–10; Lecture 3 ll. 141–210). → [[#Strain-gauge equation and gauge factor]]; [[#Gauge families and practical limits]]
- [ ] Prove that a Wheatstone bridge balances when $R_1/R_2 = R_3/R_4$, explain why trimming ($R_p$, $R_i$) is needed, and find which candidate bridge in the Vevox poll is balanced (Transducers 03 slides 13–15; Lecture 3 ll. 231–294). → [[#Balance, trimming and the quarter bridge]]; [[#Bridge balance and dummy-gauge compensation]]
- [ ] Using $V_{\text{out}} = NEG\varepsilon/4$, explain how half- and full-bridge cantilever layouts give $\times 2$ and $\times 4$ signals while cancelling axial strain and temperature, and why a two-active-gauge axial bridge needs two dummy gauges for temperature compensation (Transducers 03 slides 16–27; Lecture 3 ll. 295–486). → [[#Four-arm bridge equation and temperature compensation]]; [[#Bending, axial and torsion layouts]]; [[#Excitation limit, bridge outputs and amplifier gain]]; [[#Bridge balance and dummy-gauge compensation]]
- [ ] Explain how four gauges on a diaphragm make an absolute, gauge or differential pressure transducer, and apply Bernoulli's equation to a Venturi meter and a Pitot-static probe (Transducers 03 slides 28–35; Lecture 3 ll. 487–554). → [[#Diaphragm pressure transducers]]; [[#Venturi meter and Pitot-static probe]]; [[#Pitot-static sensitivity and Venturi flow rate]]

### Further practice

- [ ] Repeat the quarter-bridge part of the excitation-limit example ($E = 2.00\ \text{V}$, $\varepsilon = 1500\ \mu\varepsilon$, $R_G = 120.0\ \Omega$) for a doped silicon gauge with $G = 110$, and compare the linearised output $EG\varepsilon/4$ with the exact divider output to find the bridge non-linearity at large $\Delta R/R$; answer: $\Delta R/R = 0.165$, $V_{\text{out,lin}} = 82.50\ \text{mV}$ against $V_{\text{out,exact}} = 76.21\ \text{mV}$, a $7.6\%$ non-linearity error (suggested, not lecturer-set). → [[#Balance, trimming and the quarter bridge]]; [[#Excitation limit, bridge outputs and amplifier gain]]

## Transcript and slide slips

> [!warning] "Pi r squared over 4" for the wire cross-section (Lecture 3, l. 147)
> Where: [[#Strain-gauge equation and gauge factor]]
> Slide 5 gives "$A = \text{cross sectional area } \text{m}^2 = \dfrac{\pi d^2}{4}$", but the audio at l. 147 says "we can calculate the area, obviously, pi r squared over 4", blending $\pi r^2$ (in terms of radius $r$) with $\pi d^2/4$ (in terms of diameter $d = 2r$).

> [!warning] Self-corrected claim about temperature compensation of the two-gauge axial bridge (Lecture 3, ll. 442–446)
> Where: [[#Bending, axial and torsion layouts]]
> Introducing the two-active-gauge axial bridge on slide 23 (active gauges in opposite arms, fixed resistors in the other two), the speaker first says "And in this configuration, we also have the temperature compensation", then corrects it: "No, we don't have temperature compensation... A way of temperature compensating in that regime is to have these two dummy foil-based strain gauges" (slide 24).

> [!warning] Sign convention of the Venturi pressure difference (Transducers 03, slide 34)
> Where: [[#Venturi meter and Pitot-static probe]]
> Slide 34 labels the wide upstream section $a$ ($P_a$) and the narrow throat $b$ ($P_b$), and writes "$P_b - P_a = \frac{1}{2}\rho(v_a^2 - v_b^2)$". This is algebraically consistent with $P_a + \frac{1}{2}\rho v_a^2 = P_b + \frac{1}{2}\rho v_b^2$, but because the fluid accelerates in the throat ($v_b > v_a$), the throat pressure is lower ($P_b < P_a$) and both sides are negative. Writing the positive drop as $\Delta p = P_a - P_b = \frac{1}{2}\rho(v_b^2 - v_a^2) > 0$ avoids taking the square root of a negative number when solving for flow speed.
