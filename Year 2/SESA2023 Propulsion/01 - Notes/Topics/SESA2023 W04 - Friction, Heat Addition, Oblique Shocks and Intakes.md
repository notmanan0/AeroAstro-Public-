---
title: "SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 1: Introduction and Fundamentals"
order: 4
tags:
  - sesa2023
  - compressible-flow
  - oblique-shock
  - intakes
  - fanno-rayleigh
aliases: ["Gas dynamics II", "Intakes and diffusers"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]"]
next_topics: ["[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]"]
key_concepts: ["[[Friction and Heat Addition in Constant-Area Ducts]]", "[[Oblique Shock Waves]]", "[[Intake Pressure Recovery]]", "[[Normal Shock Waves]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 3 Solutions]]", "[[SESA2023 Problem Sheet 4 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 04 - Gas Dynamics II - Friction, Heat Transfer, Oblique Shocks and Intakes.pdf"]
---

# SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes

> [!abstract] Summary
> This week covers four non-isentropic extensions of W03:
> 1. **Friction** and **heat addition** in constant-area ducts both push the flow towards $M = 1$ and can choke it.
> 2. A **shock inside a C–D nozzle** is located by matching the mass flow either side.
> 3. **Oblique shocks** are normal shocks in the normal velocity component, $M_{n1} = M_1\sin\sigma$.
> 4. **Intakes** (diffusers) decelerate the flow to about M 0.4–0.5 with minimum stagnation-pressure loss. Subsonic intakes are gently divergent. Supersonic intakes use a normal shock (Pitot), several oblique shocks (external compression), or both (mixed compression).

## Key Concepts
- [[Friction and Heat Addition in Constant-Area Ducts]] · [[Oblique Shock Waves]] · [[Intake Pressure Recovery]] · [[Normal Shock Waves]]

---

## 1. Shock in a C–D nozzle (Lectures 10–11 example)
The nozzle has $p_0 = 400$ kPa, $T_0 = 800$ K, $A_t = 0.2$ m² and $A_e = 0.7$ m², with a shock at $M_1 = 2.44$.

1. **Sonic throat.** $T^* = 666.7$ K, $p^* = 211.3$ kPa, $\rho^* = 1.104$ kg/m³, $a^* = 517.6$ m/s, so $\dot m = \rho^*a^*A^* = 114.4$ kg/s.
2. **Just upstream of the shock.** $T_1 = 365.2$ K, $p_1 = 25.7$ kPa, $\rho_1 = 0.245$ kg/m³, $a_1 = 383.1$ m/s. Mass conservation gives $A_1 = \dot m/(\rho_1M_1a_1) = 0.499$ m². This matches $A/A^* = 2.49$ at M 2.44.
3. **Across the shock** (tables): $M_2 = 0.519$, $p_2/p_1 = 6.78$, $T_2/T_1 = 2.08$, $p_{02}/p_{01} = 0.523$.
4. **Continuing to the exit.** The new sonic reference area is $A_2^* = A_t/(p_{02}/p_{01}) = 0.382$ m². Then $A_e/A_2^* = 1.83$, which gives $M_e = 0.338$ on the subsonic branch and $p_e = 209.4/1.082 = 193$ kPa. This is the back pressure that puts the shock there.

## 2. Friction and heat addition in a constant-area duct
The governing equations are

$$
\rho_1u_1 = \rho_2u_2,\qquad p_1(1+\gamma M_1^2-f) = p_2(1+\gamma M_2^2),\qquad h_1\Big(1+\tfrac{\gamma-1}{2}M_1^2+q\Big) = h_2\Big(1+\tfrac{\gamma-1}{2}M_2^2\Big)
$$

Eliminating the thermodynamic variables gives a biquadratic in $M_2$:

$$
M_2^2 = \frac{-(1-2A\gamma)\pm\sqrt{1-2A(\gamma+1)}}{(\gamma-1)-2A\gamma^2},\qquad A = \frac{M_1^2\big[1+\tfrac{\gamma-1}{2}M_1^2+q\big]}{(1+\gamma M_1^2-f)^2}
$$

![[prop_duct_friction_heating.png|760]]

| | Subsonic inlet | Supersonic inlet |
|---|---|---|
| Friction $f>0$ | Accelerates towards M 1; $p$, $\rho$ fall | Decelerates towards M 1, with $p$, $\rho$, $T$ rising; or a normal shock to subsonic |
| Heating $q>0$ | Accelerates; $T$ usually rises (except $1/\gamma<M^2<1$) | Decelerates; or a shock |
| Cooling $q<0$ | Decelerates | Accelerates (always a solution) |

- **Choking**: for a given $M_1$ there is a maximum $f$ or $q$ that brings the exit to $M = 1$. Beyond it the upstream flow must adjust (the mass flow falls).
- $p_0$ always **falls** with friction.
- The friction boundary layer acts like a converging duct (displacement thickness grows).

## 3. Oblique shocks
The shock angle is $\sigma$ and the flow deflection $\delta$. The tangential velocity is unchanged, so this is a **normal shock in the normal component**:

