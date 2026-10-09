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
> The sheet covers mesh matrices, superposition, a Thévenin reduction, capacitor/inductor steady states and transients, and the danger of interrupting an inductor.
> - No answer key is printed. Every result here was **derived independently and checked numerically** (matrix solve for Q1, nodal cross-check for Q2).
> - Circuit topologies were read from high-resolution renders of the sheet.

## Theory Links
- [[FEEG1004 A6 - Mesh Analysis]] · [[FEEG1004 A7 - Thevenin, Superposition and Relays]] · [[FEEG1004 A4 - Capacitors]] · [[FEEG1004 A5 - Inductors and Electrical Resonance]] · [[RC and RL Transients]]

---

## Q1: Mesh equations for the four-window network
**Network.**
- Left window: 20 V source and 5 Ω, sharing a 4 Ω with the centre.
- Top window: 6 Ω, sharing a 2 Ω with the centre.
- Centre window: 4 Ω, 2 Ω, a 1 Ω shared with the right window, and a 10 V battery in its bottom wire.
- Right window: 3 Ω and a 15 V source.

**Step 1, loop currents**: $I_1$ (left), $I_2$ (top), $I_3$ (centre) and $I_4$ (right), all clockwise.

**Step 2, KVL per window** (rises positive, $IR$ drops negative):

$$
\begin{aligned}
&20 - 5I_1 - 4(I_1 - I_3) = 0\\
&-6I_2 - 2(I_2 - I_3) = 0\\
&-4(I_3 - I_1) - 2(I_3 - I_2) - 1(I_3 - I_4) - 10 = 0\\
&15 - 3I_4 - 1(I_4 - I_3) = 0
\end{aligned}
$$

**Step 3, matrix form** (check it against the inspection rule: diagonal = total mesh resistance, off-diagonal = −shared):

$$
\begin{pmatrix}9&0&-4&0\\0&8&-2&0\\-4&-2&7&-1\\0&0&-1&4\end{pmatrix}
\begin{pmatrix}I_1\\I_2\\I_3\\I_4\end{pmatrix} = \begin{pmatrix}20\\0\\-10\\15\end{pmatrix}
$$

**Step 4, branch currents from loop currents**:

$$
\begin{pmatrix}i_1\\i_2\\i_3\\i_4\\i_5\\i_6\\i_7\end{pmatrix} =
\begin{pmatrix}1&0&0&0\\0&-1&1&0\\1&0&-1&0\\0&0&-1&0\\0&0&1&-1\\0&1&0&0\\0&0&0&1\end{pmatrix}
\begin{pmatrix}I_1\\I_2\\I_3\\I_4\end{pmatrix}
$$

- The branches are: $i_1$ in 5 Ω, $i_2$ in 2 Ω, $i_3$ in 4 Ω (downwards), $i_4$ through the 10 V battery, $i_5$ in 1 Ω (downwards), $i_6$ in 6 Ω and $i_7$ in 3 Ω.
- The sheet only asks for the equations. Solving them anyway: $\mathbf I$ = (2.484, 0.148, 0.590, 3.898) A.
- That gives $\mathbf i$ = (2.484, 0.443, 1.894, −0.590, −3.307, 0.148, 3.898) A.
- A negative $i_5$ means 3.3 A flows **up** through the 1 Ω.

![[ee_t2_q1_mesh.png|860]]

## Q2: Superposition for $i_a$ (50 Ω) with a current source $I_s$ and a 12 V source behind 200 Ω
- **$I_s$ alone** (12 V shorted): the 200 Ω sits in parallel with the 50 Ω. The current divider gives $i_a' = I_s\times200/250 = 0.8I_s$.
- **12 V alone** ($I_s$ open): the 200 Ω and 50 Ω are in series, so $i_a'' = 12/250$ = 48 mA.
- **Sum**:

$$
i_a = 0.8I_s + 0.048\ \mathrm A
$$

