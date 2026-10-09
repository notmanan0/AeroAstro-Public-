---
title: "SESA1015 M06 - Jet Aircraft Range and Endurance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 6
tags: [sesa1015, jet, range, endurance, breguet]
aliases: ["SESA1015 Mechanics 6", "Jet Range and Endurance"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
next_topics: ["[[SESA1015 M07 - Propeller Aircraft Range and Endurance]]"]
key_concepts: ["[[Breguet Range Equation]]", "[[Minimum Drag and Minimum Power]]"]
tutorial_sheets: ["[[SESA1015 T04 - Range and Endurance Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M06 - Jet Aircraft Range and Endurance

> [!abstract] Summary
> Range is distance; endurance is time. Both emerge by integrating fuel burn as aircraft weight decreases. For a jet, fuel weight flow is proportional to thrust, so aerodynamic efficiency appears directly. Endurance favours maximum $L/D$, while constant-altitude maximum range favours a faster condition that maximises $\sqrt{C_L}/C_D$. The logarithmic mass-ratio term means extra fuel gives diminishing incremental benefit while adding take-off weight and structural demand.

## 1. Fuel-flow model

Define weight-based thrust-specific fuel consumption

$$c_T=-\frac{\dot W}{T}.$$

In steady flight $T=D$, so

$$dt=-\frac{dW}{c_TD}=-\frac{1}{c_T}\frac LD\frac{dW}{W}.$$

The derivation assumes $c_T$ and the chosen aerodynamic condition remain approximately constant.

## 2. Endurance

Integrate from initial weight $W_i$ to final weight $W_f$:

$$\boxed{E_j=\frac{1}{c_T}\frac LD\ln\frac{W_i}{W_f}}.$$

Maximum ideal jet endurance therefore uses

$$\max\frac LD\quad\Rightarrow\quad C_L=\sqrt{\frac{C_{D0}}k}.$$

## 3. Constant-speed range / cruise climb

Distance increment is $dR=Vdt$. For constant $V$ and $L/D$,

$$\boxed{R_j=\frac{V}{c_T}\frac LD\ln\frac{W_i}{W_f}}.$$

If altitude is allowed to increase as weight falls, constant $V$ and $C_L$ can be approximately maintained by descending density. This is the idealised cruise climb.

## 4. Constant-altitude range

At fixed altitude and chosen $C_L$,

$$V=\sqrt{\frac{2W}{\rho SC_L}}.$$

Substitute into $dR=Vdt$ and integrate:

$$\boxed{R_j=\frac{2}{c_T}\sqrt{\frac{2}{\rho S}}\frac{\sqrt{C_L}}{C_D}\left(\sqrt{W_i}-\sqrt{W_f}\right)}.$$

The aerodynamic quantity to maximise is now $\sqrt{C_L}/C_D$, not $C_L/C_D$.

For $C_D=C_{D0}+kC_L^2$,

$$\boxed{C_{L,R_j}=\sqrt{\frac{C_{D0}}{3k}}}.$$

This is lower than $C_{L,MD}$ and hence occurs at a higher speed.

## 5. Why mass ratio is logarithmic

![[mof_breguet_mass_ratio.png|760]]

The first units of fuel are carried by the full aircraft and help to carry later fuel. Because the logarithm grows progressively more slowly, doubling fuel fraction does not double range. Structural mass, reserves, diversion and payload compete for the same take-off mass.

## 6. Altitude effects

In the ideal constant-altitude equation, range grows as $1/\sqrt\rho$ for unchanged $c_T$ and coefficients. Real trends also depend on:

- engine thrust lapse;
- variation of TSFC with altitude and Mach;
- compressibility drag;
- operational speed schedules;
- cabin, weather and airspace constraints.

The formula reveals mechanisms; it does not by itself select an operational cruise altitude.

## 7. Worked mass-ratio check

Suppose $V=230\ \mathrm{m,s^{-1}}$, $L/D=16$, $c_T=1.8\times10^{-4}\ \mathrm{s^{-1}}$ and $W_i/W_f=1.20$:

$$R=\frac{230}{1.8\times10^{-4}}(16)\ln(1.20)\approx3.73\times10^6\ \mathrm m.$$

So $R\approx3730\ \mathrm{km}$. A units check is decisive: $V/c_T$ has units of length.

## 8. Problem workflow

1. Identify whether the task asks for time or distance.
2. Identify the cruise law: constant altitude, speed, $C_L$, or angle of attack.
3. Convert mass-based fuel consumption to the convention used in the equation.
4. Keep $W_i/W_f$ dimensionless and ordered greater than one.
5. Use the optimum appropriate to that cruise law.
6. State neglected climb, acceleration, reserves and descent segments.

> [!failure] Common errors
> - Treating endurance and range as the same optimisation.
> - Using $\log_{10}$ instead of the natural logarithm.
> - Mixing kg/s fuel flow with a weight-based TSFC.
> - Subtracting weights where a ratio is required.

## Year 2 bridge

- [[Breguet Range Equation]] collects the propulsion forms and assumptions.
- [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] links range to engine efficiency, thrust and atmospheric state.
- [[SESA2022 T5 - Finite Wing Theory]] shows how aspect ratio improves $L/D$ through induced drag.

