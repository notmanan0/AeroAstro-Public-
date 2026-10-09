---
title: "FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 2
tags: [feeg1004, machines, synchronous-generator, alternator, three-phase, star, delta, poles]
aliases: ["Electric Machines 02-03", "Synchronous generator", "Turbo-alternator", "Three-phase", "rpm = 120f/Np"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]"]
next_topics: ["[[FEEG1004 C3 - Transformers and AC Power Transmission]]"]
key_concepts: ["[[Synchronous Speed and Pole Number]]", "[[Motional EMF in Electric Machines]]", "[[Three-Phase Star and Delta Connections]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 03 - Turbo Generators EMF - Lecture Slides.pdf"]
---

# FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems

> [!abstract] Summary
> Most electricity comes from **synchronous generators**: a rotating magnet or electromagnet inside three stator coils set 120° apart.
> - The flux in each coil varies sinusoidally, so each phase produces an AC EMF. The three are 120° apart and **sum to zero**.
> - Speed and frequency are locked: $\mathrm{rpm} = 120f/N_p$.
> - Peak EMF from cutting flux: $E = N\,B\,(2L_{rotor})\,u$ with $u = \omega D/2$.
> - Phases connect in **star** or **delta**. A balanced load needs no neutral current and draws **constant** total power.

## Key Concepts
- [[Synchronous Speed and Pole Number]] · [[Motional EMF in Electric Machines]] · [[Three-Phase Star and Delta Connections]]

---

## 1. Where electricity comes from
- Heat source → heat engine → generator → transformer → grid. Heat comes from gas, coal, nuclear, biomass or solar heat; engines are steam and gas turbines, or diesels for standby sets.
- Large machines are **turbo-alternators** (about 0.7 m diameter and 7 m active length).
- Renewable examples:
  - wind, tidal and marine turbines turn slowly, so they need gearboxes to keep the generator small, plus power electronics to condition variable frequency to the 400 V, 50 Hz grid;
  - Three Gorges: 26 × 700 MW units, 18.2 GW in total (the UK averaged 34.4 GW demand in 2014).

## 2. Principle of operation (Sharkh §3.1)
- The rotor field sweeps past each stator coil. The coil flux goes as $\Phi_m\cos\theta$, so the EMF goes as $\sin\theta$: **AC**.
- **Rotating magnet vs rotating coil**: a rotating coil needs slip rings to reach the terminals and is poorly cooled inside. Only small machines (bicycle dynamos) use it. A stationary armature on the outside is easier to cool and to connect.
- **Stator laminations** stop eddy currents. Large bars use **Roebel** transposition and hollow conductors (skin effect, induced circulating currents).

![[ee_c2_synchronous_generator.png|1000]]

## 3. Speed, poles and frequency
- One N–S pole **pair** passing a coil gives one electrical cycle. A machine with $N_p$ poles gives $N_p/2$ cycles per revolution:

$$
f = \frac{N_p}{2}\cdot\frac{\mathrm{rpm}}{60}\qquad\Longleftrightarrow\qquad \mathrm{rpm} = \frac{120f}{N_p}
$$

![[ee_c2_poles_speed.png|760]]

> [!example] Machines 02–03 question: 50 Hz from a 2-pole steam set and an 80-pole hydro set
> - Steam: $120(50)/2$ = **3000 rpm**.
> - Hydro: $120(50)/80$ = **75 rpm**.
> - Slow prime movers need many poles (large diameter) or a gearbox.

## 4. EMF of a turbo-generator (Sharkh §3.2)
- Flux is hard to measure, so use the motional form $E = NBLu$:
  - the peripheral speed is $u = \omega D/2$;
  - each coil has **two** active sides, so $L = 2L_{rotor}$:

$$
E_{peak} = N\,B\,(2L_{rotor})\frac{\omega D}{2} = N B L_{rotor}\,\omega D
$$

> [!example] 2-pole, 3000 rpm, $D$ = 0.7 m, $L_{rotor}$ = 7 m, $B$ = 0.8 T, 2 turns per phase
> - $f = 3000\times2/120$ = **50 Hz** ✔.
> - $\omega = 3000\times2\pi/60$ = 314 rad/s, so $E_{peak} = 2(0.8)(7)(314)(0.7)$ = **2463 V** and $E_{rms} = 2463/\sqrt2$ = **1742 V**. The Sharkh notes' "2473" is a typo for 2463; the rms value is right.

## 5. Three-phase systems
- Three coils 120° apart give
  - $e_A = E\sin\omega t$;
  - $e_B = E\sin(\omega t - 2\pi/3)$;
  - $e_C = E\sin(\omega t - 4\pi/3)$.
- The phase EMFs sum to zero at every instant.
- **Star (Y)**: one end of each phase is joined at the neutral. **Delta (Δ)**: the phases form a ring. Both work because the EMFs sum to zero, so no current circulates round the delta.
- **Balanced load** ($R_a = R_b = R_c$):
  - $i_N = i_A + i_B + i_C = 0$, so the neutral wire is unnecessary;
  - the total power $p = \sum e_ki_k = 3E_{rms}^2/R$ is **constant** in time.

> [!tip] Homework on the slides: derive $i_N$ and $P$
> $\sum_k\sin(\theta - 2\pi k/3) = 0$, and $\sum_k\sin^2(\theta - 2\pi k/3) = 3/2$ because the $\cos2\theta$ terms cancel. Hence $p = \dfrac{E^2}{R}\cdot\dfrac{3}{2} = 3E_{rms}^2/R$. A single-phase load, by contrast, pulses at $2\omega$ ([[FEEG1004 D4 - AC Power and Power Factor]]).

![[ee_c2_three_phase_power.png|800]]

> [!example] Tutorial 5 Q4: tidal generator (24 poles, 150 rpm, 24 series coils × 10 turns per phase)
> - $f = 24\times150/120$ = **30 Hz**. Peripheral speed $u = (150\times2\pi/60)(0.2)$ = 3.14 m/s.
> - Per coil: $E = 10(0.7)(2\times0.4)(3.14)$ = 17.6 V peak. 24 coils in series give **422 V peak ≈ 299 V rms** per phase (assuming a sinusoidal gap field).
> - Into 5 Ω per phase: $I$ = **59.7 A rms**, $P = 3(298.6)^2/5$ = **53.5 kW**, **pf = 1** (resistive), **neutral current 0** (balanced).
> - Full working: [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]].

## Year 2 bridge
- **Aircraft AC systems** are 115 V, 400 Hz three-phase. At 400 Hz, transformers and generators are much smaller for the same power: the $V = 4.44fN\Phi$ and "volume ∝ torque" arguments ([[FEEG1004 C3 - Transformers and AC Power Transmission]], [[Electric and Magnetic Loading]]). The engine-driven generator needs a constant-speed drive or variable-frequency electronics because $f\propto$ rpm.
- **Turbomachinery**: steam and gas turbines drive these alternators ([[Brayton Cycle]], [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]).
- **Brushless DC motors** in reaction wheels are synchronous machines driven by electronics ([[Reaction Wheels and Momentum Dumping]]).

## Links
- Previous: [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]] · Next: [[FEEG1004 C3 - Transformers and AC Power Transmission]]
- Worked problems: [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]] (Q2, Q4)

## Sources
- Sharkh/Niu machines notes §3.1–3.3; Electric Machines 02–03 slides; Hughes Ch. 9, 31, 34.
