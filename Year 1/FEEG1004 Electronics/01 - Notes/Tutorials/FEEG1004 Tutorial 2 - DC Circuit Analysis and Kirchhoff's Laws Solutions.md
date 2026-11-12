---
title: "FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions"
module: "FEEG1004 Electronics"
type: tutorial
stream: "Part A: Electrical Fundamentals and DC Circuits"
tags: [feeg1004, tutorial-solutions, mesh-analysis, superposition, thevenin, transients, inductors]
sheet: "Tutorial Sheet 2 - Circuit Analysis"
theory_notes: ["[[FEEG1004 A6 - Mesh Analysis]]", "[[FEEG1004 A7 - Thevenin, Superposition and Relays]]", "[[FEEG1004 A4 - Capacitors]]", "[[FEEG1004 A5 - Inductors and Electrical Resonance]]"]
key_concepts: ["[[Mesh Current Method]]", "[[Superposition Theorem (Circuits)]]", "[[Thevenin and Norton Equivalent Circuits]]", "[[RC and RL Transients]]", "[[Inductance]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Tutorial Sheet 02 - DC Circuit Analysis & Kirchhoff's Laws.pdf"]
---

# FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions

> [!abstract] Sheet Info
> Mesh matrices, superposition, a Thévenin reduction, capacitor and inductor steady states and transients, and the danger of interrupting an inductor. No answer key is printed, so every result here was derived independently and checked numerically (a matrix solve for Q1 and a nodal cross-check for Q2). Circuit topologies were read from high-resolution renders of the sheet.

## Theory Links
- [[FEEG1004 A6 - Mesh Analysis]] · [[FEEG1004 A7 - Thevenin, Superposition and Relays]] · [[FEEG1004 A4 - Capacitors]] · [[FEEG1004 A5 - Inductors and Electrical Resonance]] · [[RC and RL Transients]]

---

## Q1: Mesh equations for the four-window network

The network has four windows. The left window holds the 20 V source (+ at top) and a 5 Ω resistor, and shares a 4 Ω resistor with the centre window. The top window holds a 6 Ω resistor and shares a 2 Ω resistor with the centre. The centre window contains the 4 Ω and 2 Ω resistors, a 1 Ω resistor shared with the right window, and a 10 V battery in its bottom wire (+ on the left plate, − on the right plate). The right window holds a 3 Ω resistor and a 15 V source (+ at top, − at bottom).

Assign clockwise loop currents $I_1$ (left), $I_2$ (top), $I_3$ (centre) and $I_4$ (right). In each window's KVL equation, rises are positive and $IR$ drops negative. Clockwise $I_3$ crosses the bottom 10 V battery from right (−) to left (+), a $+10\ \mathrm V$ rise, while clockwise $I_4$ crosses the right-wall 15 V battery from top (+) to bottom (−), a $-15\ \mathrm V$ drop:

$$
\begin{aligned}
&20 - 5I_1 - 4(I_1 - I_3) = 0\\
&-6I_2 - 2(I_2 - I_3) = 0\\
&10 - 4(I_3 - I_1) - 2(I_3 - I_2) - 1(I_3 - I_4) = 0\\
&-15 - 3I_4 - 1(I_4 - I_3) = 0
\end{aligned}
$$

Collecting coefficients gives the matrix form below. It agrees with the inspection rule: each diagonal entry is the total resistance around that mesh, and each off-diagonal entry is minus the resistance shared by the pair.

$$
\begin{pmatrix}9&0&-4&0\\0&8&-2&0\\-4&-2&7&-1\\0&0&-1&4\end{pmatrix}
\begin{pmatrix}I_1\\I_2\\I_3\\I_4\end{pmatrix} = \begin{pmatrix}20\\0\\10\\-15\end{pmatrix}
$$

The branch currents are $i_1$ in 5 Ω, $i_2$ in 2 Ω, $i_3$ in 4 Ω (downwards), $i_4$ through the 10 V battery (rightwards), $i_5$ in 1 Ω (downwards), $i_6$ in 6 Ω and $i_7$ in 3 Ω. In terms of the loop currents,

$$
\begin{pmatrix}i_1\\i_2\\i_3\\i_4\\i_5\\i_6\\i_7\end{pmatrix} =
\begin{pmatrix}1&0&0&0\\0&-1&1&0\\1&0&-1&0\\0&0&-1&0\\0&0&1&-1\\0&1&0&0\\0&0&0&1\end{pmatrix}
\begin{pmatrix}I_1\\I_2\\I_3\\I_4\end{pmatrix}
$$

The sheet asks only for the equations. Solving them gives $\mathbf I = (3.727, 0.846, 3.385, -2.904)$ A and hence $\mathbf i = (3.727, 2.539, 0.342, -3.385, 6.289, 0.846, -2.904)$ A. The negative values, $i_4 = -3.385$ A and $i_7 = -2.904$ A, mean that those currents flow opposite to the drawn branch arrows. (If the 10 V and 15 V cell symbols were read with reversed polarity, $\mathbf V = (20, 0, -10, 15)^{\mathsf T}$ V, giving $\mathbf I = (2.484, 0.148, 0.590, 3.898)^{\mathsf T}$ A and $\mathbf i = (2.484, 0.443, 1.894, -0.590, -3.307, 0.148, 3.898)^{\mathsf T}$ A.)

