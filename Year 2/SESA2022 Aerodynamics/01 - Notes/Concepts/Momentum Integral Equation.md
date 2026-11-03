---
title: "Momentum Integral Equation"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 2: Boundary Layers"
aliases: ["MIE", "von Karman momentum integral", "Kármán momentum integral", "viscous drag coefficient"]
tags: [sesa2022, concept, boundary-layers]
status: complete
parent_lectures: ["[[SESA2022 T2 - Boundary Layers]]"]
related_concepts: ["[[Displacement and Momentum Thickness]]", "[[Virtual Origin Method]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf", "02 - Sources/Lectures/SESA2022 Lecture 5.txt … Lecture 10.txt (2025-26 transcripts)"]
---

# Momentum Integral Equation

Von Kármán's momentum integral equation relates the streamwise growth of the momentum thickness to the wall shear stress and the pressure gradient:

$$
\frac{d\theta}{dx}+(2+H)\frac{\theta}{U_e}\frac{dU_e}{dx} = \frac{\tau_w}{\rho U_e^2} = \frac{C_f}{2} .
$$

On a flat plate, $dU_e/dx = 0$, so it reduces to $C_f = 2\,d\theta/dx$, with drag $D'(x) = \rho U_\infty^2\theta(x)$.

The flat-plate version comes from a control volume running from the leading edge to station $x$, with its top at a height $h>\delta$. Mass conservation says the deficit $\int\rho(U_\infty-u)\,dy$ leaves through the top, and $x$-momentum then gives

$$
-D' = \int\rho u^2dy+U_\infty\int\rho(U_\infty-u)dy-\rho U_\infty^2h\;\Rightarrow\;D' = \rho\int u(U_\infty-u)\,dy = \rho U_\infty^2\theta .
$$

Since $D' = \int_0^x\tau_w\,dx$, differentiating with respect to $x$ gives the equation ([[SESA2022 Exam 2016-17 Solutions]] Q3(iii) and [[SESA2022 Exam 2017-18 Solutions]] Q4 ask for this derivation).

In use it is a Pohlhausen-type method. Assume a profile shape $u/U_\infty = f(y/\delta)$, compute $\theta/\delta$ and $\tau_w = \mu U_\infty f'(0)/\delta$, substitute into $C_f = 2\,d\theta/dx$ and solve the resulting ODE for $\delta(x)$. It works even with crude profiles because $\theta$ is an integral, so errors in the shape average out: a linear profile gives $\theta/x = 0.577/\sqrt{Re_x}$ against Blasius's 0.664, and the parabolic profile in [[SESA2022 Exam 2024-25 Solutions]] Q1(b) gives $0.73/\sqrt{Re_x}$. [[SESA2022 Exam 2023-24 Solutions]] Q1(iv) runs it backwards, finding a plate length from $\theta$ via $\int C_f\,dx$.

## Related

- Full derivation and worked examples: [[SESA2022 T2 - Boundary Layers#3. Momentum integral equation and drag|T2 §3]]
- [[Displacement and Momentum Thickness]] · [[Virtual Origin Method]] · [[Boundary Layer Separation]]
