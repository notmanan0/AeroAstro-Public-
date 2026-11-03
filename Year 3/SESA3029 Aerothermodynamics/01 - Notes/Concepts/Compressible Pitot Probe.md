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

A forward-facing tube reads the pressure of the flow brought to rest at its mouth, and a separate static tapping reads $p_1$. In subsonic flow the tube reads the true stagnation pressure $p_0$. In supersonic flow a detached shock stands in front of it, so it reads $p_{02}$, the stagnation pressure behind that shock.

## Which regime?

The ratio the probe gives you tells you which analysis to use. For air, sonic flow corresponds to

$$
\left.\frac{p_0}{p}\right|_{M=1}=1.8929.
$$

A measured ratio below $1.8929$ means the flow is subsonic and isentropic deceleration applies. Above it, the flow is supersonic and you need the [[Rayleigh Pitot Formula]] or a normal-shock table.

## Subsonic case

The deceleration is isentropic all the way, so the isentropic stagnation relation inverts directly:

$$
M_1^2=\frac{2}{\gamma-1}\left[\left(\frac{p_0}{p_1}\right)^{(\gamma-1)/\gamma}-1\right],
\qquad
U_1=M_1\sqrt{\gamma RT_1}.
$$

## Supersonic case

The flow first crosses a normal shock (the centre of the detached bow shock) and then decelerates isentropically to the probe mouth:

$$
(p_1,M_1)\xrightarrow{\text{normal shock}}(p_2,M_2)
\xrightarrow{\text{isentropic deceleration}}p_{02}.
$$

So $p_{02}/p_1=(p_2/p_1)(p_{02}/p_2)$, which is what the Rayleigh formula packages into one expression in $M_1$.

## Related

- [[Stagnation Pressure and Pitot Tube]] · [[Normal-Shock Jump Relations]] · [[Rayleigh Pitot Formula]]
