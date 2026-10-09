---
title: "FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions"
module: "FEEG1004 Electronics"
type: tutorial
stream: "Part A: Electrical Fundamentals and DC Circuits"
tags: [feeg1004, tutorial-solutions, electrostatics, magnetism, resistors, kvl]
sheet: "Tutorial Sheet 1 - Electrostatics, Magnetism & Resistors"
theory_notes: ["[[FEEG1004 A1 - Electrostatics, Potential and Current]]", "[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]", "[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]", "[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
key_concepts: ["[[Coulomb's Law and Electric Field]]", "[[Ohm's Law and Resistivity]]", "[[Kirchhoff's Current and Voltage Laws]]", "[[Series and Parallel Resistors]]", "[[Faraday's Law and Lenz's Law]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Tutorial Sheet 01 - Electrostatics, Magnetism & Resistors.pdf", "02 - Sources/Tutorial Sheets/Tutorial Sheet 01 - Electrostatics, Magnetism & Resistors - Answers.pdf"]
---

# FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions

> [!abstract] Sheet Info
> Five problems spanning Coulomb's law, a battery Thévenin model, a resistor ladder, series/parallel derivations and a rotating coil.
> - The official answer sheet exists; every numerical answer is reproduced ✔.
> - The recurring trap is applying Ohm's law to the **wrong voltage**: use the voltage *across the resistor*, not the source EMF.

## Theory Links
- [[FEEG1004 A1 - Electrostatics, Potential and Current]] · [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]] · [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] · [[FEEG1004 A7 - Thevenin, Superposition and Relays]]

---

## Q1: Two +1 mC charges at $x = -10$ cm and $x = +10$ cm
**(a) Force on the left charge.**

$$
F = \frac{1}{4\pi(8.85\times10^{-12})}\frac{(10^{-3})(10^{-3})}{0.2^2} = 2.25\times10^5\ \mathrm N\ ✔
$$

The charges repel, so the force is directed **to the left** (away from the other charge).

**(b) Field between the charges.**
- Superpose the two fields at position $x$ (m), taking positive to the right.
- The left charge pushes a positive test charge right; the right charge pushes it left:

$$
E(x) = \frac{1}{4\pi\varepsilon_0}\left[\frac{0.001}{(0.1 + x)^2} - \frac{0.001}{(0.1 - x)^2}\right]\ \mathrm{N/C},\qquad -0.1 < x < 0.1\ ✔
$$

- It is zero at $x = 0$ by symmetry.
- Outside the gap both contributions point the same way, so the expression changes form.

![[ee_a1_two_charge_field.png|700]]

## Q2: Sam's car battery (13 V, nominally 10 mΩ ESR)
- **(i)** At 200 A the terminal voltage is 8 V, so the ESR drops $13 - 8 = 5$ V:
$$R_{ESR} = \frac{5}{200} = 25\ \mathrm{m\Omega}\ ✔$$
  Do not use 13/200: Ohm's law needs the voltage across the resistor.
- **(ii)** Jump lead, 2 m long, 20 mΩ, copper:
$$r = \sqrt{\frac{\rho L}{\pi R}} = \sqrt{\frac{1.678\times10^{-8}\times2}{\pi\times0.02}} = 0.731\ \mathrm{mm}\ \Rightarrow\ d = 1.46\ \mathrm{mm}\ ✔$$
- **(iii) Circuit**: each battery is an ideal source with its ESR; they are joined by two 20 mΩ leads (one in each wire).
- **(iv) Current**:
  - Guess the direction (left to right, from Sam's battery) and apply KVL: $10 - 0.025I - 0.020I - 0.010I - 13 - 0.020I = 0$.
  - This gives $I = (10 - 13)/0.075$ = **−40 A** ✔.
  - The negative sign means 40 A actually flows from the 13 V battery **into** Sam's.
- **(v) Power into Sam's battery**:
  - Charging raises the terminal voltage above the EMF: $V_t = 10 + 40(0.025)$ = 11 V.
  - $P = V_tI$ = **440 W** ✔.
  - Of this, $10\times40$ = 400 W goes into chemical storage and $40^2\times0.025$ = 40 W is heat in the ESR.

![[ee_t1_q2_jump_start.png|760]]

## Q3: Resistor ladder with a 5 V voltmeter reading
Work backwards from the known voltage. Voltages are measured relative to the bottom node.
- The voltmeter reads 5 V across a 5 Ω resistor, so its branch carries $I_1$ = 1 A.
- That current flows through 10 + 5 + 5 = 20 Ω, so the node above the branch sits at $V_x$ = 20 V.
- The ammeter branch (10 Ω) sees the same 20 V, so the **ammeter reads 2 A** ✔.
- KCL: the 2 Ω feed carries $1 + 2 = 3$ A.
- KVL: $V_s = 20 + 3\times2$ = **26 V** ✔.

![[ee_t1_q3_ladder.png|640]]

## Q4: Deriving series and parallel resistance
- **(a) Parallel**: all three resistors share $V$, so $I_k = V/R_k$. KCL gives $I_{tot} = V(1/R_1 + 1/R_2 + 1/R_3)$, and $R_p = V/I_{tot}$:
$$\frac{1}{R_p} = \frac{1}{R_1} + \frac{1}{R_2} + \frac{1}{R_3}\ ✔$$
- **(b) Series**: KCL means the same $I$ flows in all three. KVL gives $V_{tot} = V_1 + V_2 + V_3 = I(R_1 + R_2 + R_3)$, so $R_s = R_1 + R_2 + R_3$ ✔.
- **(c) What was used**:
  - **Ohm's law** for each resistor;
  - **KCL** (the currents sum at a node, or are equal in series);
  - **KVL** (the voltages sum round a loop, or are equal in parallel);
  - the assumption of ideal zero-resistance wires, so nodes are equipotential.

## Q5: 10-turn, 0.1 m² coil rotating at 20 Hz in 2 T
- The coil angle is $\theta = 2\pi(20)t = 40\pi t$. The normal flux density is $B\cos\theta$.
- Flux per turn: $\Phi = BA\cos\theta = 0.2\cos(40\pi t)$ Wb.
- Faraday:

$$
\mathcal E = -N\frac{d\Phi}{dt} = -10\times0.2\times(-40\pi)\sin(40\pi t) = 80\pi\sin(40\pi t)\approx251\sin(40\pi t)\ \mathrm V\ ✔
$$

- The overall sign is ambiguous because the coil's positive sense is not defined.
- This is a single-phase AC generator: 20 Hz output, peak $NBA\omega$ ([[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]).

![[ee_t1_q5_rotating_coil.png|680]]

## Sources
- FEEG1004 Tutorial Sheet 1 and its answer sheet.
