---
title: "SESA1015 M05 - Minimum Drag, Power and Performance Curves"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 5
tags: [sesa1015, minimum-drag, minimum-power, performance]
aliases: ["SESA1015 Mechanics 5", "Minimum Drag and Power"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M04 - Steady Level Flight and Stall]]"]
next_topics: ["[[SESA1015 M06 - Jet Aircraft Range and Endurance]]"]
key_concepts: ["[[Minimum Drag and Minimum Power]]", "[[Parabolic Drag Polar]]"]
tutorial_sheets: ["[[SESA1015 T01 - Stall and Level-Flight Solutions]]", "[[SESA1015 T04 - Range and Endurance Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M05 - Minimum Drag, Power and Performance Curves

> [!abstract] Summary
> Thrust required is drag; power required is drag multiplied by speed. That extra factor of $V$ moves the optimum: minimum drag occurs where parasite and induced drag are equal, while minimum power occurs at a lower speed where induced drag is three times parasite drag. This distinction controls best glide, minimum sink, endurance and climb.

## 1. Thrust required

For level flight with a parabolic polar,

$$T_R=D=AV^2+\frac{B}{V^2},$$

where

$$A=\frac12\rho SC_{D0},\qquad B=\frac{2kW^2}{\rho S}.$$

Differentiate:

$$\frac{dD}{dV}=2AV-\frac{2B}{V^3}=0\quad\Rightarrow\quad AV^2=\frac{B}{V^2}.$$

Thus parasite and induced drag are equal at minimum drag.

$$C_{L,MD}=\sqrt{\frac{C_{D0}}k},\qquad V_{MD}=\sqrt{\frac{2W}{\rho SC_{L,MD}}}.$$

Also

$$D_{min}=2W\sqrt{kC_{D0}},\qquad \left(\frac LD\right)_{max}=\frac{W}{D_{min}}=\frac{1}{2\sqrt{kC_{D0}}}.$$

## 2. Power required

$$P_R=DV=AV^3+\frac BV.$$

Differentiate:

$$\frac{dP_R}{dV}=3AV^2-\frac{B}{V^2}=0.$$

So at minimum power,

$$\frac{B}{V^2}=3AV^2.$$

Induced drag is three times parasite drag, giving

$$\boxed{C_{L,MP}=\sqrt{\frac{3C_{D0}}k}=\sqrt3\,C_{L,MD}}$$

and

$$\boxed{V_{MP}=3^{-1/4}V_{MD}\approx0.760V_{MD}}.$$

![[mof_power_required_speed.png|760]]

## 3. What each optimum means

| Quantity optimised | Condition | Operational meaning in the ideal model |
|---|---|---|
| minimum drag | maximum $L/D$ | best glide angle; jet endurance |
| minimum power | maximum $C_L^{3/2}/C_D$ | minimum sink; propeller endurance |
| maximum $\sqrt{C_L}/C_D$ | $C_L=\sqrt{C_{D0}/(3k)}$ | jet range at constant altitude |

> [!warning] One aircraft does not have one “best speed”
> The correct speed depends on the quantity being optimised, weight, density and configuration. Speeds change with $\sqrt{W/\rho}$ even when the optimum aerodynamic coefficient is unchanged.

## 4. Scaling laws

For any fixed target coefficient $C_L^*$,

$$V^*=\sqrt{\frac{2W}{\rho SC_L^*}}.$$

Therefore:

- optimum EAS changes with $\sqrt{W/S}$;
- optimum TAS also rises as $1/\sqrt\rho$;
- $D_{min}$ is proportional to weight but independent of density in this ideal model;
- power at the optimum depends on the speed and hence on density.

## 5. Thrust/power available intersections

Performance exists where the propulsion curve lies above the requirement curve.

- A jet engine is often introduced with approximately constant thrust available, so intersections are read on $T$–$V$ axes.
- A propeller/engine combination is often introduced with approximately constant shaft power and an efficiency, so intersections are clearer on $P$–$V$ axes.

Excess thrust controls climb angle:

$$T_A-T_R=W\sin\gamma.$$

Excess power controls rate of climb:

$$P_A-P_R=W\,ROC.$$

## 6. Worked comparison

Let $C_{D0}=0.028$, $k=0.045$, $W=60\ \mathrm{kN}$, $S=30\ \mathrm{m^2}$ and $\rho=1.225\ \mathrm{kg,m^{-3}}$.

$$C_{L,MD}=\sqrt{0.028/0.045}=0.789,$$

$$V_{MD}=\sqrt{\frac{2(60000)}{1.225(30)(0.789)}}\approx64.4\ \mathrm{m,s^{-1}}.$$

Then

$$V_{MP}=0.760(64.4)\approx48.9\ \mathrm{m,s^{-1}}.$$

Both answers must still be checked against stall and any operating limits.

## 7. Graph-reading workflow

1. Confirm whether the vertical axis is force or power.
2. Identify minimum requirement and the stall boundary.
3. Add the appropriate available curve.
4. Read intersections and reject inaccessible ones.
5. Use vertical gaps for excess thrust/power, not horizontal gaps.

## Year 2 bridge

- [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] supplies real engine performance and propulsive efficiency.
- [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]] shows why flying near a static performance optimum says nothing by itself about dynamic response.
