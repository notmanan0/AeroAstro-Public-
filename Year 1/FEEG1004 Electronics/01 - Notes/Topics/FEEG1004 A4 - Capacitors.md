---
title: "FEEG1004 A4 - Capacitors"
module: "FEEG1004 Electronics"
type: topic
stream: "Part A: Electrical Fundamentals and DC Circuits"
order: 4
tags: [feeg1004, fundamentals, capacitor, capacitance, energy-storage, transients]
aliases: ["Lecture 4", "Capacitors", "Q = CV"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A1 - Electrostatics, Potential and Current]]", "[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"]
next_topics: ["[[FEEG1004 A5 - Inductors and Electrical Resonance]]"]
key_concepts: ["[[Capacitance]]", "[[RC and RL Transients]]", "[[Hydraulic Analogy for Circuits]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W04-4 Capacitors - Recorded.pdf", "02 - Sources/S1 Fundamentals/S1-W04 Circuits and Capacitors - Interactive.pdf", "02 - Sources/S1 Fundamentals/S1-W05 Inductors Resonance and Mesh Analysis - Interactive.pdf"]
---

# FEEG1004 A4 - Capacitors

> [!abstract] Summary
> A capacitor stores energy in the **electric field** between two conductors.
> - $Q = CV$ **defines** capacitance [F = C/V]. Differentiating gives the circuit law
>
> $$i = C\frac{dv}{dt}\qquad\Longleftrightarrow\qquad v = \frac{1}{C}\int i\,dt$$
>
> - Consequences:
>   - capacitor voltage **cannot change instantaneously** (that would need infinite current);
>   - at DC steady state the current is zero, so a capacitor is an **open circuit**;
>   - stored energy is $\tfrac{1}{2}CV^2$.

## Key Concepts
- [[Capacitance]] · [[RC and RL Transients]] · [[Hydraulic Analogy for Circuits]]

---

## 1. How a capacitor charges
- Two plates separated by a gap (dielectric). A source pulls electrons off plate A and the circuit carries them to plate B. Electron flow is opposite to conventional current.
- Transfer continues until the field of the separated charge **balances** the source. In steady state $v_C = V_s$.
- Open the switch and the charge stays: the capacitor is **charged**, with plate A positive.
- **Hydraulic analogy**: an **elastic membrane** across the pipe. Water flowing in stretches it and builds a back-pressure, $V = Q/C$ ↔ back-pressure = stored water / compliance.

## 2. Parallel-plate capacitance

$$
C = \frac{\varepsilon A}{d} = \frac{\varepsilon_0\varepsilon_rA}{d}
$$

- Real capacitors minimise $d$ (limited by dielectric **breakdown** voltage) and use high-permittivity materials. That is why capacitors carry a voltage rating.
- Range: pF (ceramic SMD) to farads (supercapacitors) to MVAR grid banks ([[FEEG1004 D4 - AC Power and Power Factor]]).
- The same formula is the **capacitive displacement sensor**: vary $d$, $A$ or $\varepsilon_r$ ([[Capacitive Displacement Sensor]]).

## 3. V–I relation and energy
Differentiate $Q = CV$ with $I = dQ/dt$:

$$
i = C\frac{dv}{dt}
$$

The rate of rise of voltage is proportional to the current flowing in. As charge builds, the voltage opposes further charging.

**Energy**: charge in steps $dQ$ at voltage $V = Q/C$:

$$
E = \int_0^Q\frac{Q'}{C}\,dQ' = \frac{Q^2}{2C} = \tfrac{1}{2}CV^2 = \tfrac{1}{2}QV
$$

## 4. Charging behaviour
![[ee_a4_capacitor_charging.png|900]]

- **From a voltage source through R**: $v_C = V_s(1 - e^{-t/RC})$ and $i = (V_s/R)e^{-t/RC}$.
  - The time constant is $\tau = RC$: 63 % after $\tau$, over 99 % after $5\tau$.
  - Initially the capacitor looks like a **short** ($v_C = 0$); at steady state it looks like an **open circuit** ($i = 0$).
  - The exponential form is derived later in the course ([[RC and RL Transients]]). At this stage you need the **initial value, initial slope and final value**.
- **From a constant current source**: $V = It/C$, a linear ramp with **no steady state**.

> [!example] Lecture 4: 5 µF charged by 1 mA for 5 s
> - $Q = It$ = 5 mC, so $V = Q/C$ = **1000 V**.
> - $E = \tfrac{1}{2}CV^2$ = **2.5 J**.
> - The voltage keeps rising without limit until something breaks down.

> [!example] "Tricky capacitor question" (W5)
> - At steady state no current flows in the capacitor branch, so ignore it. What remains is a potential divider: $V_C = 2.5\times2/(0.5 + 2)$ = 2 V.
> - $Q = CV = 2\ \mu\mathrm F\times2$ V = **4 µC**.

> [!example] Lamp and capacitor with a variable-frequency AC source (W4)
> - The lamp is **brightest at high frequency** (answer C).
> - At low frequency the membrane fills and stops the flow each half-cycle. At high frequency it barely stretches before the flow reverses.
> - This is the reactance $X_C = 1/\omega C$ of [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]].

## Year 2 bridge
- $RC\,\dot v + v = V_s$ is a **first-order system**: time constant $\tau$, pole at $s = -1/\tau$, transfer function $1/(1 + s\tau)$ ([[Transfer Function]], [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]).
- A first-order sensor (thermocouple bead, RC anti-alias filter) is exactly this equation ([[Sensor Dynamic Models]], [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]).
- Solving by Laplace: [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]].
- Smoothing capacitors in power supplies and **battery/supercap storage** on spacecraft use $\tfrac{1}{2}CV^2$ and $I\,\Delta t = C\,\Delta V$ ([[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]], [[SESA2024 08 - Electrical Power Subsystem]]).

## Links
- Previous: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] · Next: [[FEEG1004 A5 - Inductors and Electrical Resonance]]
- Worked problems: [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]] (Q4)

## Sources
- Recorded lecture 4 (capacitors), P. Glynne-Jones; Week 4 and Week 5 interactive sessions.
