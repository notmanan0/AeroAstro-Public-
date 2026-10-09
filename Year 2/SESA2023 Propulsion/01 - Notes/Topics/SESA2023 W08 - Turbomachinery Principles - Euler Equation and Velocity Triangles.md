---
title: "SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 4: Turbomachinery and Propellers"
order: 8
tags:
  - sesa2023
  - turbomachinery
  - euler-work-equation
  - velocity-triangles
aliases: ["Turbomachinery principles", "Velocity triangles"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]"]
next_topics: ["[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
key_concepts: ["[[Euler Work Equation]]", "[[Velocity Triangles]]", "[[Degree of Reaction]]", "[[Compressor Stall and Surge]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 8 Turbomachinery Solutions]]"]
sources: ["02 - Sources/Lectures/Week 08 - Turbomachinery Principles.pdf"]
---

# SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles

> [!abstract] Summary
> A turbomachine exchanges energy with a flow through a **change of angular momentum (swirl)** across a rotor. Newton's second law (torque = rate of change of $\dot m\,rV_\theta$) combined with the SFEE gives the **Euler work equation**, $\Delta h_0 = U_2V_{\theta2}-U_1V_{\theta1}$.
> - **Compressors** turn the flow *towards* axial. This diffuses the flow, raising pressure, but the adverse pressure gradient risks stall, so the pressure ratio per stage is under 2.
> - **Turbines** turn the flow *away* from axial. The flow accelerates, so a stage can take a pressure ratio of about 4.
>
> **Velocity triangles** convert between the stationary frame (stators) and the rotating frame (rotors, $V_{\theta,rel} = V_\theta-U$).

## Key Concepts
- [[Euler Work Equation]] · [[Velocity Triangles]] · [[Degree of Reaction]] · [[Compressor Stall and Surge]]

---

## 1. Turbomachines
- Energy is transferred by *steadily rotating* aerodynamic surfaces. This contrasts with positive-displacement machines (pistons), where an enclosed volume changes.
- Examples: jet-engine compressors and turbines, propellers, rocket turbopumps.
- **Axial** machines have negligible radial velocity. **Radial** machines have negligible axial velocity at the rotor inlet or outlet. A **centrifugal** impeller (turbocharger) takes axial flow in and sends radial flow out.
- Large gas turbines use **axial** machines for their best efficiency at high volume flow. Several stages give the pressure ratio. Small helicopter engines use centrifugal compressors (lower specific speed).

## 2. Euler work equation
A packet of mass $\delta m = \dot m\,dt$ carries angular momentum $\delta m\,rV_\theta$. So

$$
T = \dot m(r_2V_{\theta2}-r_1V_{\theta1}),\qquad \dot W_x = T\Omega = \dot m(U_2V_{\theta2}-U_1V_{\theta1}),\quad U = r\Omega
$$

Adiabatic flow with the SFEE ($\dot W_x = \dot m\Delta h_0$) gives

$$
\boxed{\Delta h_0 = U_2V_{\theta2}-U_1V_{\theta1}}\qquad\text{constant radius: }\Delta h_0 = U\Delta V_\theta = U(V_{\theta,rel,2}-V_{\theta,rel,1})
$$

It holds with **losses** too: they don't change the work, only the pressure change achieved. It also holds for compressible and unsteady-but-periodic flows. It needs the flow to be adiabatic, or $\Delta h_0$ is no longer the work.

> [!example] Centrifugal impeller: 10 kg/s, $r_2 = 0.1$ m, 20,000 rpm, radial vanes, no inlet swirl
> - $V_{\theta2} = U_2 = 0.1(2\pi\times20000/60) = 209.4$ m/s
> - $T = 10(0.1)(209.4) = 209.4$ N m
> - $\dot W = 10(209.4)^2 = 438.6$ kW, so $\Delta h_0 = 43.9$ kJ/kg

> [!example] Axial turbine: $r = 0.3$ m, $\Omega = 1000$ rad/s, $V_{\theta1} = 500$ m/s, $\Delta h_0 = -200$ kJ/kg
> $V_{\theta2} = 500-200000/300 = -167$ m/s. The flow leaves swirling **against** the blade motion.

## 3. Axial compressors and turbines
- **Compressor stage** = rotor + stator. The rotor does work: $V_\theta$ and $h_0$ rise. The stator removes swirl at constant $h_0$, so the KE falls and **static $p$ rises**. Across a stage, $p$ and $p_0$ rise while the velocity returns to about its starting value.
- **Inlet guide vanes** pre-swirl the flow in the direction of rotation to reduce the relative Mach number on the first rotor.
- **Compressor blades** turn the flow towards axial. The stream tube widens, the flow decelerates, and $p$ rises, but the boundary layer is at risk. High positive incidence (low flow, high speed) gives **stall** and **surge**. So a stage is limited to a pressure ratio under 2 and needs many stages.
- **Turbine stage** = stator (nozzle guide vanes) + rotor. The flow accelerates in both rows, with a favourable $dp/dx$ and thin boundary layers, so more turning is possible. One turbine stage can drive about **six compressor stages**.
- **Blade loading** falls with more stages or more blades per row, but that costs weight, cost and wetted area.
- **Blade anatomy**: hub, casing, root, tip, chord, **pitch** (the circumferential spacing $s$), span. Incidence $i = \alpha_{in}-\beta_{in}$ and deviation $\delta = \alpha_{out}-\beta_{out}$, where $\beta$ is the metal angle.
- The **mean-line (mid-span)** analysis assumes 2-D, steady, constant-radius flow. Downstream of a blade row $rV_\theta$ is conserved, and the Kutta condition fixes the exit angle.

## 4. Velocity triangles

$$
V_{x,rel} = V_x,\qquad V_{\theta,rel} = V_\theta-U,\qquad \tan\alpha = V_\theta/V_x,\qquad V = V_x/\cos\alpha
$$

Angles are measured from the axial direction and are **positive in the direction of blade motion**. Keeping $V_x$ ≈ constant through a machine requires the blade height to fall as density rises.

$$
\Delta h_0 = UV_x(\tan\alpha_2-\tan\alpha_1) = UV_x(\tan\alpha_{2,rel}-\tan\alpha_{1,rel})
$$

> [!example] Compressor repeating stage: $U = 300$ m/s, $\alpha_1 = \alpha_3 = 26^\circ$, $V_x = 0.55U = 165$ m/s, $\Delta h_0 = 0.45U^2 = 40.5$ kJ/kg
>
> | | Absolute | Relative |
> |---|---|---|
> | Rotor inlet | $V_{\theta1} = 80.5$, $V_1 = 183.6$ m/s, $\alpha_1 = 26^\circ$ | $V_{\theta1,rel} = -219.5$, $V_{1,rel} = 274.6$ m/s, $\alpha_{1,rel} = -53.1^\circ$ |
> | Rotor exit | $V_{\theta2} = 80.5+135 = 215.5$, $V_2 = 271.4$ m/s, $\alpha_2 = 52.6^\circ$ | $V_{\theta2,rel} = -84.5$, $V_{2,rel} = 185.4$ m/s, $\alpha_{2,rel} = -27.1^\circ$ |
>
> The absolute speed **rises** through the rotor (work input), but the **relative** speed falls, which is the diffusion that raises static pressure. The stator then does the same in the absolute frame.

![[prop_compressor_velocity_triangles.png|760]]

**Design choices**:
- **High $V_x$** gives power density, but it is limited by compressibility (relative tip Mach).
- **Repeating stages** ($V_3 = V_1$, $\alpha_3 = \alpha_1$) make each stage a scale model of the next.
- **Mirror blading / 50 % reaction**: the stator is the mirror image of the rotor, so $\alpha_1 = -\alpha_{2,rel}$ and $\alpha_2 = -\alpha_{1,rel}$, and the static pressure rise is split equally. See [[Degree of Reaction]] and [[SESA2023 Problem Sheet 8 Turbomachinery Solutions]] Q8.3.

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]] · Next: [[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]
- Worked sheet: [[SESA2023 Problem Sheet 8 Turbomachinery Solutions]]
- Exams: [[SESA2023 Exam 2021-22 Solutions]] Q4, [[SESA2023 Exam 2022-23 Solutions]] Q4 (turbine), [[SESA2023 Exam 2024-25 Solutions]] Q4, [[SESA2023 Exam 2023-24 Solutions]] Q4 (propeller)

## Sources
- Week 8 handout (E. Richardson) and Lectures 22–24; Rolls-Royce, *The Jet Engine* (1992)
