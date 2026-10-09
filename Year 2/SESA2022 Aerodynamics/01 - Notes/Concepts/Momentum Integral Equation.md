---
title: "Momentum Integral Equation"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 2: Boundary Layers"
aliases: ["MIE", "von Karman momentum integral", "Kármán momentum integral"]
tags: [sesa2022, concept, boundary-layers]
status: complete
parent_lectures: ["[[SESA2022 T2 - Boundary Layers]]"]
related_concepts: ["[[Displacement and Momentum Thickness]]", "[[Virtual Origin Method]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf"]
---

# Momentum Integral Equation

## Definition

> [!note] Definition
> Von Kármán's momentum integral equation relates the streamwise growth of the momentum thickness to the wall shear stress and the pressure gradient:
>
> $$\frac{d\theta}{dx}+(2+H)\frac{\theta}{U_e}\frac{dU_e}{dx} = \frac{\tau_w}{\rho U_e^2} = \frac{C_f}{2}$$
>
> For a flat plate ($dU_e/dx = 0$) this reduces to $\boxed{C_f = 2\,d\theta/dx}$ and $D'(x) = \rho U_\infty^2\theta(x)$.

## Explanation
**Derivation (flat plate).** Take a control volume from the leading edge to station $x$, with its top at height $h>\delta$.
- **Mass**: the deficit $\int\rho(U_\infty-u)\,dy$ leaves through the top.
- **$x$-momentum**:

$$
-D' = \int\rho u^2dy+U_\infty\int\rho(U_\infty-u)dy-\rho U_\infty^2h\;\Rightarrow\;D' = \rho\int u(U_\infty-u)\,dy = \rho U_\infty^2\theta
$$

- Since $D' = \int_0^x\tau_w\,dx$, differentiating gives the MIE.

**Using it (the Pohlhausen-type method)**:
1. Assume a profile shape $u/U_\infty = f(y/\delta)$.
2. Compute $\theta/\delta$ and $\tau_w = \mu U_\infty f'(0)/\delta$.
3. Substitute into $C_f = 2\,d\theta/dx$ and solve the ODE for $\delta(x)$.

**Why it works even with crude profiles.** $\theta$ is an integral, so errors in the profile shape average out. For example, a linear profile gives $\theta/x = 0.577/\sqrt{Re_x}$ against Blasius's $0.664$.

## Examples
- Derivation from a CV: [[SESA2022 Exam 2016-17 Solutions]] Q3(iii) and [[SESA2022 Exam 2017-18 Solutions]] Q4.
- Parabolic profile giving $\theta/x = 0.73/\sqrt{Re_x}$: [[SESA2022 Exam 2024-25 Solutions]] Q1(b).
- Plate length from $\theta$ via $\int C_f\,dx$: [[SESA2022 Exam 2023-24 Solutions]] Q1(iv).

## Related
- Parent lectures: [[SESA2022 T2 - Boundary Layers]]
- Related concepts: [[Displacement and Momentum Thickness]], [[Virtual Origin Method]], [[Boundary Layer Separation]]

## Sources
- `02 - Sources/BL/Topic 2 Boundary layers.pdf`
