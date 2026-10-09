---
title: "SESA1015 M12 - Aircraft Constraint Analysis"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 12
tags: [sesa1015, constraint-analysis, aircraft-design, wing-loading]
aliases: ["SESA1015 Mechanics 12", "Aircraft Sizing Constraints"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M04 - Steady Level Flight and Stall]]", "[[SESA1015 M09 - Take-off and Landing Performance]]"]
next_topics: []
key_concepts: ["[[Aircraft Constraint Diagram]]", "[[Wing Loading]]"]
tutorial_sheets: ["[[SESA1015 T08 - Constraint Analysis Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Constraint Analysis.xlsx"]
---

# SESA1015 M12 - Aircraft Constraint Analysis

> [!abstract] Summary
> Constraint analysis converts performance requirements into a common design plane, usually thrust loading $T/W$ against wing loading $W/S$. Stall and landing set upper limits on wing loading; cruise, climb and take-off set lower bounds on thrust loading. Overlaying the boundaries exposes the feasible region and the cost of each requirement. It is a preliminary-sizing argument, not a final design.

## 1. Why these axes?

Wing loading $W/S$ controls the lift coefficient required at a given dynamic pressure:

$$C_L=\frac{W/S}{q}.$$

Thrust loading $T/W$ measures installed propulsive force relative to weight. Many flight equations reduce cleanly to these two ratios, allowing aircraft of different absolute size to be compared.

## 2. Stall constraint

At stall,

$$W=\frac12\rho V_s^2SC_{L,max}.$$

Therefore

$$\boxed{\frac WS\le\frac12\rho V_s^2C_{L,max}}.$$

On a $T/W$ versus $W/S$ plot, this is a vertical boundary. The feasible side is to the left.

## 3. Level-speed constraint

In level flight,

$$\frac TW=\frac DW=\frac{qSC_D}{W}.$$

Using $C_L=(W/S)/q$ and the parabolic polar,

$$\boxed{\frac TW=\frac{qC_{D0}}{W/S}+\frac{k(W/S)}q}.$$

The U-shaped boundary contains parasite and induced contributions. A maximum-speed requirement evaluates it at the specified $q$ and applies any propulsion lapse correction between design-point and flight condition.

## 4. Climb constraint

From steady climb,

$$\frac TW=\frac DW+\sin\gamma.$$

Hence the level-flight drag loading is shifted upward by the climb-gradient requirement. A rate-of-climb condition may be written using power or $ROC/V$:

$$\frac TW=\frac DW+\frac{ROC}{V}.$$

## 5. Take-off constraint

Take-off requirements are often rearranged into an approximate relation of the form

$$\frac TW\ge K_{TO}\frac{W/S}{\sigma C_{L,TO}s_{TO}}$$

where $K_{TO}$ collects units and model assumptions. The exact course expression should be used for numerical work. The trend is robust: larger wing loading needs more thrust loading for a fixed field length.

## 6. Landing constraint

Landing distance is often converted first into an allowable approach or stall speed and then into

$$\frac WS\le\frac12\rho V_{s,land}^2C_{L,max,land}.$$

Because landing weight differs from take-off weight, translate the boundary to the common reference weight:

$$\left(\frac WS\right)_{TO}=\frac{W_{TO}}{W_L}\left(\frac WS\right)_L.$$

## 7. Reading the map

![[mof_constraint_diagram.png|760]]

Each boundary has a feasible side:

- below a minimum thrust curve is infeasible;
- right of a maximum wing-loading line is infeasible;
- the final feasible region is the intersection of all acceptable half-planes.

A design point near high $W/S$ tends to reduce wing area but penalise low-speed performance. A design point near low $T/W$ reduces installed propulsion but leaves little performance margin.

## 8. Corrections before overlay

All constraints must refer to consistent quantities:

- same reference weight;
- installed sea-level-static or flight-condition thrust, with lapse factors;
- correct clean/take-off/landing drag polar and $C_{L,max}$;
- correct number of operating engines;
- consistent units.

> [!warning] A curve crossing is not automatically the design point
> The point still needs margin, technology realism, structural closure, volume, stability, cost and mission evaluation.

## 9. Workflow

1. Define the common axes and reference condition.
2. Derive each requirement independently.
3. Convert weight and thrust ratios to the common reference.
4. Mark the feasible side immediately.
5. Overlay all constraints.
6. Select a candidate with explicit margins.
7. Recover dimensional $S=W/(W/S)$ and $T=W(T/W)$.
8. Recheck the original performance equations.

## Year 2 bridge

- [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] improves propulsion and altitude corrections.
- [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]] adds trim and stability constraints.
- [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] supplies manoeuvre and transient requirements beyond steady sizing.

