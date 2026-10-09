---
title: "SESA1016 T8 - Hydrostatics"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part B: Similarity and Fluid Fundamentals"
order: 8
tags: [sesa1016, hydrostatics, pressure, buoyancy, manometer]
aliases: ["Fluids at Rest"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T7 - Fluid Properties and Viscosity]]"]
next_topics: ["[[SESA1016 T9 - Describing Flow and the Material Derivative]]"]
key_concepts: ["[[Pressure and Head]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 8.pdf"]
---

# SESA1016 T8 - Hydrostatics

> [!abstract] Summary
> A fluid at rest has no shear stress. Pressure acts normally and, at a point, equally in every direction. Balancing pressure against gravity gives $dp/dz=-\rho g$. That one differential equation explains pressure-depth variation, manometers, buoyancy and atmospheric stratification.

## 1. Pressure

$$
p=\lim_{A\to0}\frac{F_n}{A}
$$

Pressure is scalar; the pressure **force** is directional because it acts normal to a chosen surface. On a control surface with outward normal $\mathbf n$:

$$
d\mathbf F_p=-p\mathbf n\,dA.
$$

## 2. Pascal's law

Pressure applied to a confined static fluid is transmitted throughout it. A hydraulic jack gives

$$
\frac{F_1}{A_1}=\frac{F_2}{A_2}quad\Rightarrow\quad F_2=F_1\frac{A_2}{A_1}.
$$

Force is amplified, not energy: the large piston moves a correspondingly smaller distance because $A_1x_1=A_2x_2$.

## 3. Stevin's law

Take $z$ positive upward. Vertical force balance on a small fluid element gives

$$
\boxed{\frac{dp}{dz}=-\rho g}.
$$

For a constant-density liquid:

$$
p_2-p_1=\rho g(z_1-z_2)=\rho gh.
$$

Pressure depends only on vertical separation, not container shape.

![[tf_hydrostatics.png|720]]

## 4. Gauge and absolute pressure

$$
p_{abs}=p_{gauge}+p_{atm}.
$$

Manometers often give gauge pressure directly, but the ideal-gas law requires absolute pressure.

## 5. Manometer method

Choose one point and walk through connected static fluids:

- moving downward by $\Delta h$: add $\rho g\Delta h$;
- moving upward: subtract $\rho g\Delta h$;
- pressure is continuous across a stationary fluid-fluid interface.

Write every step rather than memorising a sign-specific formula.

## 6. Archimedes' principle

The net pressure force on a submerged body is upward and equals the weight of displaced fluid:

$$
\boxed{F_B=\rho_f gV_{disp}}.
$$

- floating equilibrium: $F_B=mg$;
- fraction submerged for a uniform floating body: $V_{disp}/V=\rho_{body}/\rho_f$;
- a fully submerged homogeneous body is neutrally buoyant when $\rho_{body}=\rho_f$.

## 7. Atmosphere

For an isothermal ideal-gas atmosphere, substitute $\rho=p/(RT)$ into hydrostatic balance:

$$
\frac{dp}{p}=-\frac{g}{RT}dz
\quad\Rightarrow\quad
p=p_0\exp\left[-\frac{g(z-z_0)}{RT}\right].
$$

If temperature varies, the differential equation must be integrated with the actual $T(z)$.

## 8. Hydrostatic force on a plane surface

For constant density, the resultant magnitude is

$$
F_R=\rho g h_cA,
$$

where $h_c$ is centroid depth. The centre of pressure lies below the centroid because pressure increases with depth.

## Links

- Concept: [[Pressure and Head]]
- Tutorial: [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]]
- Next: [[SESA1016 T9 - Describing Flow and the Material Derivative]]

## Sources

- `02 - Sources/Lectures/Chapter 8.pdf`, §§8.1-8.8.

