---
title: "Velocity Triangles"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["vector diagrams", "relative velocity", "absolute frame", "rotating frame", "flow angles"]
tags: [sesa2023, concept, turbomachinery]
status: complete
parent_lectures: ["[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]"]
related_concepts: ["[[Euler Work Equation]]", "[[Degree of Reaction]]", "[[Flow and Work Coefficients]]", "[[Actuator Disk Theory]]"]
sources: ["02 - Sources/Lectures/Week 08 - Turbomachinery Principles.pdf"]
---
# Velocity Triangles

## Definition

> [!note] Definition
> The vector relation between absolute velocity $\mathbf V$, relative velocity $\mathbf V_{rel}$ and blade velocity $\mathbf U$: $\mathbf V = \mathbf V_{rel}+\mathbf U$. In components:
>
> $$V_x = V_{x,rel},\qquad V_{\theta,rel} = V_\theta-U,\qquad\tan\alpha = \frac{V_\theta}{V_x},\qquad\tan\alpha_{rel} = \frac{V_\theta-U}{V_x}$$

## Explanation
- Analyse **stators in the absolute frame** and **rotors in the relative frame**. The flow follows the blade metal: zero incidence at the inlet (design) and the Kutta condition at the exit (small deviation).
- **Sign convention**: angles from axial, positive in the direction of blade motion. Compressors typically have $\alpha>0$ and $\alpha_{rel}<0$.
- **Compressor**: the rotor turns the relative flow towards axial ($|\alpha_{rel}|$ falls), so $V_{rel}$ falls (diffusion) and $p$ rises. The absolute $V$ rises (work added). The stator turns the absolute flow back towards axial, so $V$ falls and $p$ rises.
- **Turbine**: the stator (NGV) accelerates the flow and swirls it. The rotor turns the relative flow further away from axial, so $V_{rel}$ rises (acceleration) and $p$ falls. The exit absolute swirl is small or negative.
- **Useful identities**:
  - $V_x/U = \dfrac{1}{\tan\alpha-\tan\alpha_{rel}}$
  - $\psi = \phi(\tan\alpha_2-\tan\alpha_1)$
  - static rise in the rotor $= \tfrac12(V_{1,rel}^2-V_{2,rel}^2)$; in the stator $= \tfrac12(V_2^2-V_3^2)$
- **Drawing tips**:
  1. Draw $U$ tangentially and $V_x$ axially.
  2. Draw the triangles at rotor inlet and exit sharing a common $V_x$.
  3. Label all four angles and all magnitudes.
  4. Sketch the blade sections so the metal angles match $\alpha_{rel}$ (rotor) and $\alpha$ (stator).

![[prop_compressor_velocity_triangles.png|700]]

## Examples
- **Lecture compressor** ($U = 300$, $\phi = 0.55$, $\psi = 0.45$, $\alpha_1 = 26^\circ$): $\alpha_{1,rel} = -53.1^\circ$, $\alpha_2 = 52.6^\circ$, $\alpha_{2,rel} = -27.1^\circ$.
- **2021-22 Q4** ($U = 280$, $\phi = 0.5$, $\psi = 0.4$, $\alpha_1 = 23^\circ$): $V_1 = 152$, $V_{1,rel} = 261$ m/s at $-57.6^\circ$; $V_2 = 221$ m/s at $50.8^\circ$, $V_{2,rel} = 177$ m/s at $-37.8^\circ$.
- **2022-23 Q4 turbine** ($V_x = 200$, $\alpha_2 = 60^\circ$, $U = 350$, $w = 100$ kJ/kg): rotor inlet metal angle $-1.0^\circ$, exit $-55.3^\circ$.

![[prop_e2223_q4_turbine_triangles.png|700]]

## Related
- [[Euler Work Equation]] · [[Degree of Reaction]] · [[Flow and Work Coefficients]] · [[Actuator Disk Theory]]

## Sources
- Week 8 handout §8.7; Lectures 24; PS8 Turbomachinery
