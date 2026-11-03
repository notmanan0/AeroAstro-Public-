---
title: "Electric Propulsion Sizing"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["electric propulsion", "EP", "characteristic velocity", "ion thruster", "resistojet", "arcjet", "specific power", "EP optimisation"]
tags: [sesa2024, concept, propulsion, electric-propulsion]
status: lectured
parent_lectures: ["[[SESA2024 07 - Spacecraft Propulsion]]"]
related_concepts: ["[[Chemical Propulsion Systems]]", "[[Tsiolkovsky Rocket Equation]]", "[[Spacecraft Power Sources]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture Chapter 7 - Propulsion - prerecorded material.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-16.txt"]
---

# Electric Propulsion Sizing

Electric propulsion (EP) accelerates propellant with electrical power, reaching specific impulses of thousands of seconds at very low thrust; because its power plant mass grows with the square of the exhaust velocity, the exhaust velocity has an optimum rather than "the higher the better".

The thruster families are electrothermal (resistojets, up to about 700 s at an efficiency of 0.9; arcjets, 450–1500 s at about 0.3), electromagnetic (Lorentz-force plasma accelerators, short-lived) and electrostatic (gridded ion thrusters, the most efficient, limited by grid erosion and the neutraliser). The electrical power for thrust $T$ is $W=TV_{ex}/(2\eta)$, so at fixed thrust the power rises with $I_{sp}$.

To size a spacecraft, split it into propellant $M_e$, power plant $M_W$ and payload $M_p$. With specific power $\beta=W/M_W$, efficiency $\eta$, burn time $t_b$ and constant mass flow, the jet-power balance gives $M_W=M_e(V_{ex}/V_c)^2$ with the characteristic velocity

$$
V_c=\sqrt{2\eta\beta t_b}.
$$

Putting $x=V_{ex}/V_c$ and $p=M_p/M_0$ into the rocket equation,

$$
\frac{\Delta V}{V_c}=x\ln\frac{1+x^2}{x^2+p},\qquad M_e=\frac{M_0-M_p}{1+x^2},\qquad M_W=x^2M_e.
$$

Each curve peaks: at $p=0.1$ the optimum is $x=0.633$ with $\Delta V/V_c=0.651$, at $p=0.5$ it is $x=0.849$ with 0.291. Since $\eta\le1$ and $\beta$ is physically limited, a large $V_c$ comes from a long burn, which is why EP missions thrust for months or years. The course example, a 3000 kg Pluto orbiter needing 17 km/s, comes out at about 1700 s, 1.9 t of propellant, a 4.2 kW RTG power plant of about 770 kg, and 0.5 N of thrust for two years.

![[ast_ep_optimisation.png|560]]

## Related

- [[SESA2024 07 - Spacecraft Propulsion#4. Electric propulsion|Electric propulsion in the lecture note]] · [[SESA2024 07 - Spacecraft Propulsion#Pluto orbiter by electric propulsion|Pluto worked example]]
- [[Chemical Propulsion Systems]] · [[Tsiolkovsky Rocket Equation]] · [[Spacecraft Power Sources]]