- Nodal check: $I_s + (12 - V)/200 = V/50$ gives $V = 40(I_s + 0.06)$, so $i_a = V/50$ ✔.
- The graph is a straight line of slope 0.8, intercept 48 mA, crossing zero at $I_s$ = −60 mA.

![[ee_t2_q2_superposition.png|700]]

## Q3: Thévenin equivalent at A–B
- **$R_{TH}$**: short $V_1$. The 4 Ω and 12 Ω are then in parallel (3 Ω). Add the series 5 Ω to A. The two 1 Ω resistors between the middle and bottom rails are in parallel (0.5 Ω):
$$R_{TH} = 5 + 3 + 0.5 = 8.5\ \Omega$$
- **$V_{TH}$**:
  - With A–B open, no current flows in the 5 Ω or down to the bottom rail.
  - $V_1$ drives current round the 4 Ω + 12 Ω loop, so the 12 Ω carries $V_1\times12/16$.
  - The middle and bottom rails are at the same potential (no current in the 1 Ω pair).
  - Hence $V_{TH} = 0.75$ V.

![[ee_t2_q3_thevenin.png|760]]

## Q4: Capacitor and inductor steady states and transients
- **(i) V–I relations**: $i = C\,dv/dt$ and $v = L\,di/dt$.
- **(ii) Steady-state $V_{out}$**:
  - (a) Resistor with an open output: no current, so $V_{out}$ = 1 V.
  - (b) 5 Ω then 1 µF to ground: the capacitor is open at DC, so $V_{out}$ = 1 V.
  - (c) 1 µH then 5 Ω to ground: the inductor is a short, so $V_{out}$ = 1 V and $I$ = 0.2 A.
- **(iii) Stored energy**:
  - (b) $\tfrac{1}{2}CV^2 = \tfrac{1}{2}(10^{-6})(1)^2$ = **0.5 µJ**.
  - (c) $\tfrac{1}{2}LI^2 = \tfrac{1}{2}(10^{-6})(0.2)^2$ = **20 nJ**.
- **(iv) Sketches** (initial value, initial slope, final value):

| Case | $V_{out}$ | $I_{supply}$ | $\tau$ |
|---|---|---|---|
| (b) R–C | 0 → 1 V; initial slope $I/C = 0.2/10^{-6}$ V/s | 0.2 A → 0 | $RC$ = 5 µs |
| (c) L–R | 0 → 1 V (it is $iR$) | 0 → 0.2 A; initial slope $V/L = 10^6$ A/s | $L/R$ = 0.2 µs |

The hydraulic analogy: the membrane fills and stops the flow; the heavy wheel slowly spins up.

![[ee_t2_q4_transients.png|760]]

## Q5: Opening the switch on a 5 mH inductor fed from 12 V with 0.2 Ω internal resistance
- **(a)** Before opening, the only resistance in the loop is the 0.2 Ω battery resistance (the inductor is a DC short):
  $$I_0 = 12/0.2 = 60\ \mathrm A$$
  - The inductor current cannot change instantly, so at $t = 0^+$ the 60 A must flow through the only path, the air modelled as 1 MΩ:
  $$V = 60\times10^6 = 60\ \mathrm{MV}$$
  - It decays with $\tau = L/R = 5\ \mathrm{mH}/1\ \mathrm{M\Omega}$ = 5 ns.
- **(b) In practice**:
  - The spark occurs at the **switch contacts** as they separate; the gap is tiny there and the field enormous.
  - Air breaks down at about 3 MV/m and ionises. Its impedance **collapses** from megohms to a few ohms, so the voltage is limited to the arc voltage.
  - The stored $\tfrac{1}{2}LI^2 = \tfrac{1}{2}(0.005)(60)^2$ = 9 J is dumped into the arc, eroding the contacts.
  - This is the ignition-coil principle. It is also why inductive loads need a [[Flyback Diode]].

## Sources
- FEEG1004 Tutorial Sheet 2 (no printed answers; all results derived and verified numerically).
