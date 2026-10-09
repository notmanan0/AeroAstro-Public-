---
title: "Shock-Table Interpolation"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 1: Basic Toolkit"
aliases: ["normal-shock table interpolation", "IFT interpolation"]
tags: [sesa3029, concept, interpolation, shock-tables]
status: complete
parent_lectures: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]"]
related_concepts: ["[[Normal-Shock Jump Relations]]", "[[Stagnation Properties]]"]
sources: ["02 - Sources/Lectures/Lecture1-2.pdf", "02 - Sources/Lectures/Lecture1-3.pdf"]
---

# Shock-Table Interpolation

## Method

For a target value $x_t$ between table rows $a$ and $b$,

$$
\sigma=\frac{x_t-x_a}{x_b-x_a}.
$$

Use that same fractional position for every other column:

$$
y_t=y_a+\sigma(y_b-y_a).
$$

## Workflow

1. Identify the table and the column that contains the known quantity.
2. Convert ratios to the table convention. If the table lists $p/p_0$ but the question gives $p_0/p$, invert first.
3. Bracket the target with the nearest upper and lower rows.
4. Compute $\sigma$ once.
5. Apply it to $M$, $T_2/T_1$, $p_{02}/p_1$, or any other requested column.
6. Check that each interpolated value lies between its two tabulated values.

> [!warning] Common error
> Do not round $\sigma$ prematurely and do not recompute a different interpolation fraction for each output column.

## Related

- [[Normal-Shock Jump Relations]] · [[Compressible Pitot Probe]]

