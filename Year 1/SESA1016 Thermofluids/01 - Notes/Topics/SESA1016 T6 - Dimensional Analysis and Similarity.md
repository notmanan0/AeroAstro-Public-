---
title: "SESA1016 T6 - Dimensional Analysis and Similarity"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part B: Similarity and Fluid Fundamentals"
order: 6
tags: [sesa1016, dimensional-analysis, similarity, buckingham-pi]
aliases: ["Dimensional Analysis"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: []
next_topics: ["[[SESA1016 T7 - Fluid Properties and Viscosity]]"]
key_concepts: ["[[Buckingham Pi Theorem]]", "[[Reynolds Number]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 6.pdf"]
---

# SESA1016 T6 - Dimensional Analysis and Similarity

> [!abstract] Summary
> Dimensional analysis cannot replace physics, but it exposes impossible equations, reduces the number of experimental variables and shows how model tests transfer to full scale. Buckingham's theorem converts $n$ dimensional variables into $n-k$ dimensionless groups, where $k$ is the number of independent base dimensions represented.

## 1. Dimensions and homogeneity

Typical base dimensions are mass $M$, length $L$, time $T$ and temperature $\Theta$:

$$
[V]=LT^{-1},\quad [\rho]=ML^{-3},\quad [\mu]=ML^{-1}T^{-1},\quad [F]=MLT^{-2}
$$

Every additive term in a physical equation must have the same dimensions. A dimensional check can disprove an equation, but a dimensionally consistent equation may still be physically wrong or have a missing numerical constant.

## 2. Buckingham $\Pi$ theorem

If

$$
q=f(x_1,x_2,\ldots,x_{n-1})
$$

contains $n$ variables and $k$ independent base dimensions, it can be rewritten as

$$
\Pi_1=F(\Pi_2,\ldots,\Pi_{n-k}).
$$

![[tf_dimensional_similarity.png|720]]

### Repeating-variable method

1. List every physically relevant variable, including the dependent one.
2. Write each variable in base dimensions.
3. Count the dimensional rank $k$.
4. Choose $k$ repeating variables that together contain all base dimensions and are dimensionally independent.
5. Multiply each remaining variable by powers of the repeating variables.
6. Set the exponents of $M,L,T,\Theta$ to zero.
7. Interpret the groups and compare with known coefficients.

> [!warning] Repeating variables
> Do not choose two variables with identical dimensions, and do not choose a set that omits a base dimension. The dependent variable is normally excluded from the repeating set.

## 3. Example: drag on a body

Suppose $D=f(\rho,V,L,\mu)$. There are five variables and three base dimensions, giving two groups. Choose $\rho,V,L$:

$$
\Pi_1=\frac{D}{\rho V^2L^2},\qquad \Pi_2=\frac{\mu}{\rho VL}=Re^{-1}
$$

Equivalently:

$$
\boxed{C_D=F(Re)}
$$

The theorem cannot determine $F$; experiments, computation or further theory must do that.

## 4. Common dimensionless groups

| Group | Ratio represented | Dominant use |
|---|---|---|
| $Re=\rho VL/\mu$ | inertia / viscosity | transition, drag, pipe flow |
| $Ma=V/a$ | flow speed / sound speed | compressibility |
| $Fr=V/\sqrt{gL}$ | inertia / gravity | free surfaces, ships |
| $St=fL/V$ | unsteady / convective time | vortex shedding |
| $C_D=D/(\tfrac12\rho V^2A)$ | drag / dynamic-pressure force | external aerodynamics |
| $C_p=(p-p_\infty)/(\tfrac12\rho V^2)$ | pressure difference / dynamic pressure | pressure distributions |

## 5. Scale models

Similarity has three levels:

- **geometric**: all length ratios are equal;
- **kinematic**: corresponding velocity patterns scale consistently;
- **dynamic**: ratios of relevant forces match, expressed by equal $\Pi$ groups.

For Reynolds similarity:

$$
Re_m=Re_p\quad\Rightarrow\quad
\frac{\rho_mV_mL_m}{\mu_m}=\frac{\rho_pV_pL_p}{\mu_p}
$$

Once the relevant coefficients match, dimensional force is recovered from

$$
D=C_D\frac12\rho V^2A.
$$

Not every similarity condition can always be matched simultaneously; model testing then requires a justified compromise.

## 6. Reading log-log plots

If $y=Cx^n$, then

$$
\log y=\log C+n\log x
$$

so the slope is the exponent $n$. A change of slope indicates a regime change, not merely noisy data.

## Links

- Concept: [[Buckingham Pi Theorem]] · [[Reynolds Number]]
- Tutorial: [[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]]
- Continues in Propulsion: [[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]] · [[Dimensional Analysis of Turbomachines]]
- Next: [[SESA1016 T7 - Fluid Properties and Viscosity]]

## Sources

- `02 - Sources/Lectures/Chapter 6.pdf`, §§6.1-6.6.
