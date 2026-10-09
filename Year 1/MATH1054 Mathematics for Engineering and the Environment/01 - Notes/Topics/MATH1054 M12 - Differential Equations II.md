---
title: "MATH1054 M12 - Differential Equations II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 3: Differential Equations"
order: 12
tags:
  - math1054
  - odes
  - first-order-odes
  - integrating-factor
aliases: ["MATH1054 Module 12", "Differential Equations II"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M06 - Differential Equations I]]", "[[MATH1054 M03 - Differentiation I]]"]
next_topics: ["[[MATH1054 M13 - Differential Equations III]]"]
key_concepts: ["[[Homogeneous First-Order ODEs]]", "[[Exact Differential Equations]]", "[[Integrating Factor Method]]"]
tutorial_sheets: ["[[MATH1054 M12 Solutions - Differential Equations II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 12)", "02 - Sources/Modern Engineering Mathematics.pdf (§10.5.2–10.5.4)"]
---

# MATH1054 M12 - Differential Equations II

> [!abstract] Summary
> This module adds three first-order techniques to the separable method of [[MATH1054 M06 - Differential Equations I|M06]]:
> - **homogeneous-type** equations $\dot x=F(x/t)$, via $x=vt$;
> - **exact** equations, where the ODE is the total derivative of some $F(x,t)$;
> - **linear** equations $\dot x+P(t)x=Q(t)$, via the **integrating factor**.
>
> The integrating factor is the most important of the three. It solves every first-order linear ODE, and it underpins RC/RL transients and first-order control systems.

## Key Concepts
- [[Homogeneous First-Order ODEs]] · [[Exact Differential Equations]] · [[Integrating Factor Method]] · [[Separable First-Order ODEs]]

---

## 1. Equations of the form $\dot x=F(x/t)$ (James §10.5.2)
**Test**: replace $x\to\lambda x$ and $t\to\lambda t$. If $\lambda$ cancels, the right-hand side depends only on $x/t$. Equivalently, every term in the numerator and denominator has the same total degree.

**Method**: put $x=vt$, so $\dot x=v+t\dot v$. The equation becomes $t\dot v=F(v)-v$, which is **separable**:
$$
\int\frac{\mathrm dv}{F(v)-v}=\ln t+C,\quad\text{then substitute }v=x/t.
$$

## 2. Exact equations (James §10.5.3)
$f(x,t)\,\dot x+g(x,t)=0$ is **exact** if there is an $F(x,t)$ with $F_x=f$ and $F_t=g$. Then the ODE says $\frac{\mathrm d}{\mathrm dt}F(x(t),t)=0$, so $F=C$.
$$
\text{Test:}\quad\frac{\partial f}{\partial t}=\frac{\partial g}{\partial x}\qquad\text{(equality of the mixed partials, }F_{xt}=F_{tx}\text{)}
$$
1. Integrate $f$ with respect to $x$, adding an unknown function $h(t)$.
2. Differentiate with respect to $t$, match to $g$, and find $h$.
3. Write $F(x,t)=C$. This is often left implicit.

The idea is identical to finding a potential for a conservative field in MATH2048 ([[Conservative Vector Fields]]).

## 3. Linear equations and the integrating factor (James §10.5.4)
$$
\dot x+P(t)x=Q(t)\qquad\xrightarrow{\ \times\,\mu=e^{\int P\,\mathrm dt}\ }\qquad\frac{\mathrm d}{\mathrm dt}(\mu x)=\mu Q\ \Rightarrow\ x=\frac1\mu\Big[\int\mu Q\,\mathrm dt+C\Big]
$$
- Put the equation in **standard form** first, with the coefficient of $\dot x$ equal to 1. For example, $t\dot x+2x=t\cos t$ becomes $\dot x+\frac2tx=\cos t$.
- **No constant** is needed in $\int P\,\mathrm dt$. Also, $e^{\pm\ln t}=t^{\pm1}$.
- The **structure of the solution** is $x=\underbrace{C/\mu}_{\text{transient (CF)}}+\underbrace{\tfrac1\mu\int\mu Q}_{\text{particular}}$. This previews the CF + PI split in [[MATH1054 M13 - Differential Equations III|M13]].

> [!example] Engineering: an RC circuit charging
> $RC\,\dot v+v=V_0$ gives $\mu=e^{t/RC}$, so $v=V_0(1-e^{-t/RC})$ when $v(0)=0$. See [[RC and RL Transients]] (FEEG1004).

## Method checklist
1. Is it separable? Do that first.
2. Is it linear in $x$? Use the integrating factor.
3. Is it $F(x/t)$? Put $x=vt$.
4. Does $f_t=g_x$? Then it is exact: find $F$.
5. Apply initial conditions **after** finding the general solution, and choose the $\pm$ root that fits the data.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M12 Solutions - Differential Equations II]]
- Prev: [[MATH1054 M06 - Differential Equations I]] · Next: [[MATH1054 M13 - Differential Equations III]]

## Sources
- MATH1054 Module Booklet, Module 12; James §10.5.2–10.5.4