$$
M_{n1} = M_1\sin\sigma>1,\qquad M_{n2} = M_2\sin(\sigma-\delta)<1
$$

$$
\tan\delta = 2\cot\sigma\frac{M_1^2\sin^2\sigma-1}{M_1^2(\gamma+\cos2\sigma)+2},\qquad \frac{\rho_2}{\rho_1} = \frac{\tan\sigma}{\tan(\sigma-\delta)}
$$

- For a given $M_1$ there is a **$\delta_{max}$**. Beyond it the shock **detaches** into a curved bow shock.
- Below $\delta_{max}$ there are two solutions. The **weak** one (smaller $\sigma$, usually supersonic downstream) is what forms on wedges. The **strong** one is always subsonic downstream.
- As $\delta\to0$, $\sigma\to\mu = \sin^{-1}(1/M_1)$ (the Mach angle).

![[prop_oblique_shock.png|680]]

> [!example] $M_1 = 3$, $\sigma = 50^\circ$, $p_1 = 101.325$ kPa, $T_1 = 288$ K
> - $M_{n1} = 2.30$ and $\delta = 28.9^\circ$.
> - Normal-shock tables at 2.30: $M_{n2} = 0.534$, so $M_2 = 0.534/\sin21.1^\circ = 1.48$.
> - $p_2 = 607$ kPa and $T_2 = 560$ K.

## 4. Intakes / diffusers (Lecture 12)
**Requirements**:
- decelerate the flow to M 0.4–0.5 and raise the static pressure;
- deliver **uniform** flow to the compressor (often more important than minimum loss);
- minimise the $p_0$ loss, external drag and weight;
- work at incidence and yaw.

**Subsonic intake** (all civil aircraft):
- It must diverge.
- Short is good for weight and friction loss, but a steep adverse pressure gradient separates the boundary layer.
- The half-angle is at most about 10°, typically 5–7°.

**Performance measures**:

$$
\Gamma_d = \frac{p_{02}}{p_{01}},\qquad \eta_d = \frac{T_{2s}-T_1}{T_2-T_1} = \frac{\Gamma_d^{(\gamma-1)/\gamma}\big(1+\tfrac{\gamma-1}{2}M^2\big)-1}{\tfrac{\gamma-1}{2}M^2}
$$

Here $T_{02} = T_{01}$ (adiabatic) and $p_2\approx p_{02} = \Gamma_dp_{01}$ (KE negligible after the diffuser).

> [!example] Subsonic intake at 6 km, M 0.85, 100 kg/s, exit M 0.4, $\eta_d = 0.9$, half-angle 6°
> - Inlet: $T_1 = 249.2$ K, $p_1 = 47.22$ kPa, $T_{01} = 285.2$ K, $p_{01} = 75.73$ kPa.
> - Loss: $T_{02s} = 249.2+0.9(36.0) = 281.6$ K, so $p_{02} = 72.43$ kPa ($\Gamma_d = 0.957$).
> - Exit: $T_2 = 276.4$ K, $p_2 = 64.87$ kPa, $\rho_2 = 0.818$ kg/m³.
> - Velocities and areas: $u_1 = 269$ m/s and $u_2 = 133.3$ m/s, so $A_1 = 0.563$ m² and $A_2 = 0.917$ m².
> - Diameters: $d_1 = 0.847$ m and $d_2 = 1.081$ m, so the length is $L = (r_2-r_1)/\tan6^\circ = 1.11$ m.

**Supersonic intakes**:
- A shock-free converging–diverging intake is only theoretical (it has a starting problem).
- **Normal-shock (Pitot) intake**: the lightest and simplest. The loss comes from the normal-shock $p_{02}/p_{01}$, which is under 10 % loss up to M ≈ 1.5, so it is acceptable up to M 1.7–1.8. If the engine needs less flow than design, the shock moves out and the excess spills (subcritical). A "supercritical" condition pulls the shock inside, where it is stronger and loses more $p_0$.
- **External compression with oblique shocks**: $n$ weak shocks plus a final weak normal shock lose less $p_0$ (as $n\to\infty$, $\Gamma_d\to1$). But the exit flow is increasingly inclined, which raises the subsonic-diffuser loss, so there is an optimum $n$. Used at high supersonic speed; no starting problem.
- **Mixed external/internal compression**: shorter and lighter, but performance is strongly Mach dependent.

See [[Intake Pressure Recovery]].

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]] · Next: [[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]
- Ramjet with an inlet normal shock: [[SESA2023 Problem Sheet 4 Solutions]] Q4.3
- Real-ramjet $\Gamma$ values: [[SESA2023 Exam 2018-19 Solutions]] Q4, [[SESA2023 Exam 2020-21 Solutions]] Q2, [[SESA2023 Exam 2023-24 Solutions]] Q2

## Sources
- Week 4 notes (two handouts) and Lectures 10–12; Kundu et al. *Fluid Mechanics* Ch. 16; NACA Report 1135
