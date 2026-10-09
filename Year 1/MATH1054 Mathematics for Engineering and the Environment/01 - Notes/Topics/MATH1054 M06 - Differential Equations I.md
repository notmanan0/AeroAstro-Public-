---
title: "MATH1054 M06 - Differential Equations I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 3: Differential Equations"
order: 6
tags:
  - math1054
  - odes
  - separable
  - constant-coefficients
aliases: ["MATH1054 Module 6", "Differential Equations I"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M04 - Integration I]]", "[[MATH1054 M05 - Complex Numbers I]]"]
next_topics: ["[[MATH1054 M12 - Differential Equations II]]", "[[MATH1054 M13 - Differential Equations III]]"]
key_concepts: ["[[Classification of Differential Equations]]", "[[Separable First-Order ODEs]]", "[[Auxiliary Equation]]"]
tutorial_sheets: ["[[MATH1054 M06 Solutions - Differential Equations I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 6)", "02 - Sources/Modern Engineering Mathematics.pdf (§10.2–10.5, §10.9)"]
---

# MATH1054 M06 - Differential Equations I

> [!abstract] Summary
> A differential equation relates an unknown function to its derivatives. This first ODE module covers:
> - **Classification**: order, linearity, homogeneity. This tells you which methods are allowed.
> - **Counting constants**: an $n$th-order ODE has $n$ arbitrary constants, and each condition removes one.
> - **Direct integration**, when the right-hand side depends only on $t$.
> - **Separation of variables**, for $\dot x=f(t)g(x)$.
> - **Homogeneous linear constant-coefficient** second-order equations, via the auxiliary equation.
>
> M12 and M13 add integrating factors and forcing terms.

## Key Concepts
- [[Classification of Differential Equations]] · [[Separable First-Order ODEs]] · [[Auxiliary Equation]] · [[Damping Ratio and Natural Frequency]] (SESA2027)

---

## 1. Classification (James §10.3)
| Property | Test | Example |
|---|---|---|
| **Order** | highest derivative present | $(\dot x)^2+4\dot x=0$ is *first* order |
| **Linear** | $x,\dot x,\ddot x,\dots$ appear to power 1, not multiplied together, not inside functions | $\ddot x+t\dot x=4\sin t$ ✔; $\ddot x+x\dot x=\dots$ ✘ |
| **Homogeneous** (linear only) | every term contains $x$ or a derivative, with no pure-$t$ forcing | $4\dot x+(\sin t)x=0$ ✔ |
| **ODE / PDE** | one independent variable, or several (partial derivatives) | $y_{xx}-y_{tt}=0$ is a PDE |

The coefficients may depend on the **independent** variable without breaking linearity. What breaks linearity is nonlinear dependence on the **dependent** variable.

## 2. Solutions, constants and conditions (James §10.4)
- The **general solution** of an $n$th-order ODE contains $n$ arbitrary constants.
- **Initial-value problem (IVP)**: all conditions are at one point, e.g. $x(0),\dot x(0)$.
- **Boundary-value problem (BVP)**: conditions are at different points, e.g. $x(0)$ and $\dot x(\pi/\lambda)$.
- The number of constants left is the order minus the number of independent conditions (Ex 4).
- **Direct integration**: if $\dfrac{\mathrm d^nx}{\mathrm dt^n}=f(t)$, integrate $n$ times, adding a constant each time.

## 3. Separable first-order equations (James §10.5)

$$
\frac{\mathrm dx}{\mathrm dt}=f(t)\,g(x)\quad\Longrightarrow\quad\int\frac{\mathrm dx}{g(x)}=\int f(t)\,\mathrm dt+C
$$

1. Move all the $x$ terms to the left and all the $t$ terms to the right.
2. Integrate both sides, with **one** constant.
3. Apply the initial condition, then solve for $x$ if possible. Choose the $\pm$ sign from the initial data.
4. Look for any **lost solutions**, where $g(x)=0$ (e.g. $x\equiv0$ for $\dot x=6xt^2$).

> [!warning] Things that can go wrong
> - **Non-uniqueness**: if $g$ is singular at the initial point, as in Ex 14(a) with $x(0)=-2$ and $\dot x=\frac{t^2+1}{x+2}$, both square-root branches fit.
> - **Finite-time blow-up**: $\dot x=e^{x+t}$ gives $x=-\ln(1+e^{-a}-e^t)$, which escapes to infinity at $t=\ln(1+e^{-a})$. Nonlinear ODEs can do this; linear ones cannot.

## 4. Second-order linear, constant coefficients, homogeneous (James §10.9)

$$
a\ddot x+b\dot x+cx=0,\qquad x=e^{mt}\ \Rightarrow\ am^2+bm+c=0
$$

| Discriminant $b^2-4ac$ | Roots | General solution | Behaviour |
|---|---|---|---|
| $>0$ | $m_1\neq m_2$ real | $Ae^{m_1t}+Be^{m_2t}$ | over-damped / exponential |
| $=0$ | $m$ repeated | $(A+Bt)e^{mt}$ | critical |
| $<0$ | $\alpha\pm\mathrm j\beta$ | $e^{\alpha t}(A\cos\beta t+B\sin\beta t)$ | oscillatory; decays if $\alpha<0$ |

The complex case follows from [[Euler's Formula]] ([[MATH1054 M05 - Complex Numbers I|M05]]): $e^{(\alpha\pm\mathrm j\beta)t}=e^{\alpha t}(\cos\beta t\pm\mathrm j\sin\beta t)$.

![[m2048_ode_damping_regimes.png|600]]

> [!tip] Conditions at $t_0\neq0$
> Write the solution in powers of $(t-t_0)$, e.g. $x=[A+B(t-1)]e^{2(t-1)}$. The algebra for the constants then becomes trivial (Ex 59(b)).

See [[Auxiliary Equation]] (MATH2048) for why $te^{mt}$ appears for a repeated root.

## Method checklist
1. Classify the equation (order, linearity, homogeneity). This decides the method.
2. Pure $f(t)$ on the right-hand side: integrate directly.
3. First order, $f(t)g(x)$: separate.
4. Linear constant coefficients: auxiliary equation, then the table above.
5. Apply the conditions last, and count that the constants match the order.
6. Check by substituting back into the ODE.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M06 Solutions - Differential Equations I]]
- Next: [[MATH1054 M12 - Differential Equations II]] (homogeneous-type, exact, integrating factor) → [[MATH1054 M13 - Differential Equations III]] (linear operators, CF + PI, damping)
- Later: MATH2048 [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]

## Sources
- MATH1054 Module Booklet, Module 6; James §10.2–10.5, §10.9
