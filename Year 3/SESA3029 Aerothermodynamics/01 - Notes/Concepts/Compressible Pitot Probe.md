---
title: "Compressible Pitot Probe"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 1: Basic Toolkit"
aliases: ["compressible Pitot tube", "Pitot probe regimes"]
tags: [sesa3029, concept, pitot-probe, compressible-flow]
status: complete
parent_lectures: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]"]
related_concepts: ["[[Stagnation Pressure and Pitot Tube]]", "[[Rayleigh Pitot Formula]]", "[[Normal-Shock Jump Relations]]"]
sources: ["02 - Sources/Lectures/Lecture1-3.pdf", "02 - Sources/Lectures/Lecture 1-3.txt"]
---

# Compressible Pitot Probe

## Definition

> [!note] Definition
> A forward-facing tube measures the pressure obtained by decelerating the incident flow to rest. A separate static tapping measures $p_1$. The measured stagnation pressure is $p_0$ in subsonic flow and $p_{02}$ behind the detached shock in supersonic flow.

## Regime selection

For air,

$$
\left.\frac{p_0}{p}\right|_{M=1}=1.8929.
$$

- If the measured ratio is below $1.8929$, use isentropic subsonic analysis.
- If it is above $1.8929$, use the [[Rayleigh Pitot Formula]] or a normal-shock table.

## Subsonic relation

$$
M_1^2=\frac{2}{\gamma-1}\left[\left(\frac{p_0}{p_1}\right)^{(\gamma-1)/\gamma}-1\right],
\qquad
U_1=M_1\sqrt{\gamma RT_1}.
$$

## Supersonic relation

The path is

$$
(p_1,M_1)\xrightarrow{\text{normal shock}}(p_2,M_2)
\xrightarrow{\text{isentropic deceleration}}p_{02}.
$$

Thus $p_{02}/p_1=(p_2/p_1)(p_{02}/p_2)$.

## Related

- [[Stagnation Pressure and Pitot Tube]] · [[Normal-Shock Jump Relations]] · [[Rayleigh Pitot Formula]]

