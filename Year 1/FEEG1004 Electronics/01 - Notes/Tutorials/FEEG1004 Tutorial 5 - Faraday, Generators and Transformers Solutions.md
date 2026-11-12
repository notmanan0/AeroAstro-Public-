---
title: "FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions"
module: "FEEG1004 Electronics"
type: tutorial
stream: "Part C: Electric Machines"
tags: [feeg1004, tutorial-solutions, faraday, synchronous-generator, three-phase, transformer]
sheet: "Question Sheet 5 (Electric Machines 1)"
theory_notes: ["[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]", "[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]", "[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]", "[[FEEG1004 C3 - Transformers and AC Power Transmission]]"]
key_concepts: ["[[Faraday's Law and Lenz's Law]]", "[[Lorentz Force]]", "[[Synchronous Speed and Pole Number]]", "[[Three-Phase Star and Delta Connections]]", "[[Transformer EMF Equation]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Tutorial Sheet 05 - Electric Machines 1 - Faraday, Generators & Transformers.pdf"]
---

# FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions

> [!abstract] Sheet Info
> Faraday graphs, the synchronous generator, the force on a cable, a tidal-turbine generator and transformer design. No answers are printed, so the numerical results were derived and verified numerically. The descriptive answers follow the theory in the A2 and C1–C3 notes.

## Theory Links
- [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]] · [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]] · [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]] · [[FEEG1004 C3 - Transformers and AC Power Transmission]]

---

## Q1: Bar magnet falling at constant speed through a coil

**(i) Flux against time.** The flux is a bell-shaped hump. It starts near zero, rises as the leading pole enters, plateaus while the magnet is inside, falls as the trailing pole leaves and returns to zero. The axes are flux [Wb] against time [s].

**(ii) Voltage against time.** The EMF $v = -N\,d\Phi/dt$ is minus the slope of the flux graph, so it consists of two pulses of opposite sign: the first while the flux rises and the second while it falls. The axes are EMF [V] against time [s].

Point A, the maximum voltage, is where the flux graph is steepest, as each pole passes through the coil. Point B, with the magnet halfway through, is the flux maximum, where $v = 0$.

![[ee_a2_magnet_through_coil.png|760]]

## Q2: Two-pole, three-phase synchronous generator

**(A) Construction and voltages.** The cross-section shows a laminated stator with coil sides A1/A2, B1/B2 and C1/C2 in slots 120° apart, and inside it a rotor carrying a permanent magnet or a DC field winding (N and S). The three phase voltages are sinusoids of equal amplitude, with $e_B$ lagging $e_A$ by 120° and $e_C$ lagging it by 240°.

**(B) Principle and connections.** The rotating field sweeps past each phase coil. The flux linking a coil varies as $\Phi_m\cos\theta$, so Faraday's law gives $e = N\omega\Phi_m\sin\theta$, one electrical cycle per revolution for two poles. The flux and EMF in one phase are therefore 90° apart, with the EMF at its maximum where the flux crosses zero. In star connection the A2, B2 and C2 ends are joined at a neutral; in delta connection A2 joins B1, B2 joins C1 and C2 joins A1. Both connections work because the three EMFs sum to zero at every instant, so no current circulates around a delta and a balanced star needs no neutral current.

![[ee_c2_synchronous_generator.png|1000]]

## Q3: 10 m cable carrying 1 kA DC east–west across a 10⁻⁴ T northward field

The cable is perpendicular to the field, so

$$
F = BIL = 10^{-4}\times1000\times10 = 1\ \mathrm N.
$$

The force is vertical. From $\mathbf F = I\mathbf L\times\mathbf B$ with east × north = up, current flowing east is pushed up and current flowing west is pushed down. The 0.1 Ω resistance does not affect the force; it only sets the voltage drop along the cable.

## Q4: Tidal turbine with a 24-pole, 3-phase PM generator at 150 rpm

Each phase has 24 fully pitched coils of 10 turns in series. The rotor has $D = L = 0.4$ m and $B_{peak} = 0.7$ T, and the machine is star-connected into 5 Ω per phase.

**(i) Frequency.** $f = N_p\,\mathrm{rpm}/120 = 24\times150/120 = 30$ Hz.

**(ii) EMF.** The mechanical speed is $\omega_m = 150\times2\pi/60 = 15.7$ rad/s, so the rotor surface speed is $u = \omega_mD/2 = 3.14$ m/s. Each coil has two sides cutting flux, so $E_{coil} = NB(2L)u = 10(0.7)(0.8)(3.14) = 17.6$ V peak. The 24 coils in series give $E_{peak} = 422$ V, or $E_{rms} \approx 299$ V per phase, assuming a sinusoidal gap-flux distribution.

**(iii) Load.** The phase current is $I_{ph} = 298.6/5 = 59.7$ A rms, and the total power is $P = 3E^2/R = 3(298.6)^2/5 = 53.5$ kW. The load is resistive, so the power factor is 1, and it is balanced, so the neutral current is zero. Winding resistance and inductance are neglected, as the sheet instructs.

![[ee_c2_three_phase_power.png|760]]

## Q5: Single-phase transformer, 70:350 turns, 100 cm² core, 230 V at 50 Hz

**(i) Peak flux density.**

$$\Phi_m = \frac{V}{4.44fN_1} = \frac{230}{4.44(50)(70)} = 14.8\ \mathrm{mWb},\qquad B_m = \frac{0.0148}{0.01} = 1.48\ \mathrm T$$

This is right at the design limit of about 1.5 T.

**(ii) Secondary voltage.** $V_2 = 230\times350/70 = 1150$ V.

**(iii) Primary current.** An ideal transformer has $P_1 = P_2 = 10$ kW, so $I_1 = 10\,000/230 = 43.5$ A. The secondary current is $10\,000/1150 = 8.70$ A, consistent with $I_1/I_2 = N_2/N_1 = 5$.

## Sources
- FEEG1004 Question Sheet 5 (Electric Machines 1); derived and verified numerically.
