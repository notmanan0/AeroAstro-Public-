---
title: "SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 3
tags: [sesa1015, lift-curve, drag-polar, pitching-moment]
aliases: ["SESA1015 Mechanics 3", "Aerodynamic Characteristics"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]"]
next_topics: ["[[SESA1015 M04 - Steady Level Flight and Stall]]"]
key_concepts: ["[[Parabolic Drag Polar]]", "[[Dynamic Pressure and Aerodynamic Coefficients]]"]
tutorial_sheets: ["[[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Aerodynamic Coefficients.pptx", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar

> [!abstract] Summary
> Three plots form the basic aerodynamic model: $C_L$ against $\alpha$, $C_D$ against $C_L^2$, and $C_m$ against $\alpha$ or $C_L$. Their slopes and intercepts reveal lift effectiveness, zero-lift angle, parasite drag, induced-drag factor, trim and static stability. Data reduction is therefore not curve-fitting for its own sake: every fitted coefficient has a physical role in later performance equations.

## 1. Lift curve

Before stall, use the linear model

$$\boxed{C_L=C_{L_\alpha}(\alpha-\alpha_{L=0})}.$$

The slope $C_{L_\alpha}$ must be expressed consistently:

$$C_{L_\alpha}[\mathrm{rad^{-1}}]=\frac{180}{\pi}C_{L_\alpha}[\mathrm{deg^{-1}}].$$

A cambered aerofoil normally has $\alpha_{L=0}<0$. Stall breaks linearity; do not extrapolate the line to create an artificial $C_{L,max}$.

### Two-point reduction

From two measurements $(\alpha_1,C_{L1})$ and $(\alpha_2,C_{L2})$,

$$C_{L_\alpha}=\frac{C_{L2}-C_{L1}}{\alpha_2-\alpha_1},\qquad \alpha_{L=0}=\alpha_1-\frac{C_{L1}}{C_{L_\alpha}}.$$

With many points, linear regression is preferable and residuals should be inspected.

## 2. Drag polar

The elementary aircraft model is

$$\boxed{C_D=C_{D0}+kC_L^2}.$$

- $C_{D0}$ is the zero-lift/parasite-drag intercept.
- $kC_L^2$ represents lift-dependent induced drag.
- For a finite wing, $k\approx1/(\pi eAR)$.

Plotting $C_D$ against $C_L^2$ turns the model into a straight line: intercept $C_{D0}$, slope $k$.

![[mof_drag_polar.png|760]]

> [!warning] What the polar hides
> The parabolic polar is a useful subsonic, attached-flow approximation. Configuration change, Reynolds-number change, compressibility and stall can all move the curve.

## 3. Maximum lift-to-drag ratio

$$\frac LD=\frac{C_L}{C_{D0}+kC_L^2}.$$

Set the derivative with respect to $C_L$ to zero:

$$C_{D0}-kC_L^2=0.$$

Therefore

$$\boxed{C_{L,(L/D)_{max}}=\sqrt{\frac{C_{D0}}{k}}}$$

and the two drag components are equal at the optimum. Hence

$$\boxed{\left(\frac LD\right)_{max}=\frac{1}{2\sqrt{kC_{D0}}}}.$$

This is the tangent-from-origin property on a $C_D$–$C_L$ polar.

## 4. Pitching moment

In the linear range,

$$C_m=C_{m0}+C_{m_\alpha}\alpha$$

or equivalently

$$C_m=C_{m0}'+\frac{dC_m}{dC_L}C_L.$$

- $C_m=0$ is trim for the stated control setting.
- $C_{m_\alpha}<0$ indicates longitudinal static stability.
- A control deflection shifts the curve, changing the trim angle; it need not change the slope much.

The aerodynamic centre is a reference point about which moment is nearly constant with lift. The centre of pressure is the force application point that gives zero moment and may move rapidly near zero lift.

## 5. Wind-tunnel data reduction

For measured lift $L_t$, drag $D_t$ and moment $M_t$:

$$C_L=\frac{L_t}{qS},\qquad C_D=\frac{D_t}{qS},\qquad C_m=\frac{M_t}{qS\bar c}.$$

Then:

1. Fit $C_L$ versus $\alpha$ only over the visibly linear range.
2. Fit $C_D$ versus $C_L^2$ over the polar's useful range.
3. Fit $C_m$ versus $\alpha$ to locate trim and assess slope.
4. Quote units for slope and the test $Re,M$.
5. Treat an implausible intercept as a prompt to check tare corrections and reference dimensions.

## 6. Worked polar check

For $C_{D0}=0.025$ and $k=0.050$,

$$C_{L,MD}=\sqrt{0.025/0.050}=0.707,$$

$$\left(\frac LD\right)_{max}=\frac{1}{2\sqrt{(0.050)(0.025)}}\approx14.14.$$

At the optimum, $C_{D,i}=kC_L^2=0.025=C_{D0}$ and total $C_D=0.050$.

## 7. Configuration effects

- Flaps usually increase $C_{L,max}$ and $C_{D0}$ and shift the lift curve.
- Landing gear strongly increases parasite drag.
- Increasing aspect ratio reduces $k$ if span efficiency remains comparable.
- Surface contamination can lower $C_{L,max}$ and increase drag.

Never combine a clean $C_{D0}$ with a landing $C_{L,max}$ unless the model explicitly requests a mixed configuration.

## Year 2 bridge

- [[SESA2022 T2 - Boundary Layers]] explains profile drag and separation.
- [[SESA2022 T4 - Thin Aerofoil Theory]] derives the two-dimensional lift slope and moment.
- [[SESA2022 T5 - Finite Wing Theory]] derives downwash and induced drag.
- [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]] builds a full aircraft moment model from these data.

