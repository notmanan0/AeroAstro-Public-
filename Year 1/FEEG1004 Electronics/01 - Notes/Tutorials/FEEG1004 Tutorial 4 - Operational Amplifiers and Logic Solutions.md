---
title: "FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions"
module: "FEEG1004 Electronics"
type: tutorial
stream: "Part B: Electronics"
tags: [feeg1004, tutorial-solutions, op-amp, boolean-algebra, karnaugh-map, t-network]
sheet: "Question sheet 4 - Electronics B"
theory_notes: ["[[FEEG1004 B4 - Operational Amplifiers]]", "[[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]"]
key_concepts: ["[[Op-Amp Golden Rules]]", "[[Standard Op-Amp Configurations]]", "[[Boolean Algebra and De Morgan's Theorems]]", "[[Karnaugh Maps]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Tutorial Sheet 04 - Electronics B - Operational Amplifiers.pdf"]
---

# FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions

> [!abstract] Sheet Info
> Two op-amp problems (a three-stage chain and the T feedback network) and three logic problems (truth-table proofs, a gate circuit and K-maps).
> - No answer key is printed. Q4 results and the Q3 identity were **verified by exhaustive truth tables**.
> - Q5's target formula is given on the sheet and is reproduced ✔.

## Theory Links
- [[FEEG1004 B4 - Operational Amplifiers]] · [[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]] · [[Op-Amp Golden Rules]] · [[Karnaugh Maps]]

---

## Q1: Circuit transfer function of the three-stage chain
Break it into standard blocks (the Mills worked-example method).
- **Stage 1**: a 100 kΩ / 25 kΩ divider feeds a **voltage follower**. GR2 means the follower draws no current, so the divider is unloaded:

$$V_a = V_1\frac{25}{100 + 25} = 0.2V_1$$

- **Stage 2**: a **summing amplifier**, with $V_a$ through 25 kΩ and $V_2$ through 100 kΩ, and 50 kΩ feedback:

$$V_b = -50\left(\frac{V_a}{25} + \frac{V_2}{100}\right) = -(2V_a + 0.5V_2)$$

- **Stage 3**: a **non-inverting** amplifier with 150 kΩ feedback and 50 kΩ to ground, gain $1 + 150/50 = 4$.

$$
V_{out} = 4V_b = -4(0.4V_1 + 0.5V_2) = -1.6\,V_1 - 2\,V_2
$$

![[ee_t4_q1_opamp_chain.png|960]]

## Q2: Truth-table proofs
**(a)** $A\overline B + \overline AB = A\oplus B$:

| A | B | $A\overline B$ | $\overline AB$ | LHS | $A\oplus B$ |
|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 1 | 1 |
| 1 | 0 | 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 | 0 | 0 |

**(b)** $A(B + C) = AB + AC$:

| A | B | C | $B + C$ | LHS | $AB$ | $AC$ | RHS |
|---|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 | 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 | 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |

The columns agree line by line ✔.

## Q3: The gate circuit
**(a)** Label the gate outputs:
- A and B feed a **NAND**: $\overline{AB}$.
- B and C feed an **XOR**: $B\oplus C$.
- Both feed a **NOR**:

$$F = \overline{\overline{AB} + (B\oplus C)}$$

**(b)** Algebra only:
1. De Morgan: $F = \overline{\overline{AB}}\cdot\overline{B\oplus C} = AB\cdot\overline{B\oplus C}$.
2. XNOR: $\overline{B\oplus C} = BC + \overline B\,\overline C$.
3. Multiply out: $F = AB(BC + \overline B\,\overline C) = AB\cdot BC + AB\overline B\,\overline C$.
4. Idempotence ($BB = B$) and complementarity ($B\overline B = 0$): $F = ABC + 0 = A\cdot B\cdot C$ ✔.

![[ee_t4_q3_gate_circuit.png|760]]

## Q4: Karnaugh-map simplification
**(a)** $F = \overline A\,\overline B\,\overline C + \overline A\,\overline BC + A\overline B\,\overline C + A\overline BC$
- Every term has $\overline B$: the 1s fill the $AB$ = 00 and 10 columns, which are adjacent by **wrap-around**.
- One group of four gives $F = \overline B$.

**(b)** $F = \overline A\,\overline B\,\overline C + \overline C\,\overline D + A\overline B\,\overline CD + B\overline CD$
- Place each term: $\overline C\,\overline D$ fills row $CD$ = 00; $B\overline CD$ fills the $B = 1$ cells of row 01; the other two fill the remaining cells of rows 00 and 01.
- The whole top half ($C = 0$) is 1s and the bottom half is 0s. One group of eight gives $F = \overline C$.

![[ee_b5_karnaugh_maps.png|960]]

## Q5: The T feedback network
**Setup**: $R_1$ from $V_{in}$ to $V_-$; a T from $V_-$ through $R_2$ to node $V_x$, then $R_3$ from $V_x$ to ground and $R_4$ from $V_x$ to $V_{out}$.

**Step 1 (GR1)**: $V_+ = 0$, so $V_1 = V_- = 0$ (virtual earth).

**Step 2 (Ohm)**: $I_1 = V_{in}/R_1$.

**Step 3 (GR2)**: no current enters the op-amp, so $I_2 = I_1$, flowing $V_-\to V_x$ through $R_2$:

$$V_x = 0 - I_1R_2 = -\frac{R_2}{R_1}V_{in}$$

**Step 4**: $I_3$ from ground up to $V_x$ through $R_3$ is $(0 - V_x)/R_3 = \dfrac{R_2}{R_1R_3}V_{in}$.

**Step 5 (KCL at $V_x$)**: $I_4 = I_2 + I_3$. Then $V_{out} = V_x - I_4R_4$:

$$
V_{out} = -\frac{R_2}{R_1}V_{in} - R_4\left(\frac{V_{in}}{R_1} + \frac{R_2V_{in}}{R_1R_3}\right)
\ \Rightarrow\
\frac{V_{out}}{V_{in}} = -\frac{R_2}{R_1}\left(1 + \frac{R_4}{R_2} + \frac{R_4}{R_3}\right)\ ✔
$$

**Why it helps**: the input resistance is still $R_1$, but a large gain now comes from modest resistors.
- With $R_1 = R_2 = R_4$ = 100 kΩ and $R_3$ = 1 kΩ, the gain is −102.
- A plain inverting amplifier would need a 10 MΩ feedback resistor for the same gain.

![[ee_t4_q5_t_network.png|720]]

## Sources
- FEEG1004 Question sheet 4 (Electronics B); circuits read from high-resolution renders; logic results verified exhaustively.
