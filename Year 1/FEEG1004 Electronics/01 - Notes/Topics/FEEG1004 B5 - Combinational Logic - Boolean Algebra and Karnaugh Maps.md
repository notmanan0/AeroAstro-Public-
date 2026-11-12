---
title: FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps
module: FEEG1004 Electronics
type: topic
stream: 'Part B: Electronics'
order: 5
tags:
- feeg1004
- electronics
- digital-electronics
- combinational-logic
- boolean-algebra
- karnaugh-maps
aliases:
- EL4 combinational logic
- Combinational logic
date: 2026-09-27
status: lectured
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]"
- "[[FEEG1004 B4 - Operational Amplifiers]]"
next_topics:
- "[[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]"
key_concepts:
- "[[Boolean Algebra and De Morgan's Theorems]]"
- "[[Karnaugh Maps]]"
tutorial_sheets:
- "[[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions]]"
sources:
- 02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf
- 02 - Sources/S1 Electronics/S1-W11-EL4 Digital Logic 1 Combinational - Interactive.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 4a.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 4b.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 4c.txt
- 02 - Sources/Tutorial Sheets/Tutorial Sheet 04 - Electronics B - Operational Amplifiers.pdf
coverage: Lecture 4a (ll. 1–236, digital logic levels, combinational gates, truth tables, and sum-of-products extraction), Lecture 4b (ll. 1–138, Boolean algebra laws, De Morgan's theorems, NAND-only conversion, and algebraic circuit simplification), Lecture 4c (ll. 1–154, 2-, 3-, and 4-variable Karnaugh maps, Gray-code ordering, toroidal wrap-around, and grouping rules), W11-EL4 interactive session (Boolean law exceptions and K-map exercises)
---

# FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps

> [!abstract] Summary
> Digital circuits encode information in two voltage bands, logic 1 and logic 0, which makes them highly immune to noise and component drift. In a combinational circuit the output depends only on the present combination of inputs. Any such specification can be written as a truth table, converted to a sum-of-products (SOP) expression, and reduced to a minimal gate circuit either algebraically, with Boolean algebra and De Morgan's theorems, or graphically on a Gray-coded Karnaugh map. De Morgan's theorems then allow the whole circuit to be built from NAND gates alone.

> [!summary]- Exam use: quick path
> - **Use it when:** turning a word specification or a gate diagram into a Boolean expression, simplifying it, or rebuilding it from a single gate type.
> - **Assumptions:** binary, static logic ($A \in \{0, 1\}$) with zero gate propagation delay and voltages outside the indeterminate band (for 5 V TTL, logic $1 > 2.0\ \text{V}$ and logic $0 < 0.8\ \text{V}$).
> - **Method:** 1. Write the truth table ($2^n$ rows in binary counting order) or trace the gate diagram from inputs to output. 2. For every row with $F = 1$, form the minterm (variable plain if its bit is 1, barred if 0) and OR the minterms together. 3. Simplify, either one Boolean law per line or on a K-map with Gray-coded axes ($00, 01, 11, 10$): circle the 1s in rectangular groups of $2^k$ cells, as large and as few as possible, and keep the variables that are constant across each group. 4. For a NAND-only circuit, double-invert the SOP and apply De Morgan so every OR becomes a complemented AND; a NAND with tied inputs is an inverter. 5. Check the result against every input combination.
> - **Common mistakes:** ordering K-map axes in binary counting order ($00, 01, 10, 11$) instead of Gray code; drawing groups of 3 or 6 cells, or grouping diagonally.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions#Q4: Karnaugh-map simplification|Tutorial 4 Q4]]

Analogue op-amp circuits ([[FEEG1004 B4 - Operational Amplifiers]]) compute directly on continuous voltages, but reconfiguring an analogue computer means rewiring resistors and capacitors, and any noise added along a signal path corrupts the result. Digital systems avoid both problems by operating transistors as two-state switches ([[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]) and recognising only two broad voltage bands. In standard **transistor–transistor logic (TTL)**, logic 1 (HIGH or TRUE) is nominally $+5\ \text{V}$, and any input above the high threshold, $V_{\text{in}} > 2.0\ \text{V}$, is read as 1. Logic 0 (LOW or FALSE) is nominally $0\ \text{V}$, and any input below the low threshold, $V_{\text{in}} < 0.8\ \text{V}$, is read as 0.

Because a receiver only has to decide whether a signal is above $2.0\ \text{V}$ or below $0.8\ \text{V}$, hundreds of millivolts of noise can ride on a binary data stream without causing a bit error. Digital circuits fall into two classes. In **combinational logic** the present output depends only on the present inputs. In **sequential logic** ([[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]), internal feedback provides memory, so the output depends on past inputs as well.

## 1. Logic gates, truth tables and sum-of-products expressions

### Switch representation and truth tables

Consider a starter-motor safety interlock in which switch $A$ (driver's door closed) and switch $B$ (seatbelt fastened) are wired in series between a $+5\ \text{V}$ supply and a grounded load resistor, across which $V_{\text{out}}$ is measured. An open switch is binary 0 and a closed switch binary 1; $V_{\text{out}} = 0\ \text{V}$ is $F = 0$ and $V_{\text{out}} = +5\ \text{V}$ is $F = 1$. Current reaches the load, giving $F = 1$, only when switch $A$ AND switch $B$ are both closed ($A = 1$ and $B = 1$).

A **truth table** lists the output $F$ for every combination of the $n$ binary inputs. Each input independently takes two values, so an $n$-input truth table has

$$
N_{\text{rows}} = 2^n
$$

rows: $2^2 = 4$ rows for $A, B$; $2^3 = 8$ for $A, B, C$; $2^4 = 16$ for $A, B, C, D$. The input columns are filled in natural binary counting order from $00\dots 0_2$ to $11\dots 1_2$ so that no combination is missed.

### Standard logic gates

The four basic operations AND, OR, XOR (exclusive-OR) and the single-input buffer each have an inverted partner, drawn with an inversion bubble ($\circ$) on the output and written with an overbar ($\overline{\phantom{A}}$) over the expression: NAND (NOT-AND), NOR (NOT-OR), XNOR (exclusive-NOR) and the inverter (NOT).

![[ee_b5_logic_gates.png|900]]

In **Boolean algebra**, George Boole's nineteenth-century algebra of two-state logic, three primary operators and one derived operator cover all gate expressions. AND, written $A \cdot B$ or $AB$ and read "A and B", gives $F = 1$ only when all inputs are 1; a 3-input AND gate, $F = A \cdot B \cdot C$, is 1 only on row $CBA = 111_2$. OR, written $A + B$ and read "A or B", gives $F = 1$ when one or more inputs are 1; a 3-input OR gate, $F = A + B + C$, is 0 only on row $CBA = 000_2$. NOT, written $\overline{A}$ and read "not A" or "A bar", is a single-input gate whose output is the complement of its input. Its uninverted counterpart, the **buffer** ($F = A$), makes no logical change but restores degraded voltage levels on long resistive lines, so that a logic 1 does not sag towards the $2.0\ \text{V}$ threshold.

XOR, written $A \oplus B$ and read "A ex-or B", is a two-input gate drawn with a double curved input arc. Its output is 1 when exactly one input is 1, that is, when the inputs are not equal ($A \ne B$). The inclusive OR gives $1 + 1 = 1$, whereas XOR gives $1 \oplus 1 = 0$.

The inverted gates reverse these outputs. NAND, $F = \overline{A \cdot B \cdot C}$, is 0 only when all inputs are 1. NOR, $F = \overline{A + B + C}$, is 1 only when all inputs are 0. XNOR, $F = \overline{A \oplus B}$, is 1 when both inputs are equal ($A = B = 0$ or $A = B = 1$), so it acts as an **equivalence** detector.

| Input $C$ | Input $B$ | Input $A$ | AND ($A\cdot B\cdot C$) | NAND ($\overline{A\cdot B\cdot C}$) | OR ($A+B+C$) | NOR ($\overline{A+B+C}$) | 2-input XOR ($A\oplus B$) | 2-input XNOR ($\overline{A\oplus B}$) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| $0$ | $0$ | $0$ | $0$ | $1$ | $0$ | $1$ | $0$ | $1$ |
| $0$ | $0$ | $1$ | $0$ | $1$ | $1$ | $0$ | $1$ | $0$ |
| $0$ | $1$ | $0$ | $0$ | $1$ | $1$ | $0$ | $1$ | $0$ |
| $0$ | $1$ | $1$ | $0$ | $1$ | $1$ | $0$ | $0$ | $1$ |
| $1$ | $0$ | $0$ | $0$ | $1$ | $1$ | $0$ | $0$ | $1$ |
| $1$ | $0$ | $1$ | $0$ | $1$ | $1$ | $0$ | $1$ | $0$ |
| $1$ | $1$ | $0$ | $0$ | $1$ | $1$ | $0$ | $1$ | $0$ |
| $1$ | $1$ | $1$ | $1$ | $0$ | $1$ | $0$ | $0$ | $1$ |

To turn a word specification into a gate expression, identify which state of each sensor variable triggers the output. In a chemical plant alarm (Mills §3.2.2 Example 1), $F = 1$ sounds a siren if the temperature is high ($A = 1$), or the pressure is high ($B = 1$), or the raw-material feed falls below minimum. Sufficient material is $C = 1$, so low material is $C = 0$, that is $\overline{C} = 1$, and the expression is

$$
F = A + B + \overline{C}
$$

$F = 0$ on only one of the eight rows, when temperature is normal ($A = 0$), pressure is normal ($B = 0$) and material is sufficient ($C = 1$), which is row $CBA = 100_2$.

### Sum of products from a truth table

A gate network may mix XOR, NOR and NAND operators, but any Boolean expression can be rewritten in one of two canonical forms. A **sum of products (SOP)** is a logical OR ("sum", $+$) of AND terms ("products", $\cdot$), such as

$$
F = (\overline{A} \cdot B \cdot C) + (A \cdot \overline{B} \cdot C) + (A \cdot B \cdot \overline{C})
$$

A **product of sums (POS)** is a logical AND of OR brackets, such as

$$
F = (A + B + C) \cdot (A + \overline{B} + C) \cdot (\overline{A} + B + \overline{C})
$$

The SOP form is used for both algebraic simplification and Karnaugh mapping. The canonical SOP expression comes from a truth table in three steps:

1. Pick out every row in which $F = 1$.
2. For each of those rows, write an AND product (**minterm**) of all the input variables, plain (e.g. $A$) if the variable is 1 in that row and complemented (e.g. $\overline{A}$) if it is 0. The product is then $1 \cdot 1 \cdot 1 = 1$ on that row and 0 on every other row.
3. Join the minterms with OR.

For example, three 2-input XOR gates form $F = (A \oplus B) \oplus (B \oplus C)$ (Mills §3.2.2 Example 2). With intermediate columns for $A \oplus B$ and $B \oplus C$, the truth table is:

| $C$ | $B$ | $A$ | $A \oplus B$ | $B \oplus C$ | $F = (A \oplus B) \oplus (B \oplus C)$ | Minterm (for $F = 1$ rows) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| $0$ | $0$ | $0$ | $0$ | $0$ | $0$ | — |
| $0$ | $0$ | $1$ | $1$ | $0$ | $1$ | $A \cdot \overline{B} \cdot \overline{C}$ |
| $0$ | $1$ | $0$ | $1$ | $1$ | $0$ | — |
| $0$ | $1$ | $1$ | $0$ | $1$ | $1$ | $A \cdot B \cdot \overline{C}$ |
| $1$ | $0$ | $0$ | $0$ | $1$ | $1$ | $\overline{A} \cdot \overline{B} \cdot C$ |
| $1$ | $0$ | $1$ | $1$ | $1$ | $0$ | — |
| $1$ | $1$ | $0$ | $1$ | $0$ | $1$ | $\overline{A} \cdot B \cdot C$ |
| $1$ | $1$ | $1$ | $0$ | $0$ | $0$ | — |

Collecting the four rows with $F = 1$ gives

$$
F = (A \cdot \overline{B} \cdot \overline{C}) + (A \cdot B \cdot \overline{C}) + (\overline{A} \cdot \overline{B} \cdot C) + (\overline{A} \cdot B \cdot C)
$$

so the circuit can be built from NOT, AND and OR gates alone if no XOR chips are available.

## 2. Laws of Boolean algebra and De Morgan's theorems

### Table of Boolean identities

Every law of Boolean algebra is an equivalence between two two-state functions, and can be proved by comparing their truth-table columns over all $2^n$ input combinations.

| Rule number and name | OR form | AND form | Single-variable or composite form |
| :--- | :---: | :---: | :---: |
| (1) Logical inverse | — | — | $\overline{0} = 1, \quad \overline{1} = 0$ |
| (2) Involution (double negation) | — | — | $\overline{\overline{A}} = A$ |
| (3) and (4) Dominance (annulment) | $A + 1 = 1$ | $A \cdot 0 = 0$ | — |
| (5) and (6) Identity | $A + 0 = A$ | $A \cdot 1 = A$ | — |
| (7) and (8) Idempotence | $A + A = A$ | $A \cdot A = A$ | — |
| (9) and (10) Complementarity | $A + \overline{A} = 1$ | $A \cdot \overline{A} = 0$ | — |
| (11) and (12) Commutativity | $A + B = B + A$ | $A \cdot B = B \cdot A$ | — |
| (13) and (14) Associativity | $(A + B) + C = A + (B + C)$ | $(A \cdot B) \cdot C = A \cdot (B \cdot C)$ | — |
| (15) and (16) Distributivity | $A + (B \cdot C) = (A + B) \cdot (A + C)$ | $A \cdot (B + C) = (A \cdot B) + (A \cdot C)$ | — |
| (17) and (18) Absorption | $A + (A \cdot B) = A$ | $A \cdot (A + B) = A$ | — |
| (19) and (20) De Morgan's theorems | $\overline{A + B} = \overline{A} \cdot \overline{B}$ | $\overline{A \cdot B} = \overline{A} + \overline{B}$ | — |
| (21) Exclusive-OR definition | — | — | $A \oplus B = (A \cdot \overline{B}) + (\overline{A} \cdot B)$ |

> [!tip] Rules that differ from ordinary algebra
> Reading AND ($\cdot$) as multiplication and OR ($+$) as addition, identity ($A+0=A$, $A\cdot 1=A$), AND-dominance ($A\cdot 0=0$), commutativity, associativity and AND-distributivity ($A(B+C) = AB + AC$) all look like ordinary algebra. The rules that break ordinary arithmetic are the easiest to overlook in an exam. OR-dominance (3), $A + 1 = 1$ (since $1 + 1 = 1$ in logic), gives absorption (17) directly:
> $$A + (A \cdot B) = (A \cdot 1) + (A \cdot B) = A \cdot (1 + B) = A \cdot 1 = A$$
> Idempotence (7, 8), $A + A = A$ and $A \cdot A = A$, means Boolean algebra has no coefficients like $2A$ or powers like $A^2$. OR-distributivity (15), $A + (B \cdot C) = (A + B) \cdot (A + C)$, has no arithmetic counterpart; expanding the right-hand side with AND-distributivity shows why it holds:
> $$(A + B)\cdot(A + C) = A\cdot A + A\cdot C + B\cdot A + B\cdot C = A + A\cdot C + A\cdot B + B\cdot C = A\cdot(1 + C + B) + B\cdot C = A + (B \cdot C)$$

### De Morgan's theorems

Rules (19) and (20), **De Morgan's theorems**, convert a NOR into an AND with inverted inputs, and a NAND into an OR with inverted inputs:

$$
\begin{aligned}
\overline{A + B} &= \overline{A} \cdot \overline{B} \\[4pt]
\overline{A \cdot B} &= \overline{A} + \overline{B}
\end{aligned}
$$

Both extend to any number of variables ($\overline{A + B + C} = \overline{A} \cdot \overline{B} \cdot \overline{C}$ and $\overline{A \cdot B \cdot C} = \overline{A} + \overline{B} + \overline{C}$). The mnemonic is "break the line and change the sign": splitting an overbar between two sub-expressions flips the operator under the break from $+$ to $\cdot$, or from $\cdot$ to $+$.

A four-row truth table proves the NAND form $\overline{A \cdot B} = \overline{A} + \overline{B}$:

| $B$ | $A$ | $A \cdot B$ | $\text{LHS} = \overline{A \cdot B}$ | $\overline{A}$ | $\overline{B}$ | $\text{RHS} = \overline{A} + \overline{B}$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| $0$ | $0$ | $0$ | $\mathbf{1}$ | $1$ | $1$ | $\mathbf{1}$ |
| $0$ | $1$ | $0$ | $\mathbf{1}$ | $0$ | $1$ | $\mathbf{1}$ |
| $1$ | $0$ | $0$ | $\mathbf{1}$ | $1$ | $0$ | $\mathbf{1}$ |
| $1$ | $1$ | $1$ | $\mathbf{0}$ | $0$ | $0$ | $\mathbf{0}$ |

The fourth and seventh columns agree for every input pair, so the two expressions are logically identical. Applied in reverse to $F = (A \cdot B) + (C \cdot D)$, after double-negating each term by involution ($\overline{\overline{X}} = X$), the theorem gives

$$
\begin{aligned}
F &= (A \cdot B) + (C \cdot D) && \text{(given SOP expression)} \\[4pt]
&= \overline{\overline{A \cdot B}} + \overline{\overline{C \cdot D}} && \text{(involution: } X = \overline{\overline{X}}\text{)} \\[4pt]
&= \overline{(\overline{A \cdot B}) \cdot (\overline{C \cdot D})} && \text{(De Morgan's theorem: } \overline{X} + \overline{Y} = \overline{X \cdot Y}\text{)}
\end{aligned}
$$

Instead of two separate chips (a quad-AND and a quad-OR), $F = \overline{(\overline{A \cdot B}) \cdot (\overline{C \cdot D})}$ can be built from three 2-input NAND gates in a single quad-NAND package.

### Algebraic simplification, one law per line

Simplifying a multi-term expression without skipping steps means naming the law used on each line. The four-minterm SOP for $F = (A \oplus B) \oplus (B \oplus C)$ from [[#Sum of products from a truth table]] reduces as follows (Mills §3.2.4 Example 3):

$$
\begin{aligned}
F &= (A \cdot \overline{B} \cdot \overline{C}) + (A \cdot B \cdot \overline{C}) + (\overline{A} \cdot \overline{B} \cdot C) + (\overline{A} \cdot B \cdot C) && \text{(SOP from truth table)} \\[4pt]
&= (A \cdot \overline{C} \cdot \overline{B}) + (A \cdot \overline{C} \cdot B) + (\overline{A} \cdot C \cdot \overline{B}) + (\overline{A} \cdot C \cdot B) && \text{(commutativity: } X \cdot Y = Y \cdot X\text{)} \\[4pt]
&= A \cdot \overline{C} \cdot (\overline{B} + B) + \overline{A} \cdot C \cdot (\overline{B} + B) && \text{(AND-distributivity: factor out } A\cdot\overline{C}\text{ and }\overline{A}\cdot C\text{)} \\[4pt]
&= A \cdot \overline{C} \cdot (1) + \overline{A} \cdot C \cdot (1) && \text{(complementarity: } \overline{B} + B = 1\text{)} \\[4pt]
&= (A \cdot \overline{C}) + (\overline{A} \cdot C) && \text{(AND-identity: } X \cdot 1 = X\text{)} \\[4pt]
&= A \oplus C && \text{(definition of XOR)}
\end{aligned}
$$

The variable $B$ cancels completely, consistent with $A \oplus (B \oplus B) \oplus C = A \oplus 0 \oplus C = A \oplus C$.

## 3. Karnaugh maps

Algebraic manipulation becomes long and error-prone with three or four variables, when it is not obvious which law to apply next. A **Karnaugh map** (K-map) rearranges the $2^n$ rows of a truth table into a grid in which terms that can be combined by $X \cdot (Y + \overline{Y}) = X$ sit in adjacent squares.

![[ee_b5_karnaugh_maps.png|900]]

### Gray-code axes and wrap-around

Panels (a)–(c) show 2-variable ($2 \times 2 = 4$ cells), 3-variable ($2 \times 4 = 8$ cells) and 4-variable ($4 \times 4 = 16$ cells) maps. On any axis that carries two variables (such as $AB$ across the columns of a 3- or 4-variable map, or $CD$ down the rows of a 4-variable map), the four bit-pairs are ordered in **Gray code**,

$$
00, \quad 01, \quad 11, \quad 10 \qquad (\text{decimal } 0, 1, 3, 2)
$$

and never in binary counting order ($00, 01, 10, 11$). In binary order, the step from column $01$ to column $10$ flips both $A$ ($0 \to 1$) and $B$ ($1 \to 0$). In Gray code, one step horizontally or vertically changes only one variable.

The opposite edges of the map are also adjacent. The left and right columns ($AB = 00$ and $AB = 10$) differ only in $A$, since $B = 0$ in both, and the top and bottom rows of a 4-variable map ($CD = 00$ and $CD = 10$) differ only in $C$. Joining opposite edges folds the rectangle into a **toroid** (doughnut): stepping off the right edge lands on the left edge, and stepping off the bottom lands on the top.

### Filling and grouping rules

The map is filled from a truth table by placing a 1 in the cell for each row with $F = 1$ and a 0 elsewhere. From an SOP expression, each full minterm (containing all $n$ variables) fills one cell, whereas a product term missing $k$ variables fills a block of $2^k$ cells where its literals hold. On a 3-variable $(AB, C)$ map, for example, the two-literal term $\overline{A}\cdot\overline{C}$ expands by complementarity and distributivity as

$$
\overline{A}\cdot\overline{C} = \overline{A}\cdot\overline{C}\cdot(B + \overline{B}) = (\overline{A}\cdot B\cdot\overline{C}) + (\overline{A}\cdot\overline{B}\cdot\overline{C})
$$

and fills the two cells where $A = 0$ and $C = 0$ ($AB = 00, C = 0$ and $AB = 01, C = 0$). On a 4-variable map, a two-literal term such as $A\cdot B$ fills the four cells of column $AB = 11$, and a single literal such as $C$ fills the eight cells of rows $CD = 11$ and $CD = 10$. A minterm placed twice is just one 1, since $X + X = X$.

Adjacent 1s are then circled in rectangular groups, horizontally or vertically and including edge wrap-around, but never diagonally. Every group must contain a power-of-two number of cells,

$$
2^k \in \{1, 2, 4, 8, 16\}
$$

because factoring out $k$ changing variables through $(X_1 + \overline{X}_1)\cdots(X_k + \overline{X}_k) = 1$ always merges $2^k$ minterms. A group of 3, 5 or 6 cells is therefore invalid.

Each group should be as large as possible, since a group of $2^k$ cells eliminates $k$ variables from its product term, and the 1s should be covered with as few groups as possible, since each group becomes one AND term. Groups may overlap: re-using a 1 that is already circled is the same as duplicating a minterm ($X + X = X$) and is worthwhile whenever it enlarges a group. A group may never contain a 0.

Each group is read off by discarding the variables that change within it (both 0 and 1 appear) and writing the AND of the variables that stay constant, plain if fixed at 1 and barred if fixed at 0. The simplified SOP is the OR of the terms from all groups.

### Why grouping is algebraic factorisation

Mills §3.2.6 Example 5 gives the 3-variable SOP expression:

$$
F = (A \cdot B \cdot C) + (\overline{A} \cdot \overline{B} \cdot \overline{C}) + (A \cdot B \cdot \overline{C}) + (\overline{A} \cdot \overline{C})
$$

Expanding $\overline{A} \cdot \overline{C} = (\overline{A} \cdot \overline{B} \cdot \overline{C}) + (\overline{A} \cdot B \cdot \overline{C})$ and dropping the duplicate $\overline{A} \cdot \overline{B} \cdot \overline{C}$ places four 1s on the map:

| $C \setminus AB$ | $00$ | $01$ | $11$ | $10$ |
| :---: | :---: | :---: | :---: | :---: |
| **$0$** | $\mathbf{1}$ | $\mathbf{1}$ | $\mathbf{1}$ | $0$ |
| **$1$** | $0$ | $0$ | $\mathbf{1}$ | $0$ |

Row $C = 0$ has three adjacent 1s, but 3 is not a power of two, so two groups of $2^1 = 2$ cells are used. The horizontal pair at $C = 0$, $AB \in \{00, 01\}$, keeps $A = 0$ and $C = 0$ constant while $B$ changes, which is the factorisation

$$
(\overline{A} \cdot \overline{B} \cdot \overline{C}) + (\overline{A} \cdot B \cdot \overline{C}) = \overline{A} \cdot \overline{C} \cdot (\overline{B} + B) = \overline{A} \cdot \overline{C} \cdot 1 = \overline{A} \cdot \overline{C}
$$

The vertical pair at $AB = 11$, $C \in \{0, 1\}$, keeps $A = 1$ and $B = 1$ constant while $C$ changes:

$$
(A \cdot B \cdot \overline{C}) + (A \cdot B \cdot C) = A \cdot B \cdot (\overline{C} + C) = A \cdot B \cdot 1 = A \cdot B
$$

Together the two groups give the minimal two-term SOP:

$$
F = (\overline{A} \cdot \overline{C}) + (A \cdot B)
$$

In Mills §3.2.6 Example 6, $F = (\overline{A}\cdot\overline{B}\cdot C) + (\overline{A}\cdot B\cdot C) + (A\cdot B\cdot C) + (A\cdot\overline{B}\cdot C)$ fills the whole $C = 1$ row of four cells ($2^2 = 4$). Across that group both $A$ and $B$ take all combinations and drop out, leaving $F = C$.

## 4. Universal gates and logic families

### NAND-only circuits

NAND and NOR are both **universal gates**: any Boolean function, from NOT, AND, OR and XOR to an arbitrary SOP circuit, can be built from NAND gates alone, or from NOR gates alone. Standard logic ICs, such as the TTL 7400 quad 2-input NAND, hold four or six identical gates on one chip. Converting a design to NAND gates only reduces the bill of materials to a single IC type and avoids leaving unused AND, OR and NOT gates spread across several packages.

A simplified SOP expression becomes a NAND-only circuit in three steps:

1. Apply De Morgan's theorem, with involution $\overline{\overline{X}} = X$, to replace every OR with a complemented AND.
2. Place a double overbar ($\overline{\overline{F}} = F$) over the whole expression where this turns the outer OR gate directly into an output NAND gate.
3. Build each single-variable inversion $\overline{X}$ from a 2-input NAND with both inputs tied together, using idempotence:
   $$\overline{X \cdot X} = \overline{X}$$

### Logic families: TTL, CMOS and ECL

At transistor level (Mills §3.4), commercial logic gates come in three main integrated-circuit families, which trade switching speed against power consumption and packing density:

| Logic family | Transistor technology | Principal advantages | Principal disadvantages |
| :--- | :--- | :--- | :--- |
| TTL (transistor–transistor logic) | Bipolar junction transistors (BJTs) | Fast switching, rugged, inexpensive, widely standardised ($5\ \text{V}$ logic) | Relatively high DC power dissipation (milliwatts per gate) |
| CMOS (complementary metal–oxide–semiconductor) | Complementary pairs of n-channel and p-channel MOSFETs | Very low static power consumption; very high transistor density, enabling large-scale and very-large-scale integration (LSI/VLSI) microprocessors and memory | Historically slower switching than ECL, and susceptible to electrostatic discharge if handled carelessly |
| ECL (emitter-coupled logic) | Differential BJT pairs steered without saturating | Fastest switching of the three (no BJT saturation storage delay) | High power consumption and small voltage swing (poor noise immunity) |

## Worked examples

### Four-gate circuit that reduces to a single wire

In the circuit of Mills §3.2.4 Example 4, inputs $A$ and $C$ feed a 2-input OR gate and inputs $B$ and $C$ feed a 2-input NOR gate. The NOR output and $A$ feed a second OR gate, and the two OR outputs are combined in a final AND gate to give $F$. The task is to write the unsimplified expression, reduce it to $F = A$ one law per line, and check all eight input combinations.

Tracing from inputs to output, the top OR gate gives $G_1 = A + C$, the NOR gate gives $G_2 = \overline{B + C}$, the lower OR gate gives $G_3 = A + \overline{B + C}$, and the final AND gate gives

$$
F = (A + C) \cdot \left(A + \overline{B + C}\right)
$$

The simplification, one law per line, is

$$
\begin{aligned}
F &= (A + C) \cdot \left(A + \overline{B + C}\right) && \text{(circuit expression)} \\[4pt]
&= (A \cdot A) + \left(A \cdot \overline{B + C}\right) + (C \cdot A) + \left(C \cdot \overline{B + C}\right) && \text{(AND-distributivity: expand brackets)} \\[4pt]
&= A + \left(A \cdot \overline{B + C}\right) + (A \cdot C) + \left(C \cdot \overline{B + C}\right) && \text{(idempotence: } A \cdot A = A\text{, commutativity: } C \cdot A = A \cdot C\text{)} \\[4pt]
&= (A \cdot 1) + (A \cdot C) + \left(A \cdot \overline{B + C}\right) + \left(C \cdot \overline{B + C}\right) && \text{(AND-identity: } A = A \cdot 1\text{, commutativity of OR)} \\[4pt]
&= A \cdot \left(1 + C + \overline{B + C}\right) + \left(C \cdot \overline{B + C}\right) && \text{(AND-distributivity: factor out } A\text{)} \\[4pt]
&= (A \cdot 1) + \left(C \cdot \overline{B + C}\right) && \text{(OR-dominance: } 1 + X = 1\text{)} \\[4pt]
&= A + \left(C \cdot \overline{B + C}\right) && \text{(AND-identity: } A \cdot 1 = A\text{)} \\[4pt]
&= A + (C \cdot \overline{B} \cdot \overline{C}) && \text{(De Morgan's theorem: } \overline{B + C} = \overline{B} \cdot \overline{C}\text{)} \\[4pt]
&= A + (\overline{B} \cdot C \cdot \overline{C}) && \text{(commutativity and associativity of AND)} \\[4pt]
&= A + (\overline{B} \cdot 0) && \text{(complementarity: } C \cdot \overline{C} = 0\text{)} \\[4pt]
&= A + 0 && \text{(AND-dominance: } \overline{B} \cdot 0 = 0\text{)} \\[4pt]
&= A && \text{(OR-identity: } A + 0 = A\text{)}
\end{aligned}
$$

A shorter path applies OR-distributivity, $A + (X \cdot Y) = (A + X)\cdot(A + Y)$, on the first line: $(A + C)\cdot(A + \overline{B + C}) = A + (C \cdot \overline{B + C})$, which reduces by De Morgan and $C \cdot \overline{C} = 0$ to $A + 0 = A$. Either way, all four gates are redundant and can be replaced by a single wire from $A$ to $F$.

> [!check] Exhaustive check in Python
> Evaluating `f_raw = (A | C) & (A | (1 - (B | C)))` over `itertools.product([0, 1], repeat=3)` gives $F_{\text{raw}} = (0, 0, 0, 0)$ for $(A,B,C) \in \{(0,0,0), (0,0,1), (0,1,0), (0,1,1)\}$ and $(1, 1, 1, 1)$ for $(A,B,C) \in \{(1,0,0), (1,0,1), (1,1,0), (1,1,1)\}$, equal to $A$ on all eight rows (`assert all(((A | C) & (A | (1 - (B | C)))) == A for A, B, C in itertools.product([0, 1], repeat=3))`).

### Gate circuit simplified with De Morgan (Tutorial 4 Q3)

In Tutorial Sheet 4 Q3, inverters on $A$, $B$ and $C$ give $\overline{A}$, $\overline{B}$ and $\overline{C}$. $\overline{A}$ and $\overline{B}$ feed a 2-input NOR gate; $\overline{B}$ and $\overline{C}$ feed a 2-input NAND gate. The NOR output, the NAND output and the uninverted $C$ feed a 3-input AND gate whose output is $F$. Part (a) asks for the unsimplified expression and part (b) for an algebraic proof, one law per line, that $F = A \cdot B \cdot C$.

For part (a), the NOR gate driven by $\overline{A}$ and $\overline{B}$ outputs $\overline{\overline{A} + \overline{B}}$, and the NAND gate driven by $\overline{B}$ and $\overline{C}$ outputs $\overline{\overline{B} \cdot \overline{C}}$. The AND gate combines these with $C$:

$$
F = \left(\overline{\overline{A} + \overline{B}}\right) \cdot \left(\overline{\overline{B} \cdot \overline{C}}\right) \cdot C
$$

For part (b):

$$
\begin{aligned}
F &= \left(\overline{\overline{A} + \overline{B}}\right) \cdot \left(\overline{\overline{B} \cdot \overline{C}}\right) \cdot C && \text{(from circuit diagram)} \\[4pt]
&= \left(\overline{\overline{A}} \cdot \overline{\overline{B}}\right) \cdot \left(\overline{\overline{B} \cdot \overline{C}}\right) \cdot C && \text{(De Morgan's theorem on first bracket: } \overline{X + Y} = \overline{X} \cdot \overline{Y}\text{)} \\[4pt]
&= (A \cdot B) \cdot \left(\overline{\overline{B} \cdot \overline{C}}\right) \cdot C && \text{(involution: } \overline{\overline{A}} = A,\ \overline{\overline{B}} = B\text{)} \\[4pt]
&= (A \cdot B) \cdot \left(\overline{\overline{B}} + \overline{\overline{C}}\right) \cdot C && \text{(De Morgan's theorem on second bracket: } \overline{X \cdot Y} = \overline{X} + \overline{Y}\text{)} \\[4pt]
&= (A \cdot B) \cdot (B + C) \cdot C && \text{(involution: } \overline{\overline{B}} = B,\ \overline{\overline{C}} = C\text{)} \\[4pt]
&= A \cdot B \cdot ((B \cdot C) + (C \cdot C)) && \text{(AND-distributivity: multiply } (B + C)\text{ by } C\text{)} \\[4pt]
&= A \cdot B \cdot ((B \cdot C) + C) && \text{(idempotence: } C \cdot C = C\text{)} \\[4pt]
&= A \cdot B \cdot C && \text{(absorption: } (B \cdot C) + C = C\text{)}
\end{aligned}
$$

> [!check] Exhaustive check in Python
> Evaluating `f_q3 = (1 - ((1 - A) | (1 - B))) & (1 - ((1 - B) & (1 - C))) & C` over all $(A, B, C) \in \{0, 1\}^3$ gives 0 for the first seven rows, $(0,0,0)$ to $(1,1,0)$, and 1 only for $(1,1,1)$, matching `A & B & C` on all eight rows.

### Four-variable K-map and NAND-only circuit

Part (a) simplifies the SOP expression of Mills §3.2.6 Example 7 on a 4-variable K-map,

$$
F = (A \cdot B) + (\overline{C} \cdot D) + C + (\overline{B} \cdot \overline{C} \cdot D)
$$

and part (b) converts the result to a circuit of NAND gates only (Mills §3.2.6 Example 8).

Each product term can be placed directly on the $4 \times 4$ map without expanding it into minterms:

1. $A \cdot B$ has $A = 1, B = 1$ with $C, D$ free, filling the four cells of column $AB = 11$.
2. $\overline{C} \cdot D$ has $C = 0, D = 1$ with $A, B$ free, filling the four cells of row $CD = 01$.
3. $C$ has $C = 1$ with $A, B, D$ free, filling the eight cells of rows $CD = 11$ and $CD = 10$.
4. $\overline{B} \cdot \overline{C} \cdot D$ occupies $(AB = 00, CD = 01)$ and $(AB = 10, CD = 01)$, which already hold 1s from step 2.

The remaining three cells of row $CD = 00$ are 0:

| $CD \setminus AB$ | $00$ | $01$ | $11$ | $10$ |
| :---: | :---: | :---: | :---: | :---: |
| **$00$** | $0$ | $0$ | $\mathbf{1}$ | $0$ |
| **$01$** | $\mathbf{1}$ | $\mathbf{1}$ | $\mathbf{1}$ | $\mathbf{1}$ |
| **$11$** | $\mathbf{1}$ | $\mathbf{1}$ | $\mathbf{1}$ | $\mathbf{1}$ |
| **$10$** | $\mathbf{1}$ | $\mathbf{1}$ | $\mathbf{1}$ | $\mathbf{1}$ |

The thirteen 1s are covered by three overlapping groups. The bottom two rows ($CD = 11$ and $10$) form a group of $2^3 = 8$ cells in which $A$, $B$ and $D$ vary while $C = 1$, giving the term $C$. The middle two rows ($CD = 01$ and $11$, sharing row $11$ with the first group) form another group of 8 in which $D = 1$ is constant, giving $D$. The remaining 1 at $(AB = 11, CD = 00)$ is covered by the whole column $AB = 11$, a group of $2^2 = 4$ cells rather than a singleton, which eliminates both $C$ and $D$ and gives $A \cdot B$. ORing the three groups:

$$
F = (A \cdot B) + C + D
$$

For part (b), start from $F = (A \cdot B) + C + D$ and apply involution and De Morgan's theorem one step per line:

$$
\begin{aligned}
F &= (A \cdot B) + C + D && \text{(simplified SOP expression)} \\[4pt]
&= \overline{\overline{(A \cdot B) + C + D}} && \text{(involution: add double overbar)} \\[4pt]
&= \overline{\left(\overline{A \cdot B}\right) \cdot \overline{C} \cdot \overline{D}} && \text{(De Morgan's theorem on lower overbar: } \overline{X + Y + Z} = \overline{X} \cdot \overline{Y} \cdot \overline{Z}\text{)} \\[4pt]
&= \overline{\left(\overline{A \cdot B}\right) \cdot \left(\overline{C \cdot C}\right) \cdot \left(\overline{D \cdot D}\right)} && \text{(idempotence: } C = C \cdot C\text{ and } D = D \cdot D\text{ for 2-input NAND inverters)}
\end{aligned}
$$

This maps onto four NAND gates:

1. A 2-input NAND with inputs $A$ and $B$, giving $\overline{A \cdot B}$.
2. A 2-input NAND with both inputs tied to $C$, giving $\overline{C}$.
3. A 2-input NAND with both inputs tied to $D$, giving $\overline{D}$.
4. A 3-input output NAND driven by $\overline{A \cdot B}$, $\overline{C}$ and $\overline{D}$, giving $F$.

> [!check] Exhaustive 16-row check in Python
> Testing the original expression `f_orig = (A & B) | ((1 - C) & D) | C | ((1 - B) & (1 - C) & D)`, the K-map result `f_kmap = (A & B) | C | D` and the NAND network `f_nand = 1 - ((1 - (A & B)) & (1 - (C & C)) & (1 - (D & D)))` over `itertools.product([0, 1], repeat=4)` gives `f_orig == f_kmap == f_nand` on all 16 rows. All three are 0 only on $(0,0,0,0)$, $(0,1,0,0)$ and $(1,0,0,0)$, and 1 on the other 13 rows.

### Three- and four-variable K-maps (Tutorial 4 Q4)

Tutorial Sheet 4 Q4 asks for K-map simplifications of

$$
\begin{aligned}
F_a &= (\overline{A} \cdot B \cdot C) + (A \cdot \overline{B} \cdot \overline{C}) + (A \cdot B \cdot C) + (A \cdot B \cdot \overline{C}), \\[4pt]
F_b &= (A \cdot \overline{B} \cdot C) + (\overline{C} \cdot D) + (A \cdot B \cdot C \cdot \overline{D}) + (B \cdot C \cdot D).
\end{aligned}
$$

For $F_a$, the four minterms land on the $(AB, C)$ map at $\overline{A} \cdot B \cdot C \to (AB = 01, C = 1)$, $A \cdot \overline{B} \cdot \overline{C} \to (AB = 10, C = 0)$, $A \cdot B \cdot C \to (AB = 11, C = 1)$ and $A \cdot B \cdot \overline{C} \to (AB = 11, C = 0)$:

| $C \setminus AB$ | $00$ | $01$ | $11$ | $10$ |
| :---: | :---: | :---: | :---: | :---: |
| **$0$** | $0$ | $0$ | $\mathbf{1}$ | $\mathbf{1}$ |
| **$1$** | $0$ | $\mathbf{1}$ | $\mathbf{1}$ | $0$ |

Two horizontal pairs cover all four 1s. In row $C = 0$, columns $AB \in \{11, 10\}$, $A = 1$ and $C = 0$ stay constant while $B$ changes, giving $A \cdot \overline{C}$. In row $C = 1$, columns $AB \in \{01, 11\}$, $B = 1$ and $C = 1$ stay constant while $A$ changes, giving $B \cdot C$. The vertical pair at $AB = 11$ is already covered by these two groups, so adding $A \cdot B$ would be redundant:

$$
F_a = (A \cdot \overline{C}) + (B \cdot C)
$$

For $F_b$, the terms fill the $(AB, CD)$ map as follows: $A \cdot \overline{B} \cdot C$ ($A=1, B=0, C=1$, $D$ free) fills $(AB = 10, CD = 11)$ and $(AB = 10, CD = 10)$; $\overline{C} \cdot D$ ($C=0, D=1$, $A, B$ free) fills all four cells of row $CD = 01$; $A \cdot B \cdot C \cdot \overline{D}$ fills the single cell $(AB = 11, CD = 10)$; and $B \cdot C \cdot D$ ($B=1, C=1, D=1$, $A$ free) fills $(AB = 01, CD = 11)$ and $(AB = 11, CD = 11)$.

| $CD \setminus AB$ | $00$ | $01$ | $11$ | $10$ |
| :---: | :---: | :---: | :---: | :---: |
| **$00$** | $0$ | $0$ | $0$ | $0$ |
| **$01$** | $\mathbf{1}$ | $\mathbf{1}$ | $\mathbf{1}$ | $\mathbf{1}$ |
| **$11$** | $0$ | $\mathbf{1}$ | $\mathbf{1}$ | $\mathbf{1}$ |
| **$10$** | $0$ | $0$ | $\mathbf{1}$ | $\mathbf{1}$ |

Three groups of four cover all nine 1s. Row $CD = 01$ keeps $C = 0$ and $D = 1$ constant across all four columns, giving $\overline{C} \cdot D$. The $2 \times 2$ square at $AB \in \{11, 10\}$, $CD \in \{11, 10\}$ keeps $A = 1$ and $C = 1$ constant while $B$ and $D$ vary, giving $A \cdot C$. The remaining 1 at $(AB = 01, CD = 11)$ goes into the $2 \times 2$ square at $AB \in \{01, 11\}$, $CD \in \{01, 11\}$, where $B = 1$ and $D = 1$ stay constant while $A$ and $C$ vary, giving $B \cdot D$; grouping only the horizontal pair $(01, 11)$ and $(11, 11)$ would leave the unminimised three-literal term $B \cdot C \cdot D$. The minimal SOP is

$$
F_b = (A \cdot C) + (\overline{C} \cdot D) + (B \cdot D)
$$

> [!check] Exhaustive check in Python
> Running `itertools.product([0, 1], repeat=3)` for $F_a$ and `itertools.product([0, 1], repeat=4)` for $F_b$ confirms that `(A & (1 - C)) | (B & C)` equals $F_a$ on all 8 rows, and `(A & C) | ((1 - C) & D) | (B & D)` equals $F_b$ on all 16 rows.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 B4 - Operational Amplifiers]]
- Next: [[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]
- Concepts: [[Boolean Algebra and De Morgan's Theorems]] · [[Karnaugh Maps]] · [[Transistor as a Switch]]
- Worked problems: [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions]]

## Sources

- J. Mills, *Diodes, Transistors, Op-amps and Digital Electronics* (`S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf`), Section 3, *Digital Electronics*, pp. 65–83 and 92: §3.1 introduction and TTL voltage thresholds (p. 65); §3.2.1 logic gates, truth tables and Boolean expressions (pp. 65–71); §3.2.2 worked examples part A, alarm specification and XOR-to-SOP conversion (pp. 71–73); §3.2.3 Table 3.2.3, rules of Boolean algebra and De Morgan's theorems (pp. 73–74); §3.2.4 worked examples part B, algebraic simplification (pp. 74–76); §3.2.5–3.2.6 Karnaugh maps, Gray-code ordering, wrap-around and worked examples 5–8 including NAND conversion (pp. 76–83); §3.4 logic families TTL, CMOS and ECL (p. 92).
- `S1-W11-EL4 Digital Logic 1 Combinational - Interactive.pdf`: Boolean identity numbering 1–21, comparison with ordinary algebra, and K-map grouping exercises.
- `FEEG1004 Lecture 4a.txt` (ll. 1–236: digital levels, basic and inverted gates, truth tables, chemical plant alarm and SOP extraction); `FEEG1004 Lecture 4b.txt` (ll. 1–138: Boolean laws, De Morgan's truth-table proof, "split the line and change the sign", NAND-only chip motivation and algebraic simplification examples); `FEEG1004 Lecture 4c.txt` (ll. 1–154: 2-, 3- and 4-variable K-maps, the Gray sequence $00, 01, 11, 10$, wrap-around and power-of-two grouping).
- `Tutorial Sheet 04 - Electronics B - Operational Amplifiers.pdf`, Q2, Q3 and Q4.

## Self-study tasks

### Core

- [ ] Prove with truth tables that $(A \cdot \overline{B}) + (\overline{A} \cdot B) = A \oplus B$ and $A \cdot (B + C) = (A \cdot B) + (A \cdot C)$ (Tutorial Sheet 4 Q2(a)–(b)). → [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions#Q2: Truth-table proofs|Tutorial 4 Q2]] · [[#Table of Boolean identities]]
- [ ] Construct the truth table for $F = (A \oplus B) \oplus (B \oplus C)$, extract the four-minterm SOP and simplify it to $F = A \oplus C$ (Mills §3.2.2 Example 2 and §3.2.4 Example 3, pp. 72–75; Lecture 4a, ll. 158–233; Lecture 4b, ll. 81–112). → [[#Sum of products from a truth table]] · [[#Algebraic simplification, one law per line]]
- [ ] Obtain the expression for the NOR–NAND–AND gate circuit and simplify it to $F = A \cdot B \cdot C$ using Boolean algebra only (Tutorial Sheet 4 Q3(a)–(b)). → [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions#Q3: The gate circuit|Tutorial 4 Q3]] · [[#Gate circuit simplified with De Morgan (Tutorial 4 Q3)]]
- [ ] Simplify $F_a = \overline{A}BC + A\overline{B}\,\overline{C} + ABC + AB\overline{C}$ and $F_b = A\overline{B}C + \overline{C}D + ABC\overline{D} + BCD$ with Karnaugh maps (Tutorial Sheet 4 Q4(a)–(b)). → [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions#Q4: Karnaugh-map simplification|Tutorial 4 Q4]] · [[#Three- and four-variable K-maps (Tutorial 4 Q4)]]
- [ ] Simplify $F = AB + \overline{C}D + C + \overline{B}\,\overline{C}D$ on a 4-variable K-map to $F = AB + C + D$, then convert the circuit to NAND gates only (Mills §3.2.6 Examples 7 and 8, pp. 80–83; Lecture 4c, ll. 134–151). → [[#Four-variable K-map and NAND-only circuit]]

### Further practice

- [ ] Derive the expression for the OR–NOR–OR–AND network and reduce it algebraically to $F = A$ (Mills §3.2.4 Example 4, pp. 75–76; Lecture 4b, ll. 113–135). → [[#Four-gate circuit that reduces to a single wire]]
- [ ] Use the hint $A \cdot B = A \cdot B \cdot (C + \overline{C})$ to plot $F = (A \cdot B) + (A \cdot B \cdot C) + (A \cdot B \cdot \overline{C})$ on a 3-variable K-map and show that it reduces to the single vertical pair $F = A \cdot B$ (W11-EL4 interactive, slides 19–20). → [[#Filling and grouping rules]]
- [ ] Starting from $A + (A \cdot B)$, apply AND-identity ($A = A \cdot 1$), AND-distributivity and OR-dominance ($1 + B = 1$) to prove $A + (A \cdot B) = A$; then dualise the steps, using OR-distributivity $A + (A \cdot B) = (A + A)\cdot(A + B)$, to prove $A \cdot (A + B) = A$ (W11-EL4 interactive, slides 7–10). → [[#Table of Boolean identities]]

## Transcript and slide slips

### Transposed variables in the 3-input OR gate commentary

> [!warning] "A equals F or B or C"
> Where: [[#Standard logic gates]]
> In `FEEG1004 Lecture 4a.txt` (l. 85), explaining why seven of the eight rows of the 3-input OR truth table give 1, the transcript reads "because A equals F or B or C". The slide and the equation two lines earlier (l. 83) give the intended relation: $F$ equals $A$ or $B$ or $C$ ($F = A + B + C$).

### "Identity identity" for idempotence in Mills Example 4

> [!warning] $A \cdot A = A$ called the "identity identity"
> Where: [[#Four-gate circuit that reduces to a single wire]]
> On p. 76 of the Mills notes (§3.2.4 Example 4), the step from $(A \cdot A) + (A \cdot C)$ to $A \cdot (1 + C)$ is captioned "Using the identity identity and factoring gives...". Replacing $A \cdot A$ with $A$ is the **idempotence** law (rule 8 in Table 3.2.3), followed by the AND-identity $A = A \cdot 1$ (rule 6) before $A$ is factored out.

### Binary counting order called binary coded decimal

> [!warning] 2-bit truth-table order called "binary coded decimal"
> Where: [[#Gray-code axes and wrap-around]]
> In `FEEG1004 Lecture 4c.txt` (ll. 29–35), the 2-bit sequence $00, 01, 10, 11$ (decimal $0, 1, 2, 3$) used to order truth-table rows is contrasted with the K-map Gray code ($00, 01, 11, 10$) and called a "binary coded decimal (BCD) sequence". Strictly, BCD encodes each decimal digit $0$–$9$ as a 4-bit group ($0000_2$–$1001_2$); the order $00, 01, 10, 11$ (or $000$–$111$) in a truth table is natural binary counting order.
