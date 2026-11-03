---
title: "Friction and Heat Addition in Constant-Area Ducts"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["Fanno flow", "Rayleigh flow", "thermal choking", "frictional choking"]
tags: [sesa2023, concept, compressible-flow]
status: complete
parent_lectures: ["[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]"]
related_concepts: ["[[Critical Conditions and Choked Flow]]", "[[Normal Shock Waves]]", "[[Entropy Change of a Perfect Gas]]"]
sources: ["02 - Sources/Lectures/Week 04 - Gas Dynamics II - Friction, Heat Transfer, Oblique Shocks and Intakes.pdf"]
---

# Friction and Heat Addition in Constant-Area Ducts

Steady one-dimensional flow in a constant-area duct with a dimensionless friction $f$ and heating $q$ obeys

$$
\rho_1u_1 = \rho_2u_2,\quad p_1(1+\gamma M_1^2-f) = p_2(1+\gamma M_2^2),\quad h_1\Big(1+\tfrac{\gamma-1}{2}M_1^2+q\Big) = h_2\Big(1+\tfrac{\gamma-1}{2}M_2^2\Big).
$$

Both friction and heating drive the flow towards $M = 1$. Subsonic flow accelerates while its pressure and density fall; supersonic flow decelerates while $p$, $\rho$ and $T$ rise, or, if the back pressure is high, jumps to subsonic through a normal shock. For each inlet Mach number there is a maximum $f$ or $q$ that brings the outlet to $M_2 = 1$, and adding more forces the upstream flow to change, reducing the mass flow. This is the frictional (Fanno) or thermal (Rayleigh) version of nozzle choking. Cooling ($q<0$) does the opposite and always has a solution: it accelerates supersonic flow and decelerates subsonic flow.

There is one exception worth knowing for temperature: heating subsonic flow with $1/\gamma<M^2<1$ lowers $T$, because most of the heat goes into kinetic energy. Friction always lowers $p_0$ as entropy rises, and subsonic outlets with $M_2>1$ are inaccessible because they would need $\Delta s<0$. Physically, the growing displacement thickness of the boundary layer acts like a converging nozzle.

These results matter for engines because heat release in a ramjet or scramjet combustor is Rayleigh-like, which is why the combustor's $\Gamma_c<1$ even without friction, and too much heat at a supersonic combustor inlet causes thermal choking (unstart).

![[prop_duct_friction_heating.png|700]]

## Related

- [[Critical Conditions and Choked Flow]] · [[Normal Shock Waves]] · [[Entropy Change of a Perfect Gas]]