![[ee_t2_q1_mesh.png|860]]

## Q2: Superposition for ia (50 Ω) with a current source Is and a 12 V source behind 200 Ω

With $I_s$ acting alone (12 V source shorted), the 200 Ω resistor sits in parallel with the 50 Ω, and the current divider gives $i_a' = I_s\times200/250 = 0.8I_s$. With the 12 V source acting alone ($I_s$ open), the 200 Ω and 50 Ω resistors are in series, so $i_a'' = 12/250 = 48$ mA. Adding the two contributions,

$$
i_a = 0.8I_s + 0.048\ \mathrm A.
$$

A nodal check confirms this: $I_s + (12 - V)/200 = V/50$ gives $V = 40(I_s + 0.06)$, and $i_a = V/50$ reproduces the same line. The graph of $i_a$ against $I_s$ is a straight line of slope 0.8 and intercept 48 mA, crossing zero at $I_s = -60$ mA.

![[ee_t2_q2_superposition.png|700]]

## Q3: Thévenin equivalent at A–B

For $R_{TH}$, short $V_1$. The 4 Ω and 12 Ω resistors are then in parallel (3 Ω), the 5 Ω resistor to A adds in series, and the two 1 Ω resistors between the middle and bottom rails are in parallel (0.5 Ω):

$$R_{TH} = 5 + 3 + 0.5 = 8.5\ \Omega.$$

For $V_{TH}$, leave A–B open. No current then flows in the 5 Ω resistor or down to the bottom rail, so the middle and bottom rails are at the same potential. $V_1$ drives current around the 4 Ω + 12 Ω loop, and the 12 Ω resistor carries $V_1\times12/16$ of the source voltage, so $V_{TH} = 0.75$ V.

![[ee_t2_q3_thevenin.png|760]]

## Q4: Capacitor and inductor steady states and transients

**(i) V–I relations.** $i = C\,dv/dt$ for the capacitor and $v = L\,di/dt$ for the inductor.

**(ii) Steady-state output.** In circuit (a), a resistor with an open output carries no current, so $V_{out} = 1$ V. In circuit (b), with 5 Ω then 1 µF to ground, the capacitor is an open circuit at DC, so again $V_{out} = 1$ V. In circuit (c), with 1 µH then 5 Ω to ground, the inductor is a short circuit, so $V_{out} = 1$ V and $I = 0.2$ A.

**(iii) Stored energy.** The capacitor in (b) stores $\tfrac{1}{2}CV^2 = \tfrac{1}{2}(10^{-6})(1)^2 = 0.5$ µJ, and the inductor in (c) stores $\tfrac{1}{2}LI^2 = \tfrac{1}{2}(10^{-6})(0.2)^2 = 20$ nJ.

**(iv) Sketches.** Each sketch needs the initial value, initial slope and final value:

| Case | $V_{out}$ | $I_{supply}$ | $\tau$ |
|---|---|---|---|
| (b) R–C | 0 → 1 V; initial slope $I/C = 0.2/10^{-6}$ V/s | 0.2 A → 0 | $RC$ = 5 µs |
| (c) L–R | 0 → 1 V (it is $iR$) | 0 → 0.2 A; initial slope $V/L = 10^6$ A/s | $L/R$ = 0.2 µs |

In the hydraulic analogy, the capacitor's membrane stretches until it stops the flow, while the inductor's heavy wheel spins up slowly.

![[ee_t2_q4_transients.png|760]]

## Q5: Opening the switch on a 5 mH inductor fed from 12 V with 0.2 Ω internal resistance

**(a) Voltage at switch-off.** Before the switch opens, the inductor is a DC short and the only resistance in the loop is the 0.2 Ω battery resistance, so

$$I_0 = 12/0.2 = 60\ \mathrm A.$$

The inductor current cannot change instantly, so at $t = 0^+$ the 60 A must flow through the only remaining path, the air gap modelled as 1 MΩ:

$$V = 60\times10^6 = 60\ \mathrm{MV}.$$

This voltage decays with $\tau = L/R = 5\ \mathrm{mH}/1\ \mathrm{M\Omega} = 5$ ns.

**(b) In practice.** The spark occurs at the switch contacts as they separate, where the gap is tiny and the field enormous. Air breaks down at about 3 MV/m and ionises, so its impedance falls from megohms to a few ohms and the voltage is limited to the arc voltage. The stored energy $\tfrac{1}{2}LI^2 = \tfrac{1}{2}(0.005)(60)^2 = 9$ J is dumped into the arc and erodes the contacts. The same principle drives an ignition coil, and it is the reason inductive loads need a [[Flyback Diode]].

## Sources
- FEEG1004 Tutorial Sheet 2 (no printed answers; all results derived and verified numerically).
