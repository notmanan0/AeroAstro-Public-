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

## Definition

> [!note] Definition
> Geometrically similar machines with **similar streamline patterns** (similar velocity triangles) have equal values of **all** dimensionless groups.
> - Incompressible: $\dfrac{\Delta p}{\rho\Omega^2D^2},\ \eta,\ \dfrac{\dot W}{\rho\Omega^3D^5} = fn\left(\dfrac{Q}{\Omega D^3},\dfrac{\rho\Omega D^2}{\mu}\right)$.
> - Compressible: $\dfrac{p_{02}}{p_{01}},\ \dfrac{T_{02}}{T_{01}},\ \eta,\ \dfrac{\dot W}{\dot mc_pT_{01}} = fn\left(\dfrac{\dot m\sqrt{c_pT_{01}}}{D^2p_{01}},\dfrac{ND}{\sqrt{c_pT_{01}}},\gamma\right)$.

## Explanation
- **Buckingham π**: $n$ variables in $m$ fundamental dimensions give $n-m$ groups.
  - Incompressible: $Q$, $\Omega$, $D$, $\rho$, $\mu$ is 5 − 3 = **2** groups.
  - Compressible: $\dot m$, $\gamma$, $c_pT_{01}$, $D$, $N$, $p_{01}$ ($\mu$ dropped) gives $\gamma$ plus 2 groups.
- **Choosing variables** by a mental experiment: does changing this variable alone change the streamlines? Compressibility enters through the speed of sound, $a^2 = (\gamma-1)c_pT$, so $c_pT_{01}$ and $\gamma$ are needed. $p_{01}$ is used instead of $\rho_{01}$ because it is easier to measure.
- **Reynolds number**: above $2\times10^5$ its effect is small (one or two points of $\eta$ per decade), a fact established by **experiment**. Liquids also need a cavitation number.
- **For one machine on one gas**: drop $D$, $c_p$ and $\gamma$, giving $\dot m\sqrt{T_{01}}/p_{01}$ and $N/\sqrt{T_{01}}$. These are often referred to standard conditions as $\dot m\sqrt{\theta}/\delta$ and $N/\sqrt\theta$.
- **Scaling recipe** (hold every group equal):

  $$\frac{N_2D_2}{\sqrt{T_{01,2}}} = \frac{N_1D_1}{\sqrt{T_{01,1}}},\quad\frac{\dot m_2\sqrt{T_{01,2}}}{D_2^2p_{01,2}} = \frac{\dot m_1\sqrt{T_{01,1}}}{D_1^2p_{01,1}},\quad\frac{\dot W_2}{\dot m_2T_{01,2}} = \frac{\dot W_1}{\dot m_1T_{01,1}}$$

  So $\dot W\propto D^2p_{01}\sqrt{T_{01}}$ at the same non-dimensional point.

## Examples
- Hydraulic turbine, 1/10 model at 10 m head and 3000 rpm, $Q = 1.1$ m³/s, $\eta = 0.91$. Full size at 100 m head: **948.7 rpm, 347.8 m³/s, 310.5 MW** ([[SESA2023 Problem Sheet 9 Solutions]] Q9.3).
- Compressor tested at 280 K (throttled to 0.1 bar): the test speed is 3864 rpm. The measured 5 kg/s and 1.5 MW become **48.3 kg/s and 15.5 MW** at design (Q9.4).
- 1/5 scale model at 200 K against full size at 300 K and 20,000 rpm: **81,650 rpm**. The power ratio at equal $p_{01}$ is **30.6** ([[SESA2023 Exam 2021-22 Solutions]] Q4).

## Related
- [[Flow and Work Coefficients]] · [[Specific Speed]] · [[Compressor and Turbine Characteristics]]

## Sources
- Week 9 handout §9.3, §9.5; Lectures 25–26
