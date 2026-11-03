---
title: "Dimensional Analysis of Turbomachines"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["similarity", "Buckingham pi", "non-dimensional mass flow", "corrected speed", "scaling laws", "fan laws"]
tags: [sesa2023, concept, turbomachinery, dimensional-analysis]
status: complete
parent_lectures: ["[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
related_concepts: ["[[Flow and Work Coefficients]]", "[[Specific Speed]]", "[[Compressor and Turbine Characteristics]]"]
sources: ["02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics.pdf"]
---

# Dimensional Analysis of Turbomachines

Geometrically similar turbomachines with similar streamline patterns, meaning similar velocity triangles, have equal values of all their dimensionless groups. For incompressible flow

$$
\frac{\Delta p}{\rho\Omega^2D^2},\ \eta,\ \frac{\dot W}{\rho\Omega^3D^5} = fn\left(\frac{Q}{\Omega D^3},\frac{\rho\Omega D^2}{\mu}\right),
$$

and for compressible flow

$$
\frac{p_{02}}{p_{01}},\ \frac{T_{02}}{T_{01}},\ \eta,\ \frac{\dot W}{\dot mc_pT_{01}} = fn\left(\frac{\dot m\sqrt{c_pT_{01}}}{D^2p_{01}},\frac{ND}{\sqrt{c_pT_{01}}},\gamma\right).
$$

The groups come from Buckingham's π theorem: $n$ variables in $m$ fundamental dimensions give $n-m$ groups. Incompressible, $Q$, $\Omega$, $D$, $\rho$ and $\mu$ give 5 − 3 = 2; compressible, $\dot m$, $\gamma$, $c_pT_{01}$, $D$, $N$ and $p_{01}$ (with $\mu$ dropped) give $\gamma$ plus two. The variables are chosen by a mental experiment: does changing this variable alone change the streamlines? Compressibility enters through the speed of sound, $a^2 = (\gamma-1)c_pT$, so $c_pT_{01}$ and $\gamma$ are needed, and $p_{01}$ is used rather than $\rho_{01}$ because it is easier to measure. The Reynolds number matters little above about $2\times10^5$, one or two points of efficiency per decade, which is an experimental fact; liquids also need a cavitation number. For one machine running on one gas, $D$, $c_p$ and $\gamma$ drop out, leaving $\dot m\sqrt{T_{01}}/p_{01}$ and $N/\sqrt{T_{01}}$, often referred to standard conditions as $\dot m\sqrt{\theta}/\delta$ and $N/\sqrt\theta$.

To scale a machine, hold every group equal:

$$
\frac{N_2D_2}{\sqrt{T_{01,2}}} = \frac{N_1D_1}{\sqrt{T_{01,1}}},\quad\frac{\dot m_2\sqrt{T_{01,2}}}{D_2^2p_{01,2}} = \frac{\dot m_1\sqrt{T_{01,1}}}{D_1^2p_{01,1}},\quad\frac{\dot W_2}{\dot m_2T_{01,2}} = \frac{\dot W_1}{\dot m_1T_{01,1}},
$$

so $\dot W\propto D^2p_{01}\sqrt{T_{01}}$ at the same non-dimensional operating point.

Worked values: a 1/10 hydraulic-turbine model at 10 m head and 3000 rpm, with $Q = 1.1$ m³/s and $\eta = 0.91$, scales to 948.7 rpm, 347.8 m³/s and 310.5 MW at full size and 100 m head ([[SESA2023 Problem Sheet 9 Solutions]] Q9.3). A compressor tested at 280 K, throttled to 0.1 bar, runs at 3864 rpm, and its measured 5 kg/s and 1.5 MW become 48.3 kg/s and 15.5 MW at design (Q9.4). A 1/5 scale model at 200 K matching a full-size machine at 300 K and 20,000 rpm runs at 81,650 rpm, with a power ratio of 30.6 at equal $p_{01}$ ([[SESA2023 Exam 2021-22 Solutions]] Q4).

## Related

- [[Flow and Work Coefficients]] · [[Specific Speed]] · [[Compressor and Turbine Characteristics]]
