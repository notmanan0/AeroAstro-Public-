---
title: "Classification of Differential Equations"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["ODE classification", "Linear ODE", "Order of an ODE", "Homogeneous ODE"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M06 - Differential Equations I]]"]
related_concepts: ["[[Separable First-Order ODEs]]", "[[Linear Differential Operators and Superposition]]", "[[PDE Classification]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.3", "MATH1054 Module Booklet, Module 6"]
---

# Classification of Differential Equations

A differential equation is classified by whether it is ordinary or partial, by its order (the highest derivative present), by whether it is linear in the dependent variable, and, if linear, by whether it is homogeneous (every term contains the dependent variable) or inhomogeneous (some term is a forcing function of the independent variable alone).

An **ordinary** differential equation (ODE) has one independent variable; a **partial** differential equation (PDE) has several and contains partial derivatives. The order ignores powers: $(\dot x)^2+4\dot x=0$ is first order because its highest derivative is $\dot x$. An $n$th-order equation is **linear** if it can be written as

$$
a_n(t)x^{(n)}+\dots+a_1(t)\dot x+a_0(t)x=f(t),
$$

so the dependent variable and its derivatives appear only to the first power, are never multiplied together, and never sit inside a function. The coefficients may depend on the **independent** variable without breaking linearity, so $\ddot x+t\dot x=4\sin t$ is linear; nonlinearity comes from the dependent variable, through terms such as $\dot x^2$, $x\dot x$, $\ddot x\,\dot x$ or $\sin x$. A linear equation is **homogeneous** if $f(t)\equiv0$ and **inhomogeneous** (nonhomogeneous) otherwise.

The classification matters because linearity is what makes superposition work. Writing the left-hand side as $L[x]$, differentiation splits over sums, so

$$
\begin{aligned}
L[\alpha x_1+\beta x_2]&=\sum_k a_k(t)\big(\alpha x_1^{(k)}+\beta x_2^{(k)}\big)\\
&=\alpha L[x_1]+\beta L[x_2],
\end{aligned}
$$

and any combination of solutions of $L[x]=0$ is again a solution. That property is behind every general solution built as $Ax_1+Bx_2$, and behind the complementary-function-plus-particular-integral method for inhomogeneous equations. A term like $x\dot x$ produces cross terms $x_1\dot x_2+x_2\dot x_1$ and breaks it. So the classification decides the method: separation for $\dot x=f(t)g(x)$, the auxiliary equation for linear constant-coefficient equations, and an integrating factor, exact-equation test or complementary function and particular integral in [[MATH1054 M12 - Differential Equations II|M12]] and [[MATH1054 M13 - Differential Equations III|M13]].

The order also predicts the size of the answer. An $n$th-order ODE normally has a general solution with $n$ arbitrary constants, and each independent initial or boundary condition removes one. Integrating $\ddot x=4t$ twice gives $x=\tfrac23t^3+At+B$; the single condition $x(0)=2$ fixes $B=2$ and leaves one constant.

For example, $\ddot s+(\sin t)\dot s+(t+\cos t)s=e^t$ (Exercise 2(b)) is a second-order linear inhomogeneous ODE with dependent variable $s$ and independent variable $t$: the coefficients $\sin t$ and $t+\cos t$ are allowed, and $e^t$ is the forcing. By contrast $p''p'+(\sin z)p=\ln z$ (Exercise 2(a)) is nonlinear because of the product $p''p'$. The wave equation $y_{xx}-y_{tt}=0$ (Specimen Test 6, Q1) is a linear, homogeneous, second-order PDE in $y(x,t)$.

The common trap is the word homogeneous. The first-order equation $\dot x=F(x/t)$ is also called homogeneous ([[Homogeneous First-Order ODEs]]), but that is a statement about scaling, not about forcing: $\dot x=(x^2+t^2)/(xt)$ is homogeneous in that sense and nonlinear, so it has no homogeneous/inhomogeneous label in the linear sense at all. A second trap is reading a power on a derivative as raising the order.

## Related

- Topics: [[MATH1054 M06 - Differential Equations I]] · [[MATH1054 M12 - Differential Equations II]] · [[MATH1054 M13 - Differential Equations III]]
- Concepts: [[Separable First-Order ODEs]] · [[Linear Differential Operators and Superposition]] · [[Homogeneous First-Order ODEs]] · [[Auxiliary Equation]] · [[PDE Classification]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §10.3; MATH1054 Module Booklet, Module 6 (work scheme items 3–7, Specimen Test 6 Q1)
