---
title: "FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps"
module: "FEEG1004 Electronics"
type: topic
stream: "Part B: Electronics"
order: 5
tags: [feeg1004, electronics, digital, logic-gates, boolean-algebra, de-morgan, karnaugh-map, nand]
aliases: ["EL4 digital logic 1", "Combinational logic", "Boolean algebra", "K-maps", "Logic gates"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: []
next_topics: ["[[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]"]
key_concepts: ["[[Boolean Algebra and De Morgan's Theorems]]", "[[Karnaugh Maps]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W11-EL4 Digital Logic 1 Combinational - Interactive.pdf"]
---

# FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps

> [!abstract] Summary
> Digital circuits use two levels (TTL: '1' > 2 V, '0' < 0.8 V), so data survives noise.
> - **Combinational** logic: the output depends only on the **present** inputs.
> - Design flow: specification → **truth table** → **sum of products** → simplify by **Boolean algebra** or a **Karnaugh map** → gates.
> - **De Morgan** ("break the line, change the sign") and the **universal** NAND/NOR gates let any circuit be built from one gate type.

## Key Concepts
- [[Boolean Algebra and De Morgan's Theorems]] · [[Karnaugh Maps]]

---

## 1. Gates and truth tables (Mills §3.2.1)
![[ee_b5_logic_gates.png|1000]]

- $n$ inputs give $2^n$ rows. Fill the input columns by **counting in binary**.
- Each basic gate has an inverted twin: AND/NAND, OR/NOR, XOR/XNOR, and NOT.
- A bubble on an output means inversion.
- Notation: $A\cdot B$ is AND, $A + B$ is OR, $\overline A$ is NOT, $A\oplus B$ is XOR.

> [!example] Vehicle safety interlock and chemical alarm (Mills)
> - **Interlock**: the engine may start only if the door is closed AND the belt is fastened: $F = A\cdot B$, a single AND gate.
> - **Alarm** (Ex. 1): it sounds if the temperature is high OR the pressure is high OR the materials are low: $F = A + B + \overline C$.

## 2. Sum of products from a truth table (§3.2.2)
- For each row with $F = 1$, write the AND of the inputs, complemented where the input is 0. Then OR the rows together.
- Mills Ex. 2 gives $F = A\overline B\,\overline C + AB\overline C + \overline A\,\overline BC + \overline ABC$. By algebra (Ex. 3) this factors to $A\overline C + \overline AC = A\oplus C$: **the output does not depend on B**.

## 3. Boolean identities (§3.2.3, W11)
| Name | OR form | AND form |
|---|---|---|
| Dominance | $A + 1 = 1$ | $A\cdot0 = 0$ |
| Identity | $A + 0 = A$ | $A\cdot1 = A$ |
| Idempotence | $A + A = A$ | $A\cdot A = A$ |
| Complementarity | $A + \overline A = 1$ | $A\cdot\overline A = 0$ |
| Commutative / associative | as in ordinary algebra | as in ordinary algebra |
| Distributive | $A + BC = (A + B)(A + C)$ ⚠ | $A(B + C) = AB + AC$ |
| Absorption | $A + AB = A$ | $A(A + B) = A$ |
| De Morgan | $\overline{A + B} = \overline A\cdot\overline B$ | $\overline{A\cdot B} = \overline A + \overline B$ |
| XOR | $A\oplus B = A\overline B + \overline AB$ | |
| Involution | $\overline{\overline A} = A$ | |

- Replace AND with × and OR with +: most identities look like normal algebra. The **exceptions** are the traps: OR-dominance ($A + 1 = 1$), idempotence and **OR-distributivity** (the one most often forgotten).
- **Typical steps**: write XOR in full → multiply out or factorise → De Morgan → cancel double NOTs → absorption.

> [!example] Mills Ex. 4: a three-gate circuit that is really just $F = A$
> Write the gate outputs on the diagram, then expand the brackets (distributivity). Apply identity ($A\cdot A = A$) and OR-dominance ($A(1 + C) = A$), then De Morgan and complementarity. Every term except $A$ vanishes, so the other gates are redundant.

## 4. Karnaugh maps (§3.2.5–3.2.6)
- Lay the SOP out on a grid whose axes follow the **Gray code** 00, 01, 11, 10: adjacent cells differ in **one** variable.
- The map **wraps around** (it is a torus): left edge meets right, top meets bottom.
- **Group** adjacent 1s in rectangles of $2^n$ (1, 2, 4, 8). Make groups **as large and as few as possible**; they may overlap. No diagonals.
- Each group becomes one product term containing only the variables that **do not change** within it. Grouping is exactly factoring out $(B + \overline B) = 1$.

![[ee_b5_karnaugh_maps.png|1000]]

> [!example] Worked maps
> - **Mills Ex. 5**: expand the lone two-variable term (e.g. $X\cdot C = X\cdot C\cdot(B + \overline B)$) so every term is a minterm. A repeated minterm is simply ignored. Two groups of two remain, each eliminating the variable that changes inside it, giving a **two-term** answer.
> - **Mills Ex. 6**: a group of four gives $F = C$.
> - **Mills Ex. 7**: $AB + C\overline D + C + B\overline CD$ gives the three-term result $F = AB + C + D$. Terms go straight onto the map: $AB$ fills the $AB = 11$ column, $C$ fills the bottom two rows.
> - **W11 hint**: expand a missing variable with $AB = AB(C + \overline C)$ to place a term on the map.

## 5. NAND/NOR-only circuits (Mills Ex. 8)
- NAND and NOR are **universal**: any function can be built from one type. That is cheaper and simpler because an IC contains several identical gates.
- Recipe:
  1. Apply De Morgan to remove ORs.
  2. **Double-invert** the whole expression.
  3. Read the result off as NAND gates.
  4. Tie a gate's inputs together to make an inverter (idempotence).
- Example: $F = AB + C + D = \overline{\overline{AB}\cdot\overline C\cdot\overline D}$.

## 6. Logic families (§3.4)
| Family | Built from | Pros | Cons |
|---|---|---|---|
| TTL | BJTs | common, fast, cheap | high power |
| CMOS | complementary n/p MOSFET pairs | very low power, dense (LSI) | relatively slow |
| ECL | BJTs (non-saturating) | fastest | high power, low noise immunity |

## Year 2 bridge
- Flight software and **safety interlocks** (arming logic, fault-detection voting) are Boolean functions. Triple-modular redundancy uses the majority function $AB + BC + CA$.
- **Digital filtering and data handling** start where the ADC hands over bits ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]], [[Digital Filtering]]).
- Telemetry quality is measured in **bit errors** ([[Bit Error Rate and Eb-N0]], [[SESA2024 09 - Communications]]).

## Links
- Previous: [[FEEG1004 B4 - Operational Amplifiers]] · Next: [[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]
- Worked problems: [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions]] (Q2–Q4)

## Sources
- Mills notes §3.1–3.2, 3.4; Week 11 interactive session (EL4).
