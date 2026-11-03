---
title: "Flow and Work Coefficients"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["flow coefficient", "stage loading coefficient", "work coefficient", "phi", "psi", "Smith chart", "number of stages"]
tags: [sesa2023, concept, turbomachinery]
status: complete
parent_lectures: ["[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
related_concepts: ["[[Euler Work Equation]]", "[[Velocity Triangles]]", "[[Dimensional Analysis of Turbomachines]]", "[[Specific Speed]]"]
sources: ["02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics.pdf"]
---

# Flow and Work Coefficients

The **flow coefficient** and the **stage loading** (work coefficient) are the two numbers that describe a turbomachine stage's velocity triangles:

$$
\phi = \frac{V_x}{U},\qquad\psi = \frac{|\Delta h_0|}{U^2} = \frac{\Delta V_\theta}{U} .
$$

$\phi$ fixes the relative inlet angle. At the design stage a low $\phi$ means highly staggered blades and a high $\phi$ low stagger. For a blade that has already been built, running below the design $\phi$ means positive incidence, towards stall and surge, and above it negative incidence, towards choke, so a machine is efficient only in a narrow band of $\phi$. Multistage compressors keep $V_x$ roughly constant by shrinking the blade height as the density rises.

$\psi$ measures how much the flow is turned. A high $\psi$ means fewer stages, with lower cost, weight and complexity, but lower efficiency. Compressors are limited to $\psi\le0.65$, typically 0.35–0.5, by boundary-layer separation and stall; turbines to $\psi\le2.5$, by high Mach numbers and shock losses. The number of stages follows as $n\ge\Delta h_{0,overall}/(\psi_{max}U^2)$, rounded up. For turbines the Smith chart plots efficiency contours on $(\phi,\psi)$, with a peak around $\phi\approx0.6$, $\psi\approx1$; raising $\psi$ roughly halves the stage count at the cost of a few points of efficiency. The blade speed $U$ is set from $\phi$ and the axial Mach number, for example with the Data Book flow function $V/\sqrt{c_pT_0}$, and fan tips are held below a relative Mach number of about 1.6 for noise, bird strike and blade-off reasons.

Worked values: at sea level and M 0.8, with M 0.6 into the rotor and $\phi = 0.55$, $U = 380.8$ m/s; a pressure ratio of 10 with $\psi\le0.4$ needs $n = 5.24$, so 6 stages. An HPC with $r_m = 0.267$ m at 185.6 rev/s ($U = 311$ m/s) and $\Delta h_0 = 469$ kJ/kg, with $\psi\le0.45$, needs 11 stages at $\psi = 0.440$ ([[SESA2023 Problem Sheet 9 Solutions]]). An LPT at fan speed ($U = 96$ m/s) and $\psi = 2.5$ needs 23 stages, and gearing it ×3 brings that down to 3 ([[SESA2023 Exam 2020-21 Solutions]] Q4).

## Related

- [[Euler Work Equation]] · [[Velocity Triangles]] · [[Dimensional Analysis of Turbomachines]] · [[Specific Speed]]
