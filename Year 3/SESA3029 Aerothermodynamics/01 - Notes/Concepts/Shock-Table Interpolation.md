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

When the value you know falls between two rows of a shock or isentropic table, find how far between them it sits,

$$
\sigma=\frac{x_t-x_a}{x_b-x_a},
$$

and use that same fraction for every other column:

$$
y_t=y_a+\sigma(y_b-y_a).
$$

Before bracketing, make sure the known quantity is in the form the table uses. If the table lists $p/p_0$ and the question gives $p_0/p$, invert it first. Then pick the rows either side, compute $\sigma$ once, and apply it to $M$, $T_2/T_1$, $p_{02}/p_1$ or whatever else you need. Each answer should land between its two tabulated values, which is a quick check that you used the right rows.

> [!warning] Common error
> Don't round $\sigma$ early, and don't work out a fresh fraction for each output column. One $\sigma$ per row pair.

## Related

- [[Normal-Shock Jump Relations]] · [[Compressible Pitot Probe]]
