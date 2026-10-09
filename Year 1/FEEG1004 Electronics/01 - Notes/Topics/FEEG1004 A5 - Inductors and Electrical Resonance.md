---
title: "FEEG1004 A5 - Inductors and Electrical Resonance"
module: "FEEG1004 Electronics"
type: topic
stream: "Part A: Electrical Fundamentals and DC Circuits"
order: 5
tags: [feeg1004, fundamentals, inductor, inductance, resonance, lc-circuit, ignition]
aliases: ["Lecture 5a-5b", "Inductors", "Electrical resonance", "V = L di/dt"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]", "[[FEEG1004 A4 - Capacitors]]"]
next_topics: ["[[FEEG1004 A6 - Mesh Analysis]]"]
key_concepts: ["[[Inductance]]", "[[RC and RL Transients]]", "[[Resonance]]", "[[Hydraulic Analogy for Circuits]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W05-5abc Inductors and Resonance - Recorded.pdf", "02 - Sources/S1 Fundamentals/S1-W05 Inductors Resonance and Mesh Analysis - Interactive.pdf"]
---

# FEEG1004 A5 - Inductors and Electrical Resonance

> [!abstract] Summary
> An inductor stores energy in the **magnetic field** of its own current.
> - Flux linkage is proportional to current, $N\Phi = LI$ (inductance $L$ in H = Wb/A). With Faraday's law this gives
>
> $$v = L\frac{di}{dt}$$
>
> - Consequences: inductor **current cannot change instantaneously**; at DC steady state an inductor is a **short circuit**; stored energy is $\tfrac{1}{2}LI^2$.
> - Put $L$ with $C$ and energy sloshes between the two stores: electrical **resonance**. The car ignition coil uses exactly this.

## Key Concepts
- [[Inductance]] · [[RC and RL Transients]] · [[Resonance]] · [[Hydraulic Analogy for Circuits]]

---

## 1. Inductance (L5a)
- Current through a coil creates a field. The flux is proportional to the current, $N\Phi = Li$.
- Differentiate and apply Faraday ($v = N\,d\Phi/dt$ in magnitude): $v = L\,di/dt$.
- **Compare inertia**: $F = m\,dv/dt$ ↔ $V = L\,di/dt$. The rate of change of current is proportional to the applied voltage.
- **Hydraulic analogy**: a **heavy water-wheel** in the pipe. Its inertia (the stored magnetic energy) resists changes of flow by producing a pressure.
- Energy: $E = \int vi\,dt = \int Li\,di = \tfrac{1}{2}LI^2$.

> [!example] Quick checks (W5)
> - 4 V across 5 mH: $di/dt = V/L = 4/0.005$ = **800 A/s**.
> - Just after closing a switch on a series R–L: the current is still zero (it cannot jump), so $V_R = 0$ and the **whole supply appears across L**.

## 2. The R–L switch-on transient
![[ee_a5_rl_transient.png|760]]

The lecture example is a 6 V step into series L and R:

| Instant | Current | $V_R = iR$ | $V_L$ |
|---|---|---|---|
| $t = 0^+$ | 0 (cannot jump) | 0 | 6 V (all of it), so $di/dt = 6/L = 3000$ A/s → $L = 2$ mH |
| $t\to\infty$ | $6/R = 60$ mA → $R = 100$ Ω | 6 V | 0 ($di/dt = 0$: a short) |

The curves are exponentials with $\tau = L/R$ = 20 µs ([[RC and RL Transients]]).

**Switching an inductor OFF** is the dangerous case. The current must keep flowing, so $v = L\,di/dt$ becomes as large as needed to force it through whatever path exists, including an arc across the switch. See Tutorial 2 Q5 (60 MV in theory) and the flyback diode in [[FEEG1004 A7 - Thevenin, Superposition and Relays]].

## 3. Electrical resonance (L5b)
- Resonances everywhere: pendulum, mass on a spring, room acoustics, Tacoma Narrows. The amplitude grows when the system is driven near its **natural frequency**.
- In the hydraulic analogy, the **water-wheel** (inductance, kinetic-like store) and the **membrane** (capacitance, potential-like store) swap energy back and forth.
- An ideal LC loop oscillates at

$$
\omega_0 = \frac{1}{\sqrt{LC}}
$$

  This matches $\omega_n = \sqrt{k/m}$ with $L\leftrightarrow m$ and $1/C\leftrightarrow k$ ([[FEEG1002 D6 - Single Degree of Freedom Vibration]]).

> [!example] Car ignition circuit (L5b)
> 1. **Points closed**: current builds in the primary coil to $I = V/R$ = 4 A. The capacitor ("condenser") is shorted and uncharged.
> 2. **Points open**: the inductor current cannot stop. The 4 A charges the capacitor to about **300 V**, then the capacitor drives current back: **resonance**, decaying through resistance.
> 3. The coil is a transformer with many more secondary turns, so the secondary sees **~20 kV** pulses, enough to jump the spark-plug gap.
> - Modern systems replace the points with a transistor for precise timing and controlled spark energy.
>
> ![[ee_a5_ignition_resonance.png|760]]
> *Illustrative values chosen so that $\tfrac{1}{2}LI_0^2 = \tfrac{1}{2}CV_{pk}^2$ for 4 A ↔ 300 V.*

## Year 2 bridge
- A series RLC is $L\ddot q + R\dot q + q/C = v$: the **second-order system** with $\omega_n = 1/\sqrt{LC}$ and $\zeta = \tfrac{R}{2}\sqrt{C/L}$. Its poles and step response are those of [[Damping Ratio and Natural Frequency]] and [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]].
- The same maths as [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] and [[Resonance]].
- AC analysis turns $L$ into the reactance $j\omega L$ and gives the series-resonance dip of $|Z|$ ([[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]).
- **Inductive sensors** and the relay coil model build on $L$ ([[Linear Variable Differential Transformer]], [[Electromechanical Relays]]).

## Links
- Previous: [[FEEG1004 A4 - Capacitors]] · Next: [[FEEG1004 A6 - Mesh Analysis]]
- Worked problems: [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]] (Q4, Q5)

## Sources
- Recorded lecture 5a (inductors) and 5b (electrical resonance), P. Glynne-Jones; Week 5 interactive session.
